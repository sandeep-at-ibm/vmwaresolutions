---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# Introdução ao vCenter Server e ao IBM Cloud Private

Este documento fornece uma visualização da jornada de modernização de aplicativo para o IBM Cloud, focando os componentes de gerenciamento de nuvem para permitir que uma multinuvem integrada seja alavancada para modernização de aplicativo:

- **VMware vCenter Server on IBM Cloud** - o VCS é uma oferta do IBM Cloud for VMware Solutions e é uma plataforma baseada em VMware provisionada automaticamente no IBM Cloud.
- **IBM Cloud Private** - o ICP é uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados, que são projetados para serem implementados em plataformas de infraestrutura virtualizada, como o VMware.
- **IBM Kubernetes Services** - o IKS é um serviço gerenciado no IBM Cloud que alavanca o Kubernetes como o mecanismo de orquestração para automatizar a implementação, o ajuste de escala e as operações de contêineres de aplicativos em um cluster de locatário único
- **IBM Multi-Cluster Manager** – o MCM fornece visibilidade do usuário, gerenciamento centrado no aplicativo (política, implementações, funcionamento, operações) e conformidade baseada em política entre nuvens e clusters. Com o MCM, você tem o controle de seus clusters do Kubernetes.
- **IBM Cloud Automation Manager** – o CAM é uma plataforma de gerenciamento de autoatendimento multinuvem em execução no ICP que confere poderes os desenvolvedores e administradores para atender às demandas de negócios.

## Modernização de aplicativo no IBM Cloud

A modernização de aplicativo é um termo que descreve o processo de transição de aplicativos existentes para alavancar novas abordagens na nuvem. Os clientes hoje estão buscando abordagens inovadoras e eficientes que ajudam a fazer essa transição com base nos negócios e na complexidade do aplicativo.

As pressões de negócios demandam prazo de lançamento no mercado mais rápido. Seu estado existente inclui não somente aplicativos, mas dados, processos, lógica de negócios e interfaces com o usuário, todos os quais precisam se adaptar para manter novas demandas de negócios.

Os benefícios de modernização de aplicativo incluem os seguintes:
- Maior produtividade do desenvolvedor.
- Maior eficiência operacional.
- Custo reduzido para construir novos recursos.
- Capacidade expandida entregue em pouco tempo.

A IBM entende que 70% da adoção de nuvem privada está sendo impulsionada pela necessidade de modernizar os ambientes de aplicativos, no entanto, a maioria das organizações está se aproximando da modernização de aplicativo em uma abordagem montada, que necessita de uma paisagem híbrida e multinuvem, em que:
- Os aplicativos anteriores complexos e monolíticos que geralmente são executados em mainframes ou sistemas UNIX permanecem no local.
- Os ambientes x86 usados para sistemas de registro (SoR) ou aplicativos que são cargas de trabalho reguladas ou sensíveis à segurança são colocados em infraestrutura virtualizada ou em uma nuvem privada.
- Os aplicativos, como SAP, ou a computação de alto desempenho consomem recursos bare metal.
- As cargas de trabalho reguladas e sensíveis à segurança, que podem ser movidas para a nuvem pública, estão se movendo para ambientes dedicados.
- Os sistemas de engajamento (SoE), como web, móvel, IoT, AI ou Vídeo, estão se movendo para nuvens públicas.

Por exemplo, um padrão comum é ter aplicativos front-end e SOE implementados como contêineres com bancos de dados e middleware anterior implementados nas VMs em uma nuvem privada.

Como sua infraestrutura de TI e as necessidades de negócios são exclusivas, você precisa de uma abordagem para modernização que ajude a acelerar a entrega de valor de negócios, reduza seus riscos e preserve seus investimentos existentes. A IBM fornece apenas uma abordagem que pode ser customizada para atender às suas necessidades exclusivas de negócios e de tecnologia relacionadas à modernização de aplicativo.

Este documento é um dos cinco documentos que fornece diferentes visualizações sobre as tecnologias usadas na jornada de modernização de aplicativo para o IBM Cloud:

* _vCenter Server e IBM Cloud Private_ - o guia atual, que é uma arquitetura de referência para implementar as plataformas a seguir:
  - **VMware vCenter Server on IBM Cloud** - uma oferta do IBM Cloud for VMware Solutions; é uma plataforma baseada no VMware provisionada automaticamente no IBM Cloud.
  - **IBM Cloud Private** – uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados. É um ambiente integrado que inclui o orquestrador de contêineres Kubernetes, bem como um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário, que fornece um local centralizado por meio do qual é possível implementar, gerenciar, monitorar e escalar seus aplicativos.
  - **IBM Cloud Automation Manager** – uma plataforma Infrastructure as Code (IaC) pronta para empresa que fornece uma única área de janela de vidro para provisionar cargas de trabalho baseadas em VM juntamente com cargas de trabalho baseadas em Kubernetes, simplesmente usando modelos que estão armazenados e com versão em um repositório.
* [vCenter Server e serviço IBM Kubernetes](../vcsiks/vcsiks-intro.html) - Esse guia é uma arquitetura de referência para implementar as plataformas a seguir:
  - **VMware vCenter Server on IBM Cloud** - uma oferta do IBM Cloud for VMware Solutions; é uma plataforma baseada no VMware provisionada automaticamente no IBM Cloud.
  - **IBM Cloud Kubernetes Service** – serviço gerenciado no IBM Cloud que alavanca o Kubernetes como o mecanismo de orquestração para automatizar a implementação, o ajuste de escala e as operações de contêineres de aplicativos em um cluster de único locatário.
* [Rede do vCenter Server](../vcsnsxt/vcsnsxt-intro.html) - Esse guia se concentra nas tecnologias de rede usadas no VCS, no ICP e no IKS, como NSX-V, NSX-T e Calico.
* [VMware e Skate Advisor Concept Car](../vcscar/vcscar-intro.html) - Essa arquitetura de referência é um "carro conceito", ou seja, um mecanismo para destacar e mostrar tecnologias que resolvem problemas do mundo real. Queríamos demonstrar uma interação entre o Watson AI e o aprendizado de máquina de uma maneira real. Acima de tudo, através da cultura do skate, demonstramos serviços de nuvem de uma forma exclusiva. A implementação do "carro conceito" é uma extensão do aplicativo Acme Skateboard, chamado Skate Advisor. O Skate Advisor é uma ferramenta, que permite que os usuários tenham conversas sobre truques de skate com um mecanismo acionado pelo Watson.
* [VMware: a jornada de modernização do Stock Trader](../vcscontent/vcscontent-modjourney.html) - Nosso caso de uso de referência descreve um aplicativo clássico do WebSphere Application Server que está sendo modernizado usando o IBM Cloud Private, o conteúdo do IBM Middleware, o IBM Cloud Kubernetes Service e o vCenter Server on IBM Cloud. Estamos todos em uma jornada de nuvens e em pontos diferentes nessa jornada. Por meio de etapas incrementais pela arquiteta do aplicativo, Jane, e o arquiteto de infraestrutura em nuvem, Todd, modernizamos um app existente chamado Stock Trader. Ele mostra exemplos que ajudam a executar cada etapa de sua jornada, além do valor realizado para seus negócios, independentemente do tamanho de cada etapa. Concentramo-nos em quatro temas: aplicativos, DevOps, integração e gerenciamento. Cada um deles trabalha em conjunto para ajudá-lo a atingir seus objetivos e, de fato, modernizar um sem os outros resulta em problemas por toda a parte.

### Links relacionados

* [Visão geral do VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
