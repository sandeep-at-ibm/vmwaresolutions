---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-18"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Expandindo e contraindo a capacidade para instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservers}

É possível expandir ou contrair a capacidade de sua instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle, de acordo com suas necessidades de negócios, incluindo ou removendo servidores ESXi.

Iniciando com a liberação V2.9, é possível incluir novos servidores ESXi em um cluster enquanto o cluster está no modo de manutenção. Além disso, é possível incluir ou remover simultaneamente servidores do ESXi em múltiplos clusters. As operações simultâneas a seguir estão disponíveis:

* Incluir hosts em um cluster e incluir hosts em clusters adicionais.
* Remover hosts de um cluster e remover hosts de clusters adicionais.
* Incluir hosts em um cluster e remover hosts de clusters adicionais.
* Remover hosts de um cluster e incluir hosts em clusters adicionais.

Como seu cluster inicial tem o vSAN como seu armazenamento, incluir um ou mais servidores ESXi após a implementação pode aumentar a capacidade de armazenamento do cluster.

## Incluindo servidores ESXi em instâncias do vCenter Server with Hybridity Bundle

### Antes de Incluir Servidores ESXi
{: #vc_hybrid_addingremovingservers-adding-prereq}

* Não inclua servidores ESXi do Web client do VMware vSphere. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}.
* O armazenamento vSAN requer pelo menos 4 servidores ESXi.

## Procedimento para Incluir Servidores ESXi
{: #vc_hybrid_addingremovingservers-adding-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja expandir a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster no qual você deseja incluir servidores ESXi.
5. Na tabela **Servidores ESXi**, clique em **Incluir**.
6. Na janela **Incluir servidor**, insira o número de servidores que você deseja incluir.
7. Opcionalmente, marque a caixa de seleção para incluir servidores durante o modo de manutenção.
8. Revise o custo estimado e clique em **Incluir**.

### Resultados após a inclusão de servidores ESXi
{: #vc_hybrid_addingremovingservers-adding-results}

1. Você pode ter um pequeno atraso no console enquanto o status da instância é mudado de **Pronto para o uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mais mudanças na instância.
2. Você é notificado por e-mail de que sua solicitação para incluir servidores ESXi está sendo processada. No console, o status do cluster que está associado a servidores ESXi foi mudado para **Modificando**.
3. Caso não veja os novos servidores ESXi incluídos na lista no cluster, verifique as notificações por e-mail ou no console para localizar mais detalhes sobre a falha.

Se você estiver incluindo servidores ESXi durante o modo de manutenção, as máquinas virtuais (VMs) não serão migradas para os novos servidores até que você remova o cluster do modo de manutenção.   
{:important}

## Removendo servidores ESXi de instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservers-removing}

### Antes de remover servidores ESXi
{: #vc_hybrid_addingremovingservers-removing-prereq}

* Não remova servidores ESXi do Web client do VMware vSphere. As mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}.
* O armazenamento vSAN requer pelo menos 4 servidores ESXi.
* Antes de remover os servidores ESXi com os serviços F5 on {{site.data.keyword.cloud_notm}} ou FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} instalados, deve-se migrar as MVs F5 BIG-IP e FortiGate para um servidor ESXi diferente daquele que está hospedando as MVs.
* Antes de remover servidores ESXi com o serviço IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} instalado, assegure-se de que não haja operações de backup ou de restauração (com falha ou em andamento) ativas porque essas operações ativas podem evitar a remoção dos servidores ESXi.
* Quando você remover servidores ESXi, os servidores serão colocados no modo de manutenção e depois disso, todas as máquinas virtuais (MVs) em execução nos servidores serão migradas antes de serem removidas do vCenter Server. Para obter o máximo de controle sobre a realocação de MVs, é recomendável colocar os servidores ESXi a serem removidos no modo de manutenção e migrar as MVs em execução neles manualmente usando o VMware vSphere Web Client. Depois disso, remova os servidores ESXi usando o console do {{site.data.keyword.vmwaresolutions_short}}.

## Procedimento para remover servidores ESXi
{: #vc_hybrid_addingremovingservers-removing-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja contratar a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster do qual você deseja remover servidores ESXi.
5. Na tabela **Servidores ESXi**, selecione os servidores que você deseja remover e clique em **Remover**.

### Resultados após a remoção de servidores ESXi
{: #vc_hybrid_addingremovingservers-removing-results}

1. Você pode ter um pequeno atraso no console enquanto o status da instância é mudado de **Pronto para o uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mudanças adicionais na instância.
2. Você é notificado por e-mail de que sua solicitação para remover servidores ESXi está sendo processada. No console, o status do cluster associado aos servidores ESXi é mudado para **Modificando**.
3. Os servidores ESXi são totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud_notm}} no final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que é tipicamente de 30 dias.

   Você é faturado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para os servidores ESXi removidos.
   {:note}

## Links relacionados
{: #vc_hybrid_addingremovingservers-related}

* [Lista de materiais do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Requisitos e planejamento para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [Colocar um host no modo de manutenção](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Suporte ao processador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
