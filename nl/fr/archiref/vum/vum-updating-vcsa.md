---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

# Mise à jour de dispositif VCSA et instances vCenter liées à SSO

## Mise à jour PSC et VCSA 

Cette section fait référence à la fois à vCentre Server Appliance (VCSA) et Platform Services Controller (PSC). Les deux dispositifs sont des dispositifs VCSA mais avec des rôles différents. Lors de la mise à niveau de vSphere avec un contrôleur PSC externe, mettez d'abord à niveau le contrôleur PSC, puis les dispositifs VCSA, puis les hôtes ESXi et enfin les versions matérielles et VMware Tools sur les machines virtuelles.

VUM ne met pas à jour PSC/VCSA. Les informations suivantes présentent le processus de mise à jour de ces dispositifs. Les dispositifs PSC/VCSA déployés dans une instance VMware vCenter Server on {{site.data.keyword.cloud}} n'ont pas d'accès à Internet, par conséquent, le bundle de mise à jour doit être d'abord téléchargé sur un serveur intermédiaire.

Les dispositifs PSC/VCSA sont mis à jour via la console de gestion du dispositif, et non pas via vSphere Web Client. La console de gestion des dispositifs PSC/VCSA est accessible en utilisant un navigateur, l'adresse IP de PSC/VCSA et le port 5480.

Vous devez prendre une image instantanée du dispositif ou effectuer une sauvegarde de PSC/VCSA avant de procéder à la mise à jour. Vérifiez que tout fonctionne comme prévu, puis supprimez l'image instantanée au bout de quelques jours pour éviter une dégradation des performances. Passez également en revue les notes sur l'édition de VMware avant d'essayer de procéder à une mise à niveau afin de prendre connaissance des instructions spécifique à une édition donnée.

Pour mettre à jour les dispositifs PSC/VCSA, procédez comme suit :
1. Vous pouvez télécharger des mises à jour en accédant au [centre de téléchargement](https://my.vmware.com/group/vmware/patch#search) des correctifs de VMware, en vous connectant et en choisissant VC dans le menu **Search by Product**. Sélectionnez le correctif approprié et cliquez sur **Download**.
2. A l'aide de vSphere Web Client, transférez le fichier ISO vers le référentiel du magasin de données vCenter.
3. Montez le fichier ISO de mise à jour sur le serveur vCenter.
4. Prenez une image instantanée de votre serveur vCenter.
5. Connectez-vous à la console de gestion du dispositif vCenter à l'adresse suivante :
`https://pscip:5480` (pour PSC) ou `https://vcenterip:5480` (pour VCSA)
6. Accédez à la section **Update** et sélectionnez **Check Updates** puis sur **Check CDROM**. La mise à jour est répertoriée.
7. Sélectionnez **Install Updates** et **Accept** pour accepter le contrat de licence d'utilisateur final (EULA ou CLUF). L'installation de la mise à jour commence.
8. Une fois la mise à jour terminée, vous devez revenir à la console de gestion du dispositif et sélectionnez l'option de redémarrage de la console.
9. Reconnectez-vous à vSphere Web Client et recherchez les erreurs éventuelles. Exécutez une analyse manuelle de VUM, **Home** > **Hosts and Clusters**, sélectionnez ensuite un centre de données ou un cluster, puis cliquez sur l'onglet **Update Manager**, puis sur **Scan for Updates**. Si cette opération renvoie une erreur, voir l'article [Resetting VMware Update Manager database on a vCenter Server appliance 6.5 (2147284)](https://kb.vmware.com/s/article/2147284).
10. Après avoir testé, vérifiez si vous avez besoin de revenir en arrière, de rétablir une image instantanée ou de restaurer une sauvegarde précédente de vCenter.

## Instances vCenter liées à SSO

Si vous disposez d'instances vCenter Server principales et secondaires, vos dispositifs VCSA sont configurés pour figurer dans un seul domaine vCenter Single Sign-On (SSO). Chaque dispositif VCSA a une instance VUM déployée. Les propriétés de configuration que vous modifiez sont appliquées uniquement à l'instance VUM que vous indiquez et ne sont pas propagées sur d'autres instances dans le groupe.

Vous pouvez spécifiez une instance VUM en sélectionnant le nom du dispositif VCSA avec lequel est enregistrée l'instance VUM à partir de la barre de navigation. Vous pouvez également gérer les lignes de base et les groupes de lignes de base, ainsi qu'analyser et résoudre uniquement les objets d'inventaire gérés par le dispositif VCSA avec lequel est enregistrée l'instance VUM.

### Liens connexes

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (démonstrations)
