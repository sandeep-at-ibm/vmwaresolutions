---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Mise à l'échelle de clusters vSphere existants

Vous pouvez mettre à l'échelle un cluster VMware vSphere existant commandé ou sauvegardé dans la console {{site.data.keyword.vmwaresolutions_full}} en ajoutant des serveurs ESXi ou en commandant une paire de dispositifs FortiGate Security Appliance série 300 à haute disponibilité.

## Conditions requises

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Paramètres et comptes utilisateur](../vmonic/useraccount.html).
*  Vous avez passé en revue les exigences et les remarques énoncées dans [Exigences et planification pour les clusters vSphere](vs_planning.html).

## Procédure

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **VMware vSphere** dans la section **Centres de données virtuels**.
2. Sur la page **VMware vSphere on IBM Cloud**, cliquez sur **Créer**.  
3. Cliquez sur l'onglet **Mettre à l'échelle un cluster existant** et sélectionnez dans la liste **Configurations de cluster** le cluster que vous souhaitez mettre à l'échelle.
4. Passez en revue ls paramètres de cluster qui sont automatiquement renseignés.
5. Dans la section **{{site.data.keyword.baremetal_short}}**, spécifiez le nombre de serveurs {{site.data.keyword.baremetal_short}} que vous souhaitez ajouter au cluster.
6. Si le cluster n'inclut pas la paire de dispositifs FortiGate Security Appliance série 300 à haute disponibilité sur ses VLAN publics, vous pouvez en commander une en sélectionnant **Inclure avec achat** sous **Paire de dispositifs FortiGate Physical Appliance série 300 à haute disponibilité**.
7. Sur le panneau **Récapitulatif de la commande**, vérifiez la configuration de l'instance et le coût estimé.
   * Pour sauvegarder la configuration en tant que modèle sans passer de commande, cliquez sur **Sauvegarde de la configuration**.
   * Pour passer la commande, assurez-vous que le compte qui devra être facturé est correct, passez en revue et acceptez les conditions, puis cliquez sur **Mettre à disposition**.

### Résultats

Le déploiement de la mise à l'échelle du cluster démarre automatiquement et vous recevez par courrier électronique la confirmation que la commande est en cours de traitement. Lorsque le cluster est prêt pour utilisation, un courrier électronique vous en avertit.

**Remarque :** contrairement aux instances vCenter Server et Cloud Foundation, les clusters vSphere ne s'affichent pas sur la page **Instances déployées**.

### Liens connexes

* [Commande de nouveaux clusters vSphere](vs_orderinginstances.html)
* [Commande de clusters vSphere sur la base de configurations existantes](vs_orderingbasedonexistingconfig.html)
* [Mise à l'échelle de clusters créés en dehors de la console](vs_orderingforclustersoutside.html)
