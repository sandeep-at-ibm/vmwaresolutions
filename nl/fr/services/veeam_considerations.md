---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# Présentation de Veeam on IBM Cloud

Le service Veeam on {{site.data.keyword.cloud}} s'intègre directement et en toute transparence à vos hyperviseurs VMware afin d'aider votre entreprise à obtenir la haute disponibilité requise. Il peut fournir des objectifs de point et de temps de reprise pour vos applications et vos données. Les objectifs de point et de temps de reprise peuvent être fournis moins de 15 minutes après la fin de la configuration. Ce service vous permet de contrôler directement à la fois la sauvegarde et la restauration de toutes les machines virtuelles de votre infrastructure depuis la console Veeam.

**Disponibilité** : ce service est disponible uniquement sur les instances déployées en version 1.8 ou dans des éditions ultérieures.

## Spécifications techniques relatives à Veeam on IBM Cloud

Les composants suivants sont commandés et inclus dans le service Veeam on {{site.data.keyword.cloud_notm}} :

### Instances de serveur virtuel

* Une instance de serveur virtuel avec service complémentaire Veeam Backup and Replication 9.5
* Windows Server 2016 Standard Edition (64 bits)
* Coeurs 4 x 2,0 GHz
* 8 Go de mémoire RAM
* Liaison montante de réseau privé 1 Gbps
* Disque 100 Go (SAN)

### Stockage pour les sauvegardes

* Stockage Endurance iSCSI (2000, 4000, 8000 ou 12000 Go)
* Performances de stockage (0,25, 2 ou 4 IOPS/Go)

### Utilisation en réseau

Une adresse IP privée principale

### Licences et frais

Veeam Backup and Replication 9.5 Enterprise Plus (licence pour 10, 25, 50, 100 ou 200 machines virtuelles)

### Gestion

Sauvegardes de gestion configurées par défaut avec un maximum de cinq machines virtuelles et 2000 Go de stockage

## Remarques relatives à l'installation de Veeam on IBM Cloud

Le référentiel du stockage et celui du serveur Veeam se trouvent dans le pod et le centre de données d'origine. Par conséquent, les performances des opérations de sauvegarde des clusters distants peuvent se dégrader.

## Remarques relatives au retrait de Veeam on IBM Cloud

Avant de supprimer le service Veeam on {{site.data.keyword.cloud_notm}}, sachez que la suppression de ce service arrêtera toutes les sauvegardes (y compris celle des machines virtuelles de gestion) et supprimera toutes les sauvegardes précédentes (cette suppression est irréversible). Si les machines virtuelles de gestion sont endommagées par la suite, elles ne pourront pas être restaurées.

### Liens connexes

* [Commande de Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [Gestion de Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [Demande de services gérés pour Veeam on {{site.data.keyword.cloud_notm}}](managing_veeam_services.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web Veeam](https://www.veeam.com/){:new_window}
* [Centre d'information Veeam](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
