---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande de F5 on IBM Cloud
{: #f5_ordering}

Vous pouvez commander le service F5 on {{site.data.keyword.cloud}} lors de la commande d'une nouvelle instance avec le service inclus ou vous pouvez ajouter le service à votre instance existante.

## Commande de F5 on IBM Cloud pour une nouvelle instance
{: #f5_ordering-new}

Vous pouvez commander une nouvelle instance avec F5 on {{site.data.keyword.cloud_notm}} en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, lorsque vous commandez une nouvelle instance, sélectionnez **F5 on IBM Cloud** dans la section **Services**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **F5 on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une nouvelle instance**.

## Commande de F5 on IBM Cloud pour une instance existante
{: #f5_ordering-existing}

Vous pouvez ajouter le service F5 on {{site.data.keyword.cloud_notm}} dans une instance existante en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **F5 on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une instance existante**.

## Configuration du service F5 on IBM Cloud
{: #f5_ordering-config}

Lorsque vous commandez le service, indiquez les paramètres suivants :

### Connexion d'activation de Licence F5
{: #f5_ordering-config-license}

Sélectionnez **Réseau public** ou **Réseau privé** pour l'activation de licence. Si le cluster cible est configuré avec des interfaces de réseau privé uniquement, seule l'option **Réseau privé** est disponible. Cette sélection détermine de quelle façon les serveurs virtuels F5 contacteront le serveur de licences F5 ; elle n'a aucune incidence sur le plan des données de charge de travail.

Si vous sélectionnez **Réseau privé**, spécifiez les paramètres suivants :
* **Adresse IP du proxy** : adresse IPv4 du serveur proxy.
* **Numéro de port du proxy** : numéro de port du serveur proxy, généralement, 8080 ou 3128.

Le proxy authentifié n'est pas pris en charge.
{:note}

### Nom
{: #f5_ordering-config-name}

Entrez le nom du service.

### Bande passante maximale
{: #f5_ordering-config-bandwidth}

Spécifiez le débit maximal du dispositif F5 BIG–IP.

### Modèle de licence
{: #f5_ordering-config-license-model}

Le modèle de licence pour le service F5 on {{site.data.keyword.cloud_notm}} propose les options suivantes :
<dl class="dl">
        <dt class="dt dlterm">Bien</dt>
        <dd class="dd">Cette offre utilise le module BIG-IP Local Traffic Manager (LTM) VE, qui fonctionne comme une architecture passant intégralement par un proxy, afin de fournir une gestion intelligente du trafic local, une visibilité totale du trafic SSL ainsi que des données d'analyse et une surveillance de l'état de santé en vue d'assurer une disponibilité permanente des serveurs d'applications pour vos utilisateurs.</dd>
        <dt class="dt dlterm">Mieux</dt>
        <dd class="dd">Cette offre présente les mêmes avantages que l'option **Bien**, auxquels s'ajoutent les modules BIG-IP DNS, BIG-IP Advanced Firewall Manager (AFM) et BIG-IP Application Acceleration Manager (AAM). Elle fournit des services de gestion du trafic au niveau global, une optimisation des performances d'application ainsi qu'un pare-feu réseau avancé et des fonctionnalités d'atténuation des attaques par déni de service distribué (DDoS).</dd>
        <dt class="dt dlterm">Meilleur</dt>
        <dd class="dd">En plus des options **Bien** et **Mieux**, le module BIG-IP Application Security Manager (ASM) fournit une protection d'application intégrée contre les attaques DDos de la couche 7, les 10 principaux risques et vulnérabilités couverts par OWASP (Open Web Application Security Project), qui menacent les applications. Le module BIG-IP Access Policy Manager (APM) offre aux utilisateurs un accès simplifié sécurisé aux applications situées n'importe où dans un environnement multicloud, en intégrant des dispositifs, tels que la connexion unique (SSO - Single Sign-On) et l'authentification multi-facteur (MFA - Multi-Factor Authentication).</dd>
</dl>

Vous ne pouvez pas modifier le modèle de licence après installation du service. Pour modifier le modèle de licence, vous devez retirer le service existant, puis le réinstaller en choisissant un autre modèle de licence.
{:important}

## Liens connexes
{: #f5_ordering-releated}

* [Présentation de F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [Gestion de F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_f5)
* [Commande, affichage et retrait de services pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Guides de déploiement de F5](https://f5.com/solutions/deployment-guides){:new_window}
