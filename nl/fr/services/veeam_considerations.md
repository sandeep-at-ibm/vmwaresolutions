---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Présentation de Veeam on IBM Cloud

Le service Veeam on {{site.data.keyword.cloud}} s'intègre directement et en toute transparence à vos hyperviseurs VMware afin d'aider votre entreprise à obtenir la haute disponibilité requise. Il peut fournir des objectifs de point et de temps de reprise pour vos applications et vos données. Les objectifs de point et de temps de reprise peuvent être fournis moins de 15 minutes après la fin de la configuration. Ce service vous permet de contrôler directement à la fois la sauvegarde et la restauration de toutes les machines virtuelles de votre infrastructure depuis la console Veeam.

**Disponibilité** : ce service est disponible uniquement sur les instances déployées en version 1.8 ou dans des éditions ultérieures.

## Composants de Veeam on IBM Cloud

Les composants suivants sont commandés et inclus dans le service Veeam on {{site.data.keyword.cloud_notm}} :
* Une instance de serveur virtuel Windows Server 2016 avec une adresse IP privée principale et une interface 1 GbE
* Stockage par blocs {{site.data.keyword.cloud_notm}} Endurance dont vous sélectionnez la taille et les performances au moment de la commande du service

## Remarques relatives à l'installation de Veeam on IBM Cloud

* Le service sauvegarde les composants de gestion suivants :
  - VMware vCenter Server
  - Contrôleur PSC (Platform Services Controller)
  - IBM CloudDriver
  - **Instances Cloud Foundation uniquement** : VMware SDDC Manager
  - **Instances vCenter Server avec AD/DNS à haute disponibilité uniquement** : paire à haute disponibilité de serveurs AD/DNS

* Le service Veeam on {{site.data.keyword.cloud_notm}} ne sauvegarde pas les configurations des serveurs ESXi.

* Par défaut, les du contrôleur NSX et de NSX Edge sont sauvegardées à l'aide du gestionnaire NSX avec jusqu'à 14 points de restauration. Pour une restauration complète des configurations NSX, vous devez créer un ticket de demande de service {{site.data.keyword.cloud_notm}} car les sauvegardes des configurations NSX sont enregistrées dans le stockage interne à {{site.data.keyword.vmwaresolutions_full}}. Pour plus d'informations sur la gestion des sauvegardes des configurations NSX à l'aide du gestionnaire NSX, voir les [instructions techniques VMware](https://pubs.vmware.com/NSX-6/index.jsp#com.vmware.nsx.admin.doc/GUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html).
* Le référentiel du stockage et celui du serveur Veeam se trouvent dans le pod d'origine et le centre de données. Par conséquent, les performances des opérations de sauvegarde des clusters distants peuvent se dégrader.

## Remarques relatives au retrait de Veeam on IBM Cloud

Avant de supprimer le service Veeam on {{site.data.keyword.cloud_notm}}, sachez que la suppression de ce service arrêtera toutes les sauvegardes (y compris celle des machines virtuelles de gestion) et supprimera toutes les sauvegardes précédentes (cette suppression est irréversible). Si les machines virtuelles de gestion sont endommagées par la suite, elles ne pourront pas être restaurées.

## Liens connexes

* [Commande de Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [Gestion de Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [Demande de services gérés pour Veeam on {{site.data.keyword.cloud_notm}}](managing_veeam_services.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web Veeam](https://www.veeam.com/){:new_window}
* [Centre d'information Veeam](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
