---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Commande de HyTrust KeyControl on IBM Cloud

Vous pouvez commander le service HyTrust KeyControl on {{site.data.keyword.cloud}} lorsque vous commandez une nouvelle instance avec une paire à haute disponibilité de dispositifs HyTrust KeyControl incluse ou en ajoutant les dispositifs HyTrust CloudControl à votre instance existante.

## Commande de HyTrust KeyControl on IBM Cloud pour une nouvelle instance

Vous pouvez commander une nouvelle instance avec HyTrust KeyControl on {{site.data.keyword.cloud_notm}} en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, lorsque vous commandez une nouvelle instance, sélectionnez **HyTrust KeyControl on IBM Cloud** dans la section **Services**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **HyTrust KeyControl on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une nouvelle instance**.

## Commande de HyTrust KeyControl on IBM Cloud pour une instance existante

Vous pouvez ajouter le service HyTrust KeyControl on {{site.data.keyword.cloud_notm}} dans une instance existante en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **HyTrust KeyControl on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une instance existante**.

## Configuration du service HyTrust KeyControl on IBM Cloud

Lorsque vous commandez le service, indiquez les paramètres suivants :

Indiquez si vous souhaitez créer un cluster KeyControl hautement disponible à deux noeuds :
* Si vous sélectionnez cette option, deux noeuds KeyControl sont déployés et un nouveau cluster hautement disponible active-active est créé. Il s'agit de l'option par défaut.
* Si vous ne sélectionnez pas cette option, deux noeuds KeyControl autonomes sont déployés et aucun cluster n'est créé. Les noeuds autonomes peuvent être manuellement regroupés en cluster ou ajoutés à des clusters KeyControl existants après leur déploiement.

### Liens connexes

* [Présentation de HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](htkc_considerations.html)
* [Gestion de HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](managinghtkc.html)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web HyTrust](https://www.hytrust.com/)
