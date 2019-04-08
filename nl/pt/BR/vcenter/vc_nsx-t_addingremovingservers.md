---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-18"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Expandindo e contraindo a capacidade para o vCenter Server com instâncias do NSX-T
{: #vc_nsx-t_addingremovingservers}

É possível expandir ou contrair a capacidade de sua instância do VMware vCenter Server com NSX-T de acordo com suas necessidades de negócios, incluindo ou removendo servidores ESXi ou armazenamento do sistema de arquivos (NFS) de rede.

é possível incluir novos servidores ESXi em um cluster enquanto ele está no modo de manutenção. Além disso, é possível incluir ou remover simultaneamente servidores do ESXi em múltiplos clusters. As operações simultâneas a seguir estão disponíveis:

* Incluir hosts em um cluster e incluir hosts em clusters adicionais.
* Remover hosts de um cluster e remover hosts de clusters adicionais.
* Incluir hosts em um cluster e remover hosts de clusters adicionais.
* Remover hosts de um cluster e incluir hosts em clusters adicionais.https://github.ibm.com/tornado/tracker/issues/14183

É possível incluir ou remover compartilhamentos de armazenamento NFS para ou de um cluster NFS ou vSAN vCenter Server com NSX-T existente.
{:note}

Se seu cluster inicial tiver vSAN como seu armazenamento, incluir um ou mais servidores ESXi após a implementação poderá aumentar a capacidade de armazenamento do cluster.

## Incluindo servidores ESXi em instâncias do vCenter Server com NSX-T
{: #vc_nsx-t_addingremovingservers-adding}

### Antes de Incluir Servidores ESXi
{: #vc_nsx-t_addingremovingservers-adding-prereq}

* Não inclua servidores ESXi do Web client do VMware vSphere. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_full}}.
* Uma instância do vCenter Server com NSX-T com armazenamento NFS deve ter pelo menos 3 servidores ESXi. É possível expandir o cluster padrão para ter até 51 servidores ESXi. Cada um dos clusters não padrão pode ser expandido para ter até 59 servidores ESXi.
* Uma instância do vCenter Server com NSX-T com armazenamento vSAN deve ter pelo menos 4 servidores ESXi.

### Procedimento para Incluir Servidores ESXi
{: #vc_nsx-t_addingremovingservers-adding-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja expandir a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster no qual você deseja incluir servidores ESXi.
5. Na seção **Servidores ESXi**, clique em **Incluir**.
6. Na janela **Incluir servidor**, insira o número de servidores que você deseja incluir.
7. Opcionalmente, marque a caixa de seleção para incluir servidores durante o modo de manutenção.
8. Revise o custo estimado e clique em **Incluir**.

### Resultados após a inclusão de servidores ESXi
{: #vc_nsx-t_addingremovingservers-adding-results}

1. Você pode ter um pequeno atraso no console enquanto o status da instância é mudado de **Pronto para o uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mais mudanças na instância.
2. Você é notificado por e-mail de que sua solicitação para incluir servidores ESXi está sendo processada. No console, o status do cluster que está associado a servidores ESXi foi mudado para **Modificando**.
3. Se não vir os novos servidores ESXi incluídos na lista no cluster, verifique as notificações por e-mail ou do console para localizar mais detalhes sobre a falha.

Se você estiver incluindo servidores ESXi durante o modo de manutenção, as máquinas virtuais (VMs) não serão migradas para os novos servidores até que você remova o cluster do modo de manutenção.   
{:important}

## Removendo servidores ESXi de instâncias do vCenter Server com NSX-T
{: #vc_nsx-t_addingremovingservers-removing}

### Antes de remover servidores ESXi
{: #vc_nsx-t_addingremovingservers-removing-prereq}

* Não remova servidores ESXi do Web client do VMware vSphere. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}.
* Uma instância do vCenter Server com NSX-T com armazenamento NFS deve ter pelo menos 3 servidores ESXi e uma instância do vCenter Server com NSX-T com armazenamento vSAN deve ter pelo menos 4 servidores ESXi.
* Ao remover os servidores ESXi, eles são colocados no modo de manutenção e, depois disso, todas as VMs em execução nos servidores são migradas antes de serem removidas do vCenter Server. Para obter o máximo de controle sobre a realocação de MVs, é recomendável colocar os servidores ESXi a serem removidos no modo de manutenção e migrar as MVs em execução neles manualmente usando o VMware vSphere Web Client. Depois disso, remova os servidores ESXi usando o console do {{site.data.keyword.vmwaresolutions_short}}.

### Procedimento para remover servidores ESXi
{: #vc_nsx-t_addingremovingservers-removing-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja contratar a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster do qual você deseja remover servidores ESXi.
5. Na seção **Servidores ESXi**, selecione os servidores que você deseja remover e clique em **Remover**.

### Resultados após a remoção de servidores ESXi
{: #vc_nsx-t_addingremovingservers-removing-results}

1. Você pode ter um pequeno atraso no console quando o status da instância muda de **Pronto para uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mais mudanças na instância.
2. Você é notificado por e-mail de que sua solicitação para remover servidores ESXi está sendo processada. No console, o status do cluster que está associado a servidores ESXi foi mudado para **Modificando**.
3. Os servidores ESXi são totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud_notm}} no final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que é tipicamente de 30 dias.

   Você é faturado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para os servidores ESXi removidos.
   {:note}

## Incluindo armazenamento NFS nas instâncias do vCenter Server com NSX-T
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-to-vcs-nsx-t}

### Antes de Incluir o Armazenamento NFS
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-prereq}

Não inclua armazenamento NFS por meio do VMware vSphere Web Client. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}. A IBM não gerenciará compartilhamentos de arquivo NFS que você inclui manualmente em uma instância.

### Procedimento para incluir armazenamento NFS
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja expandir a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster no qual você deseja incluir armazenamento NFS.
5. Na seção  ** Armazenamento ** , clique em  ** Incluir **.
6. Na janela **Armazenamento**, conclua a configuração de armazenamento.
   * Se você desejar incluir e configurar as mesmas configurações em todos os compartilhamentos de arquivo, especifique o **Número de compartilhamentos**, **Desempenho** e **Tamanho (GB)**.
   * Se você desejar incluir e configurar compartilhamentos de arquivo individualmente, selecione **Configurar compartilhamentos individualmente** e, em seguida, clique no ícone **+** ao lado do rótulo **Incluir armazenamento compartilhado** e selecione o **Desempenho** e o **Tamanho (GB)** para cada compartilhamento de arquivo individual. Deve-se selecionar pelo menos um compartilhamento de arquivo.
7. Clique em  ** Incluir armazenamento NFS **.

### Resultados depois de incluir o armazenamento NFS
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-results}

1. Você pode ter um pequeno atraso no console enquanto o status da instância é mudado de **Pronto para o uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mais mudanças na instância.
2. Você é notificado por e-mail de que sua solicitação para incluir armazenamento NFS está sendo processada. No console, o status do cluster que está associado ao armazenamento NFS muda para **Modificando**.
3. Se você não vir o novo armazenamento NFS incluído na lista no cluster, verifique as notificações por e-mail ou do console para localizar mais detalhes sobre a falha.

## Removendo o armazenamento NFS das instâncias do vCenter Server com NSX-T
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage}

### Antes de remover o armazenamento NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-prereq}

* Não remova o armazenamento NFS do VMware vSphere Web Client. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}.
* Antes de remover o armazenamento NFS, assegure-se de ter removido todas as MVs que residem no armazenamento.
* Assegure-se de que os compartilhamentos que você planeja remover estejam associados à instância do vCenter Server
correta.
* O cluster deve estar no status **Pronto para uso**.

### Procedimento para remover o armazenamento NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja contratar a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster do qual você deseja remover o armazenamento NFS.
5. Na seção **Armazenamento**, selecione o compartilhamento de armazenamento que você deseja remover e clique em **Excluir**.
6. Clique em **Remover** na janela **Remover armazenamento**.

### Resultados após a remoção do armazenamento NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-results}

1. Você pode ter um pequeno atraso no console quando o status da instância muda de **Pronto para uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mais mudanças na instância.
2. Você é notificado por e-mail de que sua solicitação para remover o armazenamento NFS está sendo processada. No console, o status do cluster que está associado ao armazenamento NFS muda para **Modificando**.
3. O armazenamento NFS é totalmente recuperado pela infraestrutura do {{site.data.keyword.cloud_notm}} no término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias.

   Você é faturado até o término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para o armazenamento NFS removido.
   {:note}

## Links relacionados
{: #vc_nsx-t_addingremovingservers-related}

* [Lista de materiais do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Requisitos e planejamento para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [ Pedindo o vCenter Server com instâncias do NSX-T ](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server com NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_deletinginstance)
* [Colocar um host no modo de manutenção](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Suporte ao processador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
