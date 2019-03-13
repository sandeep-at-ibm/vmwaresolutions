---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande de FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering}

Vous pouvez commander le service FortiGate Virtual Appliance on {{site.data.keyword.cloud}} lors de la commande d'une nouvelle instance avec le service inclus ou vous pouvez ajouter le service à votre instance existante.

## Commande de FortiGate Virtual Appliance on IBM Cloud pour une nouvelle instance
{: #fortinetvm_ordering-new}

Vous pouvez commander une nouvelle instance avec FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, lorsque vous commandez une nouvelle instance, sélectionnez **FortiGate Virtual Appliance on IBM Cloud** dans la section **Services**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **FortiGate Virtual Appliance on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une nouvelle instance**.

## Commande de FortiGate Virtual Appliance on IBM Cloud pour une instance existante
{: #fortinetvm_ordering-existing}

Vous pouvez ajouter le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} dans une instance existante en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **FortiGate Virtual Appliance on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une instance existante**.

## Configuration du service FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering-config}

Lorsque vous commandez le service, indiquez les paramètres suivants :

### Connexion réseau FortiGuard
{: #fortinetvm_ordering-config-network-connect}

Sélectionnez **Réseau public** ou **Réseau privé** pour FortiGuard. Si le cluster cible est configuré avec des interfaces de réseau privé uniquement, seule l'option **Réseau privé** est disponible. Cette sélection détermine de quelle façon FortiGuard contactera le serveur de licences Fortinet pour activer la licence et pour télécharger les correctifs de sécurité ; elle n'a aucune incidence sur le plan des données de charge de travail.

Si vous sélectionnez **Réseau privé**, spécifiez les paramètres suivants :
* **Adresse IP du proxy** : adresse IPv4 du serveur proxy.
* **Numéro de port du proxy** : numéro de port du serveur proxy, généralement, 8080 ou 3128.
* **Nom d'utilisateur proxy** : si vous avez besoin de l'authentification proxy, entrez le nom d'utilisateur du serveur proxy.
* **Mot de passe proxy** : si vous avez besoin de l'authentification proxy, entrez le mot de passe du serveur proxy.

### Nom
{: #fortinetvm_ordering-config-name}

Entrez le nom du service.

### Taille de déploiement
{: #fortinetvm_ordering-config-size}

{{site.data.keyword.cloud_notm}} fournit les options de taille de déploiement suivantes :
* Petite (2 UC virtuelles/4 Go de RAM)
* Moyenne (4 UC virtuelles/6 Go de RAM)
* Grande (8 UC virtuelles/12 Go de RAM)

### Modèle de licence
{: #fortinetvm_ordering-config-license}

Le modèle de licence pour le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} propose les options suivantes :
<dl class="dl">
        <dt class="dt dlterm">Pare-feu standard</dt>
        <dd class="dd">Cette offre groupée inclut Inspection de paquet avec état, Protection VLAN et consignation avancée, Règles de pare-feu d'entrée et de sortie, Terminaison VPN SSL/IPSec et support 24h/24 et 7j/7.</dd>
        <dt class="dt dlterm">Pare-feu standard + UTM</dt>
        <dd class="dd">Cette offre groupée inclut tous les services de pare-feu standard en plus du service AMP (Advanced Malware Protection). Il inclut un antivirus, Botnet IP/Domain Service, Mobile Malware Security, FortiSandbox Cloud, Virus Outbreak Protection Service et Content Disarm & Reconstruct. Il inclut également les services Web Filtering, IPS, Antispam, Application Control et FortiCare.</dd>
        <dt class="dt dlterm">Pare-feu standard + Enterprise</dt>
        <dd class="dd">Cette offre groupée inclut tous les services UTM et de pare-feu standard en plus des services suivants :<ul><li>Cloud Access Security Broker (CASB) - ce service offre des fonctions de visibilité, conformité, sécurité des données et protection contre les menaces pour les services basés sur le cloud.</li><li>Sécurité industrielle - Ce service fournit des signatures pour les protocoles ICS/SCADA courants.</li><li>Evaluation de la sécurité - Ce service fournit des fonctions d'audit pour identifier les vulnérabilités critiques et les faiblesses de la configuration, et implémenter des recommandations en matière de meilleures pratiques.</li></ul></dd>
</dl>

Au cours du troisième trimestre 2018, Fortinet a ajouté trois nouveaux services (CASB, sécurité industrielle et évaluation de la sécurité) à son offre groupée d'entreprise. Ces services sont disponibles sur FortiGate 6.0 uniquement.
{:note}

Vous ne pouvez pas modifier le modèle de licence après installation du service. Pour modifier le modèle de licence, vous devez retirer le service existant, puis le réinstaller en sélectionnant une autre option de licence.
{:important}

## Liens connexes
{: #fortinetvm_ordering-related}

* [Présentation de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [Gestion de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)
* [Commande, affichage et retrait de services pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Site Web Fortinet](https://www.fortinet.com/){:new_window}
* [Bibliothèque de documents Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
