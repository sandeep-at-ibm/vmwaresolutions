---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Extension et réduction de capacité pour des instances vCenter Server

Vous pouvez augmenter ou réduire la capacité de votre instance VMware vCenter Server en fonction de vos besoins métier en ajoutant ou en supprimant des serveurs ESXi.

Si votre cluster initial dispose d'un stockage vSAN, l'ajout d'un ou plusieurs serveurs ESXi après le déploiement permet d'augmenter la capacité de stockage du cluster.

## Avant de commencer

* N'ajoutez pas ou ne retirez pas de serveurs ESXi dans le client Web VMware vSphere. Les modifications apportées sur le client Web vSphere ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_full}}.
* Une instance vCenter Server avec un stockage NFS doit disposer au minimum de 2 serveurs ESXi. Pour les instances déployées en version 2.1 ou ultérieure, vous pouvez développer le cluster par défaut jusqu'à contenir 51 serveurs ESXi. Chacun des autres clusters peut contenir jusqu'à 59 serveurs ESXi.
* Une instance vCenter Server avec un stockage vSAN doit disposer au minimum de 4 serveurs ESXi.
* Avant de retirer des serveurs ESXi avec le service F5 on {{site.data.keyword.cloud_notm}} ou FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installé, vous devez faire migrer les machines virtuelles F5 BIG-IP et FortiGate vers un autre serveur ESXi que celui sur lequel elles sont hébergées.
* Avant de supprimer des serveurs ESXi sur lesquels le service IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} est installé, vérifiez qu'aucune opération de sauvegarde ou de restauration (en échec ou en cours) n'est active, car ce type d'opération pourrait empêcher la suppression des serveurs ESXi.
* Lorsque vous supprimez des serveurs ESXi, ceux-ci sont placés en mode maintenance, puis toutes les machines virtuelles qui s'exécutent sur les serveurs sont migrées avant d'être supprimées de vCenter Server. Pour un contrôle maximum de la réimplantation des machines virtuelles, il est recommandé de placer les serveurs ESXi à supprimer en mode maintenance et de migrer manuellement les machines virtuelles qui s'exécutent sur ces serveur à l'aide du client Web VMware vSphere. Ensuite, supprimez les serveurs ESXi à l'aide de la console {{site.data.keyword.vmwaresolutions_short}}.
* Pour les instances vCenter Server déployées en version 2.0 ou antérieure, vous pouvez développer chaque cluster jusqu'à contenir 32 serveurs ESXi. Le nombre de serveurs {{site.data.keyword.baremetal_short}} que vous pouvez ajouter à la fois est le suivant :
   * Pour les configurations **Petite**, **Moyenne** et **Grande**, vous pouvez ajouter de 1 à 10 serveurs ESXi à la fois.
   * Pour la configuration **Personnalisée**, vous pouvez ajouter de 1 à 20 serveurs ESXi à la fois. Pour plus d'informations sur le nombre minimum de serveurs ESXi, voir [Une instance vCenter Server à deux noeuds est-elle à haute disponibilité ?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## Procédure

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous souhaitez étendre ou réduire la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster sur lequel vous souhaitez ajouter ou retirer des serveurs ESXi.
5. Pour ajouter des serveurs ESXi, procédez comme suit :
   1. Dans la section **Serveurs ESXi**, cliquez sur **Ajouter**.
   2. Dans la fenêtre **Ajouter un serveur**, indiquez le nombre de serveurs que vous voulez ajouter, passez en revue le coût estimé, puis cliquez sur **Ajouter**.
6. Pour supprimer des serveurs ESXi, sélectionnez les serveurs à supprimer dans la section **Serveurs ESXi**, puis cliquez sur **Retirer**.

## Résultats

Une fois l'opération d'ajout ou de suppression commencée, une courte pause peut être observée entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.

Vous recevez une notification par courrier électronique qui vous indique que l'ajout ou la suppression des serveurs ESXi est en cours. Le cluster associé aux serveurs ESXi prend le statut **Modification en cours**. Lorsque vous supprimez des serveurs, sachez que les serveurs ESXi sont totalement récupérés par l'infrastructure {{site.data.keyword.cloud_notm}} à la fin du cycle de facturation d'{{site.data.keyword.cloud_notm}}, qui est généralement de 30 jours.

**Attention :** les serveurs ESXi supprimés vous sont facturés jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.

Si vous ne voyez pas les serveurs ESXi ajoutés dans la liste du cluster, consultez vos courriers électroniques ou les notifications de la console pour obtenir plus de détails sur la cause de l'échec.

### Liens connexes

* [Nomenclature de vCenter Server](vc_bom.html)
* [Exigences et planification pour les instances vCenter Server](vc_planning.html)
* [Ajout, affichage et suppression de clusters pour des instances vCenter Server](vc_addingviewingclusters.html)
* [Activer le mode maintenance sur un hôte](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
