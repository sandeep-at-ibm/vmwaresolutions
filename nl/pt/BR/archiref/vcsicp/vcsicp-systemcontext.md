---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# Contexto do sistema

Figura 1. Diagrama de contexto de sistema
![Diagrama de contexto de sistema - vCenter Server ICP CAM](vcsicp-syscontext-vcs-icp-cam.svg)

A seguir estão os componentes principais:

- **Virtualização no local** - esse componente é um ambiente do VMware que é hospedado nas instalações do cliente ou em um local de terceiros e hospeda atualmente as máquinas virtuais (VMs) que executam os aplicativos a serem modernizados. A virtualização no local é o ambiente de origem para migrações de VM e é fracamente acoplada a uma instância do {{site.data.keyword.cloud}} via VMware Hybridity (HCX).
- **vCenter Server** – o VMware vCenter Server on {{site.data.keyword.cloud_notm}} é uma instância do {{site.data.keyword.vmwaresolutions_short}} que é o destino para VMs migradas do ambiente no local. Junto ao ambiente virtualizado no local, ele forma um ambiente híbrido que permite que as VMs se movam de um site para o outro.
- **{{site.data.keyword.cloud_notm}} Kubernetes Service** – o IKS usa o Kubernetes como a solução de orquestração do contêiner. A IBM opera e gerencia o nó principal do Kubernetes enquanto os nós do trabalhador são implementados na infraestrutura gerenciada pelo cliente. A IBM fornece ferramentas de gerenciamento para implementação de correção do sistema operacional, upgrades de mecanismo de Docker e novas versões do Kubernetes. O IKS fornece uma plataforma isolada e segura para gerenciar contêineres que são móveis, extensíveis e com capacidade de recuperação automática no caso de ocorrerem failovers.
- **{{site.data.keyword.cloud_notm}} Private** – o ICP é uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados. O ICP é um ambiente integrado que inclui o orquestrador de contêiner Kubernetes, um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário, que fornece um local centralizado por meio do qual é possível implementar, gerenciar, monitorar e escalar aplicativos.
- **{{site.data.keyword.cloud_notm}} Automation Manager** - o CAM é uma plataforma infrastructure as code (IaC) pronta para empresa que fornece uma única área de janela de vidro para provisionar cargas de trabalho baseadas em VMware juntamente com cargas de trabalho baseadas em Kubernetes. A automação de fornecimento de carga de trabalho para máquinas virtuais, contêineres e seus pré-requisitos de infraestrutura é ativada por meio do CAM.
- **IBM Multi Cloud Manager** – o MCM fornece visibilidade do usuário, gerenciamento centrado no aplicativo (política, implementações, funcionamento, operações) e conformidade baseada em política entre nuvens e clusters. Com o MCM, você tem o controle de seus clusters do Kubernetes.
- **{{site.data.keyword.cloud_notm}} Services** – o {{site.data.keyword.cloud_notm}} Services é uma ampla gama de serviços consumíveis disponíveis, incluindo ofertas de analítica, IA e IoT.

## Atores

Tabela 1. Atores

Ator | Descrição
--|--
Administrador do Sistema | O recurso qualificado do VMware vSphere que usa o vCenter Server para gerenciar a virtualização no local e a instância do vCenter Server.
Desenvolvedor | O recurso qualificado do contêiner que usa o console do CAM para criar e gerenciar contêineres. Ele cria os novos serviços como parte da modernização de aplicativo. Usando o CAM, o Desenvolvedor provisiona cargas de trabalho no vCenter Server, ICP ou IKS, edita e orquestra serviços que são construídos com VMs e contêineres e integra cadeias de ferramentas do DevOps e soluções day-2 ITSM.
Cliente | Agente externo que consome serviços da empresa. Para a Acme Skateboards, o cliente é um skatista que deseja comprar produtos de skate. O cliente requer acesso seguro à Internet para o catálogo.
IBM IKS | O recurso IBM que gerencia o Nó principal do IKS para o serviço.

## Sistemas

Tabela 2. Sistemas

Ator | Descrição
--|--
vCenter Server | Interface primária que o administrador do sistema usa para gerenciar as VMs no local e as VMs do {{site.data.keyword.cloud_notm}} na instância do vCenter Server.
VMs em pré-mise| Servidores virtualizados que hospedam os aplicativos destinados para migração no {{site.data.keyword.cloud_notm}}. Migrados inicialmente como VMs e refaturadas de VMs para contêineres para modernização de aplicativo.
VMs do {{site.data.keyword.cloud_notm}} | Servidores virtualizados que hospedam os aplicativos migrados do data center no local. Para esta arquitetura de referência e para o Acme Skateboards, uma das VMs do {{site.data.keyword.cloud_notm}} é um servidor de banco de dados, que faz parte da carga de trabalho de presença on-line.
Catálogo de conteúdo corporativo | Local centralizado por meio do qual é possível procurar e instalar pacotes em seu cluster. O catálogo contém vários pacotes IBM que são usados para criar contêineres, bem como acessar os gráficos de Helm. Helm é uma ferramenta para gerenciar os gráficos do Kubernetes. Os gráficos são pacotes de recursos pré-configurados do Kubernetes que facilitam a versão, o pacote, a liberação, a implementação, a exclusão, o upgrade e até mesmo o retrocesso de implementações do contêiner. O Helm é o sistema de gerenciamento de pacote nativo do Kubernetes e é usado para gerenciamento de aplicativo dentro de um cluster do ICP.
Core Operational Services | O ICP inclui uma série de ferramentas para coletar, armazenar e consultar logs e métricas. Essas ferramentas fornecem um armazenamento centralizado para todos os logs e métricas e entregam melhor desempenho e maior estabilidade ao acessarem e consultarem logs e métricas.
Console de Gerenciamento | O console de gerenciamento do ICP gerencia, monitora e soluciona problemas de seus aplicativos e cluster por meio de um console de gerenciamento único, centralizado e seguro.
Terraform | Manipula o fornecimento de recursos de nuvem e infraestrutura usando provedores como VMware vSphere, {{site.data.keyword.cloud_notm}}, Microsoft Azure, Amazon Web Services, Google Cloud Platform e OpenStack.
AJUDA | Gerenciador de pacotes para Kubernetes. Os gráficos Helm são usados para definir recursos do Kubernetes e implementar aplicativos.
Chef | Responsável pelo gerenciamento de configuração e automação de conformidade. O Chef implementa e configura o middleware e os aplicativos depois que o Terraform conclui o fornecimento inicial.
Serviços | Representa o Editor de serviço, que é onde os administradores criam, compõem e projetam serviços que são construídos por meio de recursos do Kubernetes e uma ou mais VMs.
Aplicativos conteinerizados | Os aplicativos que concluíram a jornada de modernização de aplicativo e agora estão em execução como contêineres. Para esta arquitetura de referência e para o Acme Skateboards, um dos aplicativos conteinerizados é um servidor da web, que faz parte da carga de trabalho de presença on-line.
Watson | Para esta arquitetura de referência e para o Acme Skateboards, o Watson representa o serviço AI que é usado na arquitetura de “Protótipo”.

A migração do aplicativo, a rede e a segurança geralmente são os aspectos mais desafiadores da modernização de aplicativo. O vCenter Server, o VMware Hybridity, o VMware NSX, o ICP e o {{site.data.keyword.cloud_notm}} Kubernetes Service abordam esses desafios e permitem que você construa aplicativos modernos resilientes, seguros e robustos.

### Links relacionados

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
