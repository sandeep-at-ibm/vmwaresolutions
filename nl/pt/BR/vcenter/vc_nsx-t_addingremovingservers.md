---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: vCenter Server NSX-T add hosts, add servers to vCenter Server NSX-T, remove hosts from vCenter Server NSX-T

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Expandindo e contraindo a capacidade para o vCenter Server com instâncias do NSX-T
{: #vc_nsx-t_addingremovingservers}

É possível expandir ou contrair a capacidade de sua instância do VMware vCenter Server com NSX-T de acordo com suas necessidades de negócios, incluindo ou removendo servidores ESXi ou armazenamento do sistema de arquivos (NFS) de rede.

* A partir da liberação V3.1, é possível incluir novos servidores ESXi em um cluster existente, selecionando uma configuração existente ou uma configuração alternativa do que os hosts existentes no cluster. As configurações existentes estão disponíveis para seleção instantânea quando você pede seu novo servidor. Para evitar problemas de desempenho ou estabilidade, é recomendável que os clusters usem a mesma configuração ou uma semelhante em relação a CPU, RAM e armazenamento. Essa funcionalidade é útil para atualizações de hardware dentro do mesmo cluster. Um cluster pode ter apenas um tipo de armazenamento.
* Iniciando com a liberação da V3.0, é possível incluir ou remover simultaneamente o armazenamento NFS e os servidores ESXi de clusters que estão no estado **Pronto para usar**. Por exemplo, é possível incluir ou remover um servidor ESXi em um cluster e incluir ou remover o armazenamento NFS em outro cluster.
* Iniciando com a liberação V2.9, é possível incluir novos servidores ESXi em um cluster enquanto os servidores estão no modo de manutenção. Além disso, é possível incluir ou remover simultaneamente servidores do ESXi em múltiplos clusters.

**Notas**:
* Se seu cluster inicial tiver vSAN como seu armazenamento, incluir um ou mais servidores ESXi após a implementação poderá aumentar a capacidade de armazenamento do cluster.
* É possível incluir ou remover compartilhamentos de armazenamento NFS para ou de um cluster existente NFS ou vSAN do vCenter Server with NSX-T.

## Incluindo servidores ESXi em instâncias do vCenter Server com NSX-T
{: #vc_nsx-t_addingremovingservers-adding}

### Antes de Incluir Servidores ESXi
{: #vc_nsx-t_addingremovingservers-adding-prereq}

* Sempre que possível, inclua servidores ESXi usando o console do {{site.data.keyword.vmwaresolutions_full}}, pois as mudanças feitas no VMware vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}. Portanto, inclua servidores ESXi no vCenter Server somente para servidores ESXi no local ou servidores ESXi que você não possa ou não gerenciará no console do {{site.data.keyword.vmwaresolutions_short}}.
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
7. Opcionalmente, marque a caixa de seleção para incluir servidores durante o modo de manutenção. A caixa de seleção é marcada por padrão.

   Quando você provisionar o novo servidor ESXi, as máquinas virtuais (VMs) serão migradas imediatamente para os novos servidores se você não marcar a caixa de seleção **Modo de manutenção**. Você não recebe uma mensagem de confirmação antes do início da migração.
   {:important}

8. Conclua a configuração do Bare Metal.
   * Selecione uma configuração dentre os hosts existentes no cluster.
   * Selecione uma nova configuração do {{site.data.keyword.baremetal_short_sing}} e especifique o modelo de CPU e o tamanho da RAM.
9. Conclua a configuração de armazenamento. Especifique os tipos de disco para os discos de capacidade e de cache, o número de discos e a edição da Licença da vSAN. Se desejar mais armazenamento, marque a caixa **Intel Optane de alto desempenho**.
10. Revise o custo estimado e clique em **Incluir**.

  Também é possível incluir os recursos provisionados na ferramenta de estimativa do {{site.data.keyword.cloud_notm}}, clicando em **Incluir na estimativa**. Isso é útil se você desejar estimar o custo dos recursos do {{site.data.keyword.vmwaresolutions_short}} selecionados com outros recursos do {{site.data.keyword.cloud_notm}} que você talvez considere comprar.

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

* Sempre que possível, remova os servidores ESXi usando o console do {{site.data.keyword.vmwaresolutions_full}}, pois as mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}. Portanto, remova os servidores ESXi do vCenter Server somente para servidores ESXi no local ou servidores ESXi que você não possa ou não gerenciará no console do {{site.data.keyword.vmwaresolutions_short}}.
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
7. Revise o custo estimado e clique em **Incluir armazenamento NFS**.

  Também é possível incluir os recursos provisionados na ferramenta de estimativa do {{site.data.keyword.cloud_notm}}, clicando em **Incluir na estimativa**. Isso é útil se você desejar estimar o custo dos recursos do {{site.data.keyword.vmwaresolutions_short}} selecionados com outros recursos do {{site.data.keyword.cloud_notm}} que você talvez considere comprar.

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
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server com NSX-T](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_addingviewingcluster#vc_nsx-t_addingviewingcluster)
* [Colocar um host no modo de manutenção](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Suporte ao processador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/s/article/1003212){:new_window}
