---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Expandindo e contraindo a capacidade para instâncias do vCenter Server

É possível expandir ou contrair a capacidade de sua instância do VMware vCenter Server de acordo com suas necessidades de negócios, incluindo ou removendo servidores ESXi ou armazenamento network file system (NFS).

É possível incluir ou remover compartilhamentos de armazenamento NFS para ou de um cluster do NFS ou do vSAN vCenter Server existente.
{:note}

Se seu cluster inicial tiver vSAN como seu armazenamento, incluir um ou mais servidores ESXi após a implementação poderá aumentar a capacidade de armazenamento do cluster.

## Incluindo servidores ESXi em instâncias do vCenter Server

### Antes de Incluir Servidores ESXi

* Não inclua servidores ESXi do Web client do VMware vSphere. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_full}}.
* Uma instância do vCenter Server com armazenamento NFS deve ter pelo menos 2 servidores ESXi. Para instâncias que são implementadas na V2.1 ou mais recente, é possível expandir o cluster padrão para ter até 51 servidores ESXi. Cada um dos clusters não padrão pode ser expandido para ter até 59 servidores ESXi.
* Uma instância do vCenter Server com armazenamento vSAN deve ter pelo menos 4 servidores ESXi.
* Para instâncias do vCenter Server que foram implementadas na V2.0 ou anterior, é possível expandir cada cluster para ter até 32 servidores ESXi. O número de {{site.data.keyword.baremetal_short}} que pode ser incluído de cada vez é o seguinte:
   * Para as configurações **Pequeno**, **Médio** e **Grande**, é possível incluir de 1 a 10 servidores ESXi de cada vez.
   * Para as configurações **Skylake** e **Broadwell**, é possível incluir de 1 a 20 servidores ESXi de cada vez. Para obter mais informações sobre o mínimo de servidores ESXi, veja [Uma instância do vCenter Server com dois nós é altamente disponível?](/docs/services/vmwaresolutions/vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

### Procedimento para Incluir Servidores ESXi

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja expandir a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster no qual você deseja incluir servidores ESXi.
5. Na seção **Servidores ESXi**, clique em **Incluir servidor**.
6. Na janela **Incluir servidor**, insira o número de servidores que você deseja incluir, revise o custo estimado e, em seguida, clique em **Incluir servidor**.

### Resultados após a inclusão de servidores ESXi

1. Você pode ter um pequeno atraso no console enquanto o status da instância é mudado de **Pronto para o uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mais mudanças na instância.
2. Você é notificado por e-mail de que sua solicitação para incluir servidores ESXi está sendo processada. No console, o status do cluster que está associado a servidores ESXi foi mudado para **Modificando**.
3. Se não vir os novos servidores ESXi incluídos na lista no cluster, verifique as notificações por e-mail ou do console para localizar mais detalhes sobre a falha.

## Removendo servidores ESXi de instâncias do vCenter Server

### Antes de remover servidores ESXi

* Não remova servidores ESXi do Web client do VMware vSphere. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}.
* Uma instância do vCenter Server com armazenamento NFS deve ter pelo menos 2 servidores ESXi e uma instância do vCenter Server com armazenamento vSAN
deve ter pelo menos 4 servidores ESXi.
* Antes de remover os servidores ESXi com os serviços F5 on {{site.data.keyword.cloud_notm}} ou FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} instalados, deve-se migrar as MVs F5 BIG-IP e FortiGate para um servidor ESXi diferente daquele que está hospedando as MVs.
* Antes de remover servidores ESXi com o serviço IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} instalado, assegure-se de que não haja nenhuma operação ativa (com falha ou em andamento) de backup ou restauração, porque essas operações ativas podem impedir que os servidores ESXi sejam removidos.
* Quando você remover servidores ESXi, os servidores serão colocados no modo de manutenção e depois disso, todas as máquinas virtuais (MVs) em execução nos servidores serão migradas antes de serem removidas do vCenter Server. Para obter o máximo de controle sobre a realocação de MVs, é recomendável colocar os servidores ESXi a serem removidos no modo de manutenção e migrar as MVs em execução neles manualmente usando o VMware vSphere Web Client. Depois disso, remova os servidores ESXi usando o console do {{site.data.keyword.vmwaresolutions_short}}.

### Procedimento para remover servidores ESXi

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja contratar a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster do qual você deseja remover servidores ESXi.
5. Na seção **Servidores ESXi**, selecione os servidores que você deseja remover e clique em **Remover**.

### Resultados após a remoção de servidores ESXi

1. Você pode ter um pequeno atraso no console quando o status da instância muda de **Pronto para uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mais mudanças na instância.
2. Você é notificado por e-mail de que sua solicitação para remover servidores ESXi está sendo processada. No console, o status do cluster que está associado a servidores ESXi foi mudado para **Modificando**.
3. Os servidores ESXi são totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud_notm}} no final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que é tipicamente de 30 dias.

   Você é faturado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para os servidores ESXi removidos.
   {:note}

## Incluindo armazenamento NFS em instâncias do vCenter Server

### Antes de Incluir o Armazenamento NFS

Não inclua armazenamento NFS por meio do VMware vSphere Web Client. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}. A IBM não gerenciará compartilhamentos de arquivo NFS que você inclui manualmente em uma instância.

### Procedimento para incluir armazenamento NFS

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja expandir a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster no qual você deseja incluir armazenamento NFS.
5. Na seção  ** Armazenamento ** , clique em  ** Incluir **.
6. Na janela **Armazenamento**, conclua a configuração de armazenamento.
   * Se você desejar incluir e configurar as mesmas configurações em todos os compartilhamentos de arquivo, especifique o **Número de compartilhamentos**, **Desempenho** e **Tamanho (GB)**.
   * Se você desejar incluir e configurar compartilhamentos de arquivo individualmente, selecione **Configurar compartilhamentos individualmente** e, em seguida, clique no ícone **+** ao lado do rótulo **Incluir armazenamento compartilhado** e selecione o **Desempenho** e o **Tamanho (GB)** para cada compartilhamento de arquivo individual. Deve-se selecionar pelo menos um compartilhamento de arquivo.
7. Clique em  ** Incluir armazenamento NFS **.

### Resultados depois de incluir o armazenamento NFS

1. Você pode ter um pequeno atraso no console enquanto o status da instância é mudado de **Pronto para o uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mais mudanças na instância.
2. Você é notificado por e-mail de que sua solicitação para incluir armazenamento NFS está sendo processada. No console, o status do cluster que está associado ao armazenamento NFS muda para **Modificando**.
3. Se você não vir o novo armazenamento NFS incluído na lista no cluster, verifique as notificações por e-mail ou do console para localizar mais detalhes sobre a falha.

## Removendo o armazenamento NFS de instâncias do vCenter Server

### Antes de remover o armazenamento NFS

* Não remova o armazenamento NFS do VMware vSphere Web Client. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}.
* Antes de remover o armazenamento NFS, assegure-se de ter removido todas as MVs que residem no armazenamento.
* Assegure-se de que os compartilhamentos que você planeja remover estejam associados à instância do vCenter Server
correta.
* O cluster deve estar no status **Pronto para uso**.

### Procedimento para remover o armazenamento NFS

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja contratar a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster do qual você deseja remover o armazenamento NFS.
5. Na seção **Armazenamento**, selecione o compartilhamento de armazenamento que você deseja remover e clique em **Excluir**.
6. Clique em **Remover** na janela **Remover armazenamento**.

### Resultados após a remoção do armazenamento NFS

1. Você pode ter um pequeno atraso no console quando o status da instância muda de **Pronto para uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mais mudanças na instância.
2. Você é notificado por e-mail de que sua solicitação para remover o armazenamento NFS está sendo processada. No console, o status do cluster que está associado ao armazenamento NFS muda para **Modificando**.
3. O armazenamento NFS é totalmente recuperado pela infraestrutura do {{site.data.keyword.cloud_notm}} no término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias.

   Você é faturado até o término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para o armazenamento NFS removido.
   {:note}


### Links relacionados

* [Lista de materiais do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_bom.html)
* [Requisitos e planejamento para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_planning.html)
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)
* [Colocar um host no modo de manutenção](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Suporte ao processador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
