---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitando Zerto on IBM Cloud
{: #zerto_ordering}

É possível pedir o serviço Zerto on {{site.data.keyword.cloud}} ao pedir uma nova instância com o serviço incluso ou incluindo o serviço em sua instância existente.

## Pedindo o Zerto on IBM Cloud para uma nova instância
{: #zerto_ordering-new}

É possível pedir uma nova instância com o Zerto on {{site.data.keyword.cloud_notm}} usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, quando você pedir uma nova instância, selecione **Zerto on IBM Cloud** na seção **Serviços**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **Zerto on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em nova instância**.

## Pedindo o Zerto on IBM Cloud para uma instância existente
{: #zerto_ordering-existing}

É possível incluir o serviço Zerto on {{site.data.keyword.cloud_notm}} em uma instância existente usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **Zerto on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em instância existente**.

Se você incluir o Zerto for {{site.data.keyword.cloud_notm}} em uma instância do vCenter Server que tenha um servidor ESXi no modo de manutenção, você deverá usar o console do Zerto Virtual Manager (ZVM) e o endereço IP do Zerto Virtual Replication Appliance (VRA) pré-preenchido para implementar manualmente a máquina virtual (VM) do VRA.
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
