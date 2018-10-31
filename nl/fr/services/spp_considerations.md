---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-28"

---

# Présentation d'IBM Spectrum Protect Plus on IBM Cloud

Le service {{site.data.keyword.IBM}} Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} fournit une solution évolutive et efficace de protection, de réutilisation et de récupération des données pour les environnements virtuels. Vous pouvez implémenter le service en tant que solution autonome ou vous pouvez l'intégrer à votre environnement IBM Spectrum Protect Plus pour décharger des copies de stockage à long terme et pour la gouvernance des données.

**Disponibilité :** ce service n'est disponible que pour les instances qui exécutent vSphere 6.5 et qui sont déployées dans (ou mises à niveau vers) la version 2.2 ou des éditions ultérieures.

**Remarques :**
* Si vous installez le service pour les instances qui sont déployées en version 2.4 ou dans des éditions ultérieures, IBM Spectrum Protect Plus V10.1.1 Patch 1 est installé.
* Si vous installez le service pour les instances qui sont déployées en version 2.3, IBM Spectrum Protect Plus V10.1.1 est installé.
* Si vous installez le service pour les instances qui sont déployées en version 2.2, IBM Spectrum Protect Plus V10.1.0 est installé.


## Spécifications techniques relatives à IBM Spectrum Protect Plus on IBM Cloud

Les composants suivants sont commandés et inclus dans le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} :

### Ressources vCenter

* Machine virtuelle de serveur exécutant un serveur IBM Spectrum Protect Plus
   * Système d'exploitation Linux 3.10.0-693.11.1.el7.x86_64
   * 4 coeurs de 2 GHz
   * 32 Go de mémoire RAM
   * Disque de 370 Go
* Machine virtuelle secondaire exécutant un serveur IBM Spectrum Protect Plus vSnap et un proxy VADP
   * Système d'exploitation Linux 3.10.0-693.11.1.el7.x86_64
   * UC et mémoire RAM configurées en fonction de la taille de stockage sélectionnée et des conseils de dimensionnement fournis dans le wiki [IBM Spectrum Protect Plus Blueprints](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints).
   * Disque de 150 Go

### Stockage pour les sauvegardes

Stockage personnalisable pour les sauvegardes avec les options suivantes :
* Nombre de stockage de fichiers : 1- 10
* Chaque stockage de fichiers de type Endurance : 500, 1000, 2000, 4000, 8000 ou 12000 Go
* Performance de stockage : 0,25, 2 ou 4 IOPS/Go

Pour la planification et le dimensionnement, voir les wikis [IBM Spectrum Protect Plus Blueprints et IBM Spectrum Protect Plus sizing tools](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints).

### Stockage pour la gestion

Un stockage de fichier Endurance (1000 Go, 2 IOPS/Go), qui héberge la machine virtuelle IBM Spectrum Protect Plus et s'exécute sur le même sous-réseau que le stockage de sauvegarde.

### Utilisation en réseau

Deux adresses IP privées portables.

### Licences et frais

* IBM Spectrum Protect Plus (10 à 1000 licences de machine virtuelle au maximum, par incréments de 10)
* Licence IBM Spectrum Protect Plus offerte via la console {{site.data.keyword.vmwaresolutions_short}} (nombre de machines virtuelles dans des packages de 10) ou proposée en mode BYOL

## Considérations à prendre en compte lorsque vous installez IBM Spectrum Protect Plus on IBM Cloud

Passez en revue les remarques suivantes avant d'installer le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

* Vérifiez que le nombre d'UC et la quantité de mémoire du cluster par défaut de votre instance suffisent pour la machine virtuelle IBM Spectrum Protect Plus.
* Vérifiez que les montages NFS disponibles sur les serveurs ESXi suffisent compte tenu de la version des serveurs ESXi.

  Les instances Cloud Foundation et vCenter Server déployées dans (ou mises à niveau vers) la version 2.2 ou des éditions ultérieures disposent d'un paramètre `NFS.MaxVolumes` dans VMware. Ce paramètre définit le nombre maximum de montages NFS sur un serveur ESXi et accepte la valeur maximale de 256 propre à la version du serveur ESXi. Pour plus d'informations, voir [Augmentation de la valeur par défaut qui définit le nombre maximum de montages NFS sur un hôte ESXi/ESX](https://kb.vmware.com/s/article/2239).

  Le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} peut utiliser jusqu'à 11 volumes NFS sur chaque serveur ESXi dans le cluster par défaut de votre instance. En outre, le service crée des montages NFS transitoires à des fins de sauvegarde et de restauration. Par conséquent, vous devez définir un minimum de 64 montages NFS pour que le service puisse être installé et fonctionner correctement.

## Considérations à prendre en compte lorsque vous retirez IBM Spectrum Protect Plus on IBM Cloud

Passez en revue les remarques suivantes avant de retirer le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} :
* Assurez-vous que toutes les configurations de tâche de sauvegarde ont été supprimées, ainsi que toute opération de sauvegarde ou de restauration active.
* Lorsque vous retirez le service, le stockage pour le référentiel des sauvegardes est supprimé de la machine virtuelle IBM Spectrum Protect Plus et la commande de stockage est annulée, ce qui supprime définitivement les données du référentiel des sauvegardes.
* Lorsque vous retirez le service, le stockage de sauvegarde qui a été commandé pour le service est également retiré. Toutes les sauvegardes deviennent inaccessibles pendant le retrait du service.

### Liens connexes

* [Planification préventive du service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestion d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Commande d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_ordering.html)
* [Documentation IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
