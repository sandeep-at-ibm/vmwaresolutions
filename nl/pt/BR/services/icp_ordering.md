---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-01"

subcollection: vmware-solutions


---

# Pedindo o IBM Cloud Private Hosted
{: #icp_ordering}

É possível pedir o serviço {{site.data.keyword.cloud}} Private Hosted ao pedir uma nova instância com o serviço incluído ou incluindo o serviço em sua instância existente.

## Pedindo o IBM Cloud Private Hosted para uma nova instância
{: #icp_ordering-new}

É possível pedir uma nova instância com o serviço {{site.data.keyword.cloud_notm}} Private Hosted incluído usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, ao pedir uma nova instância, selecione **IBM Cloud Private Hosted** na seção **Serviços opcionais**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **IBM Cloud Private Hosted**, especifique as configurações de serviço e, em seguida, selecione **Incluir em nova instância**.

## Pedindo o IBM Cloud Private Hosted para uma instância existente
{: #icp_ordering-existing}

É possível incluir o serviço {{site.data.keyword.cloud_notm}} Private Hosted em uma instância existente usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e, em seguida, clique em **Incluir**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **IBM Cloud Private Hosted**, especifique as configurações de serviço e, em seguida, selecione **Incluir em instância existente**.

## Configuração do serviço Hospedado do IBM Cloud Privado
{: #icp_ordering-config}

Ao pedir o serviço, forneça as configurações a seguir:
* Selecione **Pronto para produção** ou **Desenvolvimento/teste ** de acordo com suas necessidades.
* Marque a caixa de seleção necessária para certificar que você já obteve a licença necessária para implementar o serviço {{site.data.keyword.cloud_notm}} Private Hosted.

## Implementando nós adicionais
{: #icp_ordering-deploy-nodes}

Se desejar implementar nós adicionais, revise as informações a seguir:
* Use o modelo Ubuntu do {{site.data.keyword.cloud_notm}} Private (Ubuntu1604) implementado com a instalação inicial do {{site.data.keyword.cloud_notm}} Private Hosted.
* Para localizar o modelo Ubuntu, no VMware vSphere Web Client, acesse a guia **VMs e modelos** na pasta `cam`.
* A senha padrão para o modelo Ubuntu é `icponcloud`. Recomenda-se mudar essa senha antes de usar o modelo.
* O {{site.data.keyword.vmwaresolutions_short}} não oferece suporte para aplicar atualizações e correções para o modelo Ubuntu. Deve-se monitorar e aplicar essas atualizações sozinho.

## Links relacionados
{: #icp_ordering-related}

* [Visão geral do IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
