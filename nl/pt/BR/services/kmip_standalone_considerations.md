---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: KMIP for VMware, KMIP stand-alone, tech specs KMIP

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations}

O serviço KMIP para VMware no {{site.data.keyword.cloud}} fornece um serviço altamente disponível 24 horas por dia, 7 dias por semana para gerenciar chaves de criptografia que são usadas pelo VMware no {{site.data.keyword.cloud_notm}}. Esse serviço oferece a capacidade de tempo de execução para permitir que os clientes criem, recuperem, ativem, revoguem e destruam as chaves de criptografia. Ele também fornece a capacidade de gerenciamento para manter as
associações entre as credenciais do cliente e as chaves de criptografia.

O serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} está disponível como um serviço independente sem estar associado a uma instância do VMware. Cada instância do serviço pode atender a uma ou mais instâncias do vCenter Server ou clusters do vSphere.

## Especificações técnicas para o KMIP for VMware on IBM Cloud
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

As especificações a seguir são incluídas com o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}:

* Um Key Management Interoperability Protocol (KMIP) compatível com VMware
* Dois serviços gerenciados: [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/catalog/services/key-protect){:external} e [{{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services){:external}
* Disponível em múltiplas regiões geográficas em todo o mundo
* Dois terminais em serviço de rede KMIP fornecidos em cada região para alta disponibilidade

## Considerações ao instalar instâncias do KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations-install}

Revise as considerações a seguir antes de instalar uma instância do KMIP for VMware on {{site.data.keyword.cloud_notm}}:

* O KMIP for VMware on {{site.data.keyword.cloud_notm}} usa o serviço do IBM Key Protect for {{site.data.keyword.cloud_notm}} (Key Protect) ou o serviço {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services (HPCS) para criar, criptografar e decriptografar chaves de criptografia. Portanto, antes de instalar o KMIP for VMware on {{site.data.keyword.cloud_notm}}, assegure-se de que:
   * Você pediu uma instância de serviço do Key Protect ou HPCS utilizável na região do {{site.data.keyword.cloud_notm}} na qual a instância do KMIP for VMware on {{site.data.keyword.cloud_notm}} deve ser hospedada:
      * Para obter mais informações sobre como criar uma instância do Key Protect, consulte [Provisionando o serviço](/docs/services/key-protect?topic=key-protect-provision).
      * Para obter mais informações sobre como criar uma instância do HPCS, consulte [Provisionando o serviço](/docs/services/hs-crypto?topic=hs-crypto-provision#provision). Além de provisionar o serviço HPCS, deve-se também [inicializar sua instância criptográfica](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm) para que o HPCS possa fornecer funções relacionadas à chave.
   * Um ID do serviço {{site.data.keyword.cloud_notm}} foi criado seguindo as etapas em
[Criando um ID do serviço](/docs/iam?topic=iam-serviceids). Esse ID do serviço é usado para acessar a instância de serviço do Key Protect ou do HPCS que você criou.
   * Você concedeu os seguintes níveis de acesso para o ID do serviço:
      * No nível de acesso da plataforma: autoridade de Visualizador para sua instância de serviço do Key Protect ou do HPCS
      * No nível de acesso do serviço: autoridade de Gerenciador para sua instância de serviço do Key Protect ou do HPCS
   * Você tem uma chave API para o ID do serviço criado. A chave é necessária ao pedir o serviço.
   * Você criou pelo menos um customer root key (CRK) usando a GUI ou API do Key Protect ou HPCS:
      * Para obter mais informações sobre como criar chaves raiz com a GUI ou API do Key Protect, consulte [Criando chaves raiz](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) ou [API do IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect){:external}.
      * Para obter mais informações sobre como criar chaves raiz com a GUI ou API do HPCS, consulte [Criando chaves raiz](/docs/hs-crypto/get-started?topic=hs-crypto-create-root-keys) ou [API do IBM Cloud Hyper Protect Crypto Services](https://cloud.ibm.com/apidocs/hs-crypto){:external}.

     **Importante:** não é possível pedir o serviço sem CRKs. É altamente recomendado que você use o método
para criar uma CRK utilizando o material de chave existente e faça backup do material de chave que você está criando. Ao fazer isso, você assegura que poderá recuperar suas chaves se ocorrer uma falha do data center no qual o Key Protect ou HPCS é aplicado para armazenar seus CRKs.
* Assegure-se de que sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} esteja ativada para Virtual Routing and Forwarding (VRF) e para conectividade com os Terminais em serviço. Para obter mais informações, veja:
   * [Visão geral do Virtual Routing and Forwarding (VRF) no IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [Ativando sua conta para usar Terminais em serviço usando a CLI do IBM Cloud](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)
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
* [Eventos do Activity Tracker](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
