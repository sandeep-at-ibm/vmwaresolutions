---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# Preparando o ambiente de instalação
{: #hcxclient-planning-prep-install}

A instalação do VMware HCX on IBM Cloud tem os requisitos de software a seguir:
* vSphere 5.5 U3 ou vSphere 6.0u2 ou superior.
* Se o NSX for usado, versão 6.2.2 ou superior. O NSX é necessário para a migração de política.
* Para usar o cross-cloud vMotion, as mesmas restrições de afinidade se aplicam às nuvens como fazem no local. Para obter mais informações, veja o [FAQ do VMware EVC e de Compatibilidade da CPU](https://kb.vmware.com/s/article/1005764).

## Configurando a conectividade de rede
{: #hcxclient-planning-config-net}

O HCX deve atravessar a Internet pública e as linhas privadas e conectar-se a componentes do data center, como redes, comutadores e grupos de portas.
* Para obter informações sobre as portas que devem ser abertas para que os dispositivos virtuais HCX possam ser instalados com êxito, consulte [Requisitos de acesso à porta](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req).
* O ambiente do vSphere no local e o ambiente do VCS HCX Cloud devem permitir a sincronização de clock do Network Time Protocol (NTP) entre os dispositivos no local do vSphere e os dispositivos VCS HCX. A porta UDP 123 deve ser acessível a dispositivos virtuais e redes HCX.

## Ambiente no local
{: #hcxclient-planning-on-prem-env}

Antes de instalar o HCX, verifique se seu ambiente pode suportar as tarefas que você deseja realizar. O ambiente no local deve suportar as tarefas a seguir antes da instalação do HCX.
* Virtual Center com o vSphere 5.5 Atualização 3 ou 6.0 Atualização 2.
* O vMotion e os recursos de migração de política requerem o NSX versão 6.2.2 ou superior.
* Uma conta de serviço do vSphere com a função de sistema Administrador do vCenter Server designada a ele.
* No vCenter, espaço em disco suficiente para os dispositivos HCX a serem instalados.
* Endereços IP suficientes para as MVs locais provisionadas durante a instalação.
* Portas e firewalls abertos conforme necessário, como documentado em Requisitos de acesso à porta.
* Se o servidor de conexão única (SSO) for remoto, a URL do vCenter, do Servidor de SSO externo ou do Platform Services Controller (PSC) que executa o serviço de consulta externa deverá ser identificada. Quando o HCX Manager é registrado com o vCenter, essa URL deve ser fornecida.
* Se um vCenter não tiver sua própria instância interna do serviço de consulta, isso poderá ser por uma das razões a seguir:
  * O vCenter 6.0u2 está executando um Platform Services Controller externo.
  * O vCenter está no modo vinculado (em que o vCenter secundário usa o serviço de SSO do vCenter primário ou de um serviço de SSO externo).

## Verificando o ambiente de instalação da Camada 2
{: #hcxclient-planning-verify-layer-2-inst}

O esticamento da rede da Camada 2 tem os requisitos a seguir:
* Uma edição do vSphere Enterprise Plus.
* O vSphere vCenter deve atender aos requisitos a seguir para suportar a extensão da Camada 2:
  * licença do vSphere Enterprise Plus
  * Deve ter um vSphere Distributed Switch (vDS). O comutador distribuído está disponível com o vSphere Enterprise Plus Edition.
  * Quando instalado, o dispositivo de serviço Layer 2 Concentrator no local deve ter acesso a uma porta vNIC e quaisquer VLANs a serem estendidas.
  * Se a rede precisar ser estendida por meio da Internet pública ou de uma VPN (em um caminho alternativo), a máquina virtual L2C no VCS requererá um endereço IP. O endereço IP remoto é necessário para configurar o Layer 2 Concentrator.
  * Se múltiplos Layer 2 Concentrators forem desejados, cada um deverá ter um endereço IP no local e na nuvem.

## Planejamento de pré-implementação
{: #hcxclient-planning-predepl}

Grande parte do tempo gasto na implementação do HCX está no estágio de pré-implementação. Embora seja típico que os projetos de migração de sistemas de informações levem meses e até mesmo anos para serem concluídos, o HCX permite que a migração leve um tempo curto e que a conectividade de rede com a nuvem seja iniciada imediatamente após a implementação.

Como a
implementação do HCX para um cliente de nível corporativo geralmente
envolve segurança, rede, armazenamento e equipes de infraestrutura do vSphere, faz
sentido envolver essas equipes no POC, se possível. O gerenciamento
efetivo do projeto e a inclusão antecipada de partes interessadas são essenciais para
garantir que a velocidade de implementação e a operação do HCX sejam realizadas.

## Evitando a paralisia de análise
{: #hcxclient-planning-avoiding}

Muitos dos obstáculos e o tempo que leva na migração de uma máquina virtual (MV) ou grupo de MVs
estão lá devido à necessidade de modificar partes do ambiente de
aplicativos, o design dessas mudanças e o planejamento do
tempo de inatividade necessário para fazer essas mudanças. Após essas mudanças serem feitas, a migração torna-se difícil de reverter, aumentando ainda mais a paralisia de análise. Tentar capturar todos os aspectos da migração, coordenar entre as equipes e mudar os principais interessados pode atrasar o projeto.

O HCX permite a migração de instância cruzada do vSphere de uma MV ou um grupo de MVs
que representa um aplicativo composto parcial ou completo, sem qualquer
modificação no aplicativo. Por causa disso, a restauração de uma
migração significa mover as MVs de volta ou estender novamente as
redes. Isso anula a necessidade de uma grande parte do planejamento de migração
e permite algum paralelismo no processo de planejamento. Depois de
selecionar os aplicativos a serem movidos e criar um design de rede
de alto nível, os aplicativos podem iniciar a migração com
configuração mínima na instância da nuvem enquanto a conectividade e o
design de rede finais são trabalhados.

## Redes esticadas
{: #hcxclient-planning-stretched-net}

Os componentes de esticamento de rede da frota do HCX são muitos estáveis. Em
um cliente específico com mais de 20 VLANs estendidas para o
{{site.data.keyword.cloud}} na WAN de 1 Gbps compartilhada com outros túneis de tráfego e de migração
do HCX, não há problemas de aplicativos atribuídos à rede. Os links de rede ficam ativos por mais de 6 meses dessa maneira.

Redes mais estendidas foram incluídas e removidas sem problemas. Escolher um {{site.data.keyword.CloudDataCent_notm}} que está próximo (latência de <6 ms para esse cliente em particular) também atua na estabilidade de rede da rede estendida. Deixar as redes estendidas ativas a longo prazo não deve ser um
fator negativo em seu design, visto que você tem largura de banda suficiente e baixa
latência suficiente para seus aplicativos.

## Ciclo de vida de
{: #hcxclient-planning-mig-lifecycle}

As seções a seguir descrevem as fases dentro de um ciclo de vida de
migração típico do HCX, denotando onde os fluxos de trabalho podem ser feitos em
paralelo.

## Inventário do vSphere
{: #hcxclient-planning-vsphere-planning}

- Avaliação de alta granularidade de MVs dentro de um aplicativo a ser migrado. Alta granularidade implica em entender as MVs que participam de um
aplicativo, sem entrar em detalhes.
- Se você planeja migrar muitas MVs e a largura de banda da rede é limitada
entre os sites de origem e na nuvem, agrupe ainda mais as MVs por VLAN ou VXLAN
caso o NSX seja empregado na origem. Isso permite um plano de migração do HCX em cascata em que os grupos de VMs por VLAN são migrados e as redes L2 em que residem são estendidas apenas até o ponto em que as VLANs são liberadas.

Isso significa que o grupo inicial de redes L2 estendidas
relacionadas pode ser não estendido apenas quando o design de rede do lado da nuvem
é finalizado e implementado. Não estender implica em trocar o
tráfego específico de VXLAN para agora ser roteado por meio da infraestrutura NSX
da instância da nuvem.

## Configuração de rede de linha de base
{: #hcxclient-planning-baseline-net-config}

Crie uma rede de perímetro segura dentro da instância do vSphere do lado da nuvem. Isso geralmente consiste em um dispositivo NSX DLR ou de Borda. Se você usa o HCX Proximity Routing, não é necessário
criar nenhuma regra de firewall ou topologia de uplink, pois ela pode
ser concluída posteriormente ou simultaneamente sem afetar o tráfego L2
estendido.

## Extensão de rede
{: #hcxclient-planning-net-extension}

Ampliar a rede simplesmente significa usar a VLAN ou a VXLAN existente
do ambiente do vSphere de origem, representado por um grupo de portas do
comutador distribuído virtual (vDS) e estendendo-a para um NSX VXLAN no
lado de nuvem do HCX.

## Testes de pré-voo
{: #hcxclient-planning-preflight-tests}

Os testes de simulação envolvem a execução de uma migração do HCX tanto com a função de migração do vMotion quanto com a em massa para estabelecer uma taxa de transferência de linha de base.

## Migração de apps não de produção
{: #hcxclient-planning-mig-non-prod-apps}

A migração de VMs começa com os estágios planejados de VMs menos críticas. As equipes de Desenvolvimento e Teste usam a conectividade de Internet para migração e tráfego de L2 estendido.

## O design e a implementação da rede do Cloud começam
{: #hcxclient-planning-cloud-net-begins}

Enquanto as migrações continuam, os designs de rede do lado da nuvem são finalizados
e implementados dentro da instância do vSphere do lado da nuvem.

## Mais considerações de conectividade de rede
{: #hcxclient-planning-connect-considerations}

Enquanto as migrações continuam, a conectividade de rede da WAN privada é
pedida, uma vez que geralmente leva de algumas semanas a meses para ser estabelecida
com o provedor em nuvem. Depois que a conectividade da rede privada é
concluída, o HCX pode ser configurado para usar ambos, o link de rede
privada dedicada e a Internet para migração e tráfego L2 estendido.

## Servidores físicos
{: #hcxclient-planning-physical-servers}

Quando o objetivo for a migração do data center para a nuvem, qualquer servidor
físico que interagir com as MVs que estão sendo migradas poderá ser acessado para
migração para o {{site.data.keyword.cloud_notm}}, já que uma MV (P2V) ou um bare metal permanece
na origem. Se o servidor físico tiver que permanecer na origem e o HCX for usado apenas durante a migração, até que uma rede dedicada seja estabelecida, será importante entender se ela residirá em qualquer rede que esteja estendida na nuvem com o HCX. Nesse cenário, o HCX está permitindo que não somente as VMs, mas que a sub-rede inteira seja migrada para a nuvem.

Para remover o HCX no final da migração, a sub-rede não poderá
existir na origem e no destino se a conexão entre os dispositivos
físicos e as MVs migradas for mantida. Isso implica que quaisquer dispositivos físicos deixados para trás no site de origem que existem em redes L2 estendidas devem ser migrados para outra sub-rede da rede que possa ser roteada para o lado da nuvem. A exceção a isso é se
alguma outra tecnologia L2 estendida for empregada, como NSX L2 VPN, para
substituir os terminais L2 estendidos do HCX.

## Migrar aplicativos e aplicativos complexos
{: #hcxclient-planning-mig-prod-complex-app}

MVs com VMDKs compartilhados de vários gravadores, como clusters do Oracle RAC ou do
MS Exchange/SQL ou MVs com mapeamentos de dispositivo bruto são exemplos de MVs que
precisam de consideração extra antes da migração.

## Swing de rede
{: #hcxclient-planning-net-swing}

A Troca de rede ocorre após a evacuação das MVs nas redes do lado
de origem ser concluída e o design/implementação de rede ser
concluído no lado da nuvem. Configurar o HCX para não estender as redes relacionadas às VMs concluídas dentro das ondas de migração permite que as VMs migradas roteiem o tráfego de rede usando a infraestrutura NSX do lado da nuvem.

## Plataformas do cliente suportadas
{: #hcxclient-planning-client-platforms}

Para a extensão de rede, apenas grupos de portas com um comutador distribuído
virtual (vDS) do vSphere são suportados. Isso também implica que os hosts ESXi independentes não são suportados, pois é possível ter apenas um vDS quando hosts ESXi são gerenciados pelo vCenter.
- vSphere 5.1 (linha de comandos apenas para o vCenter 5.1 por meio da API)
- vSphere 5.5 (IU do cliente da web suportado no vCenter 5.5u3 e acima)
- vSphere 6.0
- vSphere 6.5 (o vDS deve estar em um nível 6.0)

## Plataformas de nuvem suportadas
{: #hcxclient-planning-cloud-platforms}

O lado da Nuvem do HCX é provisionado pela automação do {{site.data.keyword.cloud_notm}}.

## Opções de conectividade
{: #hcxclient-planning-connect-options}

### Conectividade HCX Padrão
{: #hcxclient-planning-standard-connect}

Conforme implementado pela automação do {{site.data.keyword.vmwaresolutions_short}}, a instalação do lado
da nuvem do HCX está configurada para se conectar à Internet pública por
padrão.

## Links relacionados
{: #hcxclient-planning-related}

* [Glossário de componentes e termos do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Implementação do cliente HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Entrelaçamento de serviços HCX no local](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrações de nuvem híbrida do VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitorando parâmetros e componentes](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Resolução de problemas do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
