---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# IBM Cloud Private
{: #vcsnsxt-overview-icp}

O {{site.data.keyword.icpfull_notm}} é uma plataforma de aplicativo para desenvolver e gerenciar aplicativos conteinerizados. É um ambiente integrado que inclui o orquestrador de contêineres Kubernetes, um repositório de imagem privada, um console de gerenciamento, estruturas de monitoramento e uma interface gráfica com o usuário, que fornece um local centralizado por meio do qual é possível implementar, gerenciar, monitorar e escalar seus aplicativos.

O {{site.data.keyword.cloud_notm}} Private tem os recursos a seguir:
-	**Instalador unificado** - o instalador configura rapidamente um cluster baseado em Kubernetes com nós principal, trabalhador e proxy usando um instalador baseado em Ansible.
-	**Console de gerenciamento do {{site.data.keyword.cloud_notm}} Private** - gerencie, monitore e solucione problemas de seus aplicativos e cluster por meio de um console de gerenciamento único, centralizado e seguro.
-	**Registro de imagem privada do Docker** - esse registro local tem todos os mesmos recursos do Docker Hub, mas também permite restringir quais usuários podem visualizar ou puxar imagens.
-	**Catálogo de software e serviços conteinerizados** - o catálogo fornece um local centralizado por meio do qual é possível procurar e instalar pacotes em seu cluster. Os pacotes para produtos IBM extras estão disponíveis por meio de repositórios curados que estão incluídos na lista de repositórios do {{site.data.keyword.cloud_notm}} Private.
-	**Redes isoladas de locatários** - o Calico permite melhor desempenho e isolamento de rede dentro de seu cluster. Com o Calico, é possível criar uma sub-rede isolada para cada projeto dentro de seu cluster. Esse isolamento de rede fornece segurança adicional durante transmissões de dados e reduz as chances de comprometer os aplicativos e seus dados. O Calico também facilita a criação de novas políticas de rede que podem ativar o controle de baixa granularidade sobre o compartilhamento de objetos dentro de um único namespace.
-	**Monitoramento robusto e criação de log com pilha ELK** - o {{site.data.keyword.cloud_notm}} Private usa o Elasticsearch, Logstash, Filebeat e Heapster para a coleta, armazenamento e consulta de logs e métricas. Esse processo de monitoramento e criação de log fornece um armazenamento centralizado para todos os logs e métricas, melhor desempenho e maior estabilidade ao acessar e consultar logs e métricas.

## Componentes do IBM Cloud Private
{: #vcsnsxt-overview-icp-comp}

Um cluster do {{site.data.keyword.cloud_notm}} Private tem quatro classes principais de nós: inicialização, principal, trabalhador e proxy. Opcionalmente, é possível especificar o gerenciamento, o Vulnerability Advisor (VA) e os nós etcd em seu cluster.
-	**Nó de inicialização** - um nó de inicialização é usado para executar instalação, configuração, ajuste de escala do nó e atualizações de cluster.
-	**Nó principal** - um nó principal fornece serviços de gerenciamento e controla os nós do trabalhador em um cluster. Nós principais hospedam processos que são responsáveis pela alocação de recurso, manutenção de estado, planejamento e monitoramento.
-	**Nó do trabalhador** - um nó do trabalhador é um nó que fornece um ambiente conteinerizado para executar tarefas. Conforme as demandas aumentam, mais nós do trabalhador podem ser facilmente incluídos em seu cluster para melhorar o desempenho e a eficiência.
-	**Nó do proxy ** - um nó do proxy é um nó que transmite a solicitação externa para os serviços criados dentro de seu cluster.
-	**Nó de gerenciamento** - um nó de gerenciamento é um nó opcional que hospeda somente serviços de gerenciamento, como monitoramento, medição e criação de log. Configurando os nós de gerenciamento dedicados, é possível evitar que o nó principal fique sobrecarregado.
-	**Nó do Vulnerability Advisor (VA)** - um nó do VA é um nó opcional que é usado para executar os serviços do Vulnerability Advisor.
-	Nó **etcd** - um nó etcd é um nó opcional que é usado para executar o armazenamento de valor de chave distribuída etcd.

## Rede Privada do IBM Cloud
{: #vcsnsxt-overview-icp-networking}

O gerenciamento de rede do {{site.data.keyword.icpfull_notm}} é facilitado pelo uso do Calico.
O Calico usa a camada 3 ou a camada de rede do modelo Open System Interconnection (OSI). O Calico usa o Protocolo de Roteamento de Borda (BGP) para construir tabelas de roteamento que facilitam a comunicação entre os nós do agente.

Para obter mais informações sobre a rede Calico, veja [{{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-overview-iks).
