---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# Introdução aos serviços vCenter Server e IBM Kubernetes

Este documento fornece uma visualização da jornada de modernização de aplicativo para o {{site.data.keyword.cloud}}, destacando os aspectos de rede das plataformas a seguir para permitir que uma multinuvem integrada seja usada para modernização do aplicativo:

Este documento fornece uma visualização da jornada de modernização de aplicativo para o {{site.data.keyword.cloud_notm}}, concentrando-se nos componentes de gerenciamento de nuvem para permitir que uma multinuvem integrada seja usada para a modernização de aplicativo:

- **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - o vCenter Server é uma oferta do {{site.data.keyword.vmwaresolutions_full}} e é uma plataforma baseada em VMware que é provisionada automaticamente no {{site.data.keyword.cloud_notm}}.
- **{{site.data.keyword.cloud_notm}} Private** – o ICP é uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados que são implementados em plataformas de infraestrutura virtualizada, como o VMware.
- **IBM Kubernetes Services** – o IKS é um serviço gerenciado no {{site.data.keyword.cloud_notm}} que usa o Kubernetes como o mecanismo de orquestração para automatizar a implementação, o ajuste de escala e as operações de contêineres de aplicativos em um cluster de único locatário.
- **IBM Multi-Cluster Manager** – o MCM fornece visibilidade do usuário, gerenciamento centrado no aplicativo (política, implementações, funcionamento, operações) e conformidade baseada em política entre nuvens e clusters. Com o MCM, você tem o controle de seus clusters do Kubernetes.
- **{{site.data.keyword.cloud_notm}} Automation Manager** – a CAM é uma plataforma de gerenciamento de autoatendimento com várias nuvens, executada no ICP, que capacita desenvolvedores e administradores para atender às demandas de negócios.

## Modernização de aplicativo no IBM Cloud
Modernização de aplicativo é um termo que descreve o processo de transição de aplicativos existentes para usar novas abordagens na nuvem. Os clientes hoje estão buscando abordagens inovadoras e eficientes que ajudam a fazer essa transição com base nos negócios e na complexidade do aplicativo.

As pressões de negócios demandam prazo de lançamento no mercado mais rápido. Seu estado existente inclui não somente aplicativos, mas dados, processos, lógica de negócios e interfaces com o usuário, todos os quais precisam se adaptar para manter novas demandas de negócios.

Os benefícios de modernização de aplicativo incluem os seguintes:
- Melhor produtividade do desenvolvedor.
- Maior eficiência operacional.
- Custo reduzido para construir novos recursos.
- Capacidade expandida entregue em pouco tempo.

A IBM entende que 70% da adoção de nuvem privada é impulsionada pela necessidade de modernizar os ambientes de aplicativos, no entanto, a maioria das organizações está se aproximando da modernização de aplicativo em uma abordagem montada, que requer uma paisagem híbrida e multinuvem, em que:
- Os aplicativos anteriores complexos e monolíticos que geralmente são executados em mainframes ou sistemas UNIX permanecem no local.
- Os ambientes x86 usados para sistemas de registro (SoR) ou aplicativos que são cargas de trabalho reguladas ou sensíveis à segurança são colocados em infraestrutura virtualizada ou em uma nuvem privada.
- Os aplicativos, como SAP, ou a computação de alto desempenho consomem recursos bare metal.
- As cargas de trabalho reguladas e sensíveis à segurança, que podem ser movidas para a nuvem pública, estão se movendo para ambientes dedicados.
- Os sistemas de engajamento (SoE), como web, móvel, IoT, AI ou Vídeo, estão se movendo para nuvens públicas.

Por exemplo, um padrão comum é ter aplicativos SoE front-end que são implementados como contêineres com bancos de dados e middleware anterior implementados nas VMs em uma nuvem privada.

Como sua infraestrutura de TI e as necessidades de negócios são exclusivas, você precisa de uma abordagem para modernização que ajude a acelerar a entrega de valor de negócios, reduza seus riscos e preserve seus investimentos existentes. A IBM fornece apenas uma abordagem que pode ser customizada para atender às suas necessidades exclusivas de negócios e de tecnologia relacionadas à modernização de aplicativo.

Este documento é um dos cinco que fornecem diferentes visualizações sobre as tecnologias usadas na jornada de modernização de aplicativo para o {{site.data.keyword.cloud_notm}}:

* [vCenter Server e {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) - uma arquitetura de referência para implementar as plataformas a seguir:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** – uma oferta do {{site.data.keyword.vmwaresolutions_full}} que é uma plataforma baseada em VMware provisionada automaticamente no {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.cloud_notm}} Private** – uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados. O ICP é um ambiente integrado que inclui o orquestrador de contêineres Kubernetes e um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário, que fornece um local centralizado por meio do qual é possível implementar, gerenciar, monitorar e escalar seus aplicativos.
  - **{{site.data.keyword.cloud_notm}} Automation Manager** – uma plataforma Infrastructure as Code (IaC) pronta para a empresa que fornece um único painel de controle para provisionar cargas de trabalho baseadas em VM ao lado de cargas de trabalho baseadas em Kubernetes usando modelos armazenados e com versão em um repositório.
* [vCenter Server e {{site.data.keyword.cloud_notm}} Private](../vcsiks/vcsiks-intro.html) - uma arquitetura de referência para implementar as plataformas a seguir:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** – uma oferta do {{site.data.keyword.vmwaresolutions_full}} que é uma plataforma baseada em VMware provisionada automaticamente no {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.cloud_notm}} Kubernetes Service** – serviço gerenciado no {{site.data.keyword.cloud_notm}} que usa o Kubernetes como o mecanismo de orquestração para automatizar a implementação, o ajuste de escala e as operações de contêineres de aplicativos em um cluster de único locatário.
* [Rede do vCenter Server](../vcsnsxt/vcsnsxt-intro.html) - concentra-se nas tecnologias de rede que são usadas dentro do vCenter Server, ICP e IKS, como NSX-V, NSX-T e Calico.
* [Carro-conceito VMware e Skate Advisor](../vcscar/vcscar-intro.html) – Essa arquitetura de referência é um "carro-conceito", isto é, um mecanismo para destacar e mostrar tecnologias que resolvem problemas do mundo real. Queríamos demonstrar uma interação entre o Watson AI e o aprendizado de máquina de uma maneira real. Por meio da cultura do skate, demonstramos os serviços de nuvem de uma maneira exclusiva. A implementação do "carro conceito" é uma extensão do aplicativo Acme Skateboard, chamado Skate Advisor. O Skate Advisor é uma ferramenta, que permite que os usuários tenham conversas sobre truques de skate com um mecanismo acionado pelo Watson.
* [VMware: a jornada de modernização do Stock Trader](../vcscontent/vcscontent-modjourney.html) – Nosso caso de uso de referência descreve um aplicativo clássico do WebSphere Application Server que está sendo modernizado usando o {{site.data.keyword.cloud_notm}} Private, o conteúdo do IBM Middleware, o {{site.data.keyword.cloud_notm}} Kubernetes Service e o vCenter Server on {{site.data.keyword.cloud_notm}}. Estamos todos em uma jornada de nuvem e em pontos diferentes nessa jornada. Por meio de etapas incrementais da arquiteta de aplicativo, Jane, e do arquiteto de infraestrutura em nuvem, Todd, modernizamos um aplicativo existente chamado Stock Trader. Ele mostra exemplos que ajudam a executar cada etapa de sua jornada, além do valor realizado para seus negócios, independentemente do tamanho de cada etapa. Concentramo-nos em quatro temas: aplicativos, DevOps, integração e gerenciamento. Cada um deles trabalha em conjunto para ajudá-lo a atingir seus objetivos e, de fato, modernizar um sem os outros resulta em problemas por toda a parte.

### Links relacionados

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
