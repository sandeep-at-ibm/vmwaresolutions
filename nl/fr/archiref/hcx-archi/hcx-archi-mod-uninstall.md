---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Modification ou désinstallation de HCX
{: #hcx-archi-mod-uninstall}

Il est possible de mettre à niveau une installation existante, ou encore de supprimer tout ou partie d'un déploiement de Services cloud hybrides.

##  Réduction d'un réseau de couche 2
{: #hcx-archi-mod-uninstall-unstretch-layer2}

Il est nécessaire de réduire un réseau de couche 2 avant de retirer le dispositif virtuel du service de concentrateur de couche 2 associé, ou avant de désinstaller des Services cloud hybrides.

1. Vérifiez les réseaux étendus.
2. Depuis la page du plug-in Services cloud hybrides, cliquez sur l'onglet Hybrid Services et consultez la section Network Extension Service. Si des travaux actifs ou planifiés sont en cours, patientez jusqu'à ce qu'ils soient terminés ou arrêtez-les avant de continuer.
3. Pour retirer le réseau, cliquez sur l'icône de suppression (X rouge) sur la droite.
4. Cliquez sur **OK** pour confirmer.

## Désinstallation des dispositifs virtuels HCX
{: #hcx-archi-mod-uninstall-uninst-hva}

Un dispositif de service peut être désinstallé dans le cadre de la préparation de la désinstallation de Services cloud hybrides ou en raison d'un changement dans l'architecture d'installation. Utilisez les Services cloud hybrides pour administrer les dispositifs, comme décrit dans la procédure ci-après.

### Prérequis pour la désinstallation des dispositifs virtuels HCX
{: #hcx-archi-mod-uninstall-prereq-uninst-hva}

* Annulez ou réinitialisez le temps d'exécution pour les migrations susceptibles de se produire pendant la tâche de désinstallation.
* Vérifiez si des migrations sont en cours sur la console des tâches de vSphere Web Client, et patientez jusqu'à ce qu'elles soient terminées.
* Assurez-vous qu'il n'y a aucun type de tâches Services cloud hybrides actives.

Ne supprimez jamais des dispositifs virtuels de l'inventaire vSphere. Utilisez toujours le portail pour interagir avec les dispositifs virtuels de service.
{:note}

### Prérequis pour la désinstallation des dispositifs virtuels HCX
{: #hcx-archi-mod-uninstall-proc-uninst-hva}

1. Dans l'interface de vSphere Web Client, sélectionnez le plug-in Services cloud hybrides dans le volet gauche.
2. Dans le volet central, cliquez sur l'onglet **Hybrid Services**.
3. Recherchez le dispositif Passerelle de cloud hybride et cliquez sur l'entrée pour afficher les détails.
4. Dans la partie inférieure droite, cliquez sur l'icône de suppression pour supprimer le dispositif.
5. Si un réseau étendu ne partage pas une adresse IP avec la passerelle de cloud hybride, vous devez le retirer séparément. Développez les détails du service d'extensions réseau, puis cliquez sur l'icône de suppression pour retirer le concentrateur de couche 2.

La passerelle de cloud hybride et les dispositifs virtuels de service hybride qui utilisent cette passerelle sont retirés à la fois de vCenter et de VCF/VCS Hybrid Cloud Services Cloud.

## Désinstallation de HCX Manager
{: #hcx-archi-mod-uninstall-unist-hcxm}

Le dispositif HCX Manager doit être désinstallé avant le retrait de la solution HCX du centre de données local. Procédez comme suit pour désinstaller la machine virtuelle Services cloud hybrides.

1. Réduisez tous les réseaux de couche 2.
2. Retirez les dispositifs virtuels de service hybride.
3. Dans le vCenter local, mettez hors tension la machine virtuelle Services cloud hybrides.
4. Supprimez la machine virtuelle Services cloud hybrides.

Tous les dispositifs de service virtuel sont retirés. Les éléments suivants peuvent rester :
* Journaux
* Machines virtuelles migrées

### Etape suivante
{: #hcx-archi-mod-uninstall-what-next}

Les machines virtuelles migrées et les journaux peuvent être sauvegardés ou supprimés manuellement.

## Connexion au portail de gestion HCX
{: #hcx-archi-mod-uninstall-log-hcxmp}

Il est possible d'administrer le déploiement des Services cloud hybrides depuis le portail de gestion à l'aide d'une interface utilisateur basée sur un navigateur.

1. Dans un navigateur Web, entrez l'adresse IP affectée aux Services cloud hybrides, puis indiquez le numéro de port 9443. Par exemple, `https://HCXip:9443`.
2. L'interface utilisateur Services cloud hybrides s'ouvre dans une fenêtre de navigateur Web à l'aide de SSL. Si nécessaire, acceptez le certificat de sécurité. L'écran de connexion VMware Hybridity and Networking s'ouvre.
3. Entrez le nom d'utilisateur et le mot de passe. Par défaut, le nom d'utilisateur est Admin. Le mot de passe est la valeur qui a été fournie lorsque le dispositif virtuel Services cloud hybrides a été installé.

## Liens connexes
{: #hcx-archi-mod-uninstall-related}

* [Traitement des incidents HCX on IBM Cloud](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-trbl)
