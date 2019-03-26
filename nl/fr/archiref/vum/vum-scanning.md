---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Analyse et révision
{: #vum-scanning}

Lorsque vous analysez des hôtes, des machines virtuelles et des dispositifs virtuels, vous les évaluez par rapport aux lignes de ligne et des groupes de lignes de base afin de déterminer leur niveau de conformité. Les objets d'inventaire sont analysés, et les résultats passés en revue pour déterminer leur conformité par rapport aux lignes de base et aux groupes de lignes de base. Les résultats d'analyse peuvent être filtrés avec une recherche de texte, une sélection de groupe ou de ligne de base et une sélection d'état de conformité. Vous pouvez initier les analyses suivantes :
*	**Lancement manuel d'une analyse d'hôtes vSphere ESXi** - Vous pouvez analyser des hôtes vSphere ESXi dans l'inventaire vSphere par rapport aux lignes de base et aux groupes de lignes de base associés.
*	**Lancement manuel d'une analyse de machines virtuelles et de dispositifs virtuels** - Vous pouvez analyser des machines virtuelles et des dispositifs virtuels dans l'inventaire vSphere par rapport aux lignes de base et aux groupes de lignes de base associés.
*	**Lancement manuel d'une analyse d'objet conteneur** - Lancez l'analyse simultanée des hôtes, des machines virtuelles et des dispositifs virtuels, en effectuant l'analyse d'un objet conteneur qui correspond à un centre de données ou un dossier de centre de données.
*	**Planification d'une analyse** - Vous pouvez configurer le client vSphere Web Client pour analyser des machines virtuelles, des dispositifs virtuels et des hôtes ESXi à des heures spécifiques ou aux intervalles qui vous conviennent.

## Lancement manuel d'une analyse d'hôtes vSphere ESXi
{: #vum-scanning-scan-hosts}

1. Cliquez sur **Scan for Updates**, sélectionnez **Patches and Extensions and Upgrades**, puis cliquez sur **OK**.
2. Une fois l'analyse terminée, sélectionnez **Critical Host Patches**. Dans le panneau inférieur, passez en revue les correctifs de chaque hôte en cliquant sur le nombre figurant dans **Number of Patches**. Une fenêtre s'affiche avec les informations relatives au correctif.
3. Passez en revue ces informations et répétez ces étapes pour les correctifs non critiques (**Non-Critical Patches**).

  Les fichiers journaux de VUM se trouvent dans le chemin suivant :_/var/log/vmware/vmware-updatemgr/vum-server/vmware-vum-server-log4cpp.log_

## Lancement manuel d'une analyse de machines virtuelles et de dispositifs virtuels
{: #vum-scanning-scan-vm-va}

Vous pouvez analyser des machines virtuelles et des dispositifs virtuels dans l'inventaire vSphere par rapport aux lignes de base et aux groupes de lignes de base associés. Les machines virtuelles et les dispositifs virtuels que vous sélectionnez sont analysés par rapport aux lignes de base associées, en fonction des options que vous avez choisies. Tous les objets enfant sont analysés, de sorte que plus l'infrastructure virtuelle est importante et plus vous lancez l'analyse au niveau le plus haut dans la hiérarchie des objets, plus l'analyse prend du temps et plus la vue de conformité est précise.

1.	A l'aide du client vSphere Web Client, sélectionnez **Home** > **VMs and Templates**.
2.	Cliquez avec le bouton droit de la souris sur une _machine virtuelle_, un _dispositif virtuel_ ou un _dossier de machines virtuelles et de dispositifs virtuels_ et cliquez sur **Scan for Updates**.
3.	Sélectionnez les types de mises à jour à rechercher. Les options possibles sont : _Virtual Appliance upgrades, VM Hardware upgrades_ et _VMware Tools upgrades_.
4.	Cliquez sur **Scan**.

##	Initiation manuelle d'une analyse d'un objet conteneur
{: #vum-scanning-scan-container}

Lancez l'analyse simultanée des hôtes, des machines virtuelles et des dispositifs virtuels, en effectuant l'analyse d'un objet conteneur qui correspond à un centre de données ou un dossier de centre de données.
1.	A l'aide du client vSphere Web Client, sélectionnez **Home** > **VMs and Templates**.
2.	Cliquez avec le bouton droit de la souris sur un _centre de données_ ou un _dossier de centre de données_, puis cliquez sur **Scan for Updates**.
3.	Sélectionnez les types de mises à jour à rechercher. Les options possibles sont : _Virtual Appliance upgrades, VM Hardware upgrades_ et _VMware Tools upgrades_.
4.	Cliquez sur **Scan**.

##	Planification d'une analyse
{: #vum-scanning-schedule}

Vous pouvez configurer le client vSphere Web Client pour analyser des machines virtuelles, des dispositifs virtuels et des hôtes vSphere ESXi à des heures spécifiques ou aux intervalles qui vous conviennent.

1.	A l'aide du client vSphere Web Client, sélectionnez un objet dans l'inventaire. Tous les objets enfant de l'objet que vous sélectionnez sont également analysés.
2.	Sélectionnez l'onglet **Monitor** et cliquez sur **Task & Events**.
3.	Sélectionnez **Scheduled Tasks** et cliquez sur **Schedule a New Task**.
4.	Sélectionnez **Scan for Updates** dans la liste déroulante qui s'affiche. L'assistant de recherche des mises à jour s'ouvre.
5.	Sur la page Edit Settings, sélectionnez les types de mises à jour à rechercher pour l'objet d'inventaire. Vous devez sélectionner au moins un type d'analyse. Sur la page des options de planification Scheduling, décrivez et planifiez la tâche d'analyse.
6.	Entrez un nom unique, et éventuellement, une description pour la tâche d'analyse. Cliquez sur **Change** pour définir la fréquence et l'heure de début de la tâche d'analyse. Cliquez sur **OK**.
7.	La tâche d'analyse est répertoriée dans la vue Scheduled Tasks de vSphere Web Client.

## Liens connexes
{: #vum-scanning-related}

* [VMware HCX on {{site.data.keyword.cloud}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (démonstrations)
