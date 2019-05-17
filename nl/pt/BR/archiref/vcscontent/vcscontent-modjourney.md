---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# Jornada de modernização
{: #vcscontent-modjourney}

Esse é um caso de uso de referência sobre como um aplicativo WebSphere Application Server clássico é modernizado usando o {{site.data.keyword.cloud}} Private, o conteúdo do IBM Middleware, o {{site.data.keyword.containerlong_notm}} e o VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

## Modernização é mais que aplicativos
{: #vcscontent-modjourney-modernization}

Estamos todos em uma jornada de nuvens e em pontos diferentes nessa jornada. Este caso de uso se concentra em como um aplicativo existente, o Stock Trader, é modernizado por meio de etapas incrementais que a arquiteta de aplicativo, Jane, e o arquiteto de infraestrutura em nuvem, Todd, planejaram. Este caso de uso mostra exemplos que ajudam a executar cada etapa em sua jornada, além do valor realizado para seus negócios, independentemente de cada etapa ser grande ou pequena.

A maior parte do nosso foco nesta jornada é a modernização do aplicativo Stock Trader. Para modernizar completamente seus negócios em um negócio nativo da nuvem, os aplicativos, o DevOps, a integração e os temas de gerenciamento devem ser discutidos. Todos os temas trabalham em conjunto para ajudá-lo a atingir suas metas. Modernizar um tema sem os outros pode resultar em problemas.

## Razões para a modernização
{: #vcscontent-modjourney-reasons}

### Modernização de aplicativo
{: #vcscontent-modjourney-app-mod}

O objetivo são os aplicativos de nuvem nativa que escalam e respondem às demandas de mudança rápida.

* É necessário modernizar os apps existentes e criar novos apps nativos de nuvem para capturar a imaginação do cliente.
* Você precisa de apps que podem escalar, atingir o mundo inteiro, ajustar-se às demandas, mudar, aprimorar e transformar rapidamente.

### Modernização do DevOps
{: #vcscontent-modjourney-devops-mod}

Enquanto você moderniza seu aplicativo, a maneira de entregar esse aplicativo, o pipeline de entrega inteiro, é modernizada para que a nova cultura de nuvem nativa que seus Desenvolvedores estão criando possa escalar como esse app é entregue.

* É necessário modernizar sua cultura de Desenvolvimento e Operações (e segurança) enquanto você moderniza seus aplicativos.
* Você precisa de equipes do DevOps que podem escalar, atingir o mundo inteiro, ajustar-se à demanda, mudar, aprimorar e transformar rapidamente.

###  Modernização de integração
{: #vcscontent-modjourney-integration-mod}

No decorrer da jornada de modernização, suas equipes precisam se integrar a ativos existentes, novos serviços de nuvem, seus dados e novos insights por meio da analítica executada nesses dados.

* É necessário usar seus ativos existentes nesta jornada de uma maneira que possa escalar, atingir o mundo inteiro, ajustar-se à demanda, mudar, aprimorar e transformar rapidamente.
* É necessário enriquecer com novos serviços de nuvem em cada etapa desta jornada.
* É necessário integrar seus dados e o insight obtidos da aplicação de analítica a seus dados.

### Gerenciamento
{: #vcscontent-modjourney-mgmt}

Modernizar suas práticas de gerenciamento é outra jornada paralela a ser feita enquanto você moderniza seus aplicativos. As ferramentas, a cultura e os principais comportamentos de como gerenciar e manter um aplicativo modernizado são muito diferentes de antes.

* É necessário gerenciar seus microsserviços e o middleware conteinerizado usando a orquestração integrada, a criação de log e o monitoramento.
* É necessário gerenciar suas plataformas híbridas multinuvem em locais em todo o mundo de uma maneira que possa escalar, atingir o mundo inteiro, ajustar-se à demanda, mudar, aprimorar e transformar rapidamente.
* É necessário automatizar como você gerencia mais de uma nuvem e os aplicativos e middleware que são executados neles.

## Conhecer Todd e Jane
{: #vcscontent-modjourney-todd-jane}

Para nossa jornada do Stock Trader, nos concentramos em duas pessoas: Todd e Jane. Todd é a liderança de operações para a empresa ACME e é responsável pela infraestrutura, segurança, ambientes de nuvem e políticas que asseguram que as cargas de trabalho executadas nelas obedeçam a várias regulamentações.

Jane é a liderança de desenvolvimento para a solução Stock Trader e agora tem a responsabilidade de modernizar o Stock Trader, o que significa trabalhar em suas equipes de desenvolvimento para mudar as ferramentas de desenvolvimento, cultura e plataformas, de modo que a solução monolítica Stock Trader existente seja modernizada em uma solução de nuvem nativa bem executada.

## Conhecer o Stock Trader
{: #vcscontent-modjourney-meet-stock-trader}

Todd e Jane construíram um aplicativo que é executado no WebSphere chamado Stock Trader. Embora tenha uma interface básica com o usuário, ele é um aplicativo confiável no qual os gerentes de portfólio vão para gerenciar portfólios, incluindo a compra e venda de ações e a visualização de níveis internos de fidelidade.

O Stock Trader é executado no WebSphere, é construído com alguns arquivos .war e usa um banco de dados Db2 tradicional que é executado no data center do qual eles dependeram durante anos. Leva muito tempo para aprimorar esse aplicativo por causa de dependências entre equipes de infraestrutura, equipes de desenvolvimento e equipes de dados.

Mas, embora o Stock Trader esteja bom, todos na empresa desejam algo melhor. Os gerentes de produto desejam incluir mídia social em seu programa de fidelidade. Jane está satisfeita porque ela pode refatorar o app em microsserviços, o que permite entregar continuamente recursos aprimorados com menos dependências. Todd adora a ideia de eficiências de nuvem, mas ainda requer controle para manter a conformidade com as políticas corporativas.

## Etapas ao longo da jornada
{: #vcscontent-modjourney-steps}

Todd e Jane sabem por experiência que uma boa jornada para modernizar as soluções inicia-se com um roteiro. Embora os planos possam mudar, é sempre bom pensar com visão e definir um caminho realista para chegar lá. Cada etapa deve trazer valor para a empresa e as etapas não devem ser tão significativas que causem interrupções caras aos seus clientes.

Para Todd e Jane, suas etapas na jornada do Stock Trader são:
1. Elevar as MVs do Stock Trader para o {{site.data.keyword.cloud_notm}}. Esta etapa permite que Todd reduza a necessidade de gerenciar seu próprio hardware e o conteúdo do VMware no data center local.

2. Transformar o Stock Trader no WebSphere Application Server em Stock Trader em contêineres. Esta etapa aumenta a resiliência porque os contêineres em execução no Kubernetes trazem orquestração e outros comportamentos de nuvem. Isso requer que o Todd prepare uma instância do {{site.data.keyword.cloud_notm}} Private em seu ambiente do VMware vCenter Server on {{site.data.keyword.cloud_notm}} e, em seguida, trabalhe com Jane e o Transformation Advisor para conteinerizar o Stock Trader.

3. Refatorar e incluir o middleware no {{site.data.keyword.cloud_notm}} Private. Esta etapa traz seu middleware existente para um ambiente de nuvem e otimiza os comportamentos de nuvem. Isso também aperfeiçoa o licenciamento e prepara a solução para
ser totalmente móvel para uso em outros ambientes do Kubernetes.

4. Enriquecer com o Watson e outros serviços de nuvem pública. Esta etapa pode incluir um valor exponencialmente na experiência do Stock Trader, puxando os serviços de IA e a capacidade de se comunicar com os data centers de nuvem mundiais.

5. Híbrido verdadeiro com o {{site.data.keyword.cloud_notm}} Kubernetes Service. Esta etapa permite que o Todd tenha um serviço Kubernetes gerenciado que ainda se conecte à mesma região de nuvem que sua instância do {{site.data.keyword.cloud_notm}} Private. Também permite que as equipes de desenvolvimento de Jane tenham um cluster de desenvolvimento e teste que elas possam experimentar enquanto ainda estiverem acessando a mesma origem de dados que seu cluster principal do {{site.data.keyword.cloud_notm}} Private.

6. Modernizar o DevOps. Ao longo desta jornada, Jane melhora como ela entrega o Stock Trader.

7. Modernizar o gerenciamento. Todd e Jane trabalharam para melhorar a maneira como gerenciam o Stock Trader e a plataforma em que ele é executado, mesmo em mais de um ambiente de cluster e de nuvem.

## Links relacionados
{: #vcscontent-modjourney-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
