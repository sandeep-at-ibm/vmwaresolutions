---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Expandindo e contraindo a capacidade para instâncias do Cloud Foundation
{: #sd_addingremovingservers}

É possível expandir ou contrair a capacidade de sua instância do VMware Cloud Foundation de acordo com as necessidades do negócio, incluindo ou removendo servidores ESXi.

Uma instância do Cloud Foundation pode ter até cinco clusters, um dos quais é o padrão. Cada cluster inicial pode ter até 51 servidores ESXi e mais clusters podem ter até 59.

## Incluindo servidores ESXi em instâncias do Cloud Foundation
{: #sd_addingremovingservers-adding}

### Antes de Incluir Servidores ESXi
{: #sd_addingremovingservers-adding-prereq}

* Não inclua servidores ESXi do Web client do VMware vSphere. As mudanças que você faz no VMware vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_full}}.
* A plataforma base que você pediu tem 4 servidores ESXi por padrão. É possível expandir a plataforma para no máximo 32 servidores ESXi. No entanto, o número de {{site.data.keyword.baremetal_short}} que você pode incluir de cada vez é o seguinte:
   * Para a configuração **Pequena** e **Grande**, é possível incluir de 1 a 10 servidores ESXi de cada vez.
   * Para a configuração **Skylake** e **Broadwell**, é possível incluir de 1 a 20 servidores ESXi de cada vez.

## Procedimento para Incluir Servidores ESXi
{: #sd_addingremovingservers-adding-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do Cloud Foundation**, clique na instância para a qual você deseja expandir a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster no qual você deseja incluir servidores ESXi.
5. Na seção **Servidores ESXi**, clique em **Incluir**.
6. Na janela **Incluir servidor**, insira o número de servidores que deseja incluir, revise o custo estimado e, em seguida, clique em **Incluir**.

### Resultados após a inclusão de servidores ESXi
{: #sd_addingremovingservers-adding-results}

1. Você pode ter um pequeno atraso no console enquanto o status da instância é mudado de **Pronto para o uso** para **Modificando**. Deixe que a operação seja totalmente concluída antes de fazer mudanças adicionais na instância.
2. Você é notificado por e-mail quando seus servidores ESXi são incluídos.
3. Se não vir os novos servidores ESXi incluídos na lista no cluster, verifique as notificações por e-mail ou do console para localizar mais detalhes sobre a falha.

## Removendo servidores ESXi de instâncias do Cloud Foundation
{: #sd_addingremovingservers-removing}

### Antes de remover servidores ESXi
{: #sd_addingremovingservers-removing-prereq}

* Não remova servidores ESXi do Web client do VMware vSphere. As mudanças que você faz no VMware vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}.
* A plataforma base que você pediu tem 4 servidores ESXi por padrão. É possível remover os servidores ESXi que você incluiu. Não é possível remover os servidores ESXi padrão.
* Antes de remover os servidores ESXi com os serviços F5 on {{site.data.keyword.cloud_notm}} ou FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} instalados, deve-se migrar as MVs F5 BIG-IP e FortiGate para um servidor ESXi diferente daquele que está hospedando as MVs.
* Antes de remover servidores ESXi com o serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} instalado, assegure-se de que não haja operações de backup ou de restauração ativas. Operações ativas, sejam com falha ou em andamento, podem evitar a remoção dos servidores ESXi.

## Procedimento para remover servidores ESXi
{: #sd_addingremovingservers-removing-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do Cloud Foundation**, clique na instância para a qual você deseja contratar capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster do qual você deseja remover servidores ESXi.
6. Na seção **Servidores ESXi**, selecione os servidores que você deseja remover e clique em **Remover**.

### Resultados após a remoção de servidores ESXi
{: #sd_addingremovingservers-removing-results}

1. Você pode ter um pequeno atraso no console enquanto o status da instância é mudado de **Pronto para o uso** para **Modificando**. Permita que a operação seja totalmente concluída antes de fazer mais mudanças na instância.
2. Você é notificado por e-mail quando seus servidores ESXi são removidos.
3. Os servidores ESXi são totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud_notm}} no final do ciclo de faturamento do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias.

   Você é faturado até o término do ciclo de faturamento do {{site.data.keyword.cloud_notm}} para os servidores ESXi removidos.
   {:note}

## Links relacionados
{: #sd_addingremovingservers-related}

* [Lista de materiais do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_bom)
* [Requisitos e planejamento para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_planning)
* [Incluindo, visualizando e excluindo clusters para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-adding-and-viewing-clusters-for-cloud-foundation-instances)
* [Colocar um host no modo de manutenção](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Suporte ao processador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
