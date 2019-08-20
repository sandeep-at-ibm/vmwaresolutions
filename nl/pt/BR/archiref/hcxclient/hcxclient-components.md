---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# Glossário de componentes e termos do HCX
{: #hcxclient-components}

O HCX consiste em um lado da nuvem (ambiente de destino ou VCD) e em um ou mais clientes (origem). Uma instância do HCX deverá ser implementada por vCenter, mesmo se os
vCenters nos quais o HCX está implementado estiverem vinculados no mesmo domínio SSO no
lado do cliente ou da nuvem. As configurações suportadas pelo HCX são, uma para uma,
uma para muitas, muitas para uma e muitas para muitas.

## Lado do destino e lado do cliente
{: #hcxclient-components-cloud-client-side}

O HCX tem o conceito de lado da nuvem (ambiente de destino ou VCD) e de lado do cliente (origem).

- Lado do destino - o HCX Cloud Manager é pré-implementado e configurado com os perfis de rede e de cálculo prontos para criação do Service Mesh.  
- Lado do cliente - quaisquer instâncias do vSphere que atendam aos pré-requisitos para instalação e operação. O lado do cliente do HCX é o mestre que
controla a instância escrava do lado da nuvem por meio de seu snap-in da interface com o usuário (IU) do Web client
do vCenter.

## HCX Managers
{: #hcxclient-components-hcx-manager}

- O lado da nuvem - O HCX Cloud Manager está configurado para receber registro, gerenciamento e tráfego de controle do lado do cliente.
- O lado do cliente - O HCX Enterprise Manager é um arquivo de imagem OVA específico do lado do cliente que fornece a funcionalidade da IU para gerenciar e operar o HCX. O
gerenciador do HCX do lado do cliente é responsável pelo registro com o gerenciador do HCX
do lado da nuvem e pela criação de um plano de gerenciamento entre os lados do cliente e
da nuvem. Além disso, ele é responsável pela implementação de um Service Mesh no lado do cliente e por instruir o lado da nuvem a fazer o mesmo.

## Componentes do Service Mesh
{: #hcxclient-components-fleet}

Os componentes do HCX Service Mesh são responsáveis pela criação dos planos de dados e de controle entre os lados do cliente e da nuvem. Implementado como máquinas virtuais (VMs) em pares espelhados, o Service Mesh consiste nos componentes a seguir:

- Interconnect Appliance (HCX-IX) - O dispositivo de interconexão cria túneis criptografados que suportam tráfego vMotion e de replicação (migração em massa).
- WAN Optimizer Appliance (HCX-WAN) - O HCX inclui um dispositivo de otimização WAN Silver Peak™ implementado opcionalmente. Ele é implementado como um dispositivo da MV. Quando implementado,
o tráfego do túnel do CGW é redirecionado para atravessar o WAN Optimizer. Como o WAN Optimizer diminui significativamente o tráfego ao longo da WAN
(geralmente observa-se 3:1 a 6:1) enquanto aumenta a confiabilidade da conexão,
recomenda-se sempre implementar o WAN Optimizer com o CGW. O
benefício adicional de implementação do WAN Optimizer é estendido para limitar a
largura de banda da WAN consumida pelo tráfego de migração da MV. A interface de
gerenciamento do WAN Optimizer não é configurada por padrão.
- Extensão de rede (HCX-NE) - Fornece recursos de extensão de rede de Camada 2, permitindo migrações entre o local e o ambiente do vSphere com a necessidade de redesignar endereços IP às VMs.
- Host ESXi do Proxy - Sempre que o HCX-IX estiver configurado para se conectar ao site do HCX do lado da nuvem, um host ESXi do proxy aparecerá no vCenter fora de qualquer cluster. Esse host ESXi tem o mesmo endereço IP de gerenciamento e do vMotion que o dispositivo HCX-IX correspondente. Isso permite que o ambiente do
vSphere nos lados do cliente e da nuvem funcione como se estivesse
executando um vMotion local. Benefícios para este método:
  - Os intervalos de IP de gerenciamento em ambos os lados podem ser sobrepostos
sem perda de funcionalidade.
  - O lado da nuvem não tem visibilidade do vSphere no lado do cliente, tornando-o mais seguro.

## Portais do usuário do HCX
{: #hcxclient-components-hcx-user-portals}

- UI da web do cliente - O portal da web do cliente HCX é a IU principal para o HCX. Após o HCX Manager do lado do cliente ser instalado, ele será mostrado como um snap-in para a IU da web do vCenter. Ele controla o registro
do HCX da nuvem remota (emparelhamento de site), a implementação do componente de frota, o esticamento da rede e a migração da MV para dentro e para fora da nuvem.
- IU do lado da nuvem - A IU do HCX do lado da nuvem é acessível por meio da URL de registro
público fornecida para o registro do cliente HCX. Por padrão, ela usa as credenciais de Administrador do vCenter do lado da nuvem `administrator@vsphere.local`. Ela é usada geralmente para fazer upgrade da
instalação e modificar alguma configuração de rede.

## Links relacionados
{: #hcxclient-components-related}

* [Requisitos de acesso à porta para o VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req)
* [Preparando o ambiente de instalação](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Implementação do cliente HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Entrelaçamento de serviços HCX no local](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrações de nuvem híbrida do VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitorando parâmetros e componentes](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Resolução de problemas do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
