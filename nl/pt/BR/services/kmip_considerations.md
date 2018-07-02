---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Visão geral do KMIP for VMware on IBM Cloud

O serviço KMIP para VMware no {{site.data.keyword.cloud}} fornece um serviço altamente disponível 24 horas por dia, 7 dias por semana para gerenciar chaves de criptografia que são usadas pelo VMware no {{site.data.keyword.cloud_notm}}. Este serviço oferece a capacidade de tempo de execução para permitir que os clientes criem, recuperem, ativem, revoguem e destruam as chaves de criptografia e também fornece a capacidade de gerenciamento para manter as associações entre as credenciais do cliente e essas chaves de criptografia.

**Disponibilidade**: esse serviço está disponível somente para instâncias implementadas na V2.2 ou liberações mais recentes.

## Considerações ao instalar o KMIP para VMware no IBM Cloud

O KMIP para VMware no {{site.data.keyword.cloud_notm}} usa o serviço IBM Key Protect for IBM Cloud para criar, criptografar e decriptografar chaves de criptografia. Portanto, antes de instalar o serviço, assegure-se de ter pedido um serviço utilizável Key Protect. Enquanto isso, um ID do serviço do {{site.data.keyword.cloud_notm}} foi criado seguindo as etapas em [Criando um ID do serviço](https://console.bluemix.net/docs/iam/serviceid.html#creating-a-service-id) para acessar a instância de serviço Key Protect que você criou.

Assegure-se de conceder os seguintes níveis de acesso para o ID de serviço:
* No nível de acesso de plataforma: autoridade de visualizador para sua instância do IBM Key Protect.
* No nível de acesso de serviço: autoridade de gravador para sua instância do IBM Key Protect.

A chave API para o ID do serviço criado é necessária ao pedir o serviço.

O serviço supõe que você já tenha criado pelo menos um customer root key (CRK) na interface com o usuário do Key Protect seguindo as etapas em [Criando chaves raiz](https://console.bluemix.net/docs/services/keymgmt/keyprotect_create_root.html#create_root_keys) ou usando a API RESTful no [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect).

Não é possível pedir o serviço sem CRKs. É altamente recomendado usar o método para criar um CRK usando o material chave existente e fazer backup do material chave que você está criando. Ao fazer isso, você assegura que possa recuperar suas chaves no caso de uma falha total do data center no qual o IBM Key Protect é aplicado para armazenar seus CRKs.

## Considerações ao usar o KMIP para VMware no IBM Cloud

* Para usar um serviço pedido KMIP para VMware no {{site.data.keyword.cloud_notm}} como um Key Management Server (KMS) registrado para VMware vCenter Server, deve-se assegurar que as configurações estejam em vigor para que a conectividade de rede do vCenter Server com o terminal do serviço pedido KMIP para VMware no {{site.data.keyword.cloud_notm}} esteja funcional.
* Para usar o serviço para criptografia do VMware vSAN, deve-se assegurar que a conectividade de rede entre os hosts no vSAN de destino e o terminal do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} pedido esteja funcional.


## Considerações ao remover o KMIP para VMware no IBM Cloud

O certificado público do VMware fornecido durante o pedido ou uso do serviço é usado como o certificado de cliente para se comunicar com a instância de serviço. Quando o serviço é removido, todas as chaves de criptografia criadas por essa instância de serviço para o certificado público do VMware associado são removidas junto.

Portanto, antes de remover o serviço, deve-se assegurar que nenhuma máquina virtual ou vSANs esteja sendo criptografado(a) usando as chaves criadas pelo serviço KMIP.

## Links relacionados

* [Pedindo o KMIP for VMware on IBM Cloud](kmip_ordering.html)
* [IBM Key Protect para {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
