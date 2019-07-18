---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: vCenter Server Hybridity add host, add server vCenter Server Hybridity, remove host vCenter Server Hybridity

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Expandindo e contraindo a capacidade para instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservers}

É possível expandir ou contrair a capacidade de sua instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle, de acordo com suas necessidades de negócios, incluindo ou removendo servidores ESXi.

A partir da liberação V3.1, é possível incluir novos servidores ESXi em um cluster existente, selecionando uma configuração existente ou uma configuração alternativa do que os hosts existentes no cluster. As configurações existentes estão disponíveis para seleção instantânea quando você pede seu novo servidor. Para evitar problemas de desempenho ou estabilidade, é recomendável que os clusters usem a mesma configuração ou uma semelhante em relação a CPU, RAM e armazenamento. Essa funcionalidade é útil para atualizações de hardware dentro do mesmo cluster. Um cluster pode ter apenas um tipo de armazenamento.

Iniciando com a liberação V2.9, é possível incluir novos servidores ESXi em um cluster enquanto o cluster está no modo de manutenção. Além disso, é possível incluir ou remover simultaneamente servidores do ESXi em múltiplos clusters. As operações simultâneas a seguir estão disponíveis:

* Incluir hosts em um cluster e incluir hosts em clusters adicionais.
* Remover hosts de um cluster e remover hosts de clusters adicionais.
* Incluir hosts em um cluster e remover hosts de clusters adicionais.
* Remover hosts de um cluster e incluir hosts em clusters adicionais.

Como seu cluster inicial tem o vSAN como seu armazenamento, incluir um ou mais servidores ESXi após a implementação pode aumentar a capacidade de armazenamento do cluster.

## Incluindo servidores ESXi em instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservers-adding}

### Antes de Incluir Servidores ESXi
{: #vc_hybrid_addingremovingservers-adding-prereq}

* Sempre que possível, inclua servidores ESXi usando o console do {{site.data.keyword.vmwaresolutions_full}}, pois as mudanças feitas no VMware vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}. Portanto, inclua servidores ESXi no vCenter Server somente para servidores ESXi no local ou servidores ESXi que você não possa ou não gerenciará no console do {{site.data.keyword.vmwaresolutions_short}}.
* O armazenamento vSAN requer pelo menos 4 servidores ESXi.

## Procedimento para Incluir Servidores ESXi
{: #vc_hybrid_addingremovingservers-adding-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual você deseja expandir a capacidade.
3. Clique em **Infraestrutura** na área de janela de navegação esquerda.
4. Na tabela **CLUSTERS**, clique no cluster no qual você deseja incluir servidores ESXi.
5. Na tabela **Servidores ESXi**, clique em **Incluir**.
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

* Sempre que possível, remova os servidores ESXi usando o console do {{site.data.keyword.vmwaresolutions_full}}, pois as mudanças feitas no vSphere Web Client não são sincronizadas com o console do {{site.data.keyword.vmwaresolutions_short}}. Portanto, remova os servidores ESXi do vCenter Server somente para servidores ESXi no local ou servidores ESXi que você não possa ou não gerenciará no console do {{site.data.keyword.vmwaresolutions_short}}.
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
* [Colocar um host no modo de manutenção](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:external}
* [Suporte ao processador Enhanced vMotion Compatibility (EVC)](https://kb.vmware.com/s/article/1003212){:external}
