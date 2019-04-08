---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Migration d'une machine virtuelle
{: #hcx-archi-migrate-vm}

HCX permet la migration bidirectionnelle : d'un site vers le cloud, ou du cloud vers le centre de données sur site. HCX utilise la technologie de réplication pendant le processus de migration. La technologie de réplication est intégrée dans le dispositif virtuel Passerelle de cloud hybride. Aucun logiciel de réplication supplémentaire ne doit être installé.

## Migration avec peu d'interruption

La migration avec peu d'interruption utilise la réplication basée sur l'hôte pour déplacer la machine virtuelle réelle d'un vCenter vers un centre de données virtuel réel ou dans la direction opposée. Pour réduire le temps d'indisponibilité, la machine virtuelle source reste en ligne pendant la réplication et elle est amorcée sur l'hôte ESX de destination une fois la réplication terminée.

1. Une demande de migration déclenche les actions suivantes :
  * La réplication commence une transfert de synchronisation intégrale dans un centre de données virtuel HCX VCF/VCS. Le temps nécessaire à la réplication dépend de la taille de la machine virtuelle et de la bande passante disponible.
  * La consommation de bande passante de réplication varie en fonction de la manière dont la charge de travail modifie les blocs sur le disque.
2. Une fois la synchronisation intégrale terminée, une synchronisation delta est effectuée.
3. Une fois la synchronisation delta terminée, HCX déclenche un basculement. Ce basculement peut démarrer immédiatement ou être programmé à une date spécifique.
4. Après le basculement, la machine virtuelle source est mise hors tension, et la réplique migrée est mise sous tension. Si pour une quelconque raison, la machine virtuelle ne peut pas se mettre sous tension, la nouvelle machine virtuelle est mise hors tension (ou elle demeure hors tension) et la machine d'origine est mise sous tension.
5. HCX renomme la machine virtuelle d'origine hors tension afin d'éviter un conflit de nom avec la machine virtuelle migrée et il ajoute un horodatage binaire au nom de la machine virtuelle d'origine.
6. S'il n'était pas spécifié d'activer **Retain MAC**, la machine virtuelle migrée obtient une nouvelle adresse MAC.
7. La migration est effectuée. Le service Services cloud hybrides copie la machine virtuelle d'origine dans le dossier **Migrated VMs** dans la vue vSphere Templates.

## vMotion sans interruption
{: #hcx-archi-migrate-vm-no-downtime-vm}

vMotion transfère une machine virtuelle réelle d'un vSphere vCenter vers un cloud VCF/VCS. Ce vMotion requiert un réseau étendu. Le transfert de vMotion capture la mémoire active de la machine virtuelle, son état d'exécution, son adresse IP et son adresse MAC.

La version matérielle de la machine virtuelle doit être au moins égale à 9, ou la migration vMotion entre clouds risque d'échouer.
{:note}

## Migration à froid
{: #hcx-archi-migrate-vm-cold-mig}

La migration à froid utilise le même plan de données que le vMotion entre clouds pour le transfert d'une machine virtuelle hors tension sur un réseau étendu. Son adresse IP et son adresse MAC sont conservées. Les exigences et les restrictions de la machine virtuelle et de vMotion sont identiques.

### Migration de machines virtuelles à l'aide de l'assistant bidirectionnel
{: #hcx-archi-migrate-vm-mig-bidir-wiz}

Avec le client vSphere Web Client, l'assistant de migration bidirectionnel est accessible depuis l'onglet de mise en route des services Services cloud hybrides. Cet assistant gère tous les détails de la migration, y compris les machines virtuelles multiples.

Depuis le client vSphere Web Client, l'assistant de migration bidirectionnelle est accessible à partir de l'onglet guide d'initiation hybride des services de cloud. Cet assistant gère tous les détails de la migration, y compris les machines virtuelles multiples.
* Depuis vSphere vers le service Services cloud hybrides VCF/VCS
* Depuis VCF/VCS HCX Cloud vers vSphere

### Vérification des machines virtuelles avant la migration
{: #hcx-archi-migrate-vm-check-vms}

Pour migrer une machine virtuelle, il est nécessaire de disposer d'une connexion sécurisée gérée par la passerelle de cloud hybride, et ka machine virtuelle doit répondre aux exigences suivantes :
* La machine virtuelle doit être sous tension.
* L'architecture sous-jacente doit être x86, quel que soit le système d'exploitation.
* Pour utiliser la migration vMotion, la version matérielle doit être supérieure à 9.
* La version matérielle doit être inférieure à 10.
* Les machines virtuelles dotées de la fonction Raw Disk Mapping en mode compatibilité peuvent être migrées.

Les machines virtuelles avec les attributs suivants ne sont pas prises en charge pour la migration :
* Machines virtuelles avec 2 To supplémentaires.
* Machines virtuelles qui partagent des fichiers VMDK.
* Machines virtuelles dotées d'un média virtuel ou reliées à des images ISO.
* Machines virtuelles dont la version matérielle est inférieure à 9.

### Surveillance d'une migration
{: #hcx-archi-migrate-vm-monitor-mig}

La progression d'un migration basée sur la réplication peut être surveillée depuis l'interface utilisateur ou depuis la ligne de commande. Vous pouvez consulter la console des tâches, comme décrit dans la procédure relative à la surveillance du déploiement d'un dispositif de service et rechercher la tâche relative à la **migration d'une machine virtuelle**. Lorsque l'état est **Completed**, la machine virtuelle est migrée et sous tension.

Cette procédure utilise une machine virtuelle non liée dans le même vCenter pour suivre la progression d'une machine virtuelle migrée.

1. Identifiez la machine virtuelle à migrer, puis choisissez la machine virtuelle d'un observateur qui peut effectuer un ping de la machine virtuelle en cours de migration.
2. Depuis l'interface utilisateur, démarrez la migration de la machine virtuelle, puis surveillez-là depuis la console des tâches.
3. À l'aide de SSH, connectez-vous à l'hôte ESXi qui exécute la machine virtuelle de l'observateur.
4. Exécutez la commande suivante pour obtenir l'ID de la machine virtuelle (le vmid) :

  ```
  # vim-cmd vmsvc/getallvms | grep -i vmname 5
  ```

5. Exécutez les commandes suivantes pour surveiller l'état de réplication, où vmid est la valeur obtenue à l'étape précédente :

  ```
  # vim-cmd hbrsvc/vmreplica.getState vmid
  # vim-cmd hbrsvc/vmreplica.queryReplicationState vmid 6
  ```

6. Ping ICMP - Surveillez le ping continu démarré plus haut.

Une interruption peut avoir lieu dans le ping continu pendant le basculement. Toutefois, le ping de test reprend rapidement la tâche **Migrate VM**, comme indiqué dans la console des tâches.

### Affichage des machines virtuelles migrées
{: #hcx-archi-migrate-vm-view-vms}

Lorsque le service Services cloud hybrides met sous tension une machine virtuelle migrée avec succès, il met hors tension la machine virtuelle en cours de migration d'origine et l'enregistre dans un dossier dans vCenter. Les machines virtuelles stockées restent ainsi jusqu'à ce qu'elles soient supprimées manuellement.

A l'issue de la migration, consultez le vCenter et notez les dossier libellés **VMs migrated from the cloud** et **VMs migrated to the cloud**.
* En tant que répliques, les machines virtuelles mises hors tension portent le nom d'origine, avec un horodatage binaire comme extension.
* Les machines virtuelles migrées peuvent être traités comme toutes les autres machines virtuelles. Par exemple, elles peuvent être déplacées vers un emplacement différent et mises sous tension.
* Les machines virtuelles non souhaitées dans ces dossiers peuvent être supprimées.
* La suppression est finale, à moins qu'une solution de sauvegarde ne soit en place.

## Liens connexes
{: #hcx-archi-migrate-vm-related}

* [Modification ou désinstallation de HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
