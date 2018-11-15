---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

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

Guia de Arquitetura de Referência – VCS-ICP e CAM - a seção atual.

Uma arquitetura de referência para implementação das plataformas a seguir:
  - **VMware vCenter Server on IBM Cloud** - uma oferta do IBM Cloud for VMware Solutions; é uma plataforma baseada no VMware provisionada automaticamente no IBM Cloud.
  - **IBM Cloud Private** – uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados. É um ambiente integrado que inclui o orquestrador de contêineres Kubernetes, bem como um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário, que fornece um local centralizado por meio do qual é possível implementar, gerenciar, monitorar e escalar seus aplicativos.
  - **IBM Cloud Automation Manager** – uma plataforma Infrastructure as Code (IaC) pronta para empresa que fornece uma única área de janela de vidro para provisionar cargas de trabalho baseadas em VM juntamente com cargas de trabalho baseadas em Kubernetes, simplesmente usando modelos que estão armazenados e com versão em um repositório.

[ Guia de Arquitetura de Referência, VCS-IKS ](../vcsiks/vcsiks-intro.html)

  Uma arquitetura de referência para implementação das plataformas a seguir:
  - **VMware vCenter Server on IBM Cloud** - uma oferta do IBM Cloud for VMware Solutions; é uma plataforma baseada no VMware provisionada automaticamente no IBM Cloud.
  - **IBM Cloud Kubernetes Service** – serviço gerenciado no IBM Cloud que alavanca o Kubernetes como o mecanismo de orquestração para automatizar a implementação, o ajuste de escala e as operações de contêineres de aplicativos em um cluster de único locatário.

[Guia de Arquitetura de referência, VCS – Rede](../vcsnsxt/vcsnsxt-intro.html)

Esse documento foca as tecnologias de rede usadas dentro do VCS, do ICP e do IKS, como o NSX-V, o NSX-T e o Calico.

[Guia de Arquitetura de Referência, o Watson e o Sk8boarding Concept Car](../vcscar/vcscar-intro.html)

Esse documento usa uma abordagem de “carro conceito” para demonstrar uma interação entre o Watson AI e o aprendizado de máquina.

O documento destaca as tecnologias a seguir:
  - **Pepper** - uma interface que inclui a capacidade de integração
com o ambiente de nuvem para executar o aplicativo e as operações de procura.
  - **VMware vCenter Server on IBM Cloud** - utilizado para hospedar elementos do aplicativo,
como as cargas de trabalho do banco de dados.
  - **IBM Cloud Kubernetes Service** - utilizado para hospedar os
elementos conteinerizados do aplicativo.
  - **IBM Cloud Private** - alavancado para fornecer a orquestração de nível de plataforma e serviços, incluiu a capacidade de hospedar e escalar o aplicativo nas plataformas de VM e de contêiner. Esse componente também permitiu a ativação dos serviços do desenvolvedor do Watson para a plataforma, permitindo o acesso aos recursos de AI.

[ Guia de Arquitetura de Referência, VCS-Conteúdo ](../vcscontent/vcscontent-intro.html)

Este documento foca os tipos de conteúdo a seguir disponíveis no IBM Cloud Automation Manager:
- Conteúdo do catálogo interno, como gráficos Helm “pré-formatados”, modelos Terraform e receitas do Chef.
- Conteúdo de serviços, como serviços Blockchain e Watson.

### Links Relacionados

  * [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
