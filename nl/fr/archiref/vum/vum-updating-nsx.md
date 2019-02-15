---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Mise à jour de NSX

Les informations suivantes sont un exemple de la procédure de mise à jour de la passerelle. Reportez-vous au guide VMware du processus de mise à jour correspondant à la version NSX vers laquelle vous effectuez la mise à niveau.

Si vous devez mettre à niveau NSX et vSphere, VMware recommande d'exécuter d'abord la mise à niveau de NSX, puis la mise à niveau de vSphere car les bundles VIB NSX sont spécifiques à la version ESXi qui est installée sur l'hôte. Cependant, il est recommandé d'utiliser VUM, comme indiqué dans ce document. Si vous effectuez la mise à niveau manuellement, utilisez le workflow suivant, un hôte à la fois :

1. **Mise à niveau de ESXi** - Une fois la mise à niveau d'ESXi terminée, l'hôte quitte le mode maintenance, mais vous ne pouvez pas déplacer les machines virtuelles connectées aux commutateurs logiques sur l'hôte tant que l'étape suivante n'est pas terminée.
2. **Mise à niveau des VIB NSX** - Lorsque les bundles VIB sont mis à niveau et que l'hôte a été retiré du mode maintenance, vous pouvez déplacer les machines virtuelles connectées aux commutateurs logiques sur l'hôte.

NSX est mis à jour en effectuant la mise à jour de NSX Manager à l'aide d'un téléchargement depuis _my.vmware.com_. Par conséquent, vous devez disposer d'un compte pour télécharger la mise à jour. Si vous consommez une licence d'abonnement à {{site.data.keyword.cloud}} avec votre instance VMware vCenter Server on {{site.data.keyword.cloud_notm}}, vous ne pourrez pas télécharger les mises à jour avec votre compte **my.vmware.com**. Il vous faudra donc [contacter le support IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html).

Avant de commencer la mise à niveau, consultez les notes relatives à NSX sur les problèmes de mise à niveau et les solutions. A l'aide de ces notes, vérifiez que vCenter satisfait à la nouvelle configuration système requise pour NSX.

Si vous avez installé d'autres logiciels provenant de partenaires commerciaux VMware, consultez la documentation de ces partenaires pour obtenir les détails de compatibilité et de mise à niveau. Si vous avez déployé des instances principales et secondaires de vCenter Server et que vous disposez d'un environnement cross-vCenter NSX, consultez les notes sur l'édition pour obtenir le processus de mise à niveau adéquat.

Dans un environnement cross-vCenter NSX, le dispositif NSX Manager principal est mis à niveau en premier, suivi de tous les dispositifs NSX Manager secondaires.
**Les rétromigrations ne sont pas prises en charge**, donc veillez à effectuer une sauvegarde de NSX Manager avant de procéder à une mise à niveau. Toutes les configurations de NSX Edge, les routeurs logiques et les passerelles ESG (Edge Services Gateway) sont sauvegardés dans le cadre de la sauvegarde de NSX Manager.

Une fois NSX Manager mis à niveau, il est impossible d'effectuer une rétromigration de NSX. Il est conseillé d'effectuer toutes les activités de maintenance dans une fenêtre de maintenance agréée, par conséquent, suivez les conseils de votre entreprise. Il est recommandé de mettre à niveau tous les composants NSX dans une seule fenêtre d'indisponibilité pour minimiser la durée d'immobilisation et réduire les dysfonctionnements. Le processus de mise à niveau de NSX peut prendre un certain temps, donc il est important de comprendre l'ordre à respecter dans la mise à niveau du déploiement NSX :
* NSX Manager
* Cluster de contrôleurs NSX
* Cluster d'hôtes NSX
* Les passerelles ESG (Edge Services Gateway) peuvent être mises à niveau à tout moment après la mise à niveau de NSX Manager
* Guest Introspection (si vous l'utilisez, suivez les instructions indiquées dans les notes sur l'édition)

Le workflow se présente comme suit :
1. Connectez-vous à votre serveur intermédiaire et ouvrez un navigateur.
2. A l'aide de vos données d'identification pour _my.vmware.com_, accédez à la section de téléchargement et recherchez _NSX for vSphere_.
3. Sélectionnez la version dont vous avez besoin.
4. Sur la page de téléchargement, sélectionnez **Upgrade Bundle, Download Now**.
5. Téléchargez un dossier approprié.
6. **Mettez à niveau NSX Manager**:
  - Connectez-vous à NSX Manager Virtual Appliance, en utilisant l'adresse IP et les données d'identification documentées dans la console IC4VS, et cliquez sur le bouton Upgrade sur la page d'accueil.
  - Connectez-vous à NSX Manager.
  - Sous **Appliance Management**, cliquez sur **Backups & Restore**.
  - Cliquez sur Backup et entrez le nom de fichier approprié. Vmware recommande de réinstaller le dispositif NSX Manager avant de restaurer les données du ce dernier. Alors qu'une opération de restauration sur un dispositif NSX Manager existant peut fonctionner, elle n'est pas prise en charge officiellement. La meilleure pratique consiste à noter les paramètres d'adresse IP du dispositif NSX Manager afin de pouvoir les utiliser pour indiquer les informations d'adresse IP et d'emplacement de sauvegarde pour le dispositif NSX Manager qui vient d'être déployé.
  - En haut à droite, cliquez sur **Upload Bundle** et chargez le fichier que vous avez téléchargé depuis _my.vmware.com_.
  - Lisez les informations de mise à niveau et sélectionnez si vous voulez activer SSH et participer au programme d'amélioration de l'expérience client de VMware.
  - Cliquez sur **Upgrade**.
  - Une fois le chargement terminé, vous êtes redirigé vers la page de connexion de NSX Manager. Reconnectez-vous et vérifiez que la version actuelle du logiciel affichée est correcte.
7. **Mettez à niveau le cluster de contrôleurs NSX** :
  - Ouvrez vSphere Web Client et connectez-vous au dispositif VCSA.
  - Accédez à **Home** > **Networking & Security** > **Installation**, sélectionnez l'onglet **Management** et cliquez sur **Upgrade Available** dans la colonne Controller Cluster Status.
  - Les contrôleurs figurant dans votre environnement sont mis à niveau et redémarrés un par un. Dès que vous avez initié la mise à niveau, le système télécharge le fichier de mise à niveau, procède à la mise à niveau, puis au redémarrage de chaque contrôleur et met à jour du statut de mise à niveau de chaque contrôleur.
8. **Mettez à niveau les clusters d'hôtes NSX** :
  - Après avoir mis à niveau NSX Manager et les contrôleurs NSX, les clusters d'hôtes sont mis à jour dans les bundles VIB NSX sur les hôtes vSphere ESXi.
  - Dans vSphere Web Client, accédez à **Home** > **Networking & Security** > **Installation**, sélectionnez l'onglet **Host Preparation**. Pour chaque cluster à mettre à niveau, cliquez sur **Upgrade available**. Le statut d'installation affiche Installing.
  - Le statut d'installation du cluster affiche _Not Ready_. Cliquez sur **Not Ready** pour en savoir plus et cliquez sur **Resolve all** pour essayer de terminer l'installation des bundles VIB. L'hôte est mis en mode maintenance et redémarré si nécessaire, pour finaliser la mise à niveau. La colonne Installation Status affiche Installing. Une fois la mise à niveau terminée, cette colonne affiche une coche verte et la version NSX mise à niveau.
9. **Passerelles ESG (Edge Services Gateway)** :
  - Lors du processus de mise à niveau, un nouveau dispositif virtuel Edge est déployé en même temps que le dispositif existant. Lorsque ce nouveau dispositif Edge est prêt, les cartes réseau virtuelles (vNIC) de l'ancien dispositif sont déconnectées et celles du nouveau dispositif sont connectées. Le nouveau dispositif Edge envoie ensuite des paquets ARP gratuits (GARP) pour mettre à jour le cache ARP des commutateurs connectés. Lorsque la haute disponibilité (HA) est déployée, le processus de mise à niveau est exécuté deux fois. Ce processus peut affecter temporairement le transfert de paquets.
  - Dans vSphere Web Client, sélectionnez **Networking & Security** > **NSX Edges**. Pour chaque instance NSX Edge, sélectionnez **Upgrade Version** dans le menu **Actions**.
  - Lorsque la mise à niveau de NSX Edge a abouti, le statut passe à Deployed et la colonne Version affiche la nouvelle version de NSX. Si un dispositif Edge ne parvient pas à se mettre à niveau et n'est pas restauré à son ancienne version, cliquez sur l'icône **Redeploy NSX Edge** et relancez la mise à niveau.

### Liens connexes

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (démonstrations)
