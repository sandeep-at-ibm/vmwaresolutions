---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Redondance des machines virtuelles vSAN
{: #vum-vsan-redundancy}

Lorsque vous placez un hôte vSphere ESXi en mode maintenance sur un cluster vSAN, vous devez sélectionner un mode d'évacuation des données. La sélection de ce mode peut avoir un impact sur les machines virtuelles et les dispositifs virtuels qui utilisent le magasin de données vSAN :
* L'option de **migration des données complète** évacue toutes les données de l'hôte et les supprime sur les autres hôtes vSphere ESXi figurant dans le cluster vSAN. Ce mode d'évacuation entraîne le transfert de la plus grande quantité de données et consomme la plupart du temps et des ressources. Tous les composants dans le stockage local de l'hôte sélectionné sont migrés ailleurs dans le cluster. Lorsque l'hôte passe en mode maintenance, toutes les machines virtuelles et les dispositifs virtuels ont accès à leurs composants de stockage et restent conformes aux règles de stockage qui leur sont affectées. L'évacuation des données complète peut prendre beaucoup de temps et peut rallonger la durée de la fenêtre de maintenance d'une mise à niveau.
* Le mode d'**évacuation des données Assurer l'accessibilité** est l'option par défaut et, lorsque l'hôte vSphere ESXi est placé en mode maintenance, vSAN garantit que toutes les machines virtuelles ou les dispositifs virtuels accessibles sur l'hôte restent accessibles. Comme l'évacuation des données n'est que partielle, la machine virtuelle ou le dispositif virtuel est susceptible de ne plus être complètement conforme à une règle de stockage VM lors de l'évacuation et risque de ne pas avoir accès à toutes ses répliques. En cas de problème lorsque l'hôte est en mode maintenance et que la valeur du niveau principal de pannes à tolérer est 1, il y a perte des données et la machine virtuelle ou le dispositif virtuel risque d'être indisponible.
* En mode **Aucune migration de données**, vSAN n'évacue pas les données de l'hôte lorsqu'il passe en mode maintenance. Alors que cela réduit le temps de passage en mode maintenance et réduit ainsi la durée de la fenêtre de maintenance, une partie des machines virtuelles ou des dispositifs virtuels peuvent devenir inaccessibles.

Cette section crée une nouvelle règle de stockage de machine virtuelle qui permet au mode d'**évacuation des données Assurer l'accessibilité** d'être sélectionné pour réduire les fenêtres de maintenance, mais réduire le risque d'échec d'un hôte lorsqu'un autre hôte est en mode maintenance rendra une machine virtuelle ou un dispositif virtuel inaccessible. Pour les machines virtuelles et les dispositifs virtuels, là où la redondance est inacceptable lorsqu'un hôte vSAN est placé en mode maintenance, exécutez le processus suivant avant d'effectuer toute action de résolution. Un cluster comportant au moins 6 hôtes est requis.

1. Créez un profil vSAN avec les paramètres RAID 5/6 et FTT =2 (RAID 6), puis appliquez cette règle aux machines virtuelles ou aux dispositifs virtuels requis.

2. Patientez jusqu'à ce que la synchronisation de vSAN soit terminée avant d'effectuer des actions de résolution. Le statut d'achèvement peut être vérifié en accédant à la page **vSAN Virtual Objects Monitoring** du cluster et en examinant le statut **Completion Status**.

## Liens connexes
{: #vum-vsan-redundancy-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (démonstrations)
