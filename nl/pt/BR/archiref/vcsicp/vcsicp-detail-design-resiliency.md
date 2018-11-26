---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# Backup, recuperação de desastre e escalabilidade

## Backup e DR

###	Backup do VCS

Como parte do {{site.data.keyword.vmwaresolutions_full}}, o software de backup do Veeam é implementado opcionalmente em uma instância de servidor virtual (VSI) do {{site.data.keyword.cloud_notm}} usando o {{site.data.keyword.cloud_notm}} Endurance Storage fora do cluster do VMware. O propósito desse software é fazer backup dos componentes de gerenciamento nessa solução.

### backup do NSX

O backup adequado de todos os componentes do NSX será crucial para restaurar o sistema para seu estado de funcionamento se ocorrer falha. Não é suficiente fazer backup das VMs do NSX, a função de backup do NSX dentro do NSX Manager deve ser empregada para um backup adequado. Isso requer que um servidor FTP ou SFTP seja especificado para o repositório de dados de backup do NSX.
O backup do NSX Manager contém toda a configuração do NSX, incluindo controladores, entidades lógicas de alternância e roteamento, segurança, regras de firewall e tudo o mais que você configurar dentro da UI ou API do NSX Manager. O banco de dados do vCenter e os elementos relacionados, como os comutadores virtuais, precisam ter backup feito separadamente. A configuração do NSX deve ser submetida a backup junto com um backup do vCenter.

###	Backup e DR para o IBM Cloud Private

Os backups para uma implementação do ICP serão cruciais para restaurar o sistema para seu estado de funcionamento se ocorrer uma falha. Em cima de um backup de VM tradicional, há um ponto de aderência, cada nó principal do ICP executa o etcd e a documentação do etcd indica claramente para não usar o backup de VM tradicional para restaurá-lo.

{{site.data.keyword.cloud_notm}} Private no nível da plataforma, é necessário fazer backup destes componentes:

-	**Etcd** — é usado para armazenar recursos do Kubernetes, bem como informações de estado do Calico.
-	**Docker Registry** — o registro de imagem privado que é usado para armazenar os arquivos de imagem de contêiner em um repositório de imagem.
-	**MongoDB** — o banco de dados que é usado pelo serviço de medição, servidor de repositório Helm, servidor da API do Helm, configuração LDAP, Locatário (namespace) e configurações de função de equipe/usuário/grupo de usuários.
-	**MariaDB** — banco de dados que é usado pelo OIDC.
-	**Elasticsearch** — armazena os logs do sistema e do aplicativo.
-	**Prometheus** — armazena dados para monitoramento.
-	**Armazenamento persistente** — usado para serviços de gerenciamento que alavancam o ICP ou o Volume Persistente do Kubernetes e o provedor de armazenamento. É possível usar a tecnologia de backup ou restauração que é fornecida pelo provedor de armazenamento. Um processo semelhante pode ser estendido no aplicativo de seu usuário também.

###	Backup e DR para CAM
O backup para uma implementação do CAM será crucial para restaurar o sistema para seu estado de funcionamento se ocorrer uma falha. O backup do CAM requer que o cliente faça backup dos componentes a seguir:
-	** Banco de Dados Mongo ** -Banco de dados CAM principal.
-	**Maria Database** - usado pelo CAM Blueprint Designer.
-	**NFS/GlusterFS** - os dados do CAM residem em quatro volumes persistentes.

### Backup e DR para IKS
Os backups do banco de dados etcd são fornecidos para o cliente como parte do serviço gerenciado, quaisquer dados do aplicativo devem ser suportados por si mesmo.

## Escalabilidade

### Escalabilidade do VCS

Após a implementação dos hosts iniciais, o usuário tem a capacidade de ampliar a escala da capacidade de cálculo de dentro do portal do {{site.data.keyword.cloud_notm}} for VMware.

Essa escala fora do ambiente segue um dos três caminhos:
- Adição de novos sites gerenciados por vCenter Servers separados.
- Adição de novos clusters.
- Adição de novos hosts em um cluster existente.

####	Implementações multissite
O VMware on {{site.data.keyword.cloud_notm}} pode aproveitar a presença do data center mundial do IBM Cloud e o backbone de rede integrada para permitir que vários casos de uso de geografia cruzada sejam implementados e funcionem dentro de uma fração do tempo que levaria para construir tal infraestrutura do zero.

####	Ampliar com novo cluster
O usuário também tem a opção de ampliar a capacidade de cálculo criando um novo cluster de dentro do console e pedindo os hosts e os novos hosts serão incluídos automaticamente no novo cluster. Essa opção criará um cluster separado no ambiente e fornecerá aos usuários a capacidade de segregar física e logicamente as cargas de trabalho de gerenciamento por meio de cargas de trabalho do aplicativo, a capacidade de segregar cargas de trabalho com base em outras características (por exemplo, cluster do banco de dados Microsoft SQL) e a capacidade de implementar aplicativos em topologias altamente disponíveis.

####	Escalar o cluster existente
O usuário pode ampliar um cluster existente pedindo hosts de dentro do console e os novos hosts serão incluídos automaticamente no cluster. Observe que os usuários podem precisar ajustar a política de reserva de HA para o cluster com base em seus requisitos de reserva.

### Escalabilidade do ICP
Com base na capacidade de cálculo disponível nos locais da nuvem e no local, o usuário tem a capacidade de ampliar a arquitetura do nó por meio do nó de inicialização implementado no início.

A ampliação do ambiente é a seguinte:
- Expanda os nós do trabalhador do ICP.
- Expanda e utilize a oferta IKS.

####	Expansão do ICP
Os nós da máquina virtual do trabalhador do ICP são escalados para expandir o cálculo/aplicativo:
  - O cliente provisiona uma nova máquina virtual, na mesma VXLAN em que o ICP é implementado.
  - Os clientes podem escalar nós do trabalhador, provisionando novas máquinas virtuais, em seguida, efetuando login no nó de inicialização e executando um comando para trazer os novos nós para o cluster.
  - Utilize o CAM para automatizar o fornecimento da VM e executar os comandos a serem incluídos no Cluster do ICP.


###  Expansão IKS
Os usuários podem provisionar um ambiente do IKS por meio do Portal do {{site.data.keyword.cloud_notm}} para ampliar/utilizar um ambiente de contêiner.

As implementações de aplicativos no IKS podem ser feitas por meio de:
- A conexão/serviços do IKS são desenvolvidos no CAM e publicados no catálogo do ICP.
- Aprimoramento futuro do Multi-Cloud Manager para gerenciar instâncias do IKS
- Linha de Comandos Helm.
- Use os clusters Multizona para aumentar a alta disponibilidade.

### Links relacionados
* [Incluindo ou removendo nós do cluster](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [Incluindo nós do trabalhador redimensionando um conjunto de trabalhadores existente](../../../../containers/cs_clusters.html#resize_pool)
* [Como fazer backup e restaurar o {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [GitHub de backup do ICP](https://github.com/ibm-cloud-architecture/icp-backup/)
* [Visão geral do VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
