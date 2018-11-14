---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de KMIP for VMware on IBM Cloud

Le service KMIP for VMware on {{site.data.keyword.cloud}} offre une haute disponibilité 24 heures sur 24 et 7 jours sur 7 permettant de gérer les clés de chiffrement qu'utilise VMware dans {{site.data.keyword.cloud_notm}}. Il propose une fonction d'exécution qui permet aux clients de créer, extraire, activer, révoquer et détruire des clés de chiffrement. Il offre également une fonction de gestion des associations entre les données d'identification du client et les clés de chiffrement.

Ce service est disponible uniquement sur les instances déployées en version 2.2 ou dans des éditions ultérieures.{:note}

## Spécifications techniques relatives à KMIP for VMware on IBM Cloud

Les spécifications suivantes sont incluses avec le service KMIP for VMware on {{site.data.keyword.cloud_notm}} :

* Un protocole KMIP (Key Management Interoperability Protocol) compatible VMware
* Un service géré
* Disponible dans plusieurs régions géographiques du monde entier
* Un noeud final de service KMIP à haute disponibilité dans chaque région

## Considérations à prendre en compte lorsque vous installez KMIP for VMware on IBM Cloud

KMIP for VMware on {{site.data.keyword.cloud_notm}} utilise le service IBM Key Protect for {{site.data.keyword.cloud_notm}} pour créer, chiffrer et déchiffrer les clés de chiffrement. Par conséquent, avant d'installer KMIP for VMware on {{site.data.keyword.cloud_notm}}, vérifiez les points suivants :
* Vous avez commandé un service Key Protect utilisable.
* Un ID de service {{site.data.keyword.cloud_notm}} a été créé en suivant les étapes décrites dans [Création d'un ID de service](https://console.bluemix.net/docs/iam/serviceid.html#creating-a-service-id). Cet ID de service permet d'accéder à l'instance de service Key Protect que vous avez créée.
* Vous avez accordé à l'ID de service les niveaux d'accès suivants :
   * Au niveau de l'accès à la plateforme : droit d'affichage sur votre instance IBM Key Protect.
   * Au niveau de l'accès au service : droit d'écriture sur votre instance IBM Key Protect.
* Vous disposez d'une clé d'API pour l'ID de service créé. La clé est requise lorsque vous commandez le service.
* Vous avez créé au moins une clé racine de client (CRK) à partir de l'interface utilisateur Key Protect en suivant les étapes décrites dans [Création de clés racine](https://console.bluemix.net/docs/services/keymgmt/keyprotect_create_root.html#create_root_keys) ou en utilisant l'API REST dans [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect).

   **Important :** vous ne pouvez pas commander le service sans clés CRK. Il est fortement recommandé d'utiliser la méthode de création d'une clé CRK (Client Root Key) à l'aide du matériel de clé existant et de sauvegarder le matériel de clé que vous créez. Ainsi, vous êtes sûr de pouvoir récupérer vos clés en cas de panne du centre de données où IBM Key Protect est appliqué pour stocker vos clés racine de client.

## Considérations à prendre en compte lorsque vous utilisez KMIP for VMware on IBM Cloud

* Pour utiliser un service KMIP for VMware on {{site.data.keyword.cloud_notm}} commandé comme serveur KMS (Key Management Server) enregistré auprès de VMware vCenter Server, assurez-vous que la connectivité du réseau entre le serveur vCenter Server et le noeud final du service KMIP for VMware on {{site.data.keyword.cloud_notm}} commandé est fonctionnelle.
* Afin d'utiliser le service pour le chiffrement VMware vSAN, assurez-vous que la connectivité réseau entre les hôtes sur le stockage vSAN cible et le noeud final du service KMIP for VMware on {{site.data.keyword.cloud_notm}} commandé est fonctionnelle.

## Considérations à prendre en compte lorsque vous retirez KMIP for VMware on IBM Cloud

Le certificat public VMware que vous avez fourni à la commande ou lorsque vous utilisez le service, est utilisé comme certificat client pour communiquer avec l'instance de service. Lorsque le service est retiré, toutes les clés de chiffrement qui sont créées par cette instance de service pour le certificat public VMware associé sont également retirées.

Par conséquent, avant de retirer le service, assurez-vous qu'aucune machine virtuelle ou stockage vSAN n'est chiffré à l'aide des clés qui sont créées par le service KMIP.

### Liens connexes

* [Commande de KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip_ordering.html)
* [IBM Key Protect pour {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [Sécurité vSphere](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Foire aux questions](../vmonic/faq.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
