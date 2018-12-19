---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Visão geral de modernização do

O diagrama a seguir mostra a arquitetura de referência de modernização do aplicativo que a Acme Skateboards implementa e é descrita detalhadamente nesta série de documentos.

Figura 1. Visão geral da arquitetura
![Diagrama de visão geral da arquitetura](vcsnsxt-aod.svg)

Essa arquitetura híbrida permite à Acme Skateboards:
- Migrar máquinas virtuais VMware (VMs) no local para o {{site.data.keyword.cloud}} com pouco ou nenhum tempo de inatividade e nenhuma reconfiguração do aplicativo.
-	Ativá-las para iniciar a jornada de modernização do aplicativo, permitindo que se concentrem na conteinerização das interfaces da web mais simples e do middleware, enquanto permite que bancos de dados mais complexos permaneçam como VMs.
-	Alavancar o Cloud Automation Manager (CAM) para o Infrastructure as code (IaC) de script para editar e orquestrar serviços que são feitos por meio de VMs e contêineres para integração às suas cadeias de ferramentas do DevOps e sua solução ITSM.

Concentrando-se na arquitetura de rede, a arquitetura de referência tem os componentes principais a seguir:
- **Virtualização no local** – esse é um cluster do VMware que hospeda atualmente as VMs da Acme Skateboards. São essas VMs que estão atualmente hospedando os aplicativos que serão modernizados. Esse cluster é necessário para atender aos pré-requisitos, conforme descrito no documento [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) para que ele possa executar o HCX. O HCX amplia as redes no local para o {{site.data.keyword.cloud_notm}}, permitindo que os clientes migrem VMs para a instância do VCS em execução no {{site.data.keyword.cloud_notm}} e de volta se necessário.
- **VMware vCenter Server on IBM Cloud** - o VCS fornece os blocos de construção fundamentais do VMware: vSphere, vCenter Server, NSX-V e opções de armazenamento, incluindo armazenamento do vSAN ou do Endurance do {{site.data.keyword.cloud_notm}}, necessários para implementar automaticamente uma solução do VMware Software Defined Data Center (SDDC). Esse cluster do VMware é o destino das VMs migradas, bem como alguns dos aplicativos modernizados em contêineres hospedados no ICP.

  Os componentes principais da arquitetura são:
 - **NSX-V** – o NSX-V fornece a camada de virtualização de rede no VCS que fornece uma sobreposição de rede para VMs da Acme Skateboards. O NSX-V ativa o BYOIP e isola as redes de carga de trabalho das redes do {{site.data.keyword.cloud_notm}}. O NSX-V é programado pelo HCX para criar as redes que a Acme Skateboards ampliará no local.
 - **IBM Cloud Private** - o ICP é uma plataforma de aplicativos para desenvolvimento e gerenciamento de aplicativos em contêiner. É um ambiente integrado que inclui o orquestrador de contêineres Kubernetes, um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário que fornece um local centralizado por meio do qual o Acme Skateboards pode implementar, gerenciar, monitorar e escalar seus aplicativos. A instância do VCS hospeda os componentes do ICP, nós principais, nós do trabalhador e assim por diante, executando-os como VMs.
  -	**IBM Cloud Automation Manager** - o CAM é uma plataforma infrastructure as code (IaC) pronta para empresa que fornece uma única área de janela de vidro para provisionar cargas de trabalho baseadas em máquina virtual juntamente com cargas de trabalho baseadas em Kubernetes, simplesmente usando modelos. O CAM é um aplicativo Dockerizado executado sobre o ICP e é fortemente integrado para autorização, RBAC e outras funções.
  - O **IBM Kubernetes Service** – o IKS permite que o Acme Skateboards implemente seus aplicativos modernizados em contêineres do Docker que são executados em clusters do Kubernetes. Os modos principais são totalmente gerenciados pela IBM enquanto os nós do trabalhador no conjunto de trabalhadores são implementados na mesma conta do {{site.data.keyword.cloud_notm}} como sua instância do VCS. Os nós do trabalhador são instâncias de servidor virtual bare metal, público ou dedicado. O Calico é instalado e configurado automaticamente no IKS. O Calico fornece conectividade de rede segura para contêineres e está configurado no IKS para usar o encapsulamento IP-in-IP para encapsular pacotes que viajam entre sub-redes e usa NAT para conexões de saída dos contêineres.
  - **Direct Link** - o {{site.data.keyword.cloud_notm}} Direct Link usa o provedor de WAN do Acme Skateboard para conectar seu data center ao {{site.data.keyword.cloud_notm}} fornecendo uma conexão de rede confiável, de baixa latência e segura. Esta conexão fornece:
      - Acesso aos aplicativos hospedados em nuvem por meio de seus usuários corporativos.
      - Tráfego entre VMs no local e VMs de nuvem.
      - Tráfego entre sistemas legados no data center no local e nas VMs de nuvem.

## Benefícios importantes para a Acme Skateboards

-	Entrega acelerada de projetos de TI para desenvolvedores e linhas de negócios, reduzindo o tempo que leva para compras, arquitetura, implementação e implementação de recursos de semanas ou mesmo meses até horas. Aguardar que as equipes de rede ou segurança provisionem serviços como balanceadores de carga, firewalls, comutadores e roteadores diminui seu tempo de maturação.
-	Segurança aprimorada com servidores bare metal dedicados em uma nuvem particular host, incluindo a implementação de terminal privado para serviços do {{site.data.keyword.cloud_notm}} como IKS e KMIP.
-	Gerenciamento e controle consistentes da nuvem híbrida implementada fornecendo acesso administrativo total ao gerenciamento de virtualização, preservando, assim, suas ferramentas, scripts e investimentos existentes do VMware em treinamento.
-	Conhecimento do VMware em escala global com o IBM Professional and Managed Services abrangendo 30+ {{site.data.keyword.CloudDataCents_notm}} no mundo inteiro.

Os clientes que se movem para plataformas de aplicativo nativo em nuvem, como o ICP e o IKS, são focados em velocidade e inovação e nem sempre têm segurança e rede em mente. Essa arquitetura de referência mostra como o VCS, o ICP e o IKS movem a Acme Skateboards com segurança ao longo da jornada de modernização do aplicativo.

## Links Relacionados

* [Visão geral do VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
