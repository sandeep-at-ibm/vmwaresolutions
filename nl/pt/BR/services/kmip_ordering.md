---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Pedindo o KMIP for VMware on IBM Cloud

É possível pedir o serviço KMIP for VMware on {{site.data.keyword.cloud}} ao pedir uma nova instância com o serviço incluso ou incluindo serviço em sua instância existente.

## Pedindo o KMIP for VMware on IBM Cloud para uma nova instância

É possível pedir uma nova instância com o KMIP for VMware on {{site.data.keyword.cloud_notm}} usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, quando você pedir uma nova instância, selecione **KMIP for VMware on IBM Cloud** na seção **Serviços**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **KMIP for VMware on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em nova instância**.

## Pedindo o KMIP for VMware on IBM Cloud para uma instância existente

É possível incluir o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} em uma instância existente usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **KMIP for VMware on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em instância existente**.

## Configuração do serviço KMIP for VMware on IBM Cloud

Quando você pedir esse serviço, forneça as configurações a seguir:

### Região do serviço

Selecione a região do {{site.data.keyword.cloud_notm}} na qual sua instância de serviço KMIP for VMware {{site.data.keyword.cloud_notm}} deve ser hospedada.

O {{site.data.keyword.cloud_notm}} mantém um terminal de serviço KMIP para VMware no {{site.data.keyword.cloud_notm}} altamente disponível em cada região em que o serviço está disponível.

### Certificado SSL do cliente

Para vCenter Server, deve-se configurar um cluster Key Server Management (KMS). O terminal em sua região selecionada se conecta de forma segura ao KMS por meio do certificado SSL do cliente. Veja a tabela a seguir para o terminal em cada região. Esses terminais usam certificados autoassinados que são mantidos pela equipe do {{site.data.keyword.vmwaresolutions_short}}. A impressão digital para os certificados é `a9 d0 ff 15 df 85 10 6b 61 88 fe 2e 8b d3 1a af 48 c8 a0 7a`.

Tabela 1. Regiões do terminal do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Região         | Terminal               |
|:---------------|:-----------------------|
| Alemanha        |  `161.156.68.107:5696` |
| Sydney         |  `130.198.73.134:5696` |
| Reino Unido |  `158.175.93.122:5696` |
| Sul dos EUA       |  `169.60.185.42:5696`  |

Essa configuração é opcional no momento da configuração inicial. É possível deixar esse campo em branco porque o certificado de cliente do KMS no vCenter Server é conhecido depois que sua instância é implementada. Mas deve-se inserir o certificado depois que sua instância é implementada para que a conexão do vCenter Server com o KMS possa ser concluída com êxito.

### Chave API para o ID do serviço

Insira a chave API para o ID do serviço do {{site.data.keyword.cloud_notm}} que é usado para acessar a instância do IBM Key Protect Service.

### Instância do Key Protect

Clique em **Recuperar** para obter a lista de instâncias disponíveis do IBM Key Protect Service e selecione aquela a ser usada para o gerenciamento de chave.

### Chave raiz do cliente

Clique em **Recuperar** para obter a chave raiz do cliente que está armazenada em sua instância selecionada do IBM Key Protect.



### Links relacionados

* [ Visão geral do KMIP for VMware on  {{site.data.keyword.cloud_notm}}  overview ](kmip_considerations.html)
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Key Protect para {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
