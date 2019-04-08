---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# Considerações operacionais para a rede do vCenter Server
{: #vcsnsxt-operations}

## Backup
{: #vcsnsxt-operations-backup}

### Backup do VMware vCenter Server on IBM Cloud
{: #vcsnsxt-operations-vcs-backup}

Como parte do {{site.data.keyword.vmwaresolutions_full}}, o software de backup Veeam é opcionalmente implementado em uma instância de servidor virtual (VSI) do {{site.data.keyword.cloud_notm}} usando o armazenamento do Endurance do {{site.data.keyword.cloud_notm}} fora do cluster do VMware. O propósito desse software é fazer backup dos componentes de gerenciamento na solução. A [Visão geral do Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) fornece detalhes sobre a oferta.

O backup de todos os componentes do NSX será crucial para restaurar o sistema para seu estado de funcionamento se ocorrer uma falha. Não é suficiente fazer backup dos dispositivos virtuais NSX, a função de backup do NSX dentro do gerenciador NSX deve ser empregada para um backup efetivo. Essa operação requer que um servidor FTP ou SFTP seja especificado para o repositório de dados de backup do NSX.

O backup do NSX Manager contém toda a configuração do NSX, incluindo controladores, entidades lógicas de roteamento e comutação, segurança, regras de firewall e tudo mais que você configura dentro da interface com o usuário ou API do NSX Manager. O banco de dados do vCenter e os elementos relacionados, como os comutadores virtuais, precisam ter backup feito separadamente. Veja [Backup baseado em arquivo do NSX](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup#nsx-file-based-backup) para obter detalhes. A configuração do NSX deve ser submetida a backup juntamente com um [backup baseado em arquivo do vCenter](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup#vcenter-file-based-backup).

### Backup e recuperação de desastre para o IBM Cloud Private
{: #vcsnsxt-operations-backup-dr-icp}

Os backups para uma implementação do {{site.data.keyword.icpfull_notm}} serão cruciais para restaurar o sistema para seu estado de funcionamento se ocorrer uma falha. Para um backup de MV tradicional, há um ponto de aderência: cada nó principal do {{site.data.keyword.icpfull_notm}} executa um serviço *etcd* e a documentação do *etcd* estabelece claramente que não se deve usar o backup de MV tradicional para restaurá-lo.

Para o {{site.data.keyword.cloud_notm}} Private no nível de plataforma, será necessário fazer backup dos componentes a seguir.
- **etcd** - o etcd é usado para armazenar recursos do Kubernetes e informações de estado do Calico.
- **Docker Registry** - esse registro de imagem privada é usado para armazenar arquivos de imagem de contêiner.
- **MongoDB**- esse banco de dados é usado pelo serviço de medição, servidor do repositório Helm, servidor de API do Helm, configuração LDAP, locatário (namespace) e configurações de função de equipe/usuário/grupo de usuários.
- **MariaDB** - esse banco de dados é usado pelo OIDC.
-	**Elasticsearch** - armazena os logs do sistema e do aplicativo.
-	**Prometheus** - armazena dados para monitoramento.
-	**Armazenamento persistente** - usado para serviços de gerenciamento que usam Volume Persistente do {{site.data.keyword.cloud_notm}} Private ou do Kubernetes Persistente e o provedor de armazenamento.

É possível usar a tecnologia de backup ou restauração que é fornecida pelo provedor de armazenamento. Um processo semelhante pode ser estendido no aplicativo de seu usuário também. Para obter mais informações, veja [Como fazer backup e restaurar o blog do {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8) ou [icp-backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/).

### Backup e recuperação de desastre para o CAM
{: #vcsnsxt-operations-backup-dr-cam}

Os backups de uma implementação do CAM serão cruciais para restaurar o sistema para seu estado de funcionamento se ocorrer uma falha. O backup do CAM requer que o cliente faça backup dos componentes a seguir:
-	** Banco de Dados Mongo ** -Banco de dados CAM principal.
-	**Maria Database** - usado pelo CAM Blueprint Designer.
-	**Sistemas de arquivos NFS/Gluster** - os dados do CAM residem em quatro volumes persistentes.

### Backup e DR para o IBM Cloud Kubernetes Service
{: #vcsnsxt-operations-backup-dr-iks}

O backup do banco de dados etcd é fornecido para o cliente como parte do serviço gerenciado, no entanto, quaisquer dados do aplicativo devem ser suportados pelo cliente.

## Escalabilidade
{: #vcsnsxt-operations-scalability}

### Escalabilidade do vCenter Server
{: #vcsnsxt-operations-vcs-scalability}

Após a implementação dos hosts iniciais, os usuários podem ampliar a capacidade de cálculo de dentro do portal do {{site.data.keyword.cloud_notm}} for VMware.

A ampliação do ambiente segue um destes caminhos:
-	Adição de novos sites gerenciados por vCenter Servers separados.
-	Adição de novos clusters.
-	Adição de novos hosts em um cluster existente.

#### Implementações multisite
{: #vcsnsxt-operations-multi-site}

O VMware on {{site.data.keyword.cloud_notm}} pode usar a presença mundial de data center do {{site.data.keyword.cloud_notm}} e o backbone de rede integrada para permitir que vários casos de uso de geografia cruzada sejam implementados e estejam funcionando dentro de uma fração do tempo que levaria para construir tal infraestrutura do zero. Informações adicionais podem ser localizadas em [Configuração de vários sites para instâncias do vCenter Server on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite).

#### Ampliar com novo cluster
{: #vcsnsxt-operations-scale-out-new-cluster}

Os usuários também podem ampliar a capacidade de cálculo criando um novo cluster de dentro do console por meio do pedido de hosts e os novos hosts são incluídos automaticamente no novo cluster. Essa opção cria um cluster separado no ambiente e fornece aos usuários a capacidade de segregar física e logicamente as cargas de trabalho de gerenciamento das cargas de trabalho do aplicativo, a capacidade de segregar cargas de trabalho com base em outras características (por exemplo, cluster de banco de dados Microsoft SQL) e a capacidade de implementar aplicativos em topologias altamente disponíveis. Para obter mais informações, veja [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

#### Escalar o cluster existente
{: #vcsnsxt-operations-scale-out-existing-cluster}

O usuário pode ampliar um cluster existente pedindo hosts de dentro do console e os novos hosts serão incluídos automaticamente no cluster. Para obter mais informações, veja [Expandindo e contraindo capacidade para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers) para obter detalhes. Talvez seja necessário ajustar a política de reserva de HA para o cluster com base em seus requisitos de reserva.

### Escalabilidade do IBM Cloud Private e do IBM Cloud Kubernetes Service
{: #vcsnsxt-operations-icp-iks-scalability}

Com base na capacidade de cálculo disponível no local ou em locais da nuvem, os usuários podem ampliar a arquitetura do nó por meio do nó de inicialização implementado inicialmente. Para ampliar o ambiente:
-	Expanda os nós do trabalhador do  {{site.data.keyword.icpfull_notm}} .
-	Expanda e use a oferta  {{site.data.keyword.containerlong_notm}} .

#### expansão do IBM Cloud Private
{: #vcsnsxt-operations-icp-expansion}

Os nós de máquina virtual do trabalhador do {{site.data.keyword.icpfull_notm}} são escalados para expandir o cálculo e o aplicativo:
- O cliente provisiona uma nova máquina virtual na mesma VXLAN em que o {{site.data.keyword.icpfull_notm}} é implementado.
- Os clientes podem escalar os nós de trabalhadores, provisionando novas máquinas virtuais, em seguida, efetuando login no nó de inicialização e executando um comando para trazer os novos nós para o cluster. Veja [Incluindo ou removendo nós do cluster](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html) para obter detalhes adicionais.
- Use o CAM para automatizar o fornecimento da MV e executar os comandos para incluí-la no Cluster do {{site.data.keyword.icpfull_notm}}.

#### expansão do IBM Cloud Kubernetes Service
{: #vcsnsxt-operations-iks-expansion}

Os usuários podem provisionar um ambiente do {{site.data.keyword.containerlong_notm}} usando o Portal do {{site.data.keyword.cloud_notm}} para ampliar e usar um ambiente de contêiner. Para obter mais informações, veja [Aprimoramentos híbridos no {{site.data.keyword.cloud_notm}} Private e no {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/community/blogs/5092bd93-e659-4f89-8de2-a7ac980487f0/entry/Hybrid_Enhancements_Across_IBM_Cloud_Private_and_IBM_Public_Cloud?lang=en_us).

As implementações do aplicativo no {{site.data.keyword.containerlong_notm}} são possíveis usando os métodos a seguir:
-	A conexão e os serviços do {{site.data.keyword.containerlong_notm}} são desenvolvidos no CAM e publicados no catálogo do {{site.data.keyword.icpfull_notm}}.
-	Multi Cloud Manager, um aprimoramento futuro para gerenciar as instâncias do {{site.data.keyword.containerlong_notm}}.
-	Linha de comandos do Helm.

## Links relacionados
{: #vcsnsxt-operations-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
