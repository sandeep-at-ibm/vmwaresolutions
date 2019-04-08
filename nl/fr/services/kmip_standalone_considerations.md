---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations}

Le service KMIP for VMware on {{site.data.keyword.cloud}} offre une haute disponibilité 24 heures sur 24 et 7 jours sur 7 permettant de gérer les clés de chiffrement qu'utilise VMware dans {{site.data.keyword.cloud_notm}}. Il propose une fonction d'exécution qui permet aux clients de créer, extraire, activer, révoquer et détruire des clés de chiffrement. Il offre également une fonction de gestion des associations entre les données d'identification du client et les clés de chiffrement.

Le service KMIP for VMware on {{site.data.keyword.cloud_notm}} est disponible en tant que service autonome sans être associé à une instance VMware. Chaque instance du service peut servir une ou plusieurs instances Cloud Foundation, vCenter Server ou clusters vSphere.

## Spécifications techniques relatives à KMIP for VMware on IBM Cloud
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

Les spécifications suivantes sont incluses avec le service KMIP for VMware on {{site.data.keyword.cloud_notm}} :

* Un protocole KMIP (Key Management Interoperability Protocol) compatible VMware
* Un service géré
* Disponible dans plusieurs régions géographiques du monde entier
* Deux noeuds finaux de service de réseau KMIP fournis dans chaque région pour la haute disponibilité

## Remarques relatives à l'installation des instances KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations-install}

Passez en revue les remarques suivantes avant d'installer une instance KMIP for VMware on {{site.data.keyword.cloud_notm}} :

* KMIP for VMware on {{site.data.keyword.cloud_notm}} utilise le service IBM Key Protect for {{site.data.keyword.cloud_notm}} pour créer, chiffrer et déchiffrer les clés de chiffrement. Par conséquent, avant d'installer KMIP for VMware on {{site.data.keyword.cloud_notm}}, vérifiez les points suivants :
   * Vous avez commandé un service Key Protect utilisable dans la région {{site.data.keyword.cloud_notm}} où votre instance KMIP for VMware on {{site.data.keyword.cloud_notm}} doit être hébergée. Pour plus d'informations, voir [Provisioning the service](/docs/services/key-protect?topic=key-protect-provision).
   * Un ID de service {{site.data.keyword.cloud_notm}} a été créé en suivant les étapes décrites dans [Création d'un ID de service](/docs/iam?topic=iam-serviceids). Cet ID de service permet d'accéder à l'instance de service Key Protect que vous avez créée.
   * Vous avez accordé à l'ID de service les niveaux d'accès suivants :
      * Au niveau de l'accès à la plateforme : droit d'affichage sur votre instance IBM Key Protect
      * Au niveau de l'accès au service : droit de gestionnaire sur votre instance IBM Key Protect.
   * Vous disposez d'une clé d'API pour l'ID de service créé. La clé est requise lorsque vous commandez le service.
   * Vous avez créé au moins une clé racine de client (CRK) à partir de l'interface utilisateur Key Protect en suivant les étapes décrites dans [Création de clés racine](/docs/services/keymgmt/keyprotect_create_root.html) ou en utilisant l'API REST dans [IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect).

     **Important :** vous ne pouvez pas commander le service sans clés CRK. Il est fortement recommandé d'utiliser la méthode de création d'une clé CRK (Client Root Key) à l'aide du matériel de clé existant et de sauvegarder le matériel de clé que vous créez. Ainsi, vous êtes sûr de pouvoir récupérer vos clés en cas de panne du centre de données où IBM Key Protect est appliqué pour stocker vos clés racine de client.
* Assurez-vous que votre compte d'infrastructure {{site.data.keyword.cloud_notm}} est activé pour le service Routage et transfert virtuel (VRF) et pour la connectivité aux noeuds finaux de service. Pour plus d'informations, voir :
   * [Aperçu du service Routage et transfert virtuel (VRF) on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [Activation de votre compte pour l'utilisation des noeuds finaux de service à l'aide de l'interface CLI IBM Cloud](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started)
* Etant donné que seule une connexion privée est prise en charge, vous n'êtes pas tenu de configurer un pare-feu ou des règles SNAT dans vCenter Server pour la connexion réseau de vCenter Server au noeud final de l'instance KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Pour plus d'informations, voir [KMIP for VMware on IBM Cloud solution architecture](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview).

## Remarques relatives à la suppression d'instances KMIP for VMware on IBM Cloud
{: #considerations-when-deleting-kmip-for-vmware-on-ibm-cloud-instances}

Toutes les données protégées par le service KMIP for VMware on IBM Cloud, y compris les sauvegardes chiffrées, ne peuvent pas être déchiffrées une fois le service supprimé.

## Liens connexes
{: #kmip_standalone_considerations-related}

* [Commande des instances KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [Ajout, affichage et suppression de certificats pour des instances KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)
* [Affichage des instances KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [Suppression des instances KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Evénements du service Activity Tracker](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
