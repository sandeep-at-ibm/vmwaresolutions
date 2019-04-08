---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations}

O serviço KMIP para VMware no {{site.data.keyword.cloud}} fornece um serviço altamente disponível 24 horas por dia, 7 dias por semana para gerenciar chaves de criptografia que são usadas pelo VMware no {{site.data.keyword.cloud_notm}}. Esse serviço oferece a capacidade de tempo de execução para permitir que os clientes criem, recuperem, ativem, revoguem e destruam as chaves de criptografia. Ele também fornece a capacidade de gerenciamento para manter as
associações entre as credenciais do cliente e as chaves de criptografia.

O serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} está disponível como um serviço independente sem estar associado a uma instância do VMware. Cada instância do serviço pode atender a uma ou mais instâncias do Cloud Foundation, instâncias do vCenter Server ou clusters do vSphere.

## Especificações técnicas para o KMIP for VMware on IBM Cloud
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

As especificações a seguir são incluídas com o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}:

* Um Key Management Interoperability Protocol (KMIP) compatível com VMware
* Um serviço gerenciado
* Disponível em múltiplas regiões geográficas em todo o mundo
* Dois terminais em serviço de rede KMIP fornecidos em cada região para alta disponibilidade

## Considerações ao instalar instâncias do KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations-install}

Revise as considerações a seguir antes de instalar uma instância do KMIP for VMware on {{site.data.keyword.cloud_notm}}:

* O KMIP for VMware on {{site.data.keyword.cloud_notm}} usa o serviço IBM Key Protect for {{site.data.keyword.cloud_notm}} para criar, criptografar e decriptografar chaves de criptografia. Portanto, antes de instalar o KMIP for VMware on {{site.data.keyword.cloud_notm}}, assegure-se de que:
   * Você pediu um serviço Key Protect utilizável na região do {{site.data.keyword.cloud_notm}} na qual sua instância do KMIP for VMware on {{site.data.keyword.cloud_notm}} deve ser hospedada. Para obter mais informações, veja [Provisionando o serviço](/docs/services/key-protect?topic=key-protect-provision).
   * Um ID do serviço {{site.data.keyword.cloud_notm}} foi criado seguindo as etapas em
[Criando um ID do serviço](/docs/iam?topic=iam-serviceids). Esse ID do
serviço é usado para acessar a instância do serviço Key Protect que você criou.
   * Você concedeu os seguintes níveis de acesso para o ID do serviço:
      * No nível de acesso da plataforma: autoridade de visualizador para sua instância do IBM Key Protect
      * No nível de acesso de serviço: autoridade de Gerenciador para sua instância do IBM Key Protect
   * Você tem uma chave API para o ID do serviço criado. A chave é necessária ao pedir o serviço.
   * Você criou pelo menos uma chave raiz do cliente (CRK) por meio da interface com o usuário do Key Protect seguindo as
etapas em [Criando as
chaves raiz](/docs/services/keymgmt/keyprotect_create_root.html) ou usando a API de REST no [IBM Key
Protect](https://cloud.ibm.com/apidocs/key-protect).

     **Importante:** não é possível pedir o serviço sem CRKs. É altamente recomendado que você use o método
para criar uma CRK utilizando o material de chave existente e faça backup do material de chave que você está criando. Ao fazer isso, você assegura que poderá recuperar suas chaves se ocorrer uma falha do data center no qual o IBM Key Protect é aplicado para armazenar seus CRKs.
* Assegure-se de que sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} esteja ativada para Virtual Routing and Forwarding (VRF) e para conectividade com os Terminais em serviço. Para obter mais informações, veja:
   * [Visão geral do Virtual Routing and Forwarding (VRF) no IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [Ativando sua conta para usar Terminais em serviço usando a CLI do IBM Cloud](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started)
* Como somente a conexão privada é suportada, você não precisa configurar nenhuma regra de firewall ou SNAT no vCenter Server para a conectividade de rede do vCenter Server para o terminal da instância do KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Para obter mais informações, veja [Arquitetura da solução KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview).

## Considerações ao excluir as instâncias do KMIP for VMware on IBM Cloud
{: #considerations-when-deleting-kmip-for-vmware-on-ibm-cloud-instances}

Todos os dados protegidos pelo serviço KMIP for VMware on IBM Cloud, incluindo backups criptografados, não podem ser decriptografados após a remoção do serviço.

## Links relacionados
{: #kmip_standalone_considerations-related}

* [Solicitando instâncias do KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [Incluindo, visualizando e excluindo certificados para instâncias do KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)
* [Visualizando instâncias do KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [Excluindo o KMIP for VMware em {{site.data.keyword.cloud_notm}} instâncias](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Eventos de rastreador de atividade](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
