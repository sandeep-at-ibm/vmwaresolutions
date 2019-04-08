---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande de VMware HCX on IBM Cloud
{: #hcx_ordering}

Vous pouvez commander le service VMware HCX on {{site.data.keyword.cloud}} lors de la commande d'une nouvelle instance VMware vCenter Server with Hybridity Bundle avec le service inclus ou vous pouvez ajouter le service à votre instance existante.

## Commande de VMware HCX on IBM Cloud pour une nouvelle instance
{: #hcx_ordering-new}

Pour commander une nouvelle instance VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle avec VMware HCX on {{site.data.keyword.cloud_notm}}, sélectionnez **VMware HCX on IBM Cloud** dans la section **Services** lorsque vous passez votre commande depuis la console {{site.data.keyword.vmwaresolutions_short}}.


## Commande de VMware HCX on IBM Cloud pour une instance existante
{: #hcx_ordering-existing}

Pour ajouter le service VMware HCX on {{site.data.keyword.cloud_notm}} dans une instance VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle existante, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter**.

## Configuration de VMware HCX on IBM Cloud
{: #hcx_ordering-config}

Pour installer HCX on {{site.data.keyword.cloud_notm}}, définissez les paramètres suivants :
1. Renseignez la zone **Type d'interconnexion HCX** en sélectionnant l'une des options suivantes :
  * **Réseau public :** HCX crée une connexion chiffrée entre les sites sur le réseau public. Les opérations d'enregistrement et de décompte des licences sont effectuées sur le réseau public.
  * **Interconnexion privée :** HCX crée une connexion chiffrée entre les sites sur le réseau privé. Les opérations d'enregistrement et de décompte des licences sont effectuées sur le réseau public.
  * **Réseau privé :** HCX crée une connexion chiffrée entre les sites sur le réseau privé. Les opérations d'enregistrement et de décompte des licences sont effectuées sur le réseau privé via un proxy HTTP.
3. Si vous sélectionnez **Réseau privé**, renseignez les zones suivantes :
  * **Adresse IP du proxy :** adresse IPv4 du serveur proxy.
  * **Port du proxy :** port du serveur proxy. Le numéro de port est généralement 8080 ou 3128.
  * **Nom d'utilisateur :** nom d'utilisateur si l'authentification par proxy est requise.
  * **Mot de passe :** mot de passe si l'authentification par proxy est requise.
  * **Confirmer le mot de passe :** saisissez à nouveau le mot de passe pour la validation de l'authentification par proxy.
2. Renseignez la zone **Type de certificat de noeud final public**. Si vous sélectionnez **Certificat de l'autorité de certification**, configurez les paramètres suivants :
  * **Contenu de certificat :** entrez le contenu du certificat de l'autorité de certification.
  * **Clé privée :** entrez la clé privée du certificat de l'autorité de certification.
  * (Facultatif) **Mot de passe :** entrez le mot de passe de la clé privée si elle est chiffrée.
  * (Facultatif) **Confirmer le mot de passe :** saisissez à nouveau le mot de passe de la clé privée.
  * (Facultatif) **Nom d'hôte :** nom d'hôte à mapper au nom usuel (CN) du certificat de l'autorité de certification. HCX on {{site.data.keyword.cloud_notm}} nécessite que le format du certificat de l'autorité de certification soit accepté par NSX Edge. Pour plus d'informations sur les formats de certificat NSX Edge, voir [Importation de certificats SSL](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## Processus de déploiement du service HCX on IBM Cloud
{: #hcx_ordering-deploy}

Le déploiement du service HCX on {{site.data.keyword.cloud_notm}} est automatisé. Que vous commandiez une instance vCenter Server with Hybridity Bundle avec le service inclus ou que vous déployez le service ultérieurement dans votre instance, les étapes suivantes sont réalisées par le processus d'automatisation de {{site.data.keyword.vmwaresolutions_short}} :
1. Trois sous-réseaux sont commandés pour le service HCX à partir de l'infrastructure {{site.data.keyword.cloud_notm}} :
   * Un sous-réseau portable privé pour la gestion HCX.
   * Un sous-réseau portable privé pour les interconnexions HCX. Ce sous-réseau est utilisé si **Réseau privé** est sélectionné pour **Type d'interconnexion HCX**.
   * Un sous-réseau portable public pour l'activation et la maintenance avec VMware. Si l'option **Réseau public** est sélectionnée pour **Type d'interconnexion HCX**, ce sous-réseau est également utilisé pour les interconnexions HCX.

   Les adresses IP dans les sous-réseaux qui sont commandées pour HCX sont conçues pour être gérées par les fonctions d'automatisation de VMware on {{site.data.keyword.cloud_notm}}. Ces adresses IP ne peuvent pas être affectées à des ressources VMware, telles que des machines virtuelles et des serveurs de périphérie NSX Edge, que vous créez. Si vous avez besoin d'adresses IP supplémentaires pour vos artefacts VMware, vous devez commander vos propres sous-réseaux depuis {{site.data.keyword.cloud_notm}}.
   {:important}
2. Si l'option **Réseau privé** a été sélectionnée comme **Type d'interconnexion HCX**, un groupe de ports nommé **SDDC-DPortGroup-HCX-Private** est créé sur le commutateur virtuel distribué (DVS) privé.
3. Une clé d'activation HCX est commandée à partir de VMware.
4. Trois pools de ressources et dossiers de machines virtuelles pour HCX, nécessaires pour les interconnexions HCX, les composants HCX locaux et les composants HCX distants, sont créés.
5. Une paire de passerelles VMware NSX ESG (Edge Services Gateway) pour le trafic de gestion HCX est déployée et configurée :
   * Des interfaces de liaison montante publique et privée sont configurées à l'aide des sous-réseaux commandés.
   * Les passerelles ESG sont configurées sous forme de paire de dispositifs Edge très volumineux à haute disponibilité.
   * Les règles de pare-feu et les règles de conversion d'adresses réseau (NAT) sont configurées pour autoriser le trafic HTTPS entrant et sortant vers et depuis HCX Manager.
   * Les règles et les pools de ressources d'équilibrage de charge sont configurés. Ces règles sont des pools de ressources utilisés pour réacheminer le trafic entrant lié à HCX vers les dispositifs virtuels appropriés de HCX Manager, vCenter Server et Platform Services Controller (PSC).
   * Un certificat SSL permettant de chiffrer le trafic HTTPS entrant associé à HCX en provenance des passerelles ESG est appliqué.

   Le serveur de périphérie de gestion HCX est dédié au trafic de gestion HCX entre les composants HCX sur site et les composants HCX côté cloud. Ne modifiez pas le serveur de périphérie de gestion HCX et ne l'utilisez pas pour des extensions de réseau HCX. Créez plutôt des serveurs de périphérie distincts pour les extensions de réseau. Par ailleurs, l'utilisation d'un pare-feu ou la désactivation des communications de serveur de périphérie de gestion HCX sur les composants de gestion IBM privés ou l'Internet public peut avoir une incidence défavorable sur la fonctionnalité HCX.
   {:important}

6. HCX Manager on {{site.data.keyword.cloud_notm}} est déployé, activé et configuré :
   * HCX Manager est enregistré auprès de vCenter Server.
   * HCX Manager, vCenter Server (avec Platform Services Controller intégré) et NSX Manager sont configurés.
   * Le parc HCX est configuré.
   * Les conteneurs de déploiement HCX locaux et distants sont configurés.
7. Le nom d'hôte et l'adresse IP de HCX Manager sont enregistrés auprès du serveur DNS de VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

## Liens connexes
{: #hcx_ordering-related}

* [Présentation de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vmware-hcx-on-ibm-cloud-overview)
* [Gestion de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Glossaire des termes HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Présentation de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentation VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)
