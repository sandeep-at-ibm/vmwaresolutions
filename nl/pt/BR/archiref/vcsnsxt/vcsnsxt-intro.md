---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Introdução à rede do vCenter Server

Este documento fornece uma visualização da jornada de modernização de aplicativo para o {{site.data.keyword.cloud}}, destacando os aspectos de rede das plataformas a seguir para permitir que uma multinuvem integrada seja usada para modernização do aplicativo:

- **VMware vCenter Server on IBM Cloud** - uma oferta do {{site.data.keyword.vmwaresolutions_short}}, que é uma plataforma baseada em VMware que é provisionada automaticamente no {{site.data.keyword.cloud_notm}}.
- **IBM Cloud Private** - uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados, que são implementados em uma plataforma de infraestrutura virtualizada, como o vCenter Server ou um ambiente do vSphere no local.
- **{{site.data.keyword.containerlong_notm}}** - um serviço gerenciado no {{site.data.keyword.cloud_notm}} que usa o Kubernetes como o mecanismo de orquestração para automatizar a implementação, o ajuste de escala e as operações de contêineres de aplicativos em um cluster de único locatário.

Os maiores desafios na modernização de aplicativo são a migração, a rede e a segurança. O vCenter Server, VMware Hybrid Cloud Extension (HCX), VMware NSX, {{site.data.keyword.containerlong_notm}} e {{site.data.keyword.icpfull_notm}} ajudam a resolver alguns desses desafios. A arquitetura de rede a seguir descreve uma abordagem que usa o Acme Skateboards como um exemplo para conectar componentes que são divididos entre ambientes de nuvem e no local.

A [visualização do NSX-T ](/docs/services/vmwaresolutions/archiref/vcsnsxt/vcsnsxt-techpreview.html) é uma visualização de tecnologia para descrever o uso de VMware NSX Transformers (NSX-T) em uma arquitetura de referência futura. O NSX-T foi projetado para tratar de estruturas de aplicativos e arquiteturas que têm terminais heterogêneos e pilhas de tecnologia. Além do vSphere, esses ambientes podem incluir outros hypervisors, KVM, contêineres e bare metal. O NSX-T permite que as equipes de TI e desenvolvimento escolham as tecnologias mais adequadas para seus aplicativos. O NSX-T também é projetado para gerenciamento, operação e consumo por organizações de desenvolvimento, além de equipes de rede.

## Modernização de aplicativo no IBM Cloud

Modernização de aplicativo é um termo que descreve o processo de transição de aplicativos existentes para usar novas abordagens de desenvolvimento e entrega na nuvem. Os clientes hoje estão buscando abordagens inovadoras e eficientes que ajudam a fazer essa transição com base nos negócios e na complexidade do aplicativo.

As pressões de negócios demandam prazo de lançamento no mercado mais rápido. Seu estado existente inclui não somente aplicativos, mas dados, processos, lógica de negócios e interfaces com o usuário, todos os quais precisam se adaptar para manter novas demandas de negócios.

Os benefícios de modernização de aplicativo incluem os seguintes:

- Melhora a produtividade do Desenvolvedor
- Aumenta a eficiência operacional
- Reduz o custo para construir novos recursos
- Expande a capacidade entregue em um curto período de tempo

A IBM entende que 70% da adoção de nuvem privada está sendo impulsionada pela necessidade de modernizar os ambientes de aplicativos, no entanto, a maioria das organizações está se aproximando da modernização de aplicativo em uma abordagem montada, que necessita de uma paisagem híbrida e multinuvem, em que:

- Os aplicativos anteriores complexos e monolíticos que geralmente são executados em mainframes ou sistemas UNIX permanecem no local.
- Ambientes x86 usados para Sistemas de Registro (SoR), aplicativos que são sensíveis à segurança e cargas de trabalho reguladas são colocados em uma infraestrutura virtualizada ou em uma nuvem privada.
- Os aplicativos, como SAP, ou a computação de alto desempenho consomem recursos bare metal.
- As cargas de trabalho reguladas e sensíveis à segurança, que podem ser movidas para a nuvem pública, estão se movendo para ambientes dedicados.
- Os sistemas de engajamento (SoE), como web, móvel, IoT, IA ou vídeo, estão sendo transferidos para nuvens públicas.

Por exemplo, um padrão comum é ter aplicativos SoE de front-end que são implementados como contêineres com bancos de dados e middleware anterior que são implementados em MVs em uma nuvem privada.

Como sua infraestrutura de TI e as necessidades de negócios são exclusivas, você precisa de uma abordagem para a modernização que acelera o valor de negócios, minimiza o tempo de entrega, reduz seus riscos e preserva seus investimentos existentes. A IBM fornece exatamente uma abordagem para modernização do aplicativo que pode ser customizada para atender às suas necessidades exclusivas de negócios e de tecnologia.

Este documento fornece diferentes visualizações sobre as tecnologias que são usadas na jornada de modernização de aplicativo para o {{site.data.keyword.cloud_notm}}:

* [vCenter Server e {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp/vcsicp-intro.html) - uma arquitetura de referência para implementar as plataformas a seguir:
   - **VMware vCenter Server on IBM Cloud** - uma oferta do {{site.data.keyword.vmwaresolutions_short}} que é uma plataforma baseada em VMware e provisionada automaticamente no {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.icpfull_notm}}** - O {{site.data.keyword.icpfull_notm}} é uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados. É um ambiente integrado que inclui o orquestrador de contêineres Kubernetes, um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário, que fornece um local centralizado por meio do qual é possível implementar, gerenciar, monitorar e escalar seus aplicativos.
   - **IBM Cloud Automation Manager** - o CAM é uma plataforma infrastructure as code pronta para empresa que fornece uma única área de janela de vidro para provisionar cargas de trabalho baseadas em MV ao lado de cargas de trabalho baseadas em Kubernetes usando modelos que são armazenados e com versão em um repositório.
* [vCenter Server e {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks/vcsiks-intro.html) - uma arquitetura de referência para implementar as plataformas a seguir:
   - **VMware vCenter Server on IBM Cloud** - uma oferta do {{site.data.keyword.vmwaresolutions_short}} que é uma plataforma baseada em VMware e provisionada automaticamente no {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.containerlong_notm}}** - um serviço gerenciado no {{site.data.keyword.cloud_notm}} que usa o Kubernetes como o mecanismo de orquestração para automatizar a implementação, o ajuste de escala e as operações de contêineres de aplicativos em um cluster de único locatário.
* _Rede do vCenter Server_ - o guia atual concentra-se nas tecnologias de rede usadas para integração entre o vCenter Server, o {{site.data.keyword.icpfull_notm}} e o {{site.data.keyword.containerlong_notm}}, como NSX-V e Calico, juntamente com uma visualização de tecnologia do NSX-T.
* [VMware e Skate Advisor Concept Car](/docs/services/vmwaresolutions/archiref/vcscar/vcscar-intro.html) - Essa arquitetura de referência é um "carro conceito", ou seja, um mecanismo para destacar e mostrar tecnologias que resolvem problemas do mundo real. Queríamos demonstrar uma interação entre o Watson AI e o aprendizado de máquina de uma maneira real. Por meio da cultura do skate, demonstramos os serviços de nuvem de uma maneira exclusiva. A implementação do "carro conceito" é uma extensão do aplicativo Acme Skateboard, chamado Skate Advisor. O Skate Advisor é uma ferramenta, que permite que os usuários tenham conversas sobre truques de skate com um mecanismo acionado pelo Watson.
* [VMware: a jornada de modernização do Stock Trader](/docs/services/vmwaresolutions/archiref/vcscontent/vcscontent-modjourney.html) - Nosso caso de uso de referência descreve um aplicativo clássico do WebSphere Application Server que está sendo modernizado usando o {{site.data.keyword.cloud_notm}} Private, o conteúdo do IBM Middleware, o {{site.data.keyword.containerlong_notm}} e o vCenter Server on {{site.data.keyword.cloud_notm}}. Estamos todos em uma jornada de nuvens e em pontos diferentes nessa jornada. Por meio de etapas incrementais da arquiteta de aplicativo, Jane, e do arquiteto de infraestrutura em nuvem, Todd, modernizamos um aplicativo existente chamado Stock Trader. Ele mostra exemplos que ajudam a executar cada etapa em sua jornada e o valor que é realizado para seus negócios, independentemente do quanto cada etapa é grande ou pequena. Concentramo-nos em quatro temas: aplicativos, DevOps, integração e gerenciamento. Todos os temas trabalham em conjunto para ajudá-lo a atingir suas metas. Modernizar um tema sem os outros pode resultar em problemas.

### Links relacionados

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
