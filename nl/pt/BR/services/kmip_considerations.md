---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-24"

---

# Visão geral do KMIP for VMware on IBM Cloud

O serviço KMIP para VMware no {{site.data.keyword.cloud}} fornece um serviço altamente disponível 24 horas por dia, 7 dias por semana para gerenciar chaves de criptografia que são usadas pelo VMware no {{site.data.keyword.cloud_notm}}. Esse serviço oferece a capacidade de tempo de execução para permitir que os clientes criem, recuperem, ativem, revoguem e destruam as chaves de criptografia. Ele também fornece a capacidade de gerenciamento para manter as
associações entre as credenciais do cliente e as chaves de criptografia.

**Disponibilidade**: esse serviço está disponível somente para instâncias implementadas na V2.2 ou liberações mais recentes.

## Especificações técnicas para o KMIP for VMware on IBM Cloud

As especificações a seguir são incluídas com o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}:

* Um Key Management Interoperability Protocol (KMIP) compatível com VMware
* Um serviço gerenciado
* Disponível em múltiplas regiões geográficas em todo o mundo
* Um terminal de serviço KMIP altamente disponível em cada região

## Considerações ao instalar o KMIP para VMware no IBM Cloud

O KMIP for VMware on {{site.data.keyword.cloud_notm}} usa o serviço IBM Key Protect for {{site.data.keyword.cloud_notm}} para criar, criptografar e decriptografar chaves de criptografia. Portanto,
antes de instalar o KMIP for VMware on {{site.data.keyword.cloud_notm}}, certifique-se de que:
* Você pediu um serviço Key Protect utilizável.
* Um ID do serviço {{site.data.keyword.cloud_notm}} foi criado seguindo as etapas em
[Criando um ID do serviço](https://console.bluemix.net/docs/iam/serviceid.html#creating-a-service-id). Esse ID do
serviço é usado para acessar a instância do serviço Key Protect que você criou.
* Você concedeu os seguintes níveis de acesso para o ID do serviço:
   * No nível de acesso de plataforma: autoridade de visualizador para sua instância do IBM Key Protect.
   * No nível de acesso de serviço: autoridade de gravador para sua instância do IBM Key Protect.
* Você tem uma chave API para o ID do serviço criado. A chave é necessária ao pedir o serviço.
* Você criou pelo menos uma chave raiz do cliente (CRK) por meio da interface com o usuário do Key Protect seguindo as
etapas em [Criando as
chaves raiz](https://console.bluemix.net/docs/services/keymgmt/keyprotect_create_root.html#create_root_keys) ou usando a API de REST no [IBM Key
Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect).

   **Importante**: não é possível pedir o serviço sem CRKs. É altamente recomendado que você use o método
para criar uma CRK utilizando o material de chave existente e faça backup do material de chave que você está criando. Ao fazer isso,
você assegura que pode recuperar as suas chaves no caso de uma falha do data center no qual o IBM Key Protect é aplicado para
armazenar as suas CRKs.

## Considerações ao usar o KMIP para VMware no IBM Cloud

* Para usar um serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} pedido como um Key Management
Server (KMS) que está registrado para o VMware vCenter Server, assegure-se de que a conectividade de rede do vCenter Server para o terminal
do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} pedido esteja funcional.
* Para usar o serviço para criptografia VMware vSAN, assegure-se de que a conectividade de rede entre os hosts no vSAN de
destino e o terminal do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} pedido esteja funcional.

## Considerações ao remover o KMIP para VMware no IBM Cloud

O certificado público do VMware fornecido durante o pedido ou uso do serviço é usado como o certificado de cliente para se comunicar com a instância de serviço. Quando o serviço é removido, todas as chaves de criptografia criadas por essa instância de serviço para o certificado público do
VMware associado também são removidas.

Portanto, antes de remover o serviço, certifique-se de que nenhuma das máquinas virtuais ou vSANs estejam sendo
criptografadas usando as chaves criadas pelo serviço KMIP.

### Links relacionados

* [ Solicitando KMIP para VMware no  {{site.data.keyword.cloud_notm}} ](kmip_ordering.html)
* [IBM Key Protect para {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
