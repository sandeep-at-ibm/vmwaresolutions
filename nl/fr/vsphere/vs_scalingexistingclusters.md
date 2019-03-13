---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Mise à l'échelle de clusters vSphere existants
{: #vs_scalingexistingclusters}

Vous pouvez mettre à l'échelle un cluster VMware vSphere existant commandé ou sauvegardé dans la console {{site.data.keyword.vmwaresolutions_full}}. Pour ce faire, ajoutez des serveurs ESXi ou commandez une paire de dispositifs FortiGate Security Appliance série 300 à haute disponibilité pour le cluster.

## Conditions requises
{: #vs_scalingexistingclusters-req}

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount#managing-user-accounts-and-settings).
*  Vous avez passé en revue les exigences et les remarques énoncées dans [Exigences et planification pour les clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).
*  Vous avez reçu un courrier électronique vous confirmant que le cluster que vous souhaitez mettre à échelle est prêt à être utilisé.

## Procédure de mise à l'échelle de clusters existants
{: #vs_scalingexistingclusters-procedure}

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **VMware vSphere** dans la section **Centres de données virtuels**.
2. Sur la page **VMware vSphere on IBM Cloud**, cliquez sur **Créer**.  
3. Cliquez sur l'onglet **Mettre à l'échelle un cluster existant** et sélectionnez dans la liste **Configurations de cluster** celui que vous désirez mettre à l'échelle.
4. Passez en revue les paramètres de cluster renseignés automatiquement.
5. Dans la section **{{site.data.keyword.baremetal_short}}**, spécifiez le nombre de serveurs {{site.data.keyword.baremetal_short}} que vous souhaitez ajouter au cluster.
6. Si le cluster n'inclut pas la paire de dispositifs FortiGate Security Appliance série 300 à haute disponibilité sur ses VLAN publics, vous pouvez en commander une. Pour ce faire, sélectionnez **Inclure avec achat** sous **Paire de dispositifs FortiGate Physical Appliance série 300 à haute disponibilité**.
7. Sur le panneau **Récapitulatif de la commande**, vérifiez la configuration de l'instance et le coût estimé.
   * Pour sauvegarder la configuration en tant que modèle sans passer de commande, cliquez sur **Sauvegarde de la configuration**.
   * Pour passer la commande, assurez-vous que le compte qui devra être facturé est correct, passez en revue et acceptez les conditions, puis cliquez sur **Mettre à disposition**.

### Résultats
{: #vs_scalingexistingclusters-results}

La mise à l'échelle du cluster démarre automatiquement. Une conformation par courrier électronique vous avise que la commande est en cours de traitement. Lorsque le cluster est prêt pour utilisation, un courrier électronique vous en avertit.

Si le cluster que vous mettez à l'échelle n'est pas prêt à être utilisé, il se peut qu'un message d'erreur s'affiche.

Contrairement aux instances vCenter Server et Cloud Foundation, les clusters vSphere ne s'affichent pas sur la page **Instances déployées**.
{:note}

## Liens connexes
{: #vs_scalingexistingclusters-related}

* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Commande de clusters vSphere on la base de configurations existantes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Mise à l'échelle de clusters créés en dehors de la console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
