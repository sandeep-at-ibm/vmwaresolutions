---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# Backup, recuperação de desastre e escalabilidade
{: #vcsicp-detail-design-resiliency}

## Backup e DR
{: #vcsicp-detail-design-resiliency-backup-dr}

### Backup do VMware vCenter Server on IBM Cloud
{: #vcsicp-detail-design-resiliency-vcs-backup}

Como parte do {{site.data.keyword.vmwaresolutions_full}}, o software de backup Veeam é opcionalmente implementado em uma instância de servidor virtual (VSI) do {{site.data.keyword.cloud_notm}} que usa o Armazenamento do Endurance do {{site.data.keyword.cloud_notm}} fora do cluster do VMware. O propósito desse software é fazer backup dos componentes de gerenciamento nessa solução.

### backup do NSX
{: #vcsicp-detail-design-resiliency-nsx-backup}

O backup adequado de todos os componentes do NSX será crucial para restaurar o sistema para seu estado de funcionamento se ocorrer falha. Não é suficiente fazer backup das máquinas virtuais (MVs) do NSX. Em vez disso, a função de backup do NSX dentro do NSX Manager deve ser empregada para um backup adequado. Um servidor FTP ou SFTP deve ser especificado para o repositório de dados de backup do NSX.
O backup do NSX Manager contém toda a configuração do NSX, incluindo controladores, entidades lógicas de comutação e roteamento, segurança, regras de firewall e qualquer outra coisa que você configurar dentro da interface com o usuário ou API do NSX Manager. O banco de dados do vCenter e os elementos relacionados, como os comutadores virtuais, devem ser submetidos a backup separadamente. A configuração do NSX deve ser submetida a backup junto a um backup do vCenter.

### Backup e DR para o IBM Cloud Private
{: #vcsicp-detail-design-resiliency-backup-dr-icp}

Os backups para uma implementação do {{site.data.keyword.icpfull_notm}} serão cruciais para restaurar o sistema para seu estado de funcionamento se ocorrer uma falha. Além de um backup de MV tradicional, cada nó principal do {{site.data.keyword.icpfull_notm}} executa o etcd. A documentação do etcd indica claramente para não usar o backup de MV tradicional para restaurá-lo.

Para o {{site.data.keyword.icpfull_notm}} no nível da plataforma, é necessário fazer backup destes componentes:
- **Etcd** é usado para armazenar recursos do Kubernetes e informações de estado Calico.
- **Docker Registry** o registro de imagem privado que é usado para armazenar arquivos de imagem de contêiner em um repositório de imagem.
- **MongoDB** o banco de dados que é usado pelo serviço de medição, servidor de repositório Helm, servidor de API do Helm, configuração do LDAP, Locatário (namespace) e configurações de função de equipe/usuário/grupo de usuários.
- **MariaDB** banco de dados que é usado pelo OIDC.
- **Elasticsearch** armazena os logs do sistema e do aplicativo.
- **Prometheus** armazena dados para monitoramento.
- **Armazenamento persistente** usado para serviços de gerenciamento que usam o {{site.data.keyword.icpfull_notm}} ou o Volume Persistente do Kubernetes e o provedor de armazenamento. É possível usar a tecnologia de backup ou restauração que é fornecida pelo provedor de armazenamento. Um processo semelhante pode ser estendido no aplicativo de seu usuário também.

### Backup e DR para CAM
{: #vcsicp-detail-design-resiliency-backup-dr-cam}

O backup para uma implementação do CAM será crucial para restaurar o sistema para seu estado de funcionamento se ocorrer uma falha. O backup do CAM requer que o cliente faça backup dos componentes a seguir:
- **Banco de dados Mongo** é o banco de dados principal do CAM.
- **Banco de dados Maria** é o banco de dados usado pelo CAM Blueprint Designer.
- **NFS/GlusterFS** é o local em que os dados do CAM residem em quatro volumes persistentes.

### Backup e DR para o IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-resiliency-backup-dr-iks}

Os backups do banco de dados etcd são fornecidos para o cliente como parte do serviço gerenciado, quaisquer dados do aplicativo devem ser suportados por si mesmo.

## Escalabilidade
{: #vcsicp-detail-design-resiliency-scalability}

### Escalabilidade do VCS
{: #vcsicp-detail-design-resiliency-vcs-scalability}

Após a implementação dos hosts iniciais, o usuário pode ampliar a capacidade de cálculo de dentro do portal do {{site.data.keyword.cloud_notm}} for VMware.

Essa escala fora do ambiente segue um dos três caminhos:
- Adição de novos sites gerenciados por vCenter Servers separados.
- Adição de novos clusters.
- Adição de novos hosts em um cluster existente.

#### Implementações multissite
{: #vcsicp-detail-design-resiliency-multi-site}

O VMware on {{site.data.keyword.cloud_notm}} pode usar a presença do data center mundial do IBM Cloud e o backbone de rede integrada para permitir que vários casos de uso de geografia cruzada sejam implementados e funcionem dentro de uma fração do tempo que levaria para construir tal infraestrutura do zero.

#### Ampliar com novo cluster
{: #vcsicp-detail-design-resiliency-scale-out-new}

O usuário pode ampliar a capacidade de cálculo criando um novo cluster de dentro do console, pedindo os hosts e os novos hosts são incluídos automaticamente no novo cluster. Essa opção cria um cluster separado no ambiente e fornece aos usuários a capacidade de segregar física e logicamente as cargas de trabalho de gerenciamento das cargas de trabalho do aplicativo, a capacidade de segregar cargas de trabalho com base em outras características (por exemplo, cluster de banco de dados Microsoft SQL) e a capacidade de implementar aplicativos em topologias altamente disponíveis.

#### Escalar o cluster existente
{: #vcsicp-detail-design-resiliency-scale-out-existing}

O usuário pode ampliar um cluster existente pedindo hosts de dentro do console e os novos hosts serão incluídos automaticamente no cluster. Os usuários podem precisar ajustar a política de reserva de HA do cluster com base em seus requisitos de reserva.

### Escalabilidade do IBM Cloud Private
{: #vcsicp-detail-design-resiliency-icp-scalability}

Com base na capacidade de cálculo disponível no local ou em locais da nuvem, o usuário pode ampliar a arquitetura do nó por meio do nó de inicialização implementado inicialmente.

A ampliação do ambiente é a seguinte:
- Expanda os nós do trabalhador do  {{site.data.keyword.icpfull_notm}} .
- Expanda e use a oferta  {{site.data.keyword.containerlong_notm}} .

#### expansão do IBM Cloud Private
{: #vcsicp-detail-design-resiliency-icp-expansion}

Os nós da MV do trabalhador do {{site.data.keyword.icpfull_notm}} são escalados para expandir o cálculo ou aplicativo:
- O cliente provisiona uma nova MV, na mesma VXLAN em que o {{site.data.keyword.icpfull_notm}} é implementado.
- Os clientes podem escalar os nós do trabalhador, provisionando nova MV e, em seguida, efetuando login no nó de inicialização e executando um comando para trazer os novos nós para o cluster.
- Use o CAM para automatizar o fornecimento da MV e executar os comandos a serem incluídos no Cluster do {{site.data.keyword.icpfull_notm}}.

###  expansão do IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-resiliency-iks-expansion}

Os usuários podem provisionar um ambiente do {{site.data.keyword.containerlong_notm}} por meio do Portal do {{site.data.keyword.cloud_notm}} para estender ou usar um ambiente de contêiner.

Use o seguinte para implementações do aplicativo no {{site.data.keyword.containerlong_notm}}:
- A conexão ou os serviços do {{site.data.keyword.containerlong_notm}} são desenvolvidos no CAM e publicados no catálogo do {{site.data.keyword.icpfull_notm}}.
- Aprimoramento futuro do Multi-Cloud Manager para gerenciar instâncias do {{site.data.keyword.containerlong_notm}}
- Interface da linha de comandos do Helm.
- Use os clusters Multizona para aumentar a alta disponibilidade.

## Links relacionados
{: #vcsicp-detail-design-resiliency-related}

* [Incluindo ou removendo nós do cluster](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [Incluindo nós do trabalhador redimensionando um conjunto de trabalhadores existente](/docs/containers?topic=containers-clusters)
* [Como fazer backup e restaurar o {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [ {{site.data.keyword.icpfull_notm}}  backup GitHub ](https://github.com/ibm-cloud-architecture/icp-backup/)
* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
