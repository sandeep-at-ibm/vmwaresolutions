---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Mise à l'échelle de clusters créés en dehors de la console
{: #vs_orderingforclustersoutside}

Vous pouvez utiliser l'offre VMware vSphere pour mettre à l'échelle des clusters vSphere existants créés en dehors de la console {{site.data.keyword.vmwaresolutions_full}}. Pour mettre à l'échelle un cluster vSphere créé en dehors de la console, recréez le cluster avec les mêmes paramètres dans la console, puis mettez-le à l'échelle.

## Conditions requises
{: #vs_orderingforclustersoutside-req}

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Gestion des paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Vous avez passé en revue les exigences et les remarques énoncées dans [Exigences et planification pour VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).

## Procédure de mise à l'échelle des clusters créés en dehors de la console
{: #vs_orderingforclustersoutside-procedure}

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **VMware vSphere** dans la section **Centres de données virtuels**.
2. Sur la page **VMware vSphere on IBM Cloud**, cliquez sur **Créer**.  
   Vérifiez que vous vous trouvez sur l'onglet **Créer** et que **Nouveau cluster** est affiché dans la liste **Configurations de cluster**.
3. Créez un cluster avec les mêmes paramètres que le cluster existant créé en dehors de la console {{site.data.keyword.vmwaresolutions_short}}. Pour plus d'informations, voir [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).  
   Dans le cadre de l'interface réseau, pour mettre à l'échelle un cluster qui est créé en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, vous devez sélectionner les VLAN existants pour le cluster.
   {:note}
4. Sur le panneau **Récapitulatif de la commande**, vérifiez la configuration du cluster, puis cliquez sur **Sauvegarde de la configuration**.   
5. Sur la page **Initiation**, cliquez sur la carte **VMware vSphere on IBM Cloud**.
6. Sur la page **VMware vSphere on IBM Cloud**, cliquez sur **Créer**.
7. Cliquez sur l'onglet **Mettre à l'échelle un cluster existant**. Dans la liste **Configurations de cluster**, sélectionnez celui que vous venez de créer.
8. Dans la section **{{site.data.keyword.baremetal_short}}**, spécifiez le nombre de serveurs {{site.data.keyword.baremetal_short}} que vous souhaitez ajouter au cluster.
9. Si le cluster n'inclut pas la paire de dispositifs FortiGate Security Appliance série 300 à haute disponibilité sur ses VLAN publics, vous pouvez en commander une en sélectionnant **Inclure avec achat** sous **Paire de dispositifs FortiGate Physical Appliance série 300 à haute disponibilité**.
10. Sur le panneau **Récapitulatif de la commande**, vérifiez la configuration de l'instance et le coût estimé, assurez-vous que le compte qui devra être facturé est correct, passez en revue et acceptez les conditions, puis cliquez sur **Mettre à disposition**.

## Résultats
{: #vs_orderingforclustersoutside-results}

Le déploiement du cluster démarre automatiquement et vous recevez par courrier électronique la confirmation que la commande est en cours de traitement. Lorsque le cluster est prêt pour utilisation, un courrier électronique vous en avertit.

Les clusters vSphere ne s'affichent pas sur la page **Ressources**, avec les instances vCenter Server.
{:note}

## Liens connexes
{: #vs_orderingforclustersoutside-related}

* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Commande de clusters vSphere on la base de configurations existantes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Mise à l'échelle de clusters vSphere existants](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
