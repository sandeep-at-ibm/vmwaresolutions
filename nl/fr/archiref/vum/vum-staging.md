---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Transfert et résolution

Les correctifs et les extensions peuvent être éventuellement transférés avant toute résolution pour garantir qu'ils sont téléchargés de VUM vers l'hôte vSphere ESXi sans appliquer les correctifs ou les extensions immédiatement. Lors de la résolution, VUM applique les correctifs, les extensions et les mises à niveau aux objets d'inventaire. Le transfert des correctifs et des extensions accélère le processus de résolution car les correctifs et les extensions sont déjà disponibles en local sur les hôtes.

Si lors du processus de résolution, un hôte ne parvient pas à passer en mode maintenance, VUM signale une erreur et le processus s'arrête et échoue. Les hôtes vSphere ESXi déjà résolus restent au niveau mis à jour.

Pour que le processus de résolution fonctionne sans heurts, il est recommandé de désactiver certaines fonctions de cluster telles que DPM, le contrôle d'admission HA, FT (Fault Tolerance) et de déconnecter tous les dispositifs amovibles des machines virtuelles pour que DRS ne rencontre pas de problèmes lors de la migration des machines virtuelles vers d'autres hôtes.
En exécutant l'assistant de résolution, vous pouvez également générer des rapports pour vérifier qu'il n'y a aucun paramètre incohérent au niveau de l'hôte ou de la machine virtuelle pouvant entraîner l'échec du processus de résolution.

1.	A l'aide du client vSphere Web Client, cliquez sur **Home** > **Hosts and Clusters**.
2.	Cliquez avec le bouton droit de la souris sur un centre de données, un cluster ou un hôte, puis cliquez sur **Stage Patches**.
3.	Dans la page de sélection des lignes de base sur l'assistant de transfert, sélectionnez les lignes de base des correctifs et extensions à transférer.
4.	Sélectionnez les hôtes sur lesquels les correctifs et les extensions seront appliqués et cliquez sur **Next**. Si vous avez choisi de transférer des correctifs et des extensions sur un seul hôte, l'hôte est sélectionné par défaut.
5.	Facultatif : désélectionnez les correctifs et les extensions à exclure de l'opération de transfert. Pour effectuer une recherche dans la liste des correctifs et des extensions, saisissez du texte dans la zone de texte de la zone de filtre. Cliquez sur **Next**.
6.	Consultez la page Ready to Complete et cliquez sur **Finish**.

Le nombre de correctifs et d'extensions transférés pour l'hôte spécifique s'affiche dans les colonnes Patches et Extensions dans le panneau inférieur de l'onglet Update Manager. Lorsqu'une résolution a abouti, tous les correctifs et toutes les extensions, qu'ils aient ou non été installés lors de la résolution, seront supprimés sur l'hôte.
La résolution est un processus au cours duquel VUM applique des correctifs, des extensions et des mises à niveau aux hôtes vSphere ESXi, aux machines virtuelles ou aux dispositifs virtuels après l'exécution d'une analyse et qui rend conformes les objets sélectionnés. Vous pouvez résoudre des hôtes, des machines virtuelles ou des dispositifs virtuels uniques ou effectuer la résolution au niveau d'un dossier, d'un cluster ou d'un centre de données. VUM prend en charge la résolution des objets d'inventaire suivants en utilisant soit une résolution manuelle, soit une résolution planifiée :
*	Hôtes ESXi pour la résolution par correctif, extension ou mise à niveau.
*	Machines virtuelles sous tension, suspendues ou hors tension et modèles pour la mise à niveau du matériel de machines virtuelles et des outils VMware Tools.
*	Dispositifs virtuels sous tension créés avec VMware Studio 2.0 et version ultérieure, pour la mise à niveau des dispositifs virtuels.

Si la mise à jour l'exige, les hôtes sont placés en mode maintenance avant la résolution. Le dispositif VCSA effectue la migration des machines virtuelles sur d'autres hôtes au sein de l'instance VCS avant que l'hôte soit en mode maintenance.

## Pour les hôtes figurant dans un cluster vSAN
Tenez compte du comportement suivant des hôtes faisant partie d'un cluster vSAN :
* L'exécution du processus de résolution d'hôte peut prendre énormément de temps.
* Conformément à la conception, il ne peut y avoir qu'un seul hôte d'un cluster VSAN en mode maintenance à la fois.
* VUM résout les hôtes faisant partie d'un cluster VSAN de manière séquentielle même si vous avez défini l'option pour les résoudre en parallèle.
* Si une machine virtuelle sur l'hôte utilise une règle de stockage de machine virtuelle avec le paramètre "Number of failures to tolerate=0", cela peut entraîner des retards inhabituels pour le passage en mode maintenance de l'hôte. Ce retard est dû au fait que vSAN doit migrer les données de la machine virtuelle d'un disque à un autre dans le cluster du magasin de données vSAN, ce qui peut prendre plusieurs heures. Vous pouvez contourner ce problème en définissant le paramètre "Number of failures to tolerate=1" pour la règle de stockage de la machine virtuelle, ce qui entraîne la création de deux copies des fichiers de la machine virtuelle dans le magasin de données vSAN.
* Si une machine virtuelle sur l'hôte utilise une règle de stockage de machine virtuelle avec le paramètre "Number of failures to tolerate=1", la machine virtuelle devient non redondante lorsque l'hôte bascule en mode maintenance. Si cela n'est pas inacceptable, voir [Redondance de machine virtuelle vSAN](vum-vsan-redundancy.html).

Pour résoudre des hôtes et des clusters, procédez comme suit :
1.	Dans le client vSphere Web Client, sélectionnez **Home** > **Hosts and Clusters**.
2.	Dans le navigateur des objets d'inventaire, sélectionnez un centre de données, un cluster ou un hôte, cliquez sur l'onglet **Update Manager**, puis sur **Remediate**. Si vous avez sélectionné un objet conteneur, tous les hôtes sous l'objet sélectionné sont résolus. L'assistant de résolution s'ouvre.
3.	Sélectionnez **Patch Baselines** ou **Extension Baselines** selon le type de mise à jour que vous souhaitez effectuer sur l'hôte. Sur la page de sélection de ligne de base de l'assistant de résolution, sélectionnez le **groupe de lignes de base** et les **lignes de base** à appliquer.
4.	Sélectionnez les hôtes cible que vous souhaitez résoudre et cliquez sur **Next**. Si vous avez opté pour la résolution d'un seul hôte et non d'un objet conteneur, l'hôte est sélectionné par défaut.
5.	Facultatif : sur la page **Patches and Extensions**, désélectionnez des correctifs et des extensions spécifiques à exclure du processus de résolution, puis cliquez sur **Next**.
6.	Facultatif : sur la page **Advanced options**, sélectionnez l'option permettant de planifier la résolution pour une exécution ultérieure et indiquez un nom unique et une description facultative pour cette tâche. L'heure que vous définissez dans la tâche planifiée correspond à l'heure sur le dispositif VCSA. Facultatif : sélectionnez l'option permettant d'ignorer les avertissements sur les dispositifs non pris en charge sur l'hôte ou sur le magasin VMFS qui n'est plus pris en charge, pour poursuivre la résolution. Cliquez sur **Next**.
7.	Sur la page **Host Remediation Options**, dans le menu déroulant **VM Power state**, vous pouvez sélectionner la modification d'état d'alimentation des machines virtuelles et des dispositifs virtuels en cours d'éxécution sur les hôtes à résoudre. Un hôte ne peut pas passer en mode maintenance tant que les machines virtuelles sur l'hôte ne sont pas hors tension, suspendues ou migrées avec vMotion sur d'autres hôtes d'un cluster DRS. Certaines mises à jour nécessitent qu'un hôte soit en mode maintenance avant la résolution. Les machines virtuelles et les dispositifs virtuels ne peuvent pas s'exécuter lorsqu'un hôte est en mode maintenance. Pour réduire le temps d'immobilisation de la résolution aux dépens de la disponibilité des machines virtuelles, vous pouvez opter d'arrêter ou de suspendre des machines virtuelles et des dispositifs virtuels avant la résolution. Dans un cluster DRS, si vous ne mettez pas les machines virtuelles hors tension, la résolution peut prendre plus de temps mais les machines virtuelles sont disponibles tout au long du processus de résolution car elles sont migrées avec vMotion sur d'autres hôtes. Les sélections se présentent comme suit :

  - **Power Off virtual machines** - Met hors tension toutes les machines virtuelles et tous les dispositifs virtuels avant la résolution.
  - **Suspend virtual machines** - Suspend toutes les machines virtuelles et tous les dispositifs virtuels avant la résolution.
  - **Do Not Change VM Power State** - Laisse les machines virtuelles et les dispositifs virtuels dans leur état d'alimentation en cours.

8.	Facultatif : sélectionnez l'option **Disable any removable media devices connected to the virtual machine on the host**. VUM ne résout pas les hôtes sur lesquels les machines virtuelles disposent de CD, DVD ou unités de disquette connectés. Dans les environnements en cluster, les unités de stockage connectées peuvent empêcher vMotion de fonctionner si l'hôte de destination n'a pas d'unité identique ou d'image ISO montée, ce qui empêche à son tour l'hôte source de basculer en mode maintenance. Après la résolution, VUM reconnecte les unités de stockage amovibles si elles sont toujours disponibles.
9.	Facultatif : sélectionnez l'option **Retry entering maintenance mode in case of failure**, indiquez le nombre de nouvelles tentatives et spécifiez le délai d'attente entre les tentatives. VUM patiente pendant ce délai et effectue une nouvelle tentative pour placer l'hôte en mode maintenance autant de fois que vous indiquez dans la zone du nombre de nouvelles tentatives.
10.	Il n'y a aucune condition requise dans une instance VCS pour sélectionner la case à cocher sous ESXi Patch Settings afin d'autoriser Update Manager à appliquer des correctifs sur des hôtes ESXi sous tension démarrés avec PXE.
11.	Cliquez sur **Next**.
12.	Si vous résolvez des hôtes dans un cluster, éditez les options de résolution du cluster. La page **Cluster remediation options** n'est accessible que lorsque vous résolvez des clusters. Les options suivantes peuvent être sélectionnées :

*	**Disable Distributed Power Management (DPM)** si DPM est activée pour l'un des clusters sélectionnés, VUM ne résout pas les clusters avec l'option DPM activée. DPM surveille l'utilisation des ressources des machines virtuelles en cours d'exécution dans le cluster. S'il y a une capacité excédentaire suffisante, DPM recommande de déplacer les machines virtuelles sur d'autres hôtes dans le cluster et de mettre l'hôte d'origine en mode veille pour économiser l'alimentation. Mettre des hôtes en mode veille peut interrompre la résolution.
*	**Disable High Availability admission control** si le contrôle d'admission HA est activé pour l'un des clusters sélectionnés - VUM ne résout pas les clusters avec le contrôle d'admission HA activé. Un contrôle d'admission est une règle utilisée par VMware HA pour assurer la capacité de reprise en cas d'incident au sein d'un cluster. Si le contrôle d'admission HA est activé durant la résolution, les machines virtuelles figurant dans un cluster risquent de ne pas être migrées avec vMotion.
*	**Disable Fault Tolerance (FT)** si FT est activée. Cela affecte toutes les machines virtuelles tolérantes aux pannes dans les clusters sélectionnés - Si FT est activée pour l'une des machines virtuelles sur un hôte, VUM ne résout pas cet hôte. Pour que FT soit activée, les hôtes sur lesquels les machines virtuelles principales et secondaires s'exécutent, doivent être de même version et avoir les mêmes correctifs installés. Si vous appliquez des correctifs différents à ces hôtes, FT ne peut pas être réactivée.
*	**Enable parallel remediation for the hosts in the selected clusters** - Résout les hôtes dans les clusters de manière parallèle. Si ce paramètre n'est pas sélectionné, VUM résout les hôtes dans un cluster de manière séquentielle. Vous pouvez sélectionnez l'une des options suivantes pour la résolution de type parallèle :
    - Vous pouvez laisser VUM évaluer en continu le nombre maximal d'hôtes qu'il peut résoudre simultanément sans affecter les paramètres DRS.
    - Vous pouvez spécifier un nombre limite d'hôtes résolus simultanément dans chaque cluster que vous corrigez. Notez que VUM résout simultanément uniquement les hôtes sur lesquels les machines virtuelles sont suspendues ou hors tension. Vous pouvez choisir de mettre hors tension ou de suspendre les machines virtuelles à partir du menu VM Power State dans le panneau des options du mode maintenance sur la page Host Remediation Options. Conformément à la conception, il ne peut y avoir qu'un seul hôte d'un cluster vSAN en mode maintenance à la fois. VUM résout les hôtes faisant partie d'un cluster vSAN de manière séquentielle même si vous sélectionnez l'option pour les résoudre en parallèle.
*	**Migrate powered off and suspended virtual machines to other hosts in the cluster**, si un hôte doit passer en mode maintenance. Update Manager effectue la migration des machines virtuelles suspendues ou hors tension depuis les hôtes qui doivent passer en mode maintenance sur d'autres hôtes du cluster. Vous pouvez choisir de mettre hors tension ou de suspendre des machines virtuelles dans le panneau **Maintenance Mode Settings**.
13.	Sur la page Ready to complete, vous pouvez éventuellement cliquer sur **Pre-check Remediation** pour générer un rapport d'options de résolution de cluster, puis cliquer sur **OK**. La boîte de dialogue correspondant à ce rapport s'ouvre. Vous pouvez exporter ce rapport ou copier les entrées pour votre propre enregistrement et cliquer sur **Next**.
14.	Consultez la page Ready to Complete et cliquez sur **Finish**.

### Liens connexes

* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (démonstrations)
