---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# Commande de KMIP for VMware on IBM Cloud

Vous pouvez commander le service KMIP for VMware on {{site.data.keyword.cloud_notm}} lors de la commande d'une nouvelle instance avec le service inclus ou vous pouvez ajouter le service à votre instance existante. 

## Commande de KMIP for VMware on IBM Cloud pour une nouvelle instance

Vous pouvez commander une nouvelle instance avec KMIP for VMware on {{site.data.keyword.cloud_notm}} à l'aide de l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_full}}, lorsque vous commandez une nouvelle instance, sélectionnez **KMIP for VMware on IBM Cloud** dans la section **Services**. 
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **KMIP for VMware on {{site.data.keyword.cloud_notm}}**, spécifiez les paramètres de service et sélectionnez **Ajouter à une nouvelle instance**.

## Commande de KMIP for VMware on IBM Cloud pour une instance existante

Vous pouvez ajouter le service KMIP for VMware Plus on {{site.data.keyword.cloud_notm}} dans une instance existante à l'aide de l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter un service**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **KMIP for VMware on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une instance existante**.

## Configuration du service KMIP for VMware on IBM Cloud

Lorsque vous commandez ce service, indiquez les paramètres suivants :

### Région de service

Sélectionnez la région {{site.data.keyword.cloud_notm}} dans laquelle votre instance de service KMIP for VMware {{site.data.keyword.cloud_notm}} doit être hébergée. 

{{site.data.keyword.cloud_notm}} gère un noeud final de service KMIP for VMware on {{site.data.keyword.cloud_notm}} à haute disponibilité dans chaque région où le service est disponible.

### Certificat SSL client

Pour vCenter Server, vous devez configurer un cluster KMS (Key Management Server). Le noeud final situé dans la région que vous avez sélectionnée se connecte de manière sécurisée à KMS via le certificat SSL client. Pour le noeud final dans chaque région, voir le tableau suivant. Ces noeuds finaux utilisent des certificats autosignés gérés par l'équipe {{site.data.keyword.vmwaresolutions_short}}. L'empreinte des certificats est `a9 d0 ff 15 df 85 10 6b 61 88 fe 2e 8b d3 1a af 48 c8 a0 7a`.

Tableau 1: Régions de noeud final de service KMIP for VMware on IBM Cloud

| Région         | Noeud final               |
|:---------------|:-----------------------|
| Sydney         |  `130.198.73.134:5696` |
| Royaume-Uni |  `158.175.93.122:5696` |
| Sud des Etats-Unis       |  `169.60.185.42:5696`  |

Ce paramètre est facultatif lors de la configuration initiale. Vous pouvez laisser cette zone vide à ce moment-là car le certificat client de KMS dans vCenter Server est connu une fois votre instance déployée. Mais vous devez indiquer le certificat une fois votre instance déployée, de sorte que votre connexion vCenter Server à KMS puisse aboutir.

### Clé d'API pour ID de service

Entrez la clé d'API pour l'ID de service {{site.data.keyword.cloud_notm}} qui est utilisé afin d'accéder à l'instance de service IBM Key Protect. 

### Instance Key Protect

Cliquez sur **Extraire** pour obtenir la liste d'instances de service IBM Key Protect disponibles et sélectionnez celle qui sera utilisée pour la gestion de clés. 

### Clé racine de client

Cliquez sur **Extraire** pour obtenir la clé racine de client qui est stockée dans votre instance IBM Key Protect sélectionnée.



## Liens connexes

* [Présentation de KMIP for VMware on IBM Cloud](kmip_considerations.html)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Key Protect pour {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [Sécurité vSphere](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Foire aux questions](../vmonic/faq.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
