---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-07"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Mise à niveau du logiciel vCenter Server vSphere de VMware vSphere 6.5 à 6.7
{: #vc_vsphere_upgrade}

L'offre vCenter Server on {{site.data.keyword.cloud}} est une solution de déploiement entièrement automatisée pour la pile VMware vSphere SDDC incluant les produits vSphere, NSX et en option vSAN. Bien que vCenter Server automatise les parties les plus complexes du déploiement, de l'extension et de la sous-traitance d'une infrastructure basée sur VMware SDDC, il ne s'agit pas d'un service géré. Comme vCenter Server a pour politique de prendre en charge l'automatisation des versions logicielles VMware SDDC dans la plage N-1, vous devez mettre à niveau les instances existantes de vCenter Server si vous souhaitez continuer à bénéficier de l'automatisation {{site.data.keyword.vmwaresolutions_short}}.

Les versions de vCenter Server qui n'appartiennent pas aux niveaux requis par l'automatisation continuent d'être prises en charge comme l'exige la politique de VMware, mais ne fonctionnent plus avec l'automatisation {{site.data.keyword.vmwaresolutions_short}}. Vous devez effectuer des correctifs et des mises à niveau périodiques du logiciel VMware tout au long du cycle de vie d'une instance vCenter Server. Ceci inclut la mise à niveau du logiciel VMware SDDC vers une version prise en charge par l'automatisation {{site.data.keyword.vmwaresolutions_short}} au besoin.

La procédure suivante décrit les étapes nécessaires pour convertir une instance vCenter Server basée sur VMware vSphere 6.5 en une instance vCenter Server basée sur VMware vSphere 6.7. Ces étapes correspondent à la mise à niveau initiale vers le dernier niveau 6.7 de vSphere, NSX et vSAN. Après cette mise à niveau, vous devrez peut-être utiliser la fonctionnalité vSphere normale pour actualiser les niveaux matériels et outils de la machine virtuelle.

vCenter Server est conçu pour permettre une mise à niveau "en continu". En d'autres termes, les charges de travail des machines virtuelles qui fonctionnent actuellement continuent à fonctionner sans interruption si vous suivez la procédure suivante. Les entreprises doivent faire appel à leurs politiques de gestion du changement pour permettre une mise à niveau structurée et communiquée et planifier les mesures d'urgence. Cependant, pendant le processus de mise à niveau de certaines fonctions de gestion, telles que vCenter et le gestionnaire NSX, il est possible que des interruptions temporaires des fonctions de gestion se produisent, ainsi que des changements de configuration ou la mise hors tension et sous tension des machines virtuelles.
{:note}

## Avant de commencer
{: #vc_vsphere_upgrade-prereq}

Le temps estimé pour effectuer la mise à niveau est variable. Il est possible que plusieurs fenêtres de maintenance soient nécessaires pour mettre complètement à jour un environnement. L'exécution des versions de niveau supérieur et inférieur du logiciel SDDC est prise en charge par VMware pendant le processus de mise à niveau. Cependant, certaines fonctions telles que vMotion, peuvent être limitées pendant ce processus.

Effectuez les étapes suivantes avant de commencer la mise à niveau :  
* Il est de votre responsabilité de mettre à niveau toute extension ou snap-in dans l'environnement vCenter Server. Consultez la documentation suivante avant de planifier votre mise à niveau :
  * [Notes sur l'édition de la version VMware vCenter Server 6.7, mise à jour 1b](https://docs.vmware.com/en/VMware-vSphere/6.7/rn/vsphere-vcenter-server-67u1b-release-notes.html){:new_window}
  * [A propos de la mise à niveau de VMware ESXi](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.upgrade.doc/GUID-65B5B313-3DBB-4490-82D2-A225446F4C99.html){:new_window}
* Configurez vSphere Update Manager (VUM) dans votre instance vCenter Server pour télécharger les dernières mises à jour de VMware vSphere. Pour plus d'informations, voir [Introduction à VMware Update Manager](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vum-intro#vum-intro).
*	Ouvrez un ticket d'assistance avec l'équipe {{site.data.keyword.vmwaresolutions_short}} pour les informer qu'une mise à niveau est en cours. Le ticket reste ouvert jusqu'à ce que l'instance soit enregistrée au niveau supérieur dans la console {{site.data.keyword.vmwaresolutions_short}}.
* Confirmez si l'instance vCenter Server que vous mettez à niveau est liée ou non à une autre instance vCenter Server comme instance principale ou secondaire dans la console {{site.data.keyword.vmwaresolutions_short}}. Toutes les instances liées doivent avoir leurs contrôleurs de services de plateforme (PSC) mis à niveau en premier dans le cadre d'une mise à niveau de site particulière.
* Confirmez ce qui suit pour les instances basées sur vSAN :
  * Assurez-vous que l'outil vSAN Health est activé et ne signale aucune erreur critique. Si des erreurs critiques sont présentes, contactez l'équipe de support IBM en indiquant l'ID du ticket de support de mise à niveau.
  * Assurez-vous qu'il y a suffisamment d'espace sur chaque noeud pour gérer la reconstruction de la redondance des objets vSAN dans le cas où un hôte ESXi ne redémarrerait pas lors de la mise à niveau. Vous devrez peut-être réduire l'utilisation du disque ou ajouter un hôte ESXi supplémentaire avant la mise à niveau.  
  * Vérifiez si le volume total du vSAN est utilisé à plus de 70 %. Vous devrez peut-être réduire l'utilisation du disque ou ajouter un hôte ESXi supplémentaire avant la mise à niveau.
* Si votre instance vCenter Server a démarré en tant que {{site.data.keyword.vmwaresolutions_short}} V2.5 ou une version ultérieure, contactez le support IBM pour obtenir le mot de passe de l'ID utilisateur **root** pour le PSC et vCenter car seul un compte de services possédant un accès **customerRoot** est visible sur le portail. Si l'ID utilisateur **root** de PSC et vCenter est visible avec son mot de passe, alors cette étape n'est pas nécessaire.
* Confirmez que vous disposez d'un ID utilisateur dans https://my.vmware.com pour télécharger les binaires de mise à niveau requis. Si ce n'est pas le cas, contactez le support IBM en indiquant l'ID du ticket de support de mise à niveau.
* Confirmez que VUM est configuré pour accéder à https://www.vmware.com pour télécharger les correctifs. S'il ne peut pas être configuré en raison des politiques de sécurité, vous devez télécharger manuellement les derniers jeux de correctifs et les charger dans le VUM. Pour plus d'informations, voir [Introduction à VMware Update Manager](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro).

### Préparation de votre jumpbox
{: #vc_vsphere_upgrade-prereq-jumpbox}

Comme le VPN d'accès client {{site.data.keyword.cloud_notm}} est limité à 512 Kbps, il est recommandé soit de fournir une VSI (instance de serveur virtuel) {{site.data.keyword.cloud_notm}} pour Windows 2012-2016 Server, soit de configurer une machine virtuelle Windows similaire sur un environnement vSphere vCenter Server séparé dans le même {{site.data.keyword.CloudDataCent_notm}}. Ceci permettra de les utiliser comme jumpbox dans l'instance vCenter Server à mettre à niveau et permettra des téléchargements rapides depuis https://my.vmware.com pour les binaires. Bien qu'il soit possible de placer cette machine virtuelle sur l'instance vCenter Server en cours de mise à niveau, cela n'est pas recommandé.

Effectuez les étapes suivantes pour commander une jumpbox VSI.

Sautez la première étape si vous avez déjà une jumpbox VSI dans votre environnement.
{:note}

1. Commandez une VSI horaire ou mensuelle sur le [portail client de l'infrastructure IBM Cloud](https://control.softlayer.com/). Commandez les attributs suivants :
  * Windows 2012 ou 2016 Server Standard
  * 2 unités centrales
  * 16 Go de mémoire
  * 100 G de disque
  * Liaisons montantes publiques et privées à 1 Gbits/s
2. Lorsque l'instance de serveur virtuel est fournie, configurez les listes de contrôle d'accès {{site.data.keyword.cloud_notm}} dans le panneau de contrôle pour autoriser toutes les entrées et sorties des liaisons privées et uniquement les sorties des liaisons publiques. Vous devez utiliser le VPN d'accès client {{site.data.keyword.cloud_notm}} pour les sessions RDP (Remote Desktop Protocol) dans l'instance de serveur virtuel Windows.
3. Effectuez une connexion RDP à l'instance de serveur virtuel Windows. Modifiez ses paramètres de système de noms de domaine (DNS) sur l'adaptateur de réseau privé pour ne pointer que vers le serveur Windows AD dans l'instance vCenter Server à mettre à niveau.
4. Téléchargez et installez le navigateur Google Chrome. Vous pouvez utiliser Mozilla Firefox, mais il a un problème de cache lors de l'utilisation des écrans VUM dans l'interface utilisateur de vCenter.
5. Téléchargez votre logiciel de terminal SSH préféré. Par exemple, Putty.
6. Utilisez Google Chrome pour accéder à l'instance vCenter Server à mettre à niveau. Utilisez **administrator@vsphere.local** et assurez-vous que vous pouvez voir l'interface utilisateur.  
7. Vérifiez que l'environnement vSphere ne contient pas d'erreurs ou de problèmes, comme indiqué dans la section précédente.
8. Utilisez votre logiciel de terminal SSH pour accéder au PSC et au vCenter avec le portail ou les mots de passe fournis par le support pour **root**.
9. Si vous le souhaitez, utilisez l'ID utilisateur et le mot de passe **root** notés dans le panneau de contrôle SL pour accéder à chaque hôte ESXi afin de vérifier le mot de passe **root**.

#### Téléchargement des fichiers binaires
{: #vc_vsphere_upgrade-prereq-jumpbox-binary}

Utilisez votre jumpbox VSI Windows et connectez-vous à votre compte https://my.vmware.com pour télécharger les binaires suivants :

*	Image VMware vSphere 6.7u1 Hypervisor (ESXi ISO) - Inclut les outils VMware
* ISO du dispositif vCenter 6.7u1b. Pas le bundle de mise à jour.
*	Bundle de mise à niveau de NSX pour vSphere 6.4.4

Pour les unités Intel Optane, téléchargez le fichier suivant pour l'utiliser dans le cadre du processus de correction après mise à niveau utilisé par VMware Update Manager.

Localisez le fichier ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` pour le pilote Intel NVMe pour Intel® Optane™ SSD DC P4800X Series SSDPED1K750GA (750 Go, HHHL) sur https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX67-INTEL-INTEL-NVME-VMD-1401016&productId=742.

#### Sauvegarde des composants

Avant de commencer la mise à niveau, sauvegardez chaque composant.

* Pour plus d'informations sur la sauvegarde de vCenter Server et des PSC, voir [Overview of Backup and Restore options in vCenter Server 6.x (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:new_window}.
* Pour lire les remarques additionnelles sur la sauvegarde de vCenter Server et des PSC, voir [Sauvegarde de niveau fichier vCenter](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup#solution_backingup-vcenter).
*	Pour obtenir des informations sur la sauvegarde NSX, voir [Backing Up NSX Manager Data](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window}.

Il est recommandé d'utiliser la sauvegarde de niveau fichier. La sauvegarde de niveau image (via vSphere Data Protection) n'est pas prise en charge dans VMware vSphere 6.7.{:note}

## Procédure de mise à niveau du logiciel IBM vCenter Server vSphere de 6.5 à 6.7
{: #vc_vsphere_upgrade-procedure}

Si vous rencontrez un problème à n'importe quel moment du processus de mise à niveau, utilisez le ticket de mise à niveau {{site.data.keyword.vmwaresolutions_short}} que vous avez ouvert au début du processus pour contacter le support IBM. Le support IBM ouvrira un ticket avec le support VMware si nécessaire.

**Important** :

* Vous devez utiliser ce chemin d'accès pour vous assurer que {{site.data.keyword.vmwaresolutions_short}} fournit au support VMware toutes les informations nécessaires sur la conception et la configuration de vCenter Server ainsi que sur {{site.data.keyword.cloud_notm}}. Si vous suivez ce processus pour vous assurer que des informations précises sont partagées avec le support VMware, la durée de l'assistance sera plus courte. Une fois que le support IBM fournit les informations nécessaires au support VMware, vous pouvez interagir directement avec le support VMware si nécessaire.
* Prenez soin de conserver une trace de tous les nouveaux mots de passe et de toutes les nouvelles données d'identification que vous créez dans le cadre de ce processus de mise à niveau. Le support IBM a besoin de ces données d'identification à la fin du processus de mise à niveau pour mettre à jour sa base de données interne. 

### Mise à niveau de VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx}

La mise à niveau de VMware NSX peut prendre un certain temps car le processus de mise à niveau met à jour les modules d'installation vSphere sur les hôtes ESXi et nécessite un redémarrage de chaque hôte. Planifiez votre fenêtre de maintenance en conséquence.

#### Avant de mettre à niveau VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-before}

* Si Zerto pour {{site.data.keyword.cloud_notm}} est installé sur votre environnement, utilisez l'interface utilisateur Zerto pour arrêter les machines virtuelles zVRA sur chaque hôte. Sélectionnez **allow Zerto to always enter hosts into maintenance mode during remediation** dans les paramètres du site Zerto de la section Policies de l'interface utilisateur de Zerto. Sinon, Zerto démarre le zVRA et empêche la mise à niveau en ne permettant pas à l'hôte ESXi mis à niveau de passer en mode maintenance.
* Si les machines virtuelles ne disposent pas d'outils VMware, arrêtez-les manuellement ou éteignez-les de force avant l'installation du module hôte NSX ESXi. Ces machines virtuelles empêchent l'hôte ESXi cible de passer en mode maintenance.

#### Procédure de mise à niveau de VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-procedure}

Pour obtenir plus de détails sur la procédure décrite ci-dessous, veuillez vous référer au [Guide de mise à niveau de NSX](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window}.

1. Lisez les notes sur l'édition de NSX 6.4.4.4 pour vous assurer de la compatibilité avec votre configuration d'environnement spécifique. Pour plus d'informations, voir [Notes sur l'édition de VMware NSX Data Center for vSphere 6.4.4](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}.
2. Mettez d'abord à niveau le gestionnaire NSX. Si vous avez plusieurs environnements NSX qui utilisent le mode "cross vCenter linked", mettez à niveau tous les gestionnaires NSX avant de mettre à niveau les composants dans le **coordinateur de mise à niveau** de l'interface utilisateur NSX.
3.	Utilisez le **Coordinateur de mise à jour** dans l'interface utilisateur de NSX au sein de l'interface utilisateur de vCenter pour mettre à jour les composants NSX.
4. Continuez à examiner et à surveiller l'interface utilisateur de la mise à niveau NSX dans l'interface utilisateur vCenter à mesure que les problèmes éventuels sont résolus pour vous assurer que la mise à niveau se poursuit jusqu'à ce que tous les composants soient mis à niveau.

### Mise à niveau du contrôleur de services de plateforme (PSC)
{: #vc_vsphere_upgrade-procedure-psc}

Si vous avez des instances liées à vCenter Server, vous devez mettre à niveau toutes les instances du PSC dans les sites principaux et secondaires de vCenter Server. Puisque les instances vCenter Server liées créent une topologie de réplication de PSC de type hub et spoke avec l'instance vCenter Server principale en tant que hub, il est recommandé de commencer par mettre à niveau le PSC de l'instance vCenter Server principale puis de mettre à niveau chaque PSC de site secondaire.

#### Avant de mettre à niveau le contrôleur de services de plateforme
{: #vc_vsphere_upgrade-procedure-psc-before}

* Préparez vos mots de passe root vCenter et PSC pour la procédure suivante. Utilisez la console {{site.data.keyword.vmwaresolutions_short}} pour noter si la version de votre instance de vCenter Server a été ou non mise à niveau de la version 2.4 ou d'une version antérieure à la version 2.7 ou à une version ultérieure.
* Sur la console {{site.data.keyword.vmwaresolutions_short}}, un seul mot de passe s'affiche pour root pour le PSC et vCenter. Cependant, il ne s'agit que du mot de passe vCenter. Vous devez contacter le support pour obtenir le mot de passe root de PSC.
* Pour éviter les conflits, utilisez l'adresse IP qui figure dans la partie supérieure du sous-réseau utilisé actuellement par vCenter et le PSC. Vous devez utiliser une adresse IP temporaire pour le déploiement du nouveau dispositif.

#### Procédure de mise à niveau du contrôleur de services de plateforme
{: #vc_vsphere_upgrade-procedure-psc-procedure}

1. Connectez-vous à la fois à l'interface utilisateur PSC, ``https://<psc-fqdn>:5480``, et à l'interface de gestion des dispositifs vCenter pour confirmer si le mot de passe root a expiré ou pas. Si la date d'expiration du mot de passe est **1970** alors il a expiré et vous devez activer SSH et l'interpréteur de commandes bash dans l'interface utilisateur de gestion des dispositifs PSC.
    1. Effectuez une connexion SSH dans PSC avec l'ID et le mot de passe root. Même si le mot de passe est expiré, il vous permet de vous connecter.
    2. Utilisez la commande shell **passwd** pour définir un nouveau mot de passe root pour le PSC et vCenter.
    3. Sauvegardez les mots de passe qui ont été affichés sur la console {{site.data.keyword.vmwaresolutions_short}} ou qui vous ont été fournis par le support IBM. Ces mots de passe seront réutilisés ultérieurement lors de la mise à niveau des dispositifs.
2. Utilisez la fonction de montage d'ISO intégrée de Windows pour monter l'ISO de vCenter 6.7u1b dans votre jumpbox.
3. Suivez d'abord les instructions VMware pour mettre à niveau tous les PSC. Pour plus d'informations, voir la publication suivante : [Mettre à niveau une instance de vCenter Server Appliance 6.0 ou 6.5 avec vCenter Single Sign-On externe ou une instance de Platform Services Controller au moyen de l'interface utilisateur graphique](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html).

Cette publication indique que **Vous devez exécuter la mise à niveau de l'interface utilisateur graphique depuis une machine Windows, Linux ou Mac située sur le même réseau que le dispositif à mettre à niveau**. Ces instructions s'appliquent à tous les sous-réseaux compris dans votre {{site.data.keyword.cloud_notm}} dans votre compte.
{:note}

Il est recommandé d'utiliser vCenter comme source et cible pour la mise à niveau.

### Mise à niveau de vCenter
{: #vc_vsphere_upgrade-procedure-vcenter}

Pour les instances liées à vCenter Server, bien qu'il soit recommandé de mettre à niveau toutes les instances vCenter dans les sites principaux et secondaires de vCenter Server, cela n'est pas obligatoire.

#### Avant de mettre à niveau vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-before}

* Préparez vos mots de passe root vCenter et PSC pour la procédure suivante. Utilisez la console {{site.data.keyword.vmwaresolutions_short}} pour noter si la version de votre instance de vCenter Server a été ou non mise à niveau de la version 2.4 ou d'une version antérieure à la version 2.7 ou à une version ultérieure.
* Pour éviter les conflits, utilisez l'adresse IP qui figure dans la partie supérieure du sous-réseau utilisé actuellement par vCenter et le PSC. Vous devez utiliser une adresse IP temporaire pour le déploiement du nouveau dispositif.

#### Procédure de mise à niveau de vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-procedure}

1. Connectez-vous à la fois à l'interface utilisateur PSC, ``https://<psc-fqdn>:5480``, et à l'interface de gestion des dispositifs vCenter pour confirmer si le mot de passe root a expiré ou pas. Si la date d'expiration du mot de passe est **1970** alors il a expiré et vous devez activer SSH et l'interpréteur de commandes bash dans l'interface utilisateur de gestion des dispositifs PSC.
    1. Effectuez une connexion SSH dans PSC avec l'ID et le mot de passe root. Même si le mot de passe est expiré, il vous permet de vous connecter.
    2. Utilisez la commande shell **passwd** pour définir un nouveau mot de passe root pour le PSC et vCenter.
    3. Sauvegardez les mots de passe qui ont été affichés sur la console {{site.data.keyword.vmwaresolutions_short}} ou qui vous ont été fournis par le support IBM. Ces mots de passe seront réutilisés ultérieurement lors de la mise à niveau des dispositifs.
2. Utilisez la fonction de montage d'ISO intégrée de Windows pour monter l'ISO de vCenter 6.7u1b dans votre jumpbox.
3. Suivez les instructions VMware pour mettre à niveau vCenter. Pour plus d'informations, voir la publication suivante : [Mettre à niveau une instance de vCenter Server Appliance 6.0 ou 6.5 avec vCenter Single Sign-On externe ou une instance de Platform Services Controller au moyen de l'interface utilisateur graphique](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html). Les instructions VMware ressemblent à celles relatives au processus de mise à niveau de PSC. Toutefois, au lieu de pointer vers le PSC, vous pointez vers le FQDN/l'adresse IP vCenter pour le processus de mise à niveau. 

**Remarques** :
* Cette publication indique que **Vous devez exécuter la mise à niveau de l'interface utilisateur graphique depuis une machine Windows, Linux ou Mac située sur le même réseau que le dispositif à mettre à niveau**. Ces instructions s'appliquent à tous les sous-réseaux compris dans votre {{site.data.keyword.cloud_notm}} dans votre compte.
* Il est recommandé d'utiliser vCenter comme source et cible pour la mise à niveau.

#### Consolidation de la fonction PSC dans vCenter

1. Une fois la mise à niveau du PSC et de vCenter terminée, connectez-vous à l'interface utilisateur vCenter FLEX et vérifiez l'état de tous les services liés au vCenter et au PSC dans la section **Configuration système**.  
2. Sauvegardez votre PSC.  Il est recommandé d'utiliser la sauvegarde de niveau fichier. Pour plus d'informations, voir [File based backup in vSphere 6.7](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-8A16C037-F1E0-40C9-B106-05C30625B9CB.html){:new_window}.
3. Accédez au répertoire ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\converge``.
4. Copiez le fichier ``converge.json`` dans une unité locale de votre machine virtuelle de rebond.
  * S'il s'agit du premier PSC que vous consolidez, vous devez supprimer la section **replication** du fichier ``json``.
  * S'il s'agit d'un PSC lié ultérieurement, vous devez remplir les attributs demandés dans la section **replication** du fichier ``json``.
5. Accédez au répertoire ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\decommission``.
6. Copiez le fichier ``decommission_psc.json`` vers une unité locale de votre machine virtuelle de rebond.
7. Editez les fichiers ``converge.json`` et ``decommission_psc.json``. Les fichiers ``json`` contiennent des instructions sur les zones à modifier. Il est recommandé d'utiliser l'hôte ESXi contenant le PSC plutôt que vCenter dans la section **managing_esxi_or_vc**.
8. Accédez au répertoire ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` dans la fenêtre de commande.
9. Exécutez le fichier ``vcsa-util.exe`` avec le commutateur **converge** et le chemin d'accès au fichier ``converge.json`` modifié précédemment. Par exemple, ``vcsa-util converge --no-ssl-certificate-verification c:\temp\converge.json -v``.
   1. Tapez **Y** pour confirmer que le PSC a été sauvegardé pour continuer.
   2. Lorsque le processus est terminé, entrez **Y** pour confirmer le redémarrage de vCenter.

   Si le processus de convergence échoue avec le message ``ERROR converge Failed to get vecs users and permissions``, voir [Converge to embedded failed!](https://virtualtassie.com/2018/vcenter-6-7-update-1-converge-to-embedded-failed/#comment-3713){:new_window} pour prendre connaissance des étapes permettant de résoudre l'erreur.
   {:note}

10. Une fois que vCenter a été redémarré, vérifiez que tout fonctionne normalement en vous connectant à l'interface utilisateur de vCenter.
11. Accédez au répertoire ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` dans la fenêtre de commande.
12. Exécutez le fichier ``vcsa-util.exe`` avec le commutateur **decommission** et le chemin d'accès au fichier ``decommission_psc.json`` édité précédemment. Par exemple, ``vcsa-util decommission --no-ssl-certificate-verification c:\temp\decommission_psc.json -v``.
13.	Une fois la commande terminée avec succès, connectez-vous à l'interface utilisateur vCenter flex et vérifiez que le dispositif vCenter est le seul listé dans les environnements non liés et que tous les services sont sains.
14. Supprimez l'ancien PSC, vCenter et les machines virtuelles consolidées non utilisées du PSC.
15. Renommez le vCenter Server dans l'interface utilisateur vCenter en **<nom_instance>_vc_separate**. Par exemple, si le nom de votre instance vCenter Server est **production**, alors le nom de l'interface utilisateur de vCenter est **production_vc_separate**. Ceci est nécessaire pour que l'automatisation puisse reprendre son fonctionnement pour cette instance vCenter Server.  

### Mise à niveau des hôtes ESXi
{: #vc_vsphere_upgrade-procedure-esxi}

La fonction VMware Update Manager de vCenter est utilisée pour mettre à niveau et corriger les hôtes ESXi au niveau 6.7u1. Comme dans la section de mise à niveau de NSX de ce document, toute machine virtuelle qui ne peut effectuer une vMotion vers un autre hôte doit être arrêtée sans problème, sinon, cela peut entraîner le blocage du processus de mise à niveau.{:note}

#### Téléchargement de l'ISO ESXi dans VUM
{: #vc_vsphere_upgrade-procedure-esxi-iso}

1. Vérifiez que VUM est configuré pour télécharger les correctifs de la page https://www.vmware.com. Pour plus d'informations, voir [Introduction à VMware Update Manager](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro#vmware-update-manager-introduction).
2. Utilisez Flex ou HTML pour ouvrir l'interface utilisateur de vCenter et accédez à la **vue d'administrateur de VUM**.
3. Dans la **vue d'administrateur de VUM**, sélectionnez l'onglet **ESXi Images** et sélectionnez **Import ESXi Images**.
4. Accédez à l'image **ESXi 6.7u1iso** qui a été téléchargée de VMware et importez-la dans le référentiel VUM.

#### Procédure de mise à niveau des hôtes ESXi
{: #vc_vsphere_upgrade-procedure-esxi-upgrade}

1. Dans l'interface utilisateur de vCenter, accédez au cluster contenant les hôtes ESXi à mettre à niveau.
2. Cliquez sur l'onglet **updates** dans le panneau de navigation. Accédez aux mises à jour d'hôte, puis cliquez sur **Attach**.
3. Sélectionnez la base de référence (image ISO pour mise à niveau ESXi) que vous avez téléchargée dans VUM et cliquez sur **Remediate**.
4. Acceptez le contrat de licence de l'utilisateur final et cliquez sur **OK**.
5. Passez en revue les hôtes qui doivent être résolus et confirmez les résultats de la vérification avant résolution. 

   Vous devez déconnecter les CD ou les DVD connectés aux machines virtuelles sinon l'hôte qui contient cette machine virtuelle n'est pas autorisé à entrer en mode maintenance.
   {:note}

6. Une fois que la vérification avant résolution a abouti, cliquez sur **Remediate**. Surveillez le processus de mise à niveau avec la tâche d'entité remediate.
7. Une fois la mise à niveau terminée, examinez la section récapitulative de l'hôte pour vérifier que ``VMware ESXi, 6.7.0`` s'affiche bien. 

Si le processus de mise à niveau échoue immédiatement et affiche le message d'erreur **host cannot enter maintenance mode** arrêtez les machines virtuelles ZVRA Zerto et réessayez. Les machines virtuelles ZVRA démarrent automatiquement lorsque chaque serveur sort de la résolution. Pour obtenir des informations sur la poursuite de la réplication Zerto pendant le processus de mise à niveau, voir [How to Place a Host with an Associated VRA into Maintenance Mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/){:new_window}.
{:note}

#### Ajout du correctif du pilote Intel NVME au référentiel VUM
{: #vc_vsphere_upgrade-procedure-esxi-nvme}

Comme décrit dans la section relative aux téléchargements de binaires, vous devez importer le contenu du fichier ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` dans le référentiel. Il est ensuite appliqué dans la section suivante en tant qu'extension d'hôte ESXi non critique.

1. Extrayez le fichier ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` vers une unité locale de votre machine virtuelle de rebond.
2. Utilisez Flex ou HTML pour ouvrir l'interface utilisateur de vCenter et accédez à la **vue d'administrateur de VUM**.
3. Dans la **vue d'administrateur de VUM**, sélectionnez l'onglet **Patch Repository** et sélectionnez **Import Patches**.
4. Parcourez le contenu extrait du répertoire ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` et sélectionnez le fichier ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-offline_bundle-8733247.zip``. Le fichier s'importe immédiatement dans le référentiel VUM.

Localisez l'image dans le référentiel de correctifs en tant qu'une extension d'hôte **importante**.

#### Correction des hôtes ESXi
{: #vc_vsphere_upgrade-procedure-esxi-patch}

Après la mise à niveau, il est recommandé d'appliquer tous les correctifs d'hôtes ESXi critiques et non critiques.

1. Dans l'interface utilisateur de vCenter, sélectionnez le cluster contenant les hôtes auxquels un correctif doit être appliqué. 
2. Cliquez sur l'onglet **updates** dans le panneau de navigation et sélectionnez l'onglet **Host Updates**. Sélectionnez **Critical Host Patches (Predefined)**. Répétez la procédure pour mettre à niveau les hôtes ESXi. 
3. Cliquez sur l'onglet **updates** dans le panneau de navigation et sélectionnez l'onglet **Host Updates**. Sélectionnez **Non-Critical Host Patches (Predefined)**. Répétez la procédure pour mettre à niveau les hôtes ESXi. 

Vous devrez peut-être arrêter à nouveau les machines virtuelles zVRA Zerto dans le cadre de ce processus.{:note}

### Mise à niveau des éléments additionnels
{: #vc_vsphere_upgrade-procedure-addtl}

#### Mise à niveau de la version de format de disque vSAN
{: #vc_vsphere_upgrade-procedure-addtl-vsan}

Mise à niveau de la version du format de disque vSAN à la version 7.

1. Accédez au cluster contenant le vSAN à mettre à jour dans l'interface utilisateur de vCenter.
2. Dans l'objet du cluster, sélectionnez **Configuration > vSAN > General**.
3. Cliquez sur **Pre-check Upgrade** pour vérifier la comptabilité de la mise à niveau et détecter d'éventuels problèmes. Attendez que la vérification renvoie le message **Ready to upgrade...**
4. Cliquez sur **Upgrade**. Comme la mise à niveau traite un groupe de disques à la fois, elle peut prendre un certain temps selon la taille du cluster. Si vous le souhaitez, vous pouvez sélectionner **reduced redundancy** durant le processus. Bien que cette opération puisse réduire considérablement la durée de la mise à niveau, elle peut entraîner une perte de données en cas de défaillance d'un disque pendant le processus de mise à niveau.

#### Mise à niveau du commutateur distribué virtuel
{: #vc_vsphere_upgrade-procedure-addtl-vds}

La mise à niveau du commutateur distribué virtuel (VDS) vers la version 6.6.0 améliore également le contrôle des E/S réseau et ajoute la prise en charge améliorée du protocole LACP (Link Aggregation Control Protocol).

1.	Si vous avez déployé HCX, vous devez annuler le déploiement de la portion Cloud Gateway de HCX avant de mettre à niveau le VDS sur lequel il réside. Assurez-vous que HCX est mis à jour vers la dernière version avant de redéployer la passerelle Cloud Gateway.
2.	Dans l'interface utilisateur de vCenter, accédez à l'onglet **Network**.
3.	Avec le bouton droit de la souris, cliquez sur le commutateur distribué à mettre à niveau (**SDDC-Dswitch-Private** ou **SDDC-Dswitch-Public**) et sélectionnez **Upgrade Distributed Switch**.

#### Mise à niveau des extensions et des plug-in de l'interface utilisateur de vCenter
{: #vc_vsphere_upgrade-procedure-addtl-extension}

Il est de votre responsabilité de mettre à niveau toute extension ou snap-in dans l'environnement vCenter Server. Dans l'interface utilisateur de vCenter, cliquez sur **Home > Administration > Solutions** pour afficher le statut et activer ou désactiver les extensions et les plug-ins de vCenter.

#### Mise à niveau des outils VMware
{: #vc_vsphere_upgrade-procedure-addtl-tools}

Utilisez l'interface utilisateur de vCenter pour effectuer les mises à niveau des outils invités VMware. Certains outils VMware peuvent être requis sur certaines machines virtuelles plus anciennes qui ont été migrées dans l'environnement vCenter Server.  

#### Mise à niveau du niveau matériel des machines virtuelles
{: #vc_vsphere_upgrade-procedure-addtl-vmhw}

Comme pour les outils invités VMware, une mise à niveau de l'environnement vCenter Server peut avoir pour effet que les anciennes machines virtuelles ne soient pas prises en charge à leur niveau matériel actuel. Utilisez l'interface utilisateur de vCenter pour trouver et mettre à jour ces machines virtuelles si nécessaire.  

#### Configuration du mode EVC (Enhanced vMotion Compatibility) sur Intel Skylake
{: #vc_vsphere_upgrade-procedure-addtl-evc}

Vous pouvez définir des hôtes avec la génération Intel Skylake pour un cluster en mode EVC (Enhanced vMotion Compatibility) Skylake après la mise à niveau. Procédez comme suit pour mettre à jour le mode EVC :

1. A partir du cluster contenant des hôtes, cliquez sur **configure**.
2. A partir de **VMware EVC**, cliquez sur **Edit** et remplacez le mode EVC par **Intel "Skylake" Generation**.

Pour plus d'informations, voir [Enhanced vMotion Compatibility (EVC) processor support (1003212)](https://kb.vmware.com/s/article/1003212){:new_window}.

#### Reconfiguration du gestionnaire NSX et du gestionnaire HCX pour qu'ils pointent vers le PSC

1. A partir d'un navigateur Web, accédez à l'interface utilisateur du gestionnaire NSX (``https://<nsx-manager-ip>`` ou ``https://<nsx-manager-hostname>``). Connectez-vous à l'aide de vos données d'identification. 
2. Sur la page d'accueil, cliquez sur **Manage vCenter Registration**.
3. Editez la zone **Lookup Service URL** pour que son contenu pointe vers l'adresse IP vCenter. La version autonome intégrée de PSC **n'existe plus**. 

## Résultats de la mise à niveau du logiciel vCenter Server vSphere
{: #vc_vsphere_upgrade-results}

Une fois votre mise à niveau terminée, l'exécution du bilan de santé du vSAN peut faire apparaître des avertissements concernant les mises à jour du firmware pour les contrôleurs RAID et réseau fournis par IBM Cloud. Une fois que vous avez déterminé les hôtes qui ont besoin de mises à jour du firmware, ouvrez un ticket auprès du support IBM pour que le firmware soit mis à jour vers les versions recommandées.

1. Dans l'interface utilisateur de vCenter, sélectionnez le cluster contenant le vSAN avec l'état de santé à vérifier.
2. Sélectionnez l'onglet **Monitor** puis l'onglet **vSAN** .
3. Sélectionnez **Health** et notez les avertissements qui s'affichent.
4. Si un avertissement de **compatibilité matérielle** s'affiche, développez l'avertissement et cliquez sur le message **Controller Firmware is VMware certified** s'il affiche un état d'avertissement.
5. Notez les hôtes qui apparaissent dans la liste avec des recommandations de mise à jour du firmware.
6. Ouvrez un ticket auprès du support IBM pour programmer une heure de mise hors service de chaque hôte afin de permettre les mises à jour du firmware.

Lorsque votre mise à niveau est terminée, mettez à jour votre ticket de support avec le support IBM. Fournissez les nouveaux mots de passe que vous avez créés dans le cadre du processus de mise à niveau. Par exemple, fournissez des mots de passe pour déployer des services de gestion de dispositif PSC et vCenter dans le ticket de demande de service. Le support IBM met ensuite à jour la console et la base de données interne {{site.data.keyword.vmwaresolutions_short}} pour reprendre l'automatisation {{site.data.keyword.vmwaresolutions_short}} au niveau 6.7. Cela inclut l'ajout et la suppression de services, d'hôtes, de clusters et d'instances vCenter Server secondaires.

## Liens connexes
{: #vc_vsphere_upgrade-related}

* [Notes sur l'édition de VMware NSX Data Center for vSphere 6.4.4](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}
* [Guide de mise à niveau de NSX](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window}
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
