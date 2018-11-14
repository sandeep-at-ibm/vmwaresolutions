---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# Mise à jour de dispositif VCSA et instances vCenter liées à SSO

## Mise à jour de dispositif VCSA

VUM ne met pas à jour VCSA, donc cette section présente le processus de mise à jour de ce dispositif. Le dispositif VCSA déployé dans une instance VCS n'a pas d'accès à Internet, par conséquent, le bundle de mise à jour doit être d'abord téléchargé sur un serveur intermédiaire.

VCSA est mis à jour via la console de gestion du dispositif, et non pas via vSphere Web Client. La console de gestion du dispositif VCSA est accessible en utilisant un navigateur, l'adresse IP de VCSA et le port 5480.

Vous devez prendre une image instantanée du dispositif ou effectuer une sauvegarde de VCSA avant de procéder à la mise à jour. Vérifiez que tout fonctionne comme prévu, puis supprimez l'image instantanée au bout de quelques jours pour éviter une dégradation des performances. Par ailleurs, consultez les notes sur l'édition avant d'entreprendre une mise à niveau.

Pour mettre à jour VCSA, procédez comme suit :
1. Vous pouvez télécharger des mises à jour en accédant au [centre de téléchargement](https://my.vmware.com/group/vmware/patch#search) des correctifs de VMware, en vous connectant et en choisissant VC dans le menu **Search by Product**. Sélectionnez le correctif approprié et cliquez sur **Download**.
2. A l'aide de vSphere Web Client, transférez le fichier ISO vers le référentiel du magasin de données vCenter.
3. Montez le fichier ISO de mise à jour sur le serveur vCenter.
4. Prenez une image instantanée de votre serveur vCenter.
5. Connectez-vous à la console de gestion du dispositif vCenter à l'adresse suivante : `https://vcenterip:5480`
6. Accédez à la section **Update** et sélectionnez **Check Updates** puis sur **Check CDROM**. La mise à jour doit être répertoriée.
7. Sélectionnez **Install Updates** et **Accept** pour accepter le contrat de licence d'utilisateur final (EULA ou CLUF). L'installation de la mise à jour commence.
8. Une fois la mise à jour terminée, vous devez revenir à la console de gestion du dispositif et sélectionnez l'option de redémarrage de la console.
9. Reconnectez-vous à vSphere Web Client et recherchez les erreurs éventuelles. Exécutez une analyse manuelle de VUM, **Home** > **Hosts and Clusters**, sélectionnez ensuite un centre de données ou un cluster, puis cliquez sur l'onglet **Update Manager**, puis sur **Scan for Updates**. Si cette opération renvoie une erreur, voir l'article [Resetting VMware Update Manager database on a vCenter Server appliance 6.5 (2147284)](https://kb.vmware.com/s/article/2147284).
10. Après avoir testé, vérifiez si vous avez besoin de revenir en arrière, de rétablir une image instantanée ou de restaurer une sauvegarde précédente de vCenter.

## Instances vCenter liées à SSO

Si vous disposez d'instances VCS principales et secondaires, vos dispositifs VCSA sont configurés pour figurer dans un seul domaine vCenter Single Sign-On (SSO). Chaque dispositif VCSA aura une instance VUM déployée. Les propriétés de configuration que vous modifiez sont appliquées uniquement à l'instance VUM que vous indiquez et ne sont pas propagées sur d'autres instances dans le groupe.

Vous pouvez spécifiez une instance VUM en sélectionnant le nom du dispositif VCSA avec lequel est enregistrée l'instance VUM à partir de la barre de navigation. Vous pouvez également gérer les lignes de base et les groupes de lignes de base, ainsi qu'analyser et résoudre uniquement les objets d'inventaire gérés par le dispositif VCSA avec lequel est enregistrée l'instance VUM.

### Liens connexes

* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (démonstrations)
