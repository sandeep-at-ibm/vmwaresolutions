---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Présentation de VMware Update Manager
{: #vum-overview}

VMware Update Manager (VUM) utilise un processus à plusieurs étapes pour mettre à niveau des objets vSphere et appliquer des correctifs ou des extensions. Ce processus permet une procédure de mise à jour sans heurts avec un minimum d'indisponibilité du système. Avant d'examiner ce processus, vous devez comprendre les termes suivants :
* **Objet d'inventaire** - Il s'agit d'un objet dans vCenter, tel qu'une machine virtuelle, un dispositif virtuel ou un hôte vSphere ESXi.
* **Ligne de base** - Les lignes de base contiennent une collection d'un ou plusieurs correctifs, extensions, packs de service, correctifs de bogue ou mises à niveau pouvant être classées comme lignes de base de correctifs, d'extensions ou de mises à niveau. Il existe deux classifications de lignes de base : Hôte et VM/VA (machine virtuelle ou dispositif virtuel) comportant des lignes de base prédéfinies par VMware et des lignes de base personnalisées pouvant être ajoutées si nécessaire.
  - Lignes de base d'hôte prédéfinies :
    - Correctifs d'hôte critiques
    - Correctifs d'hôte non critiques

  - Lignes de base de machine virtuelle ou de dispositif virtuel prédéfinies :
    - Mise à niveau de dispositif virtuel à la version la plus récente
    - Mise à niveau de matériel de machine virtuelle pour correspondre à l'hôte
    - Mise à niveau de VMware Tools pour correspondre à l'hôte

* **Groupe de lignes de base** - Ensemble de lignes de base non conflictuelles, qui combine différents types de ligne de base et qui analyse et résout un objet d'inventaire par rapport à toutes les lignes de base dans leur ensemble. Si un groupe de lignes de base contient à la fois des lignes de base de mises à niveau et des lignes de base de correctifs ou d'extensions, la ligne de base de mises à niveau s'exécute en premier.
* **Analyse** - L'analyse est le processus qui consiste à évaluer un ou plusieurs objets d'inventaire par rapport à la ligne de base ou au groupe de lignes de base.
* **Transfert** - Le transfert permet de garantir que les correctifs et les extensions sont téléchargés sur les hôtes vSphere ESXi avant l'opération de résolution. Il s'agit d'une option facultative utilisée pour réduire le plus possible le temps qu'un hôte passe en mode maintenance.
* **Résolution** - La résolution est le processus au cours duquel VUM applique des correctifs, des extensions et des mises à niveau à un ou plusieurs objets d'inventaire.

Le processus VUM se présente comme suit :
* Un objet d'inventaire ou un groupe d'objets sont analysés pour vérifier leur conformité par rapport à une ligne de base ou un groupe de lignes de base.
* Après une révision, des correctifs et des extensions peuvent être éventuellement transférés avant l'opération de résolution.

Le téléchargement des mises à niveau, des correctifs d'hôte, des extensions et des métadonnées associées est un processus automatique prédéfini pouvant être modifié. Par défaut, à intervalles réguliers pouvant être configurés, VUM contacte VMware ou des sources tierces, pour rassembler les éléments suivants sur les mises à niveau, les correctifs ou les extensions disponibles :

* Métadonnées sur tous les correctifs ESXi 5.5 et ESXi 6.x que vous disposiez ou non d'hôtes de ces versions dans votre environnement.
* Métadonnées sur les correctifs ESXi 5.5 et ESXi 6.x, ainsi que sur les extensions provenant d'adresses URL de fournisseurs tiers.
* Notifications, alertes et rappel de correctifs pour les hôtes ESXi 5.5 et ESXi 6.x.
* Métadonnées sur les mises à niveau de dispositifs virtuels.

VUM prend en charge le rappel de correctifs pour les hôtes exécutant ESXi 5.0 ou version ultérieure. Un correctif est rappelé s'il y a des problèmes ou des erreurs dans le correctif publié. Après avoir analysé les hôtes dans votre instance VMware vCenter Server on {{site.data.keyword.cloud}}, VUM vous avertit en cas d'installation du correctif rappelé sur un hôte. Les correctifs rappelés ne peuvent pas être installés sur des hôtes avec VUM. VUM supprime également tous les correctifs rappelés du référentiel des correctifs. Une fois qu'un correctif avec la résolution du problème est publié, VUM télécharge le nouveau correctif dans son référentiel de correctifs. Si vous avez installé le correctif qui pose problème, VUM vous envoie une notification indiquant que la correction du correctif a été publiée et vous invite à appliquer le nouveau correctif.

L'interface du client VUM fournit deux vues principales :
*	Vue Administration
*	Vue Conformité

##	Vue Administration
{: #vum-overview-admin-view}

L'accès à la vue Administration s'effectue en accédant à **Home** > **Update Manager** et en sélectionnant l'adresse IP de l'instance Update Manager. Dans la vue Administration, vous pouvez effectuer les tâches suivantes :
*	Configurer les paramètres d'Update Manager
*	Créer et gérer les lignes de base et les groupes de lignes de base
*	Afficher les événements d'Update Manager
*	Consulter le référentiel des correctifs et les mises à niveau de dispositifs virtuels disponibles
*	Passer en revue et vérifier les notifications
*	Importer des images ESXi

##	Vue Conformité
{: #vum-overview-compliance-view}

L'accès à la vue Conformité d'un objet d'inventaire sélectionné s'effectue en accédant à **Hosts and Clusters** ou **VMs and Templates** et en cliquant sur l'onglet **Update Manager**. Dans la vue Conformité d'Update Manager, vous pouvez effectuer les tâches suivantes :
*	Afficher l'état de conformité et analyser les résultats pour chaque objet d'inventaire sélectionné
*	Associer et dissocier des lignes de base et des groupes de lignes de base d'un objet d'inventaire sélectionné
*	Analyser un objet d'inventaire sélectionné
*	Transférer des correctifs ou des extensions sur des hôtes
*	Résoudre un objet d'inventaire sélectionné

## Liens connexes
{: #vum-overview-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (démonstrations)
