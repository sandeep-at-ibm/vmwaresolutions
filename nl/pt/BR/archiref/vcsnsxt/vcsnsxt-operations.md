---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# Considerações operacionais

## Backup

### Backup do VCS

Como parte do {{site.data.keyword.vmwaresolutions_full}}, o software de backup Veeam é opcionalmente implementado em uma instância de servidor virtual (VSI) do {{site.data.keyword.cloud_notm}} usando o armazenamento do Endurance do {{site.data.keyword.cloud_notm}} fora do cluster do VMware. O propósito desse software é fazer backup dos componentes de gerenciamento na solução. A [Visão geral do Veeam on {{site.data.keyword.cloud_notm}}](../../services/veeam_considerations.html) fornece detalhes sobre a oferta.

O backup de todos os componentes do NSX será crucial para restaurar o sistema para seu estado de funcionamento se ocorrer uma falha. Não é suficiente fazer backup dos dispositivos virtuais NSX, a função de backup do NSX dentro do gerenciador NSX deve ser empregada para um backup efetivo. Essa operação requer que um servidor FTP ou SFTP seja especificado para o repositório de dados de backup do NSX.

O backup do NSX Manager contém toda a configuração do NSX, incluindo controladores, entidades lógicas de roteamento e comutação, segurança, regras de firewall e tudo mais que você configura dentro da interface com o usuário ou API do NSX Manager. O banco de dados do vCenter e os elementos relacionados, como os comutadores virtuais, precisam ter backup feito separadamente. Veja [Backup baseado em arquivo do NSX](../solution/solution_backingup.html#nsx-file-based-backup) para obter detalhes. A configuração do NSX deve ser submetida a backup juntamente com um [backup baseado em arquivo do vCenter](../solution/solution_backingup.html#vcenter-file-based-backup).

### Backup e recuperação de desastre para o IBM Cloud Private

Os backups para uma implementação do ICP serão cruciais para restaurar o sistema para seu estado de funcionamento se ocorrer uma falha. Sobre um backup de VM tradicional, há um ponto de aderência: cada nó principal do ICP executa um serviço *etcd* e a documentação do *etcd* indica claramente para não usar o backup de VM tradicional para restaurá-lo.

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

Os backups de uma implementação do CAM serão cruciais para restaurar o sistema para seu estado de funcionamento se ocorrer uma falha. O backup do CAM requer que o cliente faça backup dos componentes a seguir:
-	** Banco de Dados Mongo ** -Banco de dados CAM principal.
-	**Maria Database** - usado pelo CAM Blueprint Designer.
-	**Sistemas de arquivos NFS/Gluster** - os dados do CAM residem em quatro volumes persistentes.

### Backup e DR para IKS

O backup do banco de dados etcd é fornecido para o cliente como parte do serviço gerenciado, no entanto, quaisquer dados do aplicativo devem ser suportados pelo cliente.

## Escalabilidade

### Escalabilidade do VCS

Após a implementação dos hosts iniciais, os usuários podem ampliar a capacidade de cálculo de dentro do portal do {{site.data.keyword.cloud_notm}} for VMware.

A ampliação do ambiente segue um destes caminhos:
-	Adição de novos sites gerenciados por vCenter Servers separados.
-	Adição de novos clusters.
-	Adição de novos hosts em um cluster existente.

#### Implementações multisite

O VMware on {{site.data.keyword.cloud_notm}} pode usar a presença mundial de data center do {{site.data.keyword.cloud_notm}} e o backbone de rede integrada para permitir que vários casos de uso de geografia cruzada sejam implementados e estejam funcionando dentro de uma fração do tempo que levaria para construir tal infraestrutura do zero. Informações adicionais podem ser localizadas em [Configuração multisite para instâncias do vCenter Server on {{site.data.keyword.cloud_notm}}](../../vcenter/vc_multisite.html).

#### Ampliar com novo cluster

Os usuários também podem ampliar a capacidade de cálculo criando um novo cluster de dentro do console por meio do pedido de hosts e os novos hosts são incluídos automaticamente no novo cluster. Essa opção cria um cluster separado no ambiente e fornece aos usuários a capacidade de segregar física e logicamente as cargas de trabalho de gerenciamento das cargas de trabalho do aplicativo, a capacidade de segregar cargas de trabalho com base em outras características (por exemplo, cluster de banco de dados Microsoft SQL) e a capacidade de implementar aplicativos em topologias altamente disponíveis. Para obter mais informações, veja [Pedindo instâncias do vCenter Server](../../vcenter/vc_orderinginstance.html).

#### Escalar o cluster existente

O usuário pode ampliar um cluster existente pedindo hosts de dentro do console e os novos hosts serão incluídos automaticamente no cluster. Para obter mais informações, veja [Expandindo e contraindo capacidade para instâncias do vCenter Server](../../vcenter/vc_addingremovingservers.html) para obter detalhes. Talvez seja necessário ajustar a política de reserva de HA para o cluster com base em seus requisitos de reserva.

### Escalabilidade do ICP e do IKS

Com base na capacidade de cálculo disponível no local ou em locais da nuvem, os usuários podem ampliar a arquitetura do nó por meio do nó de inicialização implementado inicialmente. Para ampliar o ambiente:
-	Expanda os nós do trabalhador do ICP.
-	Expanda e use a oferta IKS.

#### Expansão do ICP

Os nós da máquina virtual do trabalhador do ICP são escalados para expandir o cálculo e o aplicativo:
- O cliente provisiona uma nova máquina virtual no mesmo VXLAN em que o ICP é implementado.
- Os clientes podem escalar os nós de trabalhadores, provisionando novas máquinas virtuais, em seguida, efetuando login no nó de inicialização e executando um comando para trazer os novos nós para o cluster. Veja [Incluindo ou removendo nós do cluster](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html) para obter detalhes adicionais.
- Use o CAM para automatizar o fornecimento da VM e executar os comandos para incluí-lo no Cluster do ICP.

#### Expansão IKS

Os usuários podem provisionar um ambiente do IKS usando o {{site.data.keyword.cloud_notm}} Portal para ampliar e usar um ambiente de contêiner. Para obter mais informações, veja [Aprimoramentos híbridos no {{site.data.keyword.cloud_notm}} Private e no {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/community/blogs/5092bd93-e659-4f89-8de2-a7ac980487f0/entry/Hybrid_Enhancements_Across_IBM_Cloud_Private_and_IBM_Public_Cloud?lang=en_us).

As implementações do aplicativo no IKS são possíveis usando os métodos a seguir:
-	A conexão e os serviços do IKS são desenvolvidos no CAM e publicados no catálogo do ICP.
-	Multi Cloud Manager, um aprimoramento futuro para gerenciar instâncias do IKS.
-	Linha de comandos do Helm.

### Links relacionados

* [Visão geral do VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
