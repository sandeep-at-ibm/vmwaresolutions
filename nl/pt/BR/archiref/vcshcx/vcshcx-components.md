---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Glossário de componentes e termos do HCX
{: #vcshcx-components}

O HCX consiste em um lado da nuvem (destino) e em um ou mais clientes
(origem). Uma instância do HCX deverá ser implementada por vCenter, mesmo se os
vCenters nos quais o HCX está implementado estiverem vinculados no mesmo domínio SSO no
lado do cliente ou da nuvem. As configurações suportadas pelo HCX são, uma para uma,
uma para muitas, muitas para uma e muitas para muitas.

## Lado de nuvem e lado do cliente
{: #vcshcx-components-cloud-client-side}

O HCX tem o conceito de lado da nuvem (destino) e lado do cliente (origem).
- Lado da nuvem - vCenter Server on 	{{site.data.keyword.cloud}} with Hybridity Bundle. O lado da
nuvem do HCX é a instância escrava de um cliente HCX para o relacionamento em
nuvem. Ele é controlado pelo lado do cliente.
- Lado do cliente - Quaisquer instâncias do vSphere que atendam aos pré-requisitos
para instalação e operação. O lado do cliente do HCX é o mestre que
controla a instância escrava do lado da nuvem por meio de seu snap-in da interface com o usuário (IU) do Web client
do vCenter.

## Gerenciador de HCX
{: #vcshcx-components-hcx-manager}

- O gerenciador do HCX do lado da nuvem é a primeira parte de uma instalação do HCX
implementada no lado da nuvem pela automação do {{site.data.keyword.vmwaresolutions_short}}.
Inicialmente, é um único arquivo de imagem OVA implementado específico para o lado da
nuvem junto a um balanceador de carga-firewall de borda do NSX
configurado especificamente para a função do HCX. O gerenciador do HCX é configurado
para atender registro do lado do cliente recebido, gerenciamento e tráfego de
controle.
- O gerenciador do HCX do lado do cliente é um arquivo de imagem OVA específico do lado do cliente que fornece a funcionalidade da IU para gerenciar e operar o HCX. O
gerenciador do HCX do lado do cliente é responsável pelo registro com o gerenciador do HCX
do lado da nuvem e pela criação de um plano de gerenciamento entre os lados do cliente e
da nuvem. Além disso, ele é responsável por implementar componentes da
frota no lado do cliente e por instruir o lado da nuvem a fazer o
mesmo.

## Componentes de Frota
{: #vcshcx-components-fleet}

Os componentes de Frota do HCX são responsáveis por criar os planos de dados
e de controle entre os lados do cliente e da nuvem. Implementada como máquinas virtuais (MVs) em pares espelhados,
a frota consiste nos componentes a seguir:

- Cloud Gateway (CGW) - O Cloud Gateway é um componente opcional
responsável pela criação de túneis criptografados que suportam tráfego vMotion e
de replicação (migração em massa). Existe apenas um par por site de HCX
vinculado.
- Layer 2 Concentrator (L2C) - O Layer 2 Concentrator é um componente
opcional responsável pela criação de túneis criptografados para o plano de dados
e de controle correspondentes ao tráfego estendido da camada 2. Cada par de L2C
pode manipular até 4096 redes estendidas. Mais pares de L2C são
implementados conforme necessário. O recurso de largura de banda está limitado a ~4 Gbps, portanto, se
a capacidade da largura de banda externa for maior que 4 Gbps, o uso de
mais pares de L2C permitirá maior utilização da rede
subjacente.
- WAN Optimizer - O HCX inclui um dispositivo de otimização WAN Silver Peak™
opcionalmente implementado. Ele é implementado como um dispositivo da MV. Quando implementado,
o tráfego do túnel do CGW é redirecionado para atravessar o par do WAN Optimizer.
Como o WAN Optimizer diminui significativamente o tráfego ao longo da WAN
(geralmente observa-se 3:1 a 6:1) enquanto aumenta a confiabilidade da conexão,
recomenda-se sempre implementar o WAN Optimizer com o CGW. O
benefício adicional de implementação do WAN Optimizer é estendido para limitar a
largura de banda da WAN consumida pelo tráfego de migração da MV. A interface de
gerenciamento do WAN Optimizer não é configurada por padrão.
- Host ESX do proxy - Sempre que o CGW estiver configurado para se conectar ao site
do HCX do lado da nuvem, um host ESXi do proxy aparecerá no vCenter fora de qualquer
cluster. Esse host ESXi tem o mesmo endereço IP de gerenciamento e do vMotion
que o dispositivo CGW correspondente. Isso permite que o ambiente do
vSphere nos lados do cliente e da nuvem funcione como se estivesse
executando um vMotion local. Benefícios para este método:
    - Os intervalos de IP de gerenciamento em ambos os lados podem ser sobrepostos
sem perda de funcionalidade.
    - O lado da nuvem não tem visibilidade do vSphere no lado do cliente, tornando-o mais seguro.

## Portais do usuário do HCX
{: #vcshcx-components-hcx-user-portals}

- UI da web do cliente - O portal da web do cliente HCX é a IU principal para o HCX. Quando o gerenciador do HCX do lado do cliente é instalado, ele
aparece como um snap-in para a IU da web do vCenter. Ele controla o registro
do HCX da nuvem remota (emparelhamento de site), a implementação do componente de frota, o esticamento da rede e a migração da MV para dentro e para fora da nuvem.

- IU do lado da nuvem - A IU do HCX do lado da nuvem é acessível por meio da URL de registro
público fornecida para o registro do cliente HCX. Por padrão, ela
usa o login de SSO do vSphere do lado da nuvem (` administrator@vsphere.local`). Ela é usada geralmente para fazer upgrade da
instalação e modificar alguma configuração de rede. Ela também é usada
para construir redes virtuais dentro do HCX.

- IU de gerenciamento de dispositivo do gerenciador do HCX do cliente/nuvem - Acesse a
IU de gerenciamento de dispositivo do lado da nuvem ou do cliente por meio do
endereço IP privado da MV conforme visualizado no vCenter.
` https://<hcxmanager_IP>: 9443 `. O ID (geralmente "admin") e a senha
são fornecidos por meio do portal do {{site.data.keyword.vmwaresolutions_short}}. A IU de gerenciamento é
usada para iniciar e parar os serviços do HCX Manager, configurar o monitoramento de log,
a configuração básica de rede, os upgrades manuais, suportar a reunião de log
quando a IU da web não está funcionando, o registro com componentes do vSphere
(vCenter, PSC, NSX Manager) e o gerenciamento de certificado.

## Links relacionados
{: #vcshcx-components-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)   
