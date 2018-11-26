---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

# Visão geral de modernização do

O diagrama a seguir mostra a arquitetura de referência de modernização do aplicativo que a Acme Skateboards implementará e é descrita detalhadamente nesta série de documentos.

Figura 1. Diagrama de visão geral da arquitetura
![Diagrama de visão geral da arquitetura](vcsicp-arch-overview.svg)

Essa arquitetura híbrida permitirá à Acme Skateboards:
- Migrar VMs do VMware no local para o IBM Cloud com pouco ou nenhum tempo de inatividade e nenhuma reconfiguração do aplicativo.
- Ativá-las para iniciar a jornada de modernização do aplicativo, permitindo que se concentrem na conteinerização das interfaces da web mais simples e do middleware, enquanto permite que bancos de dados mais complexos permaneçam como VMs.
- Alavancar o Cloud Automation Manager (CAM) para infrastructure as code (IaC) de script para editar e orquestrar serviços que são feitos por meio de VMs e contêineres para se integrarem às suas cadeias de ferramentas do DevOps e à sua solução ITSM.

A arquitetura de referência tem os componentes principais a seguir:
- **Virtualização no local** - Este é um cluster do VMware que atualmente hospeda as VMs Acme Skateboards. São essas VMs que estão atualmente hospedando os aplicativos que serão modernizados. É necessário que esse cluster atenda aos pré-requisitos da arquitetura [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) para que possa executar o HCX. O HCX amplia as redes no local para o IBM Cloud, permitindo que os clientes migrem VMs para a instância do VMware vCenter Server on IBM Cloud (VCS) em execução no IBM Cloud e voltem, se necessário.

- **IBM Cloud for VMware Solutions** – a instância do VCS fornece os blocos de construção fundamentais do VMware, como vSphere, vCenter Server, NSX-V e opções de armazenamento, incluindo o armazenamento do vSAN ou do IBM Cloud Endurance, necessários para implementar automaticamente uma solução Software Defined Data Center (SDDC) do VMware. O cluster do VMware é o destino para as VMs migradas, bem como alguns dos aplicativos modernizados em contêineres hospedados no ICP. Os componentes principais no VCS são os seguintes:
    - **NSX-V** - o NSX-V fornece a camada de virtualização de rede no VCS que fornece uma sobreposição de rede para VMs da Acme Skateboards. O NSX-V ativa o BYOIP e isola as redes de carga de trabalho das redes do IBM Cloud. O NSX-V é programado pelo HCX para criar as redes que a Acme Skateboards ampliará no local.

    - **NSX-T** - o NSX-T fornece um conjunto comum de ferramentas para o gerenciamento de rede e segurança nos contêineres e VMs. O NSX-T é totalmente compatível com o Container Networking Interface (CNI) do Kubernetes e integra-se ao CNI para fornecer a rede de contêiner. O NSX-T fornece a rede de sobreposição que os aplicativos modernizados usam e está substituindo o Calico, que é usado nativamente pelo ICP e pelo IKS.

- **IBM Cloud Private** - o ICP é uma plataforma de aplicativos para desenvolvimento e gerenciamento de aplicativos em contêiner. O ICP é um ambiente integrado que inclui o orquestrador de contêineres Kubernetes, um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário, que fornece um local centralizado por meio do qual a Acme Skateboards pode implementar, gerenciar, monitorar e escalar seus aplicativos. A instância do VCS hospeda os componentes do ICP, nós principais, nós do trabalhador e assim por diante, executando-os como VMs. Hosts do ICP:
    - **IBM Cloud Automation Manager** – o CAM é uma plataforma infrastructure as code (IaC) pronta para a empresa que fornece uma única área de janela de vidro para provisionar cargas de trabalho da VM, no local ou no VCS, ao lado de cargas de trabalho do Kubernetes, no ICP ou no IKS, simplesmente usando modelos. O CAM é um aplicativo Dockerizado que é executado sobre o ICP e é fortemente integrado para autorização, controle de acesso baseado na função (RBAC) e outras funções.
    - Os aplicativos conteinerizados da Acme Skateboards que ela deseja implementar neste ambiente.

- O **IBM Kubernetes Service** – o IKS permite que o Acme Skateboards implemente seus aplicativos modernizados em contêineres do Docker que são executados em clusters do Kubernetes. Os modos principais são totalmente gerenciados pela IBM enquanto os nós do trabalhador no conjunto de trabalhadores são implementados na mesma conta do IBM Cloud que sua instância do VCS. Os nós do trabalhador podem ser: instâncias de servidor virtual bare metal, público ou dedicado. O Calico é instalado e configurado automaticamente no IKS. O Calico fornece conectividade de rede segura para contêineres e é configurado no IKS para usar o encapsulamento IP-in-IP para pacotes que percorrem as sub-redes e para usar o NAT para conexões de saída dos contêineres.

- **Link direto** - o IBM Cloud Direct Link usa o provedor WAN da Acme Skateboard para conectar seu data center ao IBM Cloud para fornecer uma conexão de rede confiável, segura e de baixa latência. Esta conexão fornece:
    - Acesso aos aplicativos hospedados em nuvem por meio de seus usuários corporativos.
    - Tráfego entre VMs no local e VMs de nuvem.
    - Tráfego entre sistemas legados no data center no local e nas VMs de nuvem.

## Benefícios importantes para a Acme Skateboards

O VMware vCenter Server on IBM Cloud (VCS) fornece os blocos de construção fundamentais que incluem VMware vSphere, vCenter Server, NSX e opções de armazenamento compartilhado, incluindo vSAN, necessários para projetar flexivelmente uma solução Software Defined Data Center (SDDC) do VMware que melhor se ajuste às cargas de trabalho do cliente.

Em resumo, as ofertas do IBM Cloud for VMware:

* Aceleram a entrega de projetos de TI para desenvolvedores e linhas de negócios, reduzindo o tempo que leva para compras, arquitetura, implementação e implementação de recursos, de semanas ou meses até horas.
* Aprimoram a segurança com servidores bare metal dedicados em uma nuvem particular host, incluindo a implementação de terminal privado em serviços do IBM Cloud, incluindo IKS e KMIP.
* Ativam o gerenciamento consistente e o controle da nuvem híbrida implementada, fornecendo acesso administrativo total ao gerenciamento de virtualização, preservando, assim, suas ferramentas, scripts e investimentos existentes do VMware em treinamento.
* Alavancam o conhecimento do VMware em escala global com o IBM Professional e o Managed Services abrangendo 30+ data centers do IBM Cloud em todo o mundo.

Os clientes que se movem para plataformas de aplicativo nativo em nuvem, como o ICP e o IKS, são focados em velocidade e inovação e nem sempre têm segurança e rede em mente. A espera de equipes de segurança ou de rede para provisionar serviços, como balanceadores de carga, firewalls, comutadores e roteadores, diminui o tempo de valorização do aplicativo. Essa arquitetura de referência mostra como o VCS, o ICP e o IKS movem a Acme Skateboards com segurança ao longo da jornada de modernização do aplicativo.

## Links relacionados

* [Visão geral do VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
