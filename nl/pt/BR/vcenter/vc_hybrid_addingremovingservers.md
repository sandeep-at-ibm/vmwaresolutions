---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Expandindo e contraindo a capacidade para instâncias do vCenter Server with Hybridity Bundle

É possível expandir ou contrair a capacidade de sua instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle, de acordo com suas necessidades de negócios, incluindo ou removendo servidores ESXi.

Como seu cluster inicial tem o vSAN como seu armazenamento, incluir um ou mais servidores ESXi após a implementação pode aumentar a capacidade de armazenamento do cluster.

## Antes de iniciar

* Não inclua nem remova servidores do ESXi do VMware vSphere Web Client. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}.
* O armazenamento vSAN requer pelo menos 4 servidores ESXi.
* Antes de remover servidores do ESXi com o serviço F5 on {{site.data.keyword.cloud_notm}} ou o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} instalado, deve-se migrar as VMs do F5 BIG-IP e do FortiGate para um servidor do ESXi diferente daquele que está atualmente hospedando as VMs.
* Antes de remover servidores ESXi com o serviço IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} instalado, assegure-se de que não haja nenhuma operação ativa (com falha ou em andamento) de backup ou restauração, porque essas operações ativas podem impedir que os servidores ESXi sejam removidos.
* Quando você remover servidores ESXi, os servidores serão colocados no modo de manutenção e depois disso, todas as máquinas virtuais (VMs) em execução nos servidores serão migradas antes de serem removidas do vCenter Server. Para obter o máximo de controle sobre a realocação de VMs, é recomendável colocar os servidores ESXi a serem removidos no modo de manutenção e migrar as VMs em execução neles manualmente usando o VMware vSphere Web Client. Depois disso, remova os servidores ESXi usando o console do {{site.data.keyword.vmwaresolutions_short}}.

## Procedimento

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual você deseja expandir ou contrair a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster no qual você deseja incluir servidores do ESXi ou do qual você deseja remover servidores do ESXi.
5. Para incluir servidores ESXi, conclua as etapas a seguir:
   1. Na tabela **Servidores ESXi**, clique em **Incluir**.
   2. Na janela **Incluir servidor**, selecione o número de servidores que você deseja incluir, clique no link de preço para revisar o custo estimado e, em seguida, clique em **Incluir**.
6. Para remover servidores ESXi, selecione os servidores que deseja remover na tabela **Servidores ESXi** e, em seguida, clique em **Remover**.

## Resultados

Depois de iniciar a operação de inclusão ou remoção é possível que haja um pequeno atraso no status da instância enquanto ela muda de **Pronta para usar** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mudanças adicionais na instância.

Você será notificado por e-mail que sua solicitação para incluir ou remover servidores ESXi está sendo processada. O status do cluster associado aos servidores ESXi é mudado para **Modificando**. Quando você remover servidores, observe que os servidores ESXi serão totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud_notm}} no término do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias.

**Atenção:** você será cobrado até o fim do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} pelos servidores ESXi removidos.

Se não vir os novos servidores ESXi incluídos na lista no cluster, verifique as notificações por e-mail ou do console para localizar mais detalhes sobre a falha.

### Links relacionados

* [Lista de materiais do vCenter Server](vc_bom.html)
* [Requisitos e planejamento para instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_planning.html)
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_addingviewingclusters.html)
* [Colocar um host no modo de manutenção](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Suporte ao processador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
