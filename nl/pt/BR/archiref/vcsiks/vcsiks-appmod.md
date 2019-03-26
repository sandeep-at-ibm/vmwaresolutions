---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

---

# Visão geral de modernização do
{: #vcsiks-appmod}

O diagrama a seguir mostra a arquitetura de referência de modernização do aplicativo que a Acme Skateboards implementa e é descrita detalhadamente nesta série de documentos.

Figura 1. Diagrama de visão geral da arquitetura
![Diagrama de visão geral da arquitetura](vcsiks-aod.svg)

Essa arquitetura híbrida permite à Acme Skateboards:
- Migrar máquinas virtuais VMware (MVs) no local para o {{site.data.keyword.cloud}} com pouco ou nenhum tempo de inatividade e nenhuma reconfiguração do aplicativo.
- Ativá-las para iniciar a jornada de modernização do aplicativo, permitindo que se concentrem na conteinerização das interfaces da web mais simples e do middleware, enquanto permite que bancos de dados mais complexos permaneçam como MVs.
- Use o Cloud Automation Manager (CAM) para o infrastructure as code (IaC) de script para editar e orquestrar serviços que são feitos por meio de MVs e contêineres para integrar às suas cadeias de ferramentas do DevOps e à sua solução ITSM.

A arquitetura de referência tem os componentes principais a seguir:
- **Virtualização no local** - a virtualização no local é um cluster do VMware que hospeda atualmente as MVs do Acme Skateboards. Essas MVs estão hospedando atualmente os aplicativos a serem modernizados. É necessário que esse cluster atenda aos pré-requisitos da arquitetura [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) para que possa executar o HCX.

O HCX amplia as redes no local para o {{site.data.keyword.cloud_notm}} permitindo que os clientes migrem MVs para a instância do VMware vCenter Server on {{site.data.keyword.cloud_notm}} que é executada no {{site.data.keyword.cloud_notm}} e de volta se necessário.
- **{{site.data.keyword.cloud_notm}} for VMware Solutions** - a instância do vCenter Server fornece os blocos de construção fundamentais do VMware, como vSphere, vCenter Server, NSX-V e opções de armazenamento que incluem o armazenamento do vSAN ou do Endurance do {{site.data.keyword.cloud_notm}}, necessários para implementar automaticamente uma solução VMware Software Defined Data Center (SDDC). O cluster do VMware é o destino para as MVs migradas e alguns dos aplicativos modernizados em contêineres hospedados no {{site.data.keyword.icpfull_notm}}. Os componentes principais no vCenter Server são conforme a seguir:
  - **NSX-V** - o NSX-V fornece a camada de virtualização de rede no vCenter Server que fornece uma sobreposição de rede para MVs do Acme Skateboards. O NSX-V ativa o BYOIP e isola as redes de carga de trabalho das redes do {{site.data.keyword.cloud_notm}}. O NSX-V é programado pelo HCX para criar as redes ampliadas pela Acme Skateboards no local.
  - **NSX-T** - o NSX-T fornece um conjunto comum de ferramentas para o gerenciamento de rede e segurança nos contêineres e MVs. O NSX-T é totalmente compatível com o Container Networking Interface (CNI) do Kubernetes e integra-se ao CNI para fornecer a rede de contêiner. O NSX-T fornece a rede de sobreposição usada pelos aplicativos modernizados e está substituindo o Calico, usado nativamente pelo {{site.data.keyword.icpfull_notm}} e pelo {{site.data.keyword.containerlong_notm}}.

- **{{site.data.keyword.icpfull_notm}}** - O {{site.data.keyword.icpfull_notm}} é uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados. O {{site.data.keyword.icpfull_notm}} é um ambiente integrado que inclui o orquestrador de contêineres Kubernetes, um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário que fornece um local centralizado do qual o Acme Skateboards pode implementar, gerenciar, monitorar e escalar seus aplicativos. A instância do vCenter Server hospeda os componentes, os nós principais, os nós do trabalhador e outros do {{site.data.keyword.icpfull_notm}}, executando-os como MVs. {{site.data.keyword.icpfull_notm}}  hosts:
- **{{site.data.keyword.cloud_notm}} Automation Manager** - o CAM é uma plataforma infrastructure as code (IaC) pronta para empresa que fornece uma única área de janela de vidro para provisionar cargas de trabalho da MV, no local ou no vCenter Server, juntamente com cargas de trabalho do Kubernetes, no {{site.data.keyword.icpfull_notm}} ou {{site.data.keyword.containerlong_notm}}, usando modelos. O CAM é um aplicativo Dockerizado executado em uma instalação do {{site.data.keyword.icpfull_notm}} e é fortemente integrado para autorização, controle de acesso baseado na função (RBAC) e outras funções.
    - Os aplicativos conteinerizados do Acme Skateboards que os clientes desejam implementar nesse ambiente.

- **{{site.data.keyword.containerlong_notm}}** - O {{site.data.keyword.containerlong_notm}} permite que o Acme Skateboards implemente seus aplicativos modernizados em contêineres do Docker executados em clusters do Kubernetes. Os modos principais são totalmente gerenciados pela IBM enquanto os nós do trabalhador no conjunto de trabalhadores são implementados na mesma conta do {{site.data.keyword.cloud_notm}} que sua instância do vCenter Server. Os nós do trabalhador podem ser: instâncias de servidor virtual bare metal, público ou dedicado. O Calico é instalado e configurado automaticamente no {{site.data.keyword.containerlong_notm}}. O Calico fornece conectividade de rede segura para contêineres e está configurado no {{site.data.keyword.containerlong_notm}} para usar o encapsulamento IP-in-IP para pacotes que viajam pelas sub-redes e para usar NAT para conexões de saída dos contêineres.

- **Direct Link** – o {{site.data.keyword.cloud_notm}} Direct Link usa o provedor WAN da Acme Skateboard para conectar seu data center ao {{site.data.keyword.cloud_notm}} para fornecer uma conexão de rede confiável, segura e de baixa latência. Esta conexão fornece:
  - Acesso aos aplicativos hospedados em nuvem por meio de seus usuários corporativos.
  - Tráfego entre MVs no local e MVs de nuvem.
  - Tráfego entre sistemas legados no data center no local e nas MVs de nuvem.

## Benefícios importantes para a Acme Skateboards
{: #vcsiks-appmod-benefits}

O vCenter Server fornece os blocos de construção fundamentais que incluem o VMware vSphere, o vCenter Server, o NSX e as opções de armazenamento compartilhado que incluem o vSAN, necessário para projetar uma solução flexível do VMware Software Defined Data Center (SDDC) que melhor se ajuste às suas cargas de trabalho.

Em resumo, as ofertas do {{site.data.keyword.cloud_notm}} for VMware:
* Acelere a entrega de projetos de TI para os Desenvolvedores e linhas de
negócios, reduzindo o tempo que leva para compras, arquitetura,
implementação e implantação de recursos de semanas ou meses para
horas.
* Aprimore a segurança com servidores bare metal dedicados em uma nuvem privada hospedada, incluindo a implementação do terminal em serviço de rede privada para os serviços do {{site.data.keyword.cloud_notm}}, incluindo o {{site.data.keyword.containerlong_notm}} e o KMIP.
* Ative o gerenciamento e o controle consistentes da nuvem híbrida
implementada, fornecendo acesso administrativo total para o gerenciamento
de virtualização. O gerenciamento preserva as ferramentas, os scripts e os investimentos
existentes do VMware em treinamento.
* Use o conhecimento do VMware em escala global com o IBM Professional and
Managed Services abrangendo mais de 30 {{site.data.keyword.CloudDataCents_notm}} no mundo inteiro.

O {{site.data.keyword.containerlong_notm}} é uma oferta gerenciada do Kubernetes para entregar ferramentas de gerenciamento poderosas, uma experiência do usuário intuitiva e segurança e isolamento integrados para permitir a entrega rápida de aplicativos, todos enquanto usam o Cloud Services, incluindo recursos cognitivos do Watson. A IBM é um membro Platinum do Cloud Native Computing Foundation (CNCF)
e a nossa oferta obedece ao programa de teste de conformidade do Kubernetes
do CNCF.

O {{site.data.keyword.containerlong_notm}}  fornece recursos nativos do Kubernetes, tais como:
- O planejamento inteligente maximiza o uso dos recursos de cluster
subjacentes, implementando apps de maneira a assegurar que os pods de uso
intensivo de CPU e de RAM sejam coalocados.
- Capacidade de recuperação automática para aplicativos e microsserviços conteinerizados,
assegurando que esses componentes sejam reimplementados automaticamente se algo
der errado.
- Escala horizontal para permitir que você configure uma política de implementação,
que o orquestrador usa para assegurar que as cargas de trabalho tenham a
capacidade necessária.
- A descoberta de serviço e o balanceamento de carga fornecem um DNS leve
dentro do cluster do Kubernetes que permite que os serviços se registrem e
eliminem a necessidade de codificação estática de seus microsserviços. O balanceamento
de carga distribui as solicitações recebidas para o número de instâncias
executadas em sua arquitetura.
- Os lançamentos e retrocessos automatizados suportam equipes que implementam novos
recursos e correções de uma maneira controlada. Se algo quebra, podemos
retroceder automaticamente para a versão anteriormente bem conhecida da
imagem.
- Gerenciamento de segredo e configuração. Os segredos são um objeto dentro
do Kubernetes que armazena dados sensíveis, como uma senha, um token ou
uma chave. Esses segredos são criptografados por padrão e asseguram que o acesso a esses dados sensíveis seja controlado.

Os clientes voltados para plataformas de aplicativos nativos de nuvem, como o {{site.data.keyword.icpfull_notm}} e o {{site.data.keyword.containerlong_notm}} concentram-se na velocidade e na inovação e nem sempre têm segurança e rede em mente. O tempo de maturação do aplicativo diminuirá se ele precisar esperar até que a rede ou as equipes de segurança possam pedir serviços como balanceadores de carga, firewalls, comutadores e roteadores.

Essa arquitetura de referência mostra como o VCS, o {{site.data.keyword.icpfull_notm}} e o {{site.data.keyword.containerlong_notm}} movem o Acme Skateboards de forma segura pela jornada de modernização do aplicativo.

## Links relacionados
{: #vcsiks-appmod-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
