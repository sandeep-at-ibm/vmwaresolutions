---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Expandindo e contraindo a capacidade para instâncias do VMware Federal

É possível expandir ou contrair a capacidade de sua instância do VMware Federal de acordo com suas necessidades de negócios, incluindo ou removendo servidores ESXi.

Se o seu cluster primário tiver vSAN como seu armazenamento, incluir um ou mais servidores ESXi após a implementação poderá aumentar a capacidade de armazenamento do cluster.

**Nota:** este recurso está disponível apenas para instâncias do VMware Federal que não foram protegidas.

## Antes de iniciar

* Não inclua nem remova servidores do ESXi do VMware vSphere Web Client. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_full}}.
* Uma instância do VMware Federal com armazenamento NFS deve ter pelo menos 2 servidores ESXi. É possível expandir o cluster padrão para ter até 51 servidores ESXi. Cada um dos clusters não padrão pode ser expandido para ter até 59 servidores ESXi.
* Uma instância do VMware Federal com armazenamento vSAN deve ter pelo menos 4 servidores ESXi.
*  Quando você remover servidores ESXi, os servidores serão colocados no modo de manutenção e depois disso, todas as máquinas virtuais (VMs) em execução nos servidores serão migradas antes de serem removidas do vCenter Server. Para obter o máximo de controle sobre a realocação de VMs, é recomendável colocar os servidores ESXi a serem removidos no modo de manutenção e migrar as VMs em execução neles manualmente usando o VMware vSphere Web Client. Depois disso, remova os servidores ESXi usando o console do {{site.data.keyword.vmwaresolutions_short}}.

## Procedimento

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual você deseja expandir ou contrair a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster no qual você deseja incluir servidores do ESXi ou do qual você deseja remover servidores do ESXi.
5. Para incluir servidores ESXi, conclua as etapas a seguir:
   1. Na tabela **Servidores ESXi**, clique em **Incluir**.
   2. Na janela **Incluir servidor** janela, selecione o número de servidores que você deseja incluir, clique no link de preço para revisar o custo estimado e, em seguida, clique em **Incluir**.
6. Para remover servidores ESXi, selecione os servidores que deseja remover na tabela **Servidores ESXi** e, em seguida, clique em **Remover**.

## Resultados

Depois de iniciar a operação de inclusão ou remoção é possível que haja um pequeno atraso no status da instância enquanto ela muda de **Pronta para usar** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mudanças adicionais na instância.

Você será notificado por e-mail que sua solicitação para incluir ou remover servidores ESXi está sendo processada. O status do cluster associado aos servidores ESXi é mudado para **Modificando**. Quando você remover servidores, observe que os servidores ESXi serão totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud_notm}} no término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias.

**Atenção:** você será cobrado até o fim do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} pelos servidores ESXi removidos.

Se não vir os novos servidores ESXi incluídos na lista no cluster, verifique as notificações por e-mail ou do console para localizar mais detalhes sobre a falha.

### Links relacionados

* [Requisitos e planejamento para as instâncias do VMware Federal](vc_fed_planning.html)
* [Incluindo, visualizando e excluindo clusters para instâncias do VMware Federal](fed_addviewdeleteclusters.html)
* [Colocar um host no modo de manutenção](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Suporte ao processador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
