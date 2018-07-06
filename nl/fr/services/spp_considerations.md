---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Présentation d'IBM Spectrum Protect Plus on IBM Cloud

Le service IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} fournit une solution évolutive et efficace de protection, de réutilisation et de reprise des données pour les environnements virtuels. Vous pouvez implémenter le service en tant que solution autonome ou vous pouvez l'intégrer à votre environnement IBM Spectrum Protect Plus pour décharger des copies de stockage à long terme et pour la gouvernance des données.

**Disponibilité :** ce service n'est disponible que pour les instances qui exécutent vSphere 6.5 et qui sont déployées dans (ou mises à niveau vers) la version 2.2 ou des éditions ultérieures.

**Remarques :**
* Si vous installez le service pour les instances qui sont déployées en version 2.4 ou dans des éditions ultérieures, IBM Spectrum Protect Plus V10.1.1 Patch 1 est installé. Le service fournit automatiquement la prise en charge de la reprise pour les machines virtuelles de gestion.
* Si vous installez le service pour les instances qui sont déployées en version 2.3, IBM Spectrum Protect Plus V10.1.1 est installé. Le service fournit automatiquement la sauvegarde des machines virtuelles de gestion.
* Si vous installez le service pour les instances qui sont déployées en version 2.2, IBM Spectrum Protect Plus V10.1.0 est installé. Ce service fournit une protection des données uniquement pour les machines virtuelles de charge de travail.


## Composants d'IBM Spectrum Protect Plus on IBM Cloud

Les composants suivants sont commandés et inclus dans le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} :

### Ressources vCenter

* Une seule machine virtuelle exécutant le serveur IBM Spectrum Protect Plus
* 4 Coeurs de 2,0 GHz
* 32 Go de mémoire RAM
* Disque de 370 Go

### Stockage pour les sauvegardes

Stockage personnalisable pour les sauvegardes avec les options suivantes :
* Nombre de stockage de fichiers : 1, 2, 3 ou 4
* Chaque stockage de fichiers de type Endurance : 500, 1000, 2000, 4000, 8000 ou 12000 Go
* Performance de stockage : 0,25, 2 ou 4 IOPS/Go

### Stockage pour la gestion

Un stockage de fichiers de type Endurance (500 Go, 2 IOPS/Go) hébergeant la machine virtuelle IBM Spectrum Protect Plus et s'exécutant sur le même sous-réseau que le stockage de sauvegarde commandé pour le service.

### Utilisation en réseau

Une adresse IP privée portable.

### Licences et frais

Les licences IBM Spectrum Protect Plus peuvent être obtenue sur la console {{site.data.keyword.vmwaresolutions_short}} pour 10 à 1000 machines virtuelles au maximum, par incréments de 10. Vous pouvez également utiliser votre propre licence (mode BYOL) et télécharger le fichier de licence durant le processus d'installation.

## Remarques relatives à l'installation du service IBM Spectrum Protect Plus on IBM Cloud

Passez en revue les remarques suivantes avant d'installer le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

* Vérifiez que le nombre d'UC et la quantité de mémoire du cluster par défaut de votre instance suffisent pour la machine virtuelle IBM Spectrum Protect Plus.
* Vérifiez que les montages NFS disponibles sur les serveurs ESXi suffisent compte tenu de la version des serveurs ESXi.

  Les instances Cloud Foundation et vCenter Server déployées dans (ou mises à niveau vers) la version 2.2 ou des éditions ultérieures disposent d'un paramètre `NFS.MaxVolumes`  dans VMware. Ce paramètre définit le nombre maximum de montages NFS sur un serveur ESXi et accepte la valeur maximale de 256 propre à la version du serveur ESXi. Pour plus d'informations, voir [Augmentation de la valeur par défaut qui définit le nombre maximum de montages NFS sur un hôte ESXi/ESX](https://kb.vmware.com/s/article/2239).

  Le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} peut consommer jusqu'à cinq des volumes NFS sur chaque serveur ESXi dans le cluster par défaut de votre instance. En outre, le service créera des montages NFS transitoires à des fins de sauvegarde et de restauration. Par conséquent, vous devez définir un minimum de 64 montages NFS pour que le service puisse être installé et fonctionne correctement.

## Remarques relatives au retrait du service IBM Spectrum Protect Plus on IBM Cloud

Passez en revue les remarques suivantes avant de supprimer le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} :
* Vérifiez que toutes les configurations de tâche de sauvegarde ont été supprimées et qu'il ne reste aucune opération de sauvegarde ou de restauration active.
* Lorsque vous supprimez le service, le stockage du référentiel de sauvegarde est supprimé de la machine virtuelle IBM Spectrum Protect Plus et la commande de stockage est annulée, ce qui supprime définitivement les données du référentiel de sauvegarde.
* Lorsque vous supprimez le service, le stockage de sauvegarde commandé pour le service est également supprimé. Par conséquent, toutes les sauvegardes sont inaccessibles pendant la suppression du service.

## Liens connexes

* [Planification préventive du service IBM Spectrum Protect Plus on IBM Cloud](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestion d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Commande d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_ordering.html)
* [Documentation IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
