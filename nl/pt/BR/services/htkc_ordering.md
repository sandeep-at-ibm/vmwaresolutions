---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-11"

---

# Pedindo o HyTrust KeyControl on IBM Cloud

É possível pedir o serviço HyTrust KeyControl on {{site.data.keyword.cloud}} ao pedir uma nova instância com um par de HA dos dispositivos HyTrust KeyControl incluídos ou incluindo os dispositivos HyTrust KeyControl em sua instância existente.

## Pedindo o HyTrust KeyControl on IBM Cloud para uma nova instância

É possível pedir uma nova instância com o HyTrust KeyControl on {{site.data.keyword.cloud_notm}} usando um dos seguintes métodos:
* No console do {{site.data.keyword.vmwaresolutions_short}}, ao pedir uma nova instância, selecione **HyTrust KeyControl on IBM Cloud** na seção **Serviços**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **HyTrust KeyControl on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir na nova instância**.

## Pedindo o HyTrust KeyControl on IBM Cloud para uma instância existente

É possível incluir o serviço HyTrust KeyControl on {{site.data.keyword.cloud_notm}} em uma instância existente usando um dos seguintes métodos:
* No console do {{site.data.keyword.vmwaresolutions_short}}, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **HyTrust KeyControl on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir na instância existente**.

## Configuração do serviço HyTrust KeyControl on IBM Cloud

Quando você pedir o serviço, forneça as configurações a seguir.

Especifique se deseja criar um cluster KeyControl altamente disponível de dois nós:
* Se selecionar essa opção, dois nós do KeyControl serão implementados e um novo cluster ativo/ativo altamente disponível será criado. Esse é a opção padrão.
* Se não selecionar essa opção, dois nós independentes do KeyControl serão implementados sem a criação do cluster. Os nós independentes podem ser agrupados manualmente ou incluídos em clusters existentes do KeyControl após a implementação.

### Links relacionados

* [Visão geral do HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](htkc_considerations.html)
* [Gerenciando o HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](managinghtkc.html)
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [HyTrust Website](https://www.hytrust.com/)
