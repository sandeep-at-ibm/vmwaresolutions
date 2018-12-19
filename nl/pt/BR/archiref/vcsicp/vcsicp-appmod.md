---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-15"

---

# Visão geral de modernização do

O diagrama a seguir mostra a arquitetura de referência de modernização de aplicativo que o Acme Skateboards implementa. A arquitetura é descrita em profundidade nesta série de documentos.

Figura 1. Diagrama de visão geral da arquitetura
![Diagrama de visão geral da arquitetura](vcsicp-arch-overview.svg)

Essa arquitetura híbrida permite que o Acme Skateboards atinja os objetivos a seguir:
- Migrar máquinas virtuais VMware (VMs) no local para o {{site.data.keyword.cloud}} com pouco ou nenhum tempo de inatividade e nenhuma reconfiguração do aplicativo.
- Ativar o início da jornada de modernização de aplicativo, permitindo o foco na conteinerização das interfaces da web e middleware mais simples, enquanto permite que os bancos de dados mais complexos permaneçam como VMs.
- Usar o {{site.data.keyword.cloud_notm}} Automation Manager (CAM) para o infrastructure as code (IaC) de script para editar e orquestrar serviços que são feitos por meio de VMs e contêineres para integração às suas cadeias de ferramentas do DevOps e sua solução ITSM.

A arquitetura de referência tem os componentes principais a seguir:
- **Virtualização no local** - um cluster do VMware que hospeda atualmente as VMs do Acme Skateboards. Essas VMs hospedam atualmente os aplicativos a serem modernizados. É necessário que esse cluster atenda aos pré-requisitos da arquitetura [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) para que possa executar o HCX. O HCX amplia as redes no local para o {{site.data.keyword.cloud_notm}}, permitindo que os clientes migrem VMs para a instância do VMware vCenter Server on {{site.data.keyword.cloud_notm}} que está em execução no {{site.data.keyword.cloud_notm}} e de volta se necessário.

- **{{site.data.keyword.vmwaresolutions_short}}** – a instância do vCenter Server fornece os blocos de construção fundamentais do VMware, como vSphere, vCenter Server, NSX-V e opções de armazenamento, incluindo o armazenamento do vSAN ou do Endurance do {{site.data.keyword.cloud_notm}}, necessários para implementar automaticamente uma solução VMware Software Defined Data Center (SDDC). O cluster do VMware é o destino das VMs migradas e alguns dos aplicativos modernizados em contêineres hospedados no ICP. A seguir estão os componentes principais no vCenter Server:
    - **NSX-V** – o NSX-V fornece a camada de virtualização de rede no VCS que fornece uma sobreposição de rede para VMs da Acme Skateboards. O NSX-V ativa o BYOIP e isola as redes de carga de trabalho das redes do IBM Cloud. O NSX-V é programado pelo HCX para criar as redes ampliadas pela Acme Skateboards no local.

    - **NSX-T** - o NSX-T fornece um conjunto comum de ferramentas para o gerenciamento de rede e segurança nos contêineres e VMs. O NSX-T é totalmente compatível com o Container Networking Interface (CNI) do Kubernetes e integra-se ao CNI para fornecer a rede de contêiner. O NSX-T fornece a rede de sobreposição que os aplicativos modernizados usam e está substituindo o Calico, que é usado nativamente pelo ICP e pelo IKS.

- **IBM Cloud Private** - o ICP é uma plataforma de aplicativos para desenvolvimento e gerenciamento de aplicativos em contêiner. O ICP é um ambiente integrado que inclui o orquestrador de contêineres Kubernetes, um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário, que fornece um local centralizado por meio do qual a Acme Skateboards pode implementar, gerenciar, monitorar e escalar seus aplicativos. A instância do vCenter Server hospeda os componentes do ICP, nós principais, nós do trabalhador, executando-os como VMs. O ICP hospeda o seguinte:
    - **{{site.data.keyword.cloud_notm}} Automation Manager ** - o CAM é uma plataforma infrastructure as code (IaC) pronta para empresa que fornece uma única área de janela de vidro para provisiona cargas de trabalho da VM, no local ou no VCS, juntamente com cargas de trabalho do Kubernetes, no ICP ou IKS, usando modelos. O CAM é um aplicativo Dockerizado que é executado no ICP e é fortemente integrado para autorização, controle de acesso baseado na função (RBAC) e outras funções.
    - Os aplicativos conteinerizados da Acme Skateboards que eles desejam implementar nesse ambiente.

- O **IBM Kubernetes Service** – o IKS permite que o Acme Skateboards implemente seus aplicativos modernizados em contêineres do Docker que são executados em clusters do Kubernetes. Os modos principais são totalmente gerenciados pela IBM enquanto os nós do trabalhador no conjunto de trabalhadores são implementados na mesma conta do {{site.data.keyword.cloud_notm}} que sua instância do vCenter Server. Os nós do trabalhador podem ser instâncias de servidor virtual bare metal, público ou dedicado. O Calico é instalado e configurado automaticamente no IKS. O Calico fornece conectividade de rede segura para contêineres e está configurado no IKS para usar o encapsulamento IP-in-IP para pacotes que estão viajando em sub-redes e para usar NAT para conexões de saída dos contêineres.

- **Direct Link** – o {{site.data.keyword.cloud_notm}} Direct Link usa o provedor WAN da Acme Skateboard para conectar seu data center ao {{site.data.keyword.cloud_notm}} para fornecer uma conexão de rede confiável, segura e de baixa latência. Essa conexão fornece o seguinte:
    - Acesso aos aplicativos hospedados em nuvem por meio de seus usuários corporativos.
    - Tráfego entre VMs no local e VMs de nuvem.
    - Tráfego entre sistemas legados no data center no local e nas VMs de nuvem.

## Benefícios importantes para a Acme Skateboards

 O vCenter Server fornece os blocos de construção fundamentais que incluem o VMware vSphere, o vCenter Server, o NSX e as opções de armazenamento compartilhado que incluem o vSAN, necessário para projetar de forma flexível uma solução VMware Software Defined Data Center (SDDC) que melhor se ajuste às cargas de trabalho do cliente.

Em resumo, as ofertas do {{site.data.keyword.vmwaresolutions_short}} fornecem os benefícios a seguir:

* Acelera a entrega de projetos de TI para os Desenvolvedores e linhas de negócios, reduzindo o tempo que leva para compras, arquitetura, implementação e implementação de recursos de semanas ou meses até horas.
* Aprimora a segurança com servidores bare metal dedicados em uma nuvem particular host, incluindo a implementação de terminal privado em serviços do {{site.data.keyword.cloud_notm}}, incluindo IKS e KMIP.
* Permite o gerenciamento e o controle consistentes da nuvem híbrida implementada, fornecendo acesso administrativo total ao gerenciamento de virtualização, preservando suas ferramentas, scripts e investimentos existentes do VMware em treinamento.
* Usa o conhecimento do VMware em escala global com o IBM Professional and Managed Services abrangendo 30+ {{site.data.keyword.CloudDataCents_notm}} no mundo inteiro.

Os clientes que se movem para plataformas de aplicativo nativo em nuvem, como o ICP e o IKS, são focados em velocidade e inovação e nem sempre têm segurança e rede em mente. Aguardar que as equipes de rede ou segurança peçam serviços como balanceadores de carga, firewalls, comutadores e roteadores diminui o tempo de maturação do aplicativo. Essa arquitetura de referência mostra como o VCS, o ICP e o IKS movem a Acme Skateboards com segurança ao longo da jornada de modernização do aplicativo.

## Links relacionados

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
