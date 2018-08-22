---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Commande de F5 on IBM Cloud

Vous pouvez commander le service F5 on {{site.data.keyword.cloud}} lors de la commande d'une nouvelle instance avec BIG-IP Virtual Edition (VE) inclus ou vous pouvez ajouter  BIG-IP VE à votre instance existante.

## Commande de F5 on IBM Cloud pour une nouvelle instance

Vous pouvez commander une nouvelle instance avec F5 on {{site.data.keyword.cloud_notm}} à l'aide de l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, lorsque vous commandez une nouvelle instance, sélectionnez **F5 on IBM Cloud** dans la section **Services**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **F5 on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une nouvelle instance**.

## Commande de F5 on IBM Cloud pour une instance existante

Vous pouvez ajouter le service F5 on {{site.data.keyword.cloud_notm}} dans une instance existante à l'aide de l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **F5 on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une instance existante**.

## Configuration du service F5 on IBM Cloud

Lorsque vous commandez le service, indiquez les paramètres suivants :

### Nom

Entrez le nom du service.

### Modèle de licence

Le modèle de licence pour le service F5 on {{site.data.keyword.cloud_notm}} propose les options suivantes :
<dl class="dl">
        <dt class="dt dlterm">Bien</dt>
        <dd class="dd">Cette offre exploite le module BIG-IP Local Traffic Manager (LTM) VE, qui fonctionne comme une architecture passant intégralement par un proxy, afin de fournir une gestion intelligente du trafic local, une visibilité totale du trafic SSL ainsi que des données d'analyse et une surveillance de l'état de santé en vue d'assurer une disponibilité permanente des serveurs d'applications pour vos utilisateurs.</dd>
        <dt class="dt dlterm">Mieux</dt>
        <dd class="dd">Cette offre présente les mêmes avantages que l'option **Bien**, auxquels s'ajoutent les modules BIG-IP DNS, BIG-IP Advanced Firewall Manager (AFM) et BIG-IP Application Acceleration Manager (AAM). Elle fournit des services de gestion du trafic au niveau global, une optimisation des performances d'application ainsi qu'un pare-feu réseau avancé et des fonctionnalités d'atténuation des attaques par déni de service distribué (DDoS).</dd>
        <dt class="dt dlterm">Meilleur</dt>
        <dd class="dd">En plus des options **Bien** et **Mieux**, le module BIG-IP Application Security Manager (ASM) fournit une protection d'application intégrée contre les attaques DDos de la couche 7, les 10 principaux risques et vulnérabilités couverts par OWASP (Open Web Application Security Project), qui menacent les applications. Le module BIG-IP Access Policy Manager (APM) offre aux utilisateurs un accès simplifié sécurisé aux applications situées n'importe où dans un environnement multicloud, en intégrant des dispositifs, tels que la connexion unique (SSO - Single Sign-On) et l'authentification multi-facteur (MFA - Multi-Factor Authentication).</dd>
</dl>

**Important** : vous ne pouvez pas modifier le modèle de licence après l'installation du service. Pour modifier le modèle de licence, vous devez retirer le service existant, puis le réinstaller en utilisant un autre modèle de licence.

### Bande passante maximale

Spécifiez le débit maximal du dispositif F5 BIG–IP.

### Liens connexes

* [Présentation de F5 on {{site.data.keyword.cloud_notm}}](f5_considerations.html)
* [Gestion de F5 on {{site.data.keyword.cloud_notm}}](managing_f5.html)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Guides de déploiement de F5](https://f5.com/solutions/deployment-guides){:new_window}
