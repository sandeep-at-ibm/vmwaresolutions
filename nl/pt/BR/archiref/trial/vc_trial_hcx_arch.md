---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Design de arquitetura do HCX on IBM Cloud para o Single-node Trial for vCenter Server on IBM Cloud
{: #vc_trial_hcx_arch}

O VMware HCX on {{site.data.keyword.cloud}} com o Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud_notm}} é uma nova oferta que permite a conexão contínua entre as instâncias do {{site.data.keyword.vmwaresolutions_short}} e um data center virtualizado do VMware no local. Embora a recomendação para o vCenter Server seja um mínimo de três nós, a avaliação de nó único fornece um caminho de baixo custo para testar e experimentar os benefícios de uma implementação de nuvem híbrida.

O {{site.data.keyword.vmwaresolutions_short}} inclui implementações totalmente automatizadas e rápidas de configurações do vCenter Server no {{site.data.keyword.cloud_notm}}. A oferta Single-node Trial for vCenter Server complementa a infraestrutura no local e permite que as cargas de trabalho existentes e futuras sejam executadas no {{site.data.keyword.cloud_notm}} sem conversão. A oferta usa as mesmas ferramentas, qualificações e processos usados no local. Para obter mais informações sobre ofertas do {{site.data.keyword.vmwaresolutions_short}}, veja o [IBM Architecture Center](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture).

O serviço HCX on {{site.data.keyword.cloud_notm}} combina as instâncias do vCenter Server com os data centers virtualizados existentes no local, permitindo a criação de extensões de rede contínua e migração bidirecional de cargas de trabalho. Os componentes do HCX on IBM Cloud, que são implementados como máquinas virtuais (MVs) no site de destino do {{site.data.keyword.cloud_notm}} VMware, permitem o estabelecimento de uma conexão com os componentes do HCX on {{site.data.keyword.cloud_notm}} que estão instalados no site de origem no local do peer.

Figura 1. arquitetura HCX

![HCX architecture](hcx-architecture.svg "HCX architecture")

As informações a seguir fornecem o design da implementação do serviço HCX on {{site.data.keyword.cloud_notm}}. Isso inclui os componentes na instância do {{site.data.keyword.vmwaresolutions_short}} do lado de destino e os componentes que são implementados na origem, no local.

## Visão geral do HCX no IBM Cloud
{: #vc_trial_hcx_arch-ovw}

O {{site.data.keyword.cloud_notm}} integra de forma contínua as redes do vSphere vCenter no local a implementações do {{site.data.keyword.vmwaresolutions_short}}. A rede híbrida estende as redes do vSphere vCenter no local para o {{site.data.keyword.cloud_notm}}, suportando a mobilidade bidirecional da MV.

O HCX possui os processos de criptografia e decriptografia de origem e de destino, o que garante a segurança consistente e fornece admissão para fluxos de trabalho híbridos, como migração da MV e extensão de rede. Essa oferta cria uma rede de longa distância (WAN) otimizada e definida por software para aumentar o desempenho da rede estendida, permitindo que o desempenho se aproxime da velocidade de rede local (LAN). O HCX permite a migração bidirecional de carga de trabalho e de política de segurança do VMware NSX para o {{site.data.keyword.cloud_notm}}, integra-se ao vSphere vCenter e é gerenciado por meio do vSphere Web Client.

### Extensão de rede da camada 2
{: #vc_trial_hcx_arch-layer-2-extension}

O HCX permite um estado do vSphere no local existente para estender com segurança uma rede de seu vCenter no local para um {{site.data.keyword.CloudDataCent_notm}} executando o VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} ou o vCenter Server. Os itens a seguir ativam esse recurso:

* O HCX fornece um dispositivo chamado Layer 2 Concentrator (L2C).
* As redes estendidas são vinculadas a dispositivos {{site.data.keyword.cloud_notm}} NSX Edge implementados no vCenter Server.
* A capacidade de implementar mais de um Layer 2 Concentrator padrão para atingir a escalabilidade e aumentar o rendimento do vCenter no local.
* As MVs são migradas por meio do Cloud Gateway e sobre a Camada 2 estendida podem reter seus endereços IP e MAC.

### Migração da máquina virtual
{: #vc_trial_hcx_arch-vm-mig}

O HCX fornece os três métodos a seguir de movimento da MV:

* Migração de baixa atividade
* Migração do vSphere vMotion
* Migração fria

#### Migração de baixa atividade
{: #vc_trial_hcx_arch-low-downtime-mig}

A migração de tempo de inatividade baixo depende do vSphere Replication, que é uma tecnologia distribuída que é implementada no hypervisor VMware ESX ou VMware ESXi. A implementação do HCX no local cria uma réplica de uma MV em tempo real no {{site.data.keyword.cloud_notm}}, executa uma comutação para desligar a MV de origem e ligar a MV migrada. O caminho de migração é sempre por meio do Cloud Gateway. O transporte pode ser a Internet, uma rede estendida da Camada 2 ou uma linha de Conexão direta. É possível migrar uma MV mais de uma vez em qualquer direção.

#### Migração do vSphere vMotion
{: #vc_trial_hcx_arch-vmotion-mig}

É possível transferir MVs em tempo real usando a migração do vSphere vMotion em uma rede que é estendida para o {{site.data.keyword.cloud_notm}}. A migração do vMotion também é chamada de migração de tempo de inatividade zero ou vMotion entre nuvens.

#### Migração fria
{: #vc_trial_hcx_arch-cold-mig}

A migração fria fornece a capacidade de transferir uma MV desligada para o {{site.data.keyword.cloud_notm}} por meio de uma rede estendida criada via Layer 2 Concentrator.

#### Recursos comuns de migração
{: #vc_trial_hcx_arch-common-feat}

Os recursos a seguir estão disponíveis nos três tipos de migração:

* WAN Optimization definido por software que aumenta o rendimento e a velocidade da migração.
* Planeje sua migração para um horário especificado.
* Mantenha o nome do host, o nome da MV ou ambos.

### Rede
{: #vc_trial_hcx_arch-network}

Os recursos de rede a seguir são construídos no Cloud Gateway e nos Layer 2 Concentrators.

#### Roteamento de fluxo inteligente
{: #vc_trial_hcx_arch-intel-flow}

O roteamento de fluxo inteligente seleciona automaticamente a melhor conexão com base no caminho da Internet, inundando eficientemente a conexão inteira de modo que as cargas de trabalho sejam movidas o mais rápido possível. Quando fluxos maiores, como backup ou replicação, causam a contenção de CPU, fluxos menores são roteados para CPUs menos ocupadas, melhorando o desempenho do tráfego interativo.

#### Roteamento de proximidade
{: #vc_trial_hcx_arch-prox-routing}

O roteamento de proximidade assegura que o encaminhamento entre MVs conectadas a redes estendidas e roteadas, no local e na nuvem, seja simétrico. Esse recurso requer o Advanced Networks Services with Dynamic Routing que é configurado entre as instalações do cliente e a nuvem.

Quando os usuários estendem suas redes para a nuvem, a conectividade da Camada 2 é estendida para as redes do {{site.data.keyword.cloud_notm}}. No entanto, sem a otimização de rota, as solicitações de comunicação da Camada 3 devem retornar para a origem de rede no local para serem roteadas. Essa viagem de retorno é chamada de "tromboning" ou "hairpinning". O tromboning é ineficiente porque os pacotes devem viajar entre a origem da rede e a nuvem, mesmo quando as MVs de origem e de destino residem na nuvem.

Se o caminho de encaminhamento incluir firewalls stateful ou outro equipamento sequencial que deve ver os dois lados da conexão, a comunicação poderá falhar. A falha na comunicação da MV, sem otimização da rota, ocorre quando o caminho de egresso que está saindo da nuvem é a rede estendida da Camada 2 ou a Rede roteada da organização. A rede no local não sabe sobre o "atalho" de rede estendida. Esse problema é chamado de roteamento assimétrico. A solução é ativar o roteamento de proximidade para que a rede no local possa aprender as rotas por meio do {{site.data.keyword.cloud_notm}}.

O Cloud Gateway mantém um inventário de MVs na nuvem. Ele também entende os estados da MV a seguir:

* Transferido para o {{site.data.keyword.cloud_notm}} com vMotion (migração de tempo de inatividade zero)
* Migrados para a nuvem usando a replicação baseada em host (migração de tempo de inatividade baixo)
* Criado na nuvem (em uma rede estendida)

#### Segurança
{: #vc_trial_hcx_arch-sec}

O Cloud Gateway oferece o AES-GCM com IKEv2 compatível com o Conjunto B, a transferência de AES-NI e o controle de admissão baseado em fluxo. O HCX também possui o processo de criptografia e decriptografia de origem e de destino, garantindo segurança e administração consistentes para fluxos de trabalho híbridos, como migração de MV e extensão de rede. É possível migrar políticas de segurança que estão definidas e designadas a uma MV no local com a MV no {{site.data.keyword.cloud_notm}}.

As condições a seguir são necessárias para a migração de política:

* O data center no local está executando o NSX V6.2.2 ou superior.
* No vSphere, a política de segurança é uma única Seção NSX que pode ter muitas regras.
* É possível nomear um conjunto de endereços IP ou endereços MAC para participar da política.
* O nome do Conjunto de MACs ou do Conjunto de IPs não pode exceder 218 caracteres.
* As regras suportadas especificam os endereços IP da Camada 3 ou Conjuntos de IPs, ou endereços de Controle de Acesso à Mídia da Camada 2 ou Conjuntos de Controle de Acesso à Mídia como a origem ou o destino.

### Componentes do HCX
{: #vc_trial_hcx_arch-hcx-comp}

O serviço HCX on {{site.data.keyword.cloud_notm}} implementa quatro dispositivos virtuais que estão instalados e configurados no data center no local e no destino do IBM Cloud. As informações a seguir descrevem cada um dos quatro dispositivos virtuais necessários. Opcionalmente, os dispositivos de borda podem ser necessários, dependendo do design de implementação.

#### Gerenciador de HCX
{: #vc_trial_hcx_arch-hcx-manager}

O dispositivo virtual HCX Manager é uma extensão para o vCenter local. O dispositivo é implementado como uma MV e sua estrutura do arquivo contém os outros dispositivos virtuais de serviço híbrido. O HCX Manager supervisiona a implementação e a configuração do Cloud Gateway, dos Layer 2 Concentrators e do dispositivo virtual WAN Optimization, no local e no {{site.data.keyword.cloud_notm}}.

#### Gateway de Nuvem Híbrido
{: #vc_trial_hcx_arch-hcg}

O Hybrid Cloud Gateway (CGW) mantém um canal seguro entre os locais do vSphere no local e o {{site.data.keyword.cloud_notm}}. O HCX usa criptografia avançada para autoinicialização de uma conexão de site para site com o {{site.data.keyword.cloud_notm}}. O canal seguro entre o vSphere e o {{site.data.keyword.cloud_notm}} evita problemas de segurança de "meia milha" de rede. O Cloud Gateway também incorpora a tecnologia de replicação do vSphere para executar a migração bidirecional.

#### Otimização de WAN
{: #vc_trial_hcx_arch-wan-opt}

O dispositivo WAN Optimization é o componente que executa o condicionamento da WAN para reduzir os efeitos de latência. Ele também incorpora a Correção de erro de encaminhamento para negar cenários de perda de pacote e deduplicação de padrões de tráfego redundantes. Juntos, eles reduzem o uso da largura da banda e asseguram o melhor uso da capacidade de rede disponível para expedir a transferência de dados para e do {{site.data.keyword.cloud_notm}}.

A migração da MV depende da combinação dos dispositivos Cloud Gateway e WAN Optimization para atingir a mobilidade sem paralelo entre o vSphere local e o {{site.data.keyword.cloud_notm}}. Além disso, a extensão da Camada 2 se beneficia da otimização de WAN quando o caminho de dados é roteado por meio do Cloud Gateway.
{:important}

#### Concentradores de Camada 2
{: #vc_trial_hcx_arch-layer-2-conc}

Os dispositivos Layer 2 Concentrators (L2C) permitem a extensão de uma rede da Camada 2 do data center do vSphere no local para o {{site.data.keyword.cloud_notm}}.

Os Layer 2 Concentrators têm as interfaces a seguir:

* **Interface de tronco interno**: essa interface manipula o tráfego da MV no local para as redes estendidas usando um mapeamento de ponte translacional para uma rede estendida correspondente no {{site.data.keyword.cloud_notm}}.
* **Interface de uplink**: o HCX usa essa interface para enviar o tráfego de sobreposição encapsulado para e do {{site.data.keyword.cloud_notm}}. Os dados do aplicativo viajam por meio da interface de Uplink.

### Arquitetura
{: #vc_trial_hcx_arch-deployment}

Para obter informações sobre a implementação do HCX on {{site.data.keyword.cloud_notm}}, veja [Implementação e operações do
VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/VMware-HCX-on-IBM-Cloud-Deployment-and-Operations.pdf).
