---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Commande de KMIP for VMware on IBM Cloud - Obsolète
{: #kmip_ordering}

La version actuelle de KMIP for VMware on IBM Cloud va devenir obsolète. Pour plus d'informations, voir [Contacter le support IBM](../vmonic/trbl_support.html).
{:deprecated}

Vous pouvez commander le service KMIP for VMware on {{site.data.keyword.cloud}} lors de la commande d'une nouvelle instance avec le service inclus ou en ajoutant le service à votre instance existante.

## Commande de KMIP for VMware on IBM Cloud pour une nouvelle instance
{: #kmip_ordering-new}

Vous pouvez commander une nouvelle instance avec KMIP for VMware on {{site.data.keyword.cloud_notm}} en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, lorsque vous commandez une nouvelle instance, sélectionnez **KMIP for VMware on IBM Cloud** dans la section **Services**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **KMIP for VMware on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une nouvelle instance**.

## Commande de KMIP for VMware on IBM Cloud pour une instance existante
{: #kmip_ordering-existing}

Vous pouvez ajouter le service KMIP for VMware Plus on {{site.data.keyword.cloud_notm}} dans une instance existante en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **KMIP for VMware on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une instance existante**.

## Configuration du service KMIP for VMware on IBM Cloud
{: #kmip_ordering-config}

Lorsque vous commandez ce service, indiquez les paramètres suivants :

### Région de service
{: #kmip_ordering-service-region}

Sélectionnez la région {{site.data.keyword.cloud_notm}} dans laquelle votre instance de service KMIP for VMware {{site.data.keyword.cloud_notm}} doit être hébergée.

{{site.data.keyword.cloud_notm}} gère un noeud final de service KMIP for VMware on {{site.data.keyword.cloud_notm}} à haute disponibilité dans chaque région où le service est disponible.

### Certificat SSL client
{: #kmip_ordering-ssl}

Pour vCenter Server, vous devez configurer un cluster KMS (Key Management Server). Le noeud final situé dans la région que vous avez sélectionnée se connecte de manière sécurisée à KMS via le certificat SSL client. Pour le noeud final dans chaque région, voir le tableau suivant. Ces noeuds finaux utilisent des certificats autosignés gérés par l'équipe {{site.data.keyword.vmwaresolutions_short}}. L'empreinte des certificats est `a9 d0 ff 15 df 85 10 6b 61 88 fe 2e 8b d3 1a af 48 c8 a0 7a`.

Tableau 1. Régions de noeud final de service KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Région         | Noeud final               |
|:---------------|:-----------------------|
| Allemagne        |  `161.156.68.107:5696` |
| Sydney         |  `130.198.73.134:5696` |
| Royaume-Uni |  `158.175.93.122:5696` |
| Sud des Etats-Unis       |  `169.60.185.42:5696`  |

Ce paramètre est facultatif lors de la configuration initiale. Vous pouvez laisser cette zone vide car le certificat client de KMS dans vCenter Server est connu une fois votre instance déployée. Mais vous devez indiquer le certificat une fois votre instance déployée pour que votre connexion vCenter Server à KMS puisse aboutir.

### Clé d'API pour ID de service
{: #kmip_ordering-api-key}

Entrez la clé d'API pour l'ID de service {{site.data.keyword.cloud_notm}} qui est utilisé afin d'accéder à l'instance de service IBM Key Protect.

### Instance Key Protect
{: #kmip_ordering-key-protect}

Cliquez sur **Extraire** pour obtenir la liste d'instances de service IBM Key Protect disponibles et sélectionnez celle qui sera utilisée pour la gestion de clés.

### Clé racine de client
{: #kmip_ordering-root-key}

Cliquez sur **Extraire** pour obtenir la clé racine de client qui est stockée dans votre instance IBM Key Protect sélectionnée.

## Liens connexes
{: #kmip_ordering-related}

* [Présentation de KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip_considerations.html)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Evénements {{site.data.keyword.cloudaccesstrailshort}}](../vmonic/at-events.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](../../keymgmt/index.html)
* [Sécurité vSphere](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Foire aux questions](../vmonic/faq.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
