---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# Introdução ao VMware vCenter Server on IBM Cloud e ao IBM Cloud Private
{: #vcsicp-intro}

Este documento fornece uma visualização da jornada de modernização de aplicativo para o {{site.data.keyword.cloud}}, concentrando-se nos componentes de gerenciamento de nuvem para permitir que uma multinuvem integrada seja usada para a modernização de aplicativo:

- **vCenter Server on {{site.data.keyword.cloud_notm}}** - o vCenter Server é uma oferta do {{site.data.keyword.vmwaresolutions_short}} e é uma plataforma baseada em VMware provisionada automaticamente no {{site.data.keyword.cloud_notm}}.
- **{{site.data.keyword.icpfull_notm}}** - O {{site.data.keyword.icpfull_notm}} é uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados que são implementados em plataformas de infraestrutura virtualizada, como o VMware.
- **{{site.data.keyword.containerlong_notm}}** - O {{site.data.keyword.containerlong_notm}} é um serviço gerenciado no {{site.data.keyword.cloud_notm}} que usa o Kubernetes como o mecanismo de orquestração para automatizar a implementação, o ajuste de escala e as operações de contêineres de aplicativos em um único cluster de locatário
- **IBM Multi-Cluster Manager** – o MCM fornece visibilidade do usuário, gerenciamento centrado no aplicativo (política, implementações, funcionamento, operações) e conformidade baseada em política entre nuvens e clusters. Com o MCM, você tem o controle de seus clusters do Kubernetes.
- **{{site.data.keyword.cloud_notm}} Automation Manager** – CAM é uma plataforma de gerenciamento de autoatendimento com várias nuvens executada no {{site.data.keyword.icpfull_notm}} que permite que Desenvolvedores e administradores atendam às demandas de negócios.

## Modernização de aplicativo no IBM Cloud
{: #vcsicp-intro-app-mod}

Modernização de aplicativo é um termo que descreve o processo de transição de aplicativos existentes para usar novas abordagens na nuvem. Os clientes hoje estão buscando abordagens inovadoras e eficientes que ajudam a fazer essa transição com base nos negócios e na complexidade do aplicativo.

As pressões de negócios demandam prazo de lançamento no mercado mais rápido. Seu estado existente inclui não somente aplicativos, mas dados, processos, lógica de negócios e interfaces com o usuário, todos os quais precisam se adaptar para manter novas demandas de negócios.

Os benefícios de modernização de aplicativo incluem os seguintes:

- Melhor produtividade do desenvolvedor.
- Maior eficiência operacional.
- Custo reduzido para construir novos recursos.
- Capacidade expandida entregue em pouco tempo.

A IBM entende que 70% da adoção de nuvem privada é impulsionada pela necessidade de modernizar os ambientes de aplicativos. No entanto, a maioria das organizações está se aproximando da modernização de aplicativo em uma abordagem montada, que requer uma paisagem híbrida e multinuvem, em que:

- Os aplicativos anteriores complexos e monolíticos que geralmente são executados em mainframes ou sistemas UNIX permanecem no local.
- Ambientes x86 usados para Sistemas de Registro (SoR), aplicativos que são sensíveis à segurança e cargas de trabalho reguladas são colocados em uma infraestrutura virtualizada ou em uma nuvem privada.
- Os aplicativos, como SAP, ou a computação de alto desempenho consomem recursos bare metal.
- As cargas de trabalho reguladas e sensíveis à segurança, que podem ser movidas para a nuvem pública, estão se movendo para ambientes dedicados.
- Os sistemas de engajamento (SoE), como web, móvel, IoT, AI ou Vídeo, estão se movendo para nuvens públicas.

Por exemplo, um padrão comum é ter aplicativos SoE front-end que são implementados como contêineres com bancos de dados e middleware anterior implementados nas MVs em uma nuvem privada.

Como sua infraestrutura de TI e as necessidades de negócios são exclusivas, você precisa de uma abordagem para modernização que ajude a acelerar a entrega de valor de negócios, reduza seus riscos e preserve seus investimentos existentes. A IBM fornece apenas uma abordagem que pode ser customizada para atender às suas necessidades exclusivas de negócios e de tecnologia relacionadas à modernização de aplicativo.

Este documento é um dos cinco que fornecem diferentes visualizações sobre as tecnologias usadas na jornada de modernização de aplicativo para o {{site.data.keyword.cloud_notm}}:

* _vCenter Server e {{site.data.keyword.icpfull_notm}}_ - o guia atual, que é uma arquitetura de referência para implementar as plataformas a seguir:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** – uma oferta do {{site.data.keyword.vmwaresolutions_short}} que é uma plataforma baseada em VMware provisionada automaticamente no {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.icpfull_notm}}** - uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados. O {{site.data.keyword.icpfull_notm}} é um ambiente integrado que inclui o orquestrador de contêineres Kubernetes, um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário, que fornece um local centralizado por meio do qual é possível implementar, gerenciar, monitorar e escalar seus aplicativos.
  - **{{site.data.keyword.cloud_notm}} Automation Manager** – uma plataforma Infrastructure as Code (IaC) pronta para a empresa que fornece um único painel de controle para provisionar cargas de trabalho baseadas em MV ao lado de cargas de trabalho baseadas em Kubernetes usando modelos armazenados e com versão em um repositório.
* [vCenter Server e {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) - uma arquitetura de referência para implementar as plataformas a seguir:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** – uma oferta do {{site.data.keyword.vmwaresolutions_short}} que é uma plataforma baseada em VMware provisionada automaticamente no {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.containerlong_notm}}** - Serviço gerenciado no {{site.data.keyword.cloud_notm}} que usa o Kubernetes o mecanismo de orquestração para automatizar a implementação, o ajuste de escala e as operações de contêineres de aplicativos em um cluster de único locatário.
* [Rede do vCenter Server](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro) - esse guia se concentra nas tecnologias de rede que são usadas no vCenter Server, {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}, como NSX-V, NSX-T e Calico.
* [Carro-conceito VMware e Skate Advisor](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro) – Essa arquitetura de referência é um "carro-conceito", isto é, um mecanismo para destacar e mostrar tecnologias que resolvem problemas do mundo real. Queríamos demonstrar uma interação entre o Watson AI e o aprendizado de máquina de uma maneira real. Por meio da cultura do skate, demonstramos os serviços de nuvem de uma maneira exclusiva. A implementação do "carro conceito" é uma extensão do aplicativo Acme Skateboard, chamado Skate Advisor. O Skate Advisor é uma ferramenta, que permite que os usuários tenham conversas sobre truques de skate com um mecanismo acionado pelo Watson.
* [VMware: a jornada de modernização do Stock Trader](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney) - nosso caso de uso de referência descreve um aplicativo clássico do WebSphere Application Server que é modernizado usando o {{site.data.keyword.icpfull_notm}}, o conteúdo do IBM Middleware, o {{site.data.keyword.containerlong_notm}} e o vCenter Server. Estamos todos em uma jornada de nuvem e em pontos diferentes nessa jornada. Por meio de etapas incrementais pela arquiteta do aplicativo, Jane, e o arquiteto de infraestrutura em nuvem, Todd, modernizamos um app existente chamado Stock Trader. Isso mostra exemplos que ajudam a executar cada etapa em sua jornada e o valor que é realizado para seus negócios, independentemente de cada etapa ser grande ou pequena. Concentramo-nos em quatro temas: aplicativos, DevOps, integração e gerenciamento. Todos os temas trabalham em conjunto para ajudá-lo a atingir suas metas. Modernizar um tema sem os outros pode resultar em problemas.

## Links relacionados
{: #vcsicp-intro-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
