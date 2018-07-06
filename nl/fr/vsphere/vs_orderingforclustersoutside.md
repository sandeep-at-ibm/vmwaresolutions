---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Mise à l'échelle de clusters créés en dehors de la console

Vous pouvez utiliser l'offre VMware vSphere pour mettre à l'échelle des clusters vSphere existants créés en dehors de la console {{site.data.keyword.vmwaresolutions_full}}. Pour mettre à l'échelle un cluster vSphere qui est créé en dehors de la console, recréez le cluster avec les mêmes paramètres que la console, puis procédez à la mise à l'échelle du cluster.

## Conditions requises

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Gestion des paramètres et comptes utilisateur](../vmonic/useraccount.html).
*  Vous avez passé en revue les exigences et les remarques énoncées dans [Exigences et planification pour VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_planning.html).

## Procédure

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **VMware vSphere** dans la section **Centres de données virtuels**.
2. Sur la page **VMware vSphere on IBM Cloud**, cliquez sur **Créer**.  
   Vérifiez que vous vous trouvez sur l'onglet **Créer** et que **Nouveau cluster** est affiché dans la liste **Configurations de cluster**.
3. Créez un nouveau cluster avec les mêmes paramètres que ceux du cluster existant qui est créé en dehors de la console {{site.data.keyword.vmwaresolutions_short}}. Pour plus d'informations, voir [Commande de nouveaux clusters vSphere](vs_orderinginstances.html).  
   **Remarque** : dans le cadre de l'interface réseau, pour mettre à l'échelle un cluster qui est créé en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, vous devez sélectionner les VLAN existants pour le cluster.  
4. Sur le panneau **Récapitulatif de la commande**, vérifiez la configuration du cluster, puis cliquez sur **Sauvegarde de la configuration**.   
5. Sur la page **Initiation**, cliquez sur la carte **VMware vSphere on IBM Cloud**.
6. Sur la page **VMware vSphere on IBM Cloud**, cliquez sur **Créer**.
7. Cliquez sur l'onglet **Mettre à l'échelle un cluster existant** et sélectionnez dans la liste **Configurations de cluster** le cluster que vous venez de créer.
8. Dans la section **{{site.data.keyword.baremetal_short}}**, spécifiez le nombre de serveurs {{site.data.keyword.baremetal_short}} que vous souhaitez ajouter au cluster.
9. Si le cluster n'inclut pas la paire de dispositifs FortiGate Security Appliance série 300 à haute disponibilité sur ses VLAN publics, vous pouvez en commander une en sélectionnant **Inclure avec achat** sous **Paire de dispositifs FortiGate Physical Appliance série 300 à haute disponibilité**.
10. Sur le panneau **Récapitulatif de la commande**, vérifiez la configuration de l'instance et le coût estimé, assurez-vous que le compte qui devra être facturé est correct, passez en revue et acceptez les conditions, puis cliquez sur **Mettre à disposition**.

## Résultats

Le déploiement du cluster démarre automatiquement et vous recevez par courrier électronique la confirmation que la commande est en cours de traitement. Lorsque le cluster est prêt pour utilisation, un courrier électronique vous en avertit.

**Remarque :** les clusters vSphere ne s'affichent pas sur la page **Instances déployées**, avec les instances vCenter Server et Cloud Foundation.

## Liens connexes

* [Commande de nouveaux clusters vSphere](vs_orderinginstances.html)
* [Commande de clusters vSphere sur la base de configurations existantes](vs_orderingbasedonexistingconfig.html)
* [Mise à l'échelle de clusters vSphere existants](vs_scalingexistingclusters.html)
