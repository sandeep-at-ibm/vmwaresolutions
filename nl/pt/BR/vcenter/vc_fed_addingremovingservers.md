---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Expandindo e contraindo a capacidade para instâncias do VMware Federal

É possível expandir ou contrair a capacidade de sua instância do VMware Federal de acordo com suas necessidades de negócios, incluindo ou removendo servidores ESXi.

Se o seu cluster primário tiver vSAN como seu armazenamento, incluir um ou mais servidores ESXi após a implementação poderá aumentar a capacidade de armazenamento do cluster.

Esse recurso está disponível apenas para instâncias do VMware Federal que não foram protegidas.
{:note}

## Incluindo servidores ESXi em instâncias do VMware Federal

### Antes de Incluir Servidores ESXi

* Não inclua servidores ESXi do Web client do VMware vSphere. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_full}}.
* Uma instância do VMware Federal com armazenamento NFS deve ter pelo menos 2 servidores ESXi. É possível expandir o cluster padrão para ter até 51 servidores ESXi. Cada um dos clusters não padrão pode ser expandido para ter até 59 servidores ESXi.
* Uma instância do VMware Federal com armazenamento vSAN deve ter pelo menos 4 servidores ESXi.

## Procedimento para Incluir Servidores ESXi

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja expandir a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster no qual você deseja incluir servidores ESXi.
5. Na tabela **Servidores ESXi**, clique em **Incluir**.
6. Na janela **Incluir servidor** janela, selecione o número de servidores que você deseja incluir, clique no link de preço para revisar o custo estimado e, em seguida, clique em **Incluir**.

### Resultados após a inclusão de servidores ESXi

1. Você pode ter um pequeno atraso no console enquanto o status da instância é mudado de **Pronto para o uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mudanças adicionais na instância.
2. Você é notificado por e-mail de que sua solicitação para incluir servidores ESXi está sendo processada. No console, o status do cluster associado aos servidores ESXi é mudado para **Modificando**.
3. Se não vir os novos servidores ESXi incluídos na lista no cluster, verifique as notificações por e-mail ou do console para localizar mais detalhes sobre a falha.

## Removendo servidores ESXi de instâncias do VMware Federal

### Antes de remover servidores ESXi

* Não remova servidores ESXi do Web client do VMware vSphere. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}.
* Uma instância do VMware Federal com armazenamento NFS deve ter pelo menos 2 servidores ESXi e uma instância do VMware Federal com armazenamento vSAN deve ter pelo menos 4 servidores ESXi.
* Quando você remover servidores ESXi, os servidores serão colocados no modo de manutenção e depois disso, todas as máquinas virtuais (MVs) em execução nos servidores serão migradas antes de serem removidas do vCenter Server. Para obter o máximo de controle sobre a realocação de MVs, é recomendável colocar os servidores ESXi a serem removidos no modo de manutenção e migrar as MVs em execução neles manualmente usando o VMware vSphere Web Client. Depois disso, remova os servidores ESXi usando o console do {{site.data.keyword.vmwaresolutions_short}}.

## Procedimento para remover servidores ESXi

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja contratar a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster do qual você deseja remover servidores ESXi.
5. Na tabela **Servidores ESXi**, selecione os servidores que você deseja remover e clique em **Remover**.

### Resultados após a remoção de servidores ESXi

1. Você pode ter um pequeno atraso no console enquanto o status da instância é mudado de **Pronto para o uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mudanças adicionais na instância.
2. Você é notificado por e-mail de que sua solicitação para remover servidores ESXi está sendo processada. No console, o status do cluster associado aos servidores ESXi é mudado para **Modificando**.
3. Os servidores ESXi são totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud_notm}} no final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que é tipicamente de 30 dias.

   Você é faturado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para os servidores ESXi removidos.
   {:note}

### Links relacionados

* [Requisitos e planejamento para as instâncias do VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_planning.html)
* [Incluindo, visualizando e excluindo clusters para instâncias do VMware Federal](/docs/services/vmwaresolutions/vcenter/fed_addviewdeleteclusters.html)
* [Colocar um host no modo de manutenção](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Suporte ao processador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
