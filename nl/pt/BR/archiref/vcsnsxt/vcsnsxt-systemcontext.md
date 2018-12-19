---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Contexto do sistema
O diagrama de contexto de sistema define os elementos chave de um sistema, o limite do sistema e as entidades que interagem com ele juntamente com as interações. É um diagrama de alto nível que fornece ao leitor uma visualização inicial do sistema.

Figura 1. Contexto de sistema
![Diagrama de contexto de sistema](vcsnsxt-networking.svg)

Os quatro componentes principais, de uma perspectiva de rede, são conforme a seguir:
- **Virtualização no local** - um ambiente do VMware que é hospedado nas instalações do cliente ou de um terceiro e hospeda atualmente as máquinas virtuais (VMs) que executam os aplicativos a serem modernizados. É o ambiente de origem para migrações de VM e é fracamente acoplado ao {{site.data.keyword.cloud}} via VMware HCX.
- **vCenter Server** - uma instância do {{site.data.keyword.vmwaresolutions_short}} que é o destino para VMs migradas por meio do ambiente no local. Junto com a virtualização no local, isso forma um ambiente híbrido que permite que as VMs se movam ininterruptamente de um ambiente para o outro.
- **IBM Cloud Kubernetes Service** - ele usa o Kubernetes como a solução de orquestração de contêineres. A IBM opera e gerencia o nó principal do Kubernetes enquanto os nós do trabalhador são implementados na infraestrutura gerenciada pelo cliente. A IBM fornece ferramentas de gerenciamento para implementação de correção do sistema operacional, upgrades de mecanismo de Docker e novas versões do Kubernetes. O IBM Kubernetes Service fornece uma plataforma isolada e segura para gerenciar contêineres que são móveis, extensíveis e com capacidade de recuperação automática em caso de failovers.
- **IBM Cloud Private** - uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados. Ele é um ambiente integrado que inclui o orquestrador de contêineres Kubernetes, um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário, que fornece um local centralizado de onde é possível implementar, gerenciar, monitorar e escalar aplicativos.
-	**IBM Cloud Services** - uma ampla variedade de serviços disponíveis por meio do {{site.data.keyword.cloud_notm}} que são consumíveis. As opções de serviço incluem analítica, AI e IoT como exemplos.

## Atores

O diagrama de contexto de sistema identifica os agentes a seguir.

Tabela 1. Atores

Ator  |  Descrição
---|---
Administrador do Sistema |Os administradores de sistema são os recursos corporativos do VMware que usam o vCenter e o plug-in HCX. Eles identificam candidatos para migração, estendem redes, migram VMs e gerenciam NSX-V. Eles usam o console do {{site.data.keyword.cloud_notm}} para provisionar instâncias do VCS e para escalar a capacidade.
Desenvolvedor | Os desenvolvedores são os recursos de contêiner qualificados para a empresa que usam os consoles e APIs do IKS/ICP/CAM para criar e gerenciar contêineres. Ele cria os novos serviços como parte da modernização de aplicativo.
Usuário corporativo | Esse recurso corporativo requer acesso à rede para os aplicativos para realizar processos de negócios, como atualizar conteúdo.
Cliente | O cliente é um agente externo que deseja consumir serviços da empresa. No caso de Acme Skateboards, é um skatista que deseja comprar produtos de skate. O Cliente requer acesso seguro à Internet para o catálogo.
IBM IKS | Esse é um recurso IBM que gerencia o Nó principal do IKS do serviço.

## Sistemas

O diagrama de contexto de sistema identifica os sistemas a seguir.

Tabela 2. Sistemas

Ator | Descrição
---|---
vCenter | O vCenter é a interface primária para que o administrador do sistema gerencie as VMs no local e acesse o plug-in HCX para estender redes e migrar VMs. Com o vCenter Server with Hybridity Bundle, o administrador de sistemas pode integrar ininterruptamente as redes do vSphere no local à instância do VCS em execução no {{site.data.keyword.cloud_notm}}. A rede híbrida amplia as redes no local para o {{site.data.keyword.cloud_notm}} permitindo que os clientes migrem seus aplicativos para uma instância do VCS em execução no {{site.data.keyword.cloud_notm}} e de volta para o local, se necessário. Para obter mais detalhes sobre o vCenter Server with Hybridity Bundle, consulte o documento [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).
VMs em pré-mise | As VMs no local hospedam os aplicativos que estão migrando para a nuvem. Inicialmente, eles são migrados como VMs e, em seguida, por meio da jornada de modernização de aplicativo migrada de VMs para contêineres.
Nas VMs em nuvem | Nas VMs em nuvem, os aplicativos de host que foram migrados de no local. Elas se comunicam com os aplicativos no local por meio da rede L2 estendida. No caso desta arquitetura de referência e neste exemplo para Acme Skateboards, uma das VMs em nuvem é um servidor de banco de dados, que faz parte da carga de trabalho de presença on-line.
NSX-V | O NSX-V no VCS fornece a rede de sobreposição definida pelo software que é gerenciada pelo administrador do sistema. A rede de sobreposição é o destino para redes estendidas HCX, uma vez que manipula o tráfego das VMs para o ICP. O NSX-V fornece a arquitetura de referência com recursos como implementação, reconfiguração e destruição de redes virtuais sob demanda e serviços de microssegmentação no VMware usando vSphere distributed switches (vDS). Para obter mais informações, veja [Visão geral do NSX-V](vcsnsxt-overview-ic4vnsxv.html).
CAM | O {{site.data.keyword.cloud_notm}} Automation Manager (CAM) é executado no ICP e fornece uma única área de janela de vidro para provisionar cargas de trabalho baseadas em VM ao lado de cargas de trabalho baseadas em Kubernetes, simplesmente usando modelos. O CAM permite ao desenvolvedor: <br> - Provisionar cargas de trabalho no VCS, ICP ou IKS.<br> - Editar e orquestrar serviços que são constituídos de VMs e contêineres. <br> -Integrar suas cadeias de ferramentas do DevOps e a solução day-2 ITSM.
Aplicativos conteinerizados | Estes são os apps que passaram pela jornada de modernização de aplicativo e agora estão sendo executados como contêineres. No caso desta arquitetura de referência e neste exemplo para Acme Skateboards, um dos apps conteinerizados é um servidor da web, que faz parte da carga de trabalho de presença on-line.
Watson | No caso desta arquitetura de referência e neste exemplo para Acme Skateboards, o Watson representa o serviço AI que é usado na arquitetura de “Protótipo”.

### Links Relacionados

* [Visão geral do VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
