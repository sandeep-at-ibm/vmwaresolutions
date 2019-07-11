---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: Zerto, Zerto replication billing, order Zerto

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitando Zerto on IBM Cloud
{: #zerto_ordering}

É possível pedir o serviço Zerto on {{site.data.keyword.cloud}} ao pedir uma nova instância com o serviço incluso ou incluindo o serviço em sua instância existente.

## Faturamento para replicação do Zerto
{: #zerto_ordering-billing}

As VMs replicadas usando o Zerto são medidas pelo Zerto e pelo {{site.data.keyword.cloud_notm}}. Sua fatura para esse uso é cobrada por meio de uma conta faturável do {{site.data.keyword.cloud_notm}}, em vez de uma conta de infraestrutura do {{site.data.keyword.cloud_notm}}.

Antes de pedir o Zerto on {{site.data.keyword.cloud_notm}}, assegure-se de que sua conta do {{site.data.keyword.cloud_notm}} seja uma conta faturável e que ela esteja vinculada à mesma conta de infraestrutura do {{site.data.keyword.cloud_notm}} em que sua instância está implementada.

Se você tiver uma instalação do Zerto on {{site.data.keyword.cloud_notm}} da V3.0 ou anterior, os custos de replicação da VM ainda estarão sendo faturados usando o faturamento de infraestrutura do {{site.data.keyword.cloud_notm}}. Se as suas contas e configurações de faturamento atenderem aos requisitos listados anteriormente, será possível converter seu método de faturamento do Zerto em faturável.

No console do {{site.data.keyword.vmwaresolutions_short}}, você é solicitado a converter do plano de infraestrutura do {{site.data.keyword.cloud_notm}} em um plano faturável e fazer upgrade de sua conta do {{site.data.keyword.cloud_notm}} para uma conta faturável, se necessário.

* Para obter informações sobre contas grátis e faturáveis, consulte [Tipos de contas](/docs/account?topic=account-accounts).
* Para obter informações sobre como fazer upgrade para uma conta faturável, consulte [Fazendo upgrade de sua conta](/docs/account?topic=account-upgrading-account).
* Para obter informações sobre como vincular o {{site.data.keyword.cloud_notm}} e suas contas de infraestrutura do {{site.data.keyword.cloud_notm}}, consulte [Alternando para o IBMid e vinculando contas](/docs/account?topic=account-unifyingaccounts).

## Pedindo o Zerto on IBM Cloud para uma nova instância
{: #zerto_ordering-new}

É possível pedir uma nova instância com o Zerto on {{site.data.keyword.cloud_notm}} usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, quando você pedir uma nova instância, selecione **Zerto on IBM Cloud** na seção **Serviços**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **Zerto on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em nova instância**.

## Pedindo o Zerto on IBM Cloud para uma instância existente
{: #zerto_ordering-existing}

É possível incluir o serviço Zerto on {{site.data.keyword.cloud_notm}} em uma instância existente usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, visualize a instância na qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **Zerto on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em instância existente**.

Caso você inclua o Zerto on {{site.data.keyword.cloud_notm}} em uma instância do vCenter Server que tenha um servidor ESXi que está no modo de manutenção, deve-se usar o console do Zerto Virtual Manager (ZVM) e o endereço IP pré-preenchido do Zerto Virtual Replication Appliance (VRA) para implementar manualmente a máquina virtual (VM) do VRA.
{:note}

## Pedindo o Zerto on IBM Cloud para instâncias somente privadas
{: #zerto_ordering-private-only}

Se desejar incluir o Zerto on {{site.data.keyword.cloud_notm}} em uma instância somente privada, assegure-se de que os requisitos a seguir sejam atendidos:
* Você é responsável por configurar seu próprio servidor proxy para se conectar à Internet. Para obter mais informações, consulte [Conectividade de rede pública](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity).
* Deve-se configurar também o recurso Call Home para o Zerto. Para obter mais informações sobre o Zerto Call Home, consulte [Relatório do Zerto para ambientes corporativos (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:new_window}.

## Links relacionados
{: #zerto_ordering-related}

* [ Zerto on  {{site.data.keyword.cloud_notm}}  visão geral ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Gerenciando o Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Solicitando serviços gerenciados para o Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Website zerto.com](https://www.zerto.com){:new_window}
* [Documentação técnica do Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
