---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Présentation de Zerto on IBM Cloud

Le service Zerto on {{site.data.keyword.cloud}} fournit des fonctions de réplication et de reprise après incident, qui peuvent être intégrées aux offres de déploiement de manière à assurer la protection et la récupération des données dans votre environnement virtuel VMware sur {{site.data.keyword.cloud_notm}}.

## Composants du service Zerto on IBM Cloud

Les composants suivants sont commandés et inclus dans le service Zerto on {{site.data.keyword.cloud_notm}} :

* Un sous-réseau portable privé issu de l'infrastructure {{site.data.keyword.cloud_notm}} à l'usage des dispositifs de réplication Zerto Virtual Replication Appliance
* Une instance de service virtuel Microsoft Windows sur laquelle la réplication virtuelle Zerto avait été installée.
* Des dispositifs de réplication Zerto Virtual Replication Appliance à déployer et configurer sur tous les serveurs ESXi

**Remarque** : les composants de Zerto Virtual Manager (ZVM) ne seront déployés que dans le cluster par défaut.


## Liens connexes

* [A propose de {{site.data.keyword.vmwaresolutions_short}}](../vmonic/prod_overview.html)
* [Commande de Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [Gestion de Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Demande de services gérés pour Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Site Web zerto.com](https://www.zerto.com){:new_window}
* [Documentation technique Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
