---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-13"

---

# Introdução ao VMware e ao Protótipo do Skate Advisor

A arquitetura de referência a seguir é um “protótipo”, isto é, um mecanismo para
destacar e mostrar tecnologias que resolvem problemas do mundo real. O “protótipo” não representa de modo algum um
serviço prontamente disponível hoje.

A arquitetura de referência também fornece as informações a seguir:

-   Fornece linguagem comum para as várias partes interessadas.
-   Fornece consistência de implementação de tecnologia para resolver problemas.
-   Suporta a validação de soluções com relação a uma arquitetura de referência
comprovada.
-   Incentiva a adesão a normas,
especificações e padrões comuns.

## Sobre o ACME Skate Advisor

Desejávamos demonstrar uma interação entre a inteligência artificial
do Watson e o aprendizado de máquina de uma maneira real e por meio disso explorar
mais profundamente a cultura do skateboarding. Demonstramos os serviços disponíveis e a infraestrutura em nuvem de uma forma exclusiva, demonstrando a capacidade técnica e os avanços nesta área. A implementação do "protótipo" é uma extensão do
aplicativo Acme Skateboard demonstrativo, chamado Skate Advisor. O Skate Advisor é uma ferramenta, que permite que os usuários tenham conversas sobre truques de skate com um mecanismo acionado pelo Watson. As citações a seguir são uma conversa de amostra:

-   “Watson, mostre-me as combinações da manobra Casper”
-   “Watson, mostre-me locais comuns para executar uma manobra”
-   “Watson, mostre-me um vídeo da manobra Casper”

O Acme Skate Advisor aproveita o Watson Discovery Service para
alimentar artigos, vídeos, blogs e outros conteúdos baseados na Internet para
criar um banco de dados de manobras aprendidas, que pode ser consultado pelo
aplicativo.

O aplicativo Skate Advisor também é implementado na plataforma de
modernização de aplicativo, que fornece serviços baseados em contêiner por meio do
{{site.data.keyword.cloud}} Private (ICP) hospedado na plataforma {{site.data.keyword.cloud_notm}} for VMware Services.

O aplicativo Acme Skate Advisor aproveita tanto a plataforma
Watson quanto a plataforma de modernização de aplicativo.

## Casos de uso

### Demonstração de modernização de aplicativo

Demonstre um aplicativo que tenha sido implementado na plataforma de
modernização de aplicativo. A plataforma inclui os componentes ICP, CAM e NSX
implementados no {{site.data.keyword.cloud_notm}} para a oferta VMware vCenter Server on
{{site.data.keyword.cloud_notm}}.

### Reconhecimento de voz do Watson com o Watson Assistant

O Acme Skate Advisor se comunica com os usuários por meio de um serviço de
fala para texto e de texto para fala que é fornecido com a plataforma Watson.

### Uso e treinamento do Watson Discovery Service

O Acme Skate Advisor usa o Watson Discovery Services para manter
o controle de um banco de dados de Manobras para as quais uma linguagem de classificação é aplicada e as manobras descobertas por meio de serviços on-line.

### Uso de serviços do Watson

Os serviços do Watson a seguir foram usados para criar o Acme Skate
Advisor:
-   Watson Text to Speech.
-   Watson Speech to Text.
-   Watson Advisor.
-   Watson Discovery Service.
-   Watson Knowledge Studio.

## Modernização de aplicativo no IBM Cloud

Modernização de aplicativo é um termo que descreve o processo de transição de aplicativos existentes para usar novas abordagens de desenvolvimento e entrega na nuvem. Os clientes hoje estão buscando abordagens inovadoras e eficientes que ajudam a fazer essa transição com base nos negócios e na complexidade do aplicativo.

As pressões de negócios demandam prazo de lançamento no mercado mais rápido. Seu estado existente inclui não somente aplicativos, mas dados, processos, lógica de negócios e interfaces com o usuário, todos os quais precisam se adaptar para manter novas demandas de negócios.

A lista a seguir descreve os benefícios da modernização de aplicativo:

- Melhora a produtividade do Desenvolvedor
- Aumenta a eficiência operacional
- Reduz o custo para construir novos recursos
- Expande a capacidade entregue em um curto período de tempo

A IBM entende que 70 por cento da adoção de nuvem privada é impulsionada pela
necessidade de modernizar os ambientes de aplicativos. No entanto, a maioria
das organizações está se aproximando da modernização de aplicativo em uma abordagem
montada, que requer uma paisagem híbrida e multinuvem, em que:

- Aplicativos legados complexos e monolíticos que geralmente são executados em
mainframes ou sistemas UNIX que permanecem no local.
- Os ambientes x86 usados para Sistemas de registro (SoR) ou aplicativos que são cargas de trabalho reguladas ou sensíveis à segurança são colocados em infraestrutura virtualizada ou em uma nuvem privada.
- Aplicativos como o SAP ou a computação de alto desempenho usam
recursos bare metal.
- As cargas de trabalho reguladas e sensíveis à segurança, que podem ser movidas para a nuvem pública, estão se movendo para ambientes dedicados.
- Os sistemas de engajamento (SoE), como web, móvel, IoT, IA ou vídeo, estão sendo transferidos para nuvens públicas.

Por exemplo, um padrão comum é ter aplicativos SoE de front-end implementados como contêineres com bancos de dados e middleware legado que são implementados em
VMs em uma nuvem privada.

Como a infraestrutura de TI e as necessidades de negócios são exclusivas, uma abordagem à modernização deve fornecer as prioridades a seguir:

* Acelerar valor de negócios
* Minimizar o tempo de entrega
* Reduzir riscos
* Preservar investimentos existentes.

A IBM fornece exatamente uma abordagem para modernização do aplicativo que pode ser customizada para atender às suas necessidades exclusivas de negócios e de tecnologia.

Os documentos a seguir fornecem diferentes visualizações sobre as tecnologias que são usadas na jornada de modernização de aplicativo para o {{site.data.keyword.cloud_notm}}:

* [vCenter Server e {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) - uma arquitetura de referência para implementar as plataformas a seguir.
   - **VMware vCenter Server on IBM Cloud** – o vCenter Server é uma oferta do {{site.data.keyword.vmwaresolutions_short}} que é uma plataforma baseada em VMware provisionada automaticamente no {{site.data.keyword.cloud_notm}}.
   - **IBM Cloud Private** – o ICP é uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados. O ICP é um ambiente integrado que inclui o orchestrator de contêineres Kubernetes, um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário. A interface com o usuário fornece um local centralizado por meio do qual é possível implementar, gerenciar, monitorar e escalar seus aplicativos.
   - **IBM Cloud Automation Manager** - o CAM é uma plataforma infrastructure as code pronta para empresa que fornece uma única área de janela de vidro para provisionar cargas de trabalho baseadas em VM ao lado de cargas de trabalho baseadas em Kubernetes usando modelos que são armazenados e com versão em um repositório.
* [vCenter Server e IBM Kubernetes Service](../vcsiks/vcsiks-intro.html) - uma arquitetura de referência para implementar as plataformas a seguir.
   - **VMware vCenter Server on IBM Cloud** – o vCenter Server é uma oferta do {{site.data.keyword.vmwaresolutions_short}} que é uma plataforma baseada em VMware provisionada automaticamente no {{site.data.keyword.cloud_notm}}.
   - **IBM Cloud Kubernetes Service** - o IKS é um serviço gerenciado no {{site.data.keyword.cloud_notm}} que usa o Kubernetes como o mecanismo de orquestração para automatizar a implementação, o ajuste de escala e as operações de contêineres de aplicativos em um cluster de único locatário.
* [Rede do vCenter Server](../vcsnsxt/vcsnsxt-intro.html) - concentra-se nas tecnologias de rede que são usadas para integração entre o vCenter Server, o ICP e o IKS, como NSX-V e Calico, juntamente com uma visualização de tecnologia do NSX-T.
* _Guia do VMware e do Protótipo do Skate Advisor_ - uma arquitetura de referência que é um “protótipo”, ou seja, um mecanismo para destacar e mostrar tecnologias que resolvem problemas reais do mundo. Queríamos demonstrar uma interação entre o Watson AI e o aprendizado de máquina de uma maneira real. Por meio da cultura do skate, demonstramos os serviços de nuvem de uma maneira exclusiva. A implementação do "carro conceito" é uma extensão do aplicativo Acme Skateboard, chamado Skate Advisor. O Skate Advisor é uma ferramenta, que permite que os usuários tenham conversas sobre truques de skate com um mecanismo acionado pelo Watson.
* [VMware: a jornada de modernização do Stock Trader](../vcscontent/vcscontent-modjourney.html) - um caso de uso de referência que descreve um aplicativo clássico do WebSphere Application Server que é modernizado usando o {{site.data.keyword.cloud_notm}} Private, o conteúdo do IBM Middleware, o {{site.data.keyword.cloud_notm}} Kubernetes Service e o vCenter Server on {{site.data.keyword.cloud_notm}}. Estamos todos em uma jornada de nuvem e estamos todos em pontos diferentes nessa jornada. Por meio de etapas incrementais da arquiteta de aplicativo, Jane, e do arquiteto de infraestrutura em nuvem, Todd, modernizamos um aplicativo existente chamado Stock Trader. Revise exemplos que ajudam a executar cada etapa em sua jornada e o valor que é realizado para seus negócios, independentemente de cada etapa ser grande ou pequena. Concentramo-nos em quatro temas: aplicativos, DevOps, integração e gerenciamento. Cada um deles trabalha em conjunto para ajudá-lo a atingir seus objetivos e, de fato, modernizar um sem os outros resulta em problemas por toda a parte.

### Links relacionados

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
