---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

#	Mises à niveau orchestrées
{: #vum-orchestr-updates}

Vous pouvez utiliser des mises à niveau orchestrées pour mettre à niveau le matériel virtuel et les outils VMware Tools des machines virtuelles dans l'inventaire après la mise à jour des hôtes vSphere ESXi. Une fois les hôtes mis à jour, la ligne de base de mise à niveau de VMware Tools s'exécute en premier, suivie par la ligne de base de mise à niveau du matériel des machines virtuelles. Vous pouvez utiliser les mises à niveau orchestrées au niveau d'un cluster, d'un dossier ou d'un centre de données.

VUM vous permet d'effectuer des mises à niveau orchestrées des hôtes, puis des machines virtuelles en utilisant des groupes de lignes de base. Un groupe de lignes de base contenant une ligne de base de mise à niveau d'un seul hôte et plusieurs lignes de base de correctifs ou d'extensions est utilisé. VUM commence par mettre à niveau les hôtes et applique ensuite les lignes de base de correctifs ou d'extensions. Pour effectuer une mise à niveau orchestrée des machines virtuelles, utilisez un groupe de lignes de base de machine virtuelle contenant les lignes de base suivantes :
* Mise à niveau de matériel de machine virtuelle pour correspondre à l'hôte (VM Hardware Upgrade to Match Host)
* Mise à niveau de VMware Tools pour correspondre à l'hôte (VMware Tools Upgrade to Match Host)

Les mises à niveau orchestrées de VUM vous permettent de mettre à niveau des objets d'inventaire dans VCSA via un processus en deux étapes. Les hôtes vSphere ESXi sont mis à niveau en premier, suivis des mises à niveau des machines virtuelles. Ce processus en deux étapes peut être configuré au niveau du cluster ou vous pouvez le configurer au niveau de l'hôte vSphere ESXi individuel ou de la machine virtuelle pour plus de contrôle granulaire.

Dans la mise à niveau orchestrée, le cluster est résolu en premier par rapport au groupe de lignes de base d'hôte, qui applique des correctifs, des extensions et des mises à niveau. Une fois cette mise à niveau effectuée, les machines virtuelles figurant dans le cluster sont résolues par rapport au groupe de lignes de base de mise à niveau des machines virtuelles contenant les lignes de base VM Hardware Upgrade to Match Host et VMware Tools Upgrade to Match Host.

Si le groupe de lignes de base contient également une ligne de base de mise à niveau, VUM met à niveau les hôtes vSphere ESXi en premier et applique ensuite les lignes de base de correctifs ou d'extensions car les correctifs sont applicables à la version de l'hôte spécifique. Pour les machines virtuelles, les outils VMware Tools sont d'abord mis à jour, suivis par la mise à jour de matériel de machine virtuelle.

Par conséquent, lors de la mise à niveau des outils VMware Tools, les machines virtuelles sont mises sous tension. Si elles sont hors tension ou suspendues, VUM les remet sous tension, exécute la mise à niveau et restaure leur état d'alimentation d'origine. Par conséquent, lors d'une mise à niveau de machines virtuelles, les machines virtuelles doivent être hors tension. Si certaines sont sous tension, VUM les arrête, met à niveau le matériel des machines virtuelles et les remet sous tension.

Par défaut, la résolution des hôtes ESXi s'effectue de manière séquentielle et résout un hôte à la fois. Lorsque le processus est terminé pour un hôte, VUM commence à résoudre l'hôte suivant. Ce comportement par défaut peut être modifié pour activer une résolution en parallèle de sorte que plusieurs hôtes soient résolus à la fois. Cependant, c'est possible uniquement si vous disposez de la capacité de basculement adéquate sur votre cluster.

Si les hôtes vSphere ESXI font partie d'un cluster vSAN, le processus de résolution est toujours séquentiel même si vous avez sélectionné une résolution parallèle dans l'assistant de résolution, car il ne peut y avoir qu'un seul hôte d'un cluster vSAN en mode maintenance à tout moment. VUM est intelligent et exécute un calcul du nombre d'hôtes pouvant être résolus en parallèle sans affecter les paramètres DRS.

Autrement, vous pouvez définir le nombre limite d'hôtes pouvant être résolus en parallèle lorsque vous utilisez l'assistant de résolution.

La procédure suivante décrit le processus pour exécuter une mise à niveau orchestrée :

## Etape 1
{: #vum-orchestr-updates-step1}

1. Utilisez le client vSphere Web Client pour vous connecter au dispositif VCSA.
2. Sélectionnez **Home** > **Update Manager** puis, dans l'onglet **Objects**, sélectionnez une instance **Update Manager**.
3. Cliquez sur l'onglet **Manage**, puis sur l'onglet **Host Baselines** et cliquez sur **New Baseline Group**.
4. Entrez un nom unique pour le groupe de lignes de base et cliquez sur **Next**.
5. Sélectionnez une ligne de base de mise à niveau d'hôte pour l'inclure dans le groupe de lignes de base.
6. Créez éventuellement une nouvelle ligne de base de mise à niveau d'hôte en cliquant sur **Create a new Host Upgrade Baseline** au bas de la page Upgrades et exécutez l'assistant de nouvelle ligne de base. Cliquez sur **Next**.
7. Sélectionnez les lignes de base de correctifs que vous souhaitez inclure dans le groupe de lignes de base.
8. Créez éventuellement une nouvelle ligne de base de correctifs en cliquant sur **Create a new Host Patch Baseline** au bas de la page Patches et exécutez l'assistant de nouvelle ligne de base. Cliquez sur **Next**.
9. Sélectionnez les lignes de base d'extensions à inclure dans le groupe de lignes de base.
10. Créez éventuellement une nouvelle ligne de base d'extension en cliquant sur **Create a new Extension Baseline** au bas de la page Extensions et exécutez l'assistant nouvelle ligne de base.
11. Passez en revue la page **Ready to Complete**, cliquez sur **Finish** et le groupe de lignes de base d'hôte s'affiche dans le panneau Baseline Groups.

## Etape 2
{: #vum-orchestr-updates-step2}

1. Créez un groupe de lignes de base de machines virtuelles, contenant la ligne de base VMware Tools Upgrade to Match Host et la ligne de base VM Hardware Upgrade to Match Host, dans la vue d'administration VUM.
2. Rattachez le groupe de lignes de base à un objet conteneur vCenter contenant les machines virtuelles que vous souhaitez mettre à niveau.
3. Analysez l'objet conteneur pour afficher l'état de conformité des machines virtuelles dans le conteneur. Vous pouvez lancer l'analyse manuellement ou planifier une tâche d'analyse.
4. Passez en revue les résultats d'analyse affichés dans la vue de conformité de VUM Client.
5. Résolvez les machines virtuelles non conformes dans l'objet conteneur pour les rendre conformes par rapport au groupe de lignes de base attaché. Vous pouvez lancer la résolution manuellement ou planifier une tâche de résolution.
* Lors d'une mise à niveau de VMware Tools, les machines virtuelles doivent être sous tension. Si une machine virtuelle est hors tension ou suspendue avant la résolution, VUM met la machine sous tension. Une fois la mise à niveau terminée, VUM redémarre la machine et restaure l'état d'alimentation d'origine de la machine virtuelle.
* Lors d'une mise à niveau de matériel de machine virtuelle, les machines virtuelles doivent être arrêtées. Une fois la résolution terminée, VUM restaure l'état d'alimentation d'origine des machines virtuelles. Si une machine virtuelle est sous tension, VUM la met hors tension, met à niveau le matériel de la machine virtuelle, puis la remet sous tension.

Vous pouvez désormais utiliser ces groupes de lignes de base dans les processus d'analyse, de révision, de transfert et de résolution.

## Liens connexes
{: #vum-orchestr-updates-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [Démonstrations {{site.data.keyword.vmwaresolutions_full}}](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (démonstrations)
