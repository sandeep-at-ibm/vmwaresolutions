---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Expandindo e contraindo a capacidade para instâncias do vCenter Server

É possível expandir ou contrair a capacidade de sua instância do VMware vCenter Server de acordo com suas necessidades de negócios, incluindo ou removendo servidores ESXi.

Se seu cluster inicial tiver vSAN como seu armazenamento, incluir um ou mais servidores ESXi após a implementação poderá aumentar a capacidade de armazenamento do cluster.

## Antes de iniciar

* Não inclua nem remova servidores do ESXi do VMware vSphere Web Client. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_full}}.
* Uma instância do vCenter Server com armazenamento NFS deve ter pelo menos 2 servidores ESXi. Para instâncias que são implementadas na V2.1 ou mais recente, é possível expandir o cluster padrão para ter até 51 servidores ESXi. Cada um dos clusters não padrão pode ser expandido para ter até 59 servidores ESXi.
* Uma instância do vCenter Server com armazenamento vSAN deve ter pelo menos 4 servidores ESXi.
* Antes de remover servidores do ESXi com o serviço F5 on {{site.data.keyword.cloud_notm}} ou o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} instalado, deve-se migrar as VMs do F5 BIG-IP e do FortiGate para um servidor do ESXi diferente daquele que está atualmente hospedando as VMs.
* Antes de remover servidores ESXi com o serviço IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} instalado, assegure-se de que não haja nenhuma operação ativa (com falha ou em andamento) de backup ou restauração, porque essas operações ativas podem impedir que os servidores ESXi sejam removidos.
* Quando você remover servidores ESXi, os servidores serão colocados no modo de manutenção e depois disso, todas as máquinas virtuais (VMs) em execução nos servidores serão migradas antes de serem removidas do vCenter Server. Para obter o máximo de controle sobre a realocação de VMs, é recomendável colocar os servidores ESXi a serem removidos no modo de manutenção e migrar as VMs em execução neles manualmente usando o VMware vSphere Web Client. Depois disso, remova os servidores ESXi usando o console do {{site.data.keyword.vmwaresolutions_short}}.
* Para instâncias do vCenter Server que foram implementadas na V2.0 ou anterior, é possível expandir cada cluster para ter até 32 servidores ESXi. O número de {{site.data.keyword.baremetal_short}} que pode ser incluído de cada vez é o seguinte:
   * Para as configurações **Pequeno**, **Médio** e **Grande**, é possível incluir de 1 a 10 servidores ESXi de cada vez.
   * Para a configuração **Customizado**, é possível incluir de 1 a 20 servidores ESXi de cada vez. Para obter mais informações sobre o mínimo de servidores ESXi, veja [Uma instância do vCenter Server com dois nós é altamente disponível?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## Procedimento

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual você deseja expandir ou contrair a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster no qual você deseja incluir servidores do ESXi ou do qual você deseja remover servidores do ESXi.
5. Para incluir servidores ESXi, conclua as etapas a seguir:
   1. Na seção **Servidores ESXi**, clique em **Incluir**.
   2. Na janela **Incluir servidor**, insira o número de servidores que deseja incluir, revise o custo estimado e, em seguida, clique em **Incluir**.
6. Para remover servidores ESXi, selecione os servidores que deseja remover na seção **Servidores ESXi** e, em seguida, clique em **Remover**.

## Resultados

Depois de iniciar a operação de inclusão ou remoção é possível que haja um pequeno atraso no status da instância enquanto ela muda de **Pronta para usar** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mudanças adicionais na instância.

Você será notificado por e-mail que sua solicitação para incluir ou remover servidores ESXi está sendo processada. O status do cluster associado aos servidores ESXi é mudado para **Modificando**. Quando você remover servidores, observe que os servidores ESXi serão totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud_notm}} no término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias.

**Atenção:** você será cobrado até o fim do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} pelos servidores ESXi removidos.

Se não vir os novos servidores ESXi incluídos na lista no cluster, verifique as notificações por e-mail ou do console para localizar mais detalhes sobre a falha.

### Links relacionados

* [Lista de materiais do vCenter Server](vc_bom.html)
* [Requisitos e planejamento para instâncias do vCenter Server](vc_planning.html)
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server](vc_addingviewingclusters.html)
* [Colocar um host no modo de manutenção](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Suporte ao processador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
