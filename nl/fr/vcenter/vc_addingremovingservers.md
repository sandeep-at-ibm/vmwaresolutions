---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-05"

---

# Extension et réduction de capacité pour des instances vCenter Server

Vous pouvez accroître ou réduire la capacité de votre instance VMware vCenter Server en fonction de vos besoins métier en ajoutant ou en supprimant des serveurs ESXi.

Si votre cluster initial dispose d'un stockage vSAN, l'ajout d'un ou plusieurs serveurs ESXi après le déploiement permet d'accroître la capacité de stockage du cluster.

## Ajout de serveurs ESXi à des instances vCenter Server

### Avant d'ajouter des serveurs ESXi

* N'ajoutez pas de serveurs ESXi depuis le client Web VMware vSphere. Les modifications apportées sur le client Web vSphere ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_full}}.
* Une instance vCenter Server avec un stockage NFS doit disposer au minimum de 2 serveurs ESXi. Pour les instances déployées en version 2.1 ou ultérieure, vous pouvez développer le cluster par défaut jusqu'à contenir 51 serveurs ESXi. Chacun des autres clusters peut contenir jusqu'à 59 serveurs ESXi.
* Une instance vCenter Server avec un stockage vSAN doit disposer au minimum de 4 serveurs ESXi.
* Pour les instances vCenter Server déployées en version 2.0 ou antérieure, vous pouvez développer chaque cluster jusqu'à contenir 32 serveurs ESXi. Le nombre de serveurs {{site.data.keyword.baremetal_short}} que vous pouvez ajouter à la fois est le suivant :
   * Pour les configurations **Petite**, **Moyenne** et **Grande**, vous pouvez ajouter de 1 à 10 serveurs ESXi à la fois.
   * Pour la configuration **Personnalisée**, vous pouvez ajouter de 1 à 20 serveurs ESXi à la fois. Pour plus d'informations sur le nombre minimum de serveurs ESXi, voir [Une instance vCenter Server à deux noeuds est-elle à haute disponibilité ?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## Procédure d'ajout de serveurs ESXi

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez accroître la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster auquel vous désirez ajouter des serveurs ESXi.
5. Dans la section **Serveurs ESXi**, cliquez sur **Ajouter**.
6. Dans la fenêtre **Ajouter un serveur**, indiquez le nombre de serveurs que vous voulez ajouter, passez en revue le coût estimé, puis cliquez sur **Ajouter**.

### Résultats après l'ajout de serveurs ESXi

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande d'ajout de serveurs ESXi est en cours de traitement. Sur la console, le statut du cluster qui est associé aux serveurs ESXi passe à **Modification en cours**.
3. Si vous ne voyez pas les serveurs ESXi ajoutés dans la liste du cluster, consultez vos courriers électroniques ou les notifications de la console pour obtenir plus de détails sur la cause de l'échec.

## Retrait de serveurs ESXi dans des instances vCenter Server

### Avant de retirer des serveurs ESXi

* Ne retirez pas de serveurs ESXi depuis le client Web VMware vSphere. Les modifications apportées sur le client Web vSphere ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_full}}.
* Une instance vCenter Server avec stockage NFS doit disposer d'au moins 2 serveurs ESXi et une instance vCenter Server avec stockage vSAN d'au moins 4 serveurs ESXi.
* Avant de retirer des serveurs ESXi avec le service F5 on {{site.data.keyword.cloud_notm}} ou FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installé, vous devez faire migrer les machines virtuelles F5 BIG-IP et FortiGate vers un autre serveur ESXi que celui sur lequel elles sont hébergées.
* Avant de supprimer des serveurs ESXi sur lesquels le service IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} est installé, vérifiez qu'aucune opération de sauvegarde ou de restauration (en échec ou en cours) n'est active, car ce type d'opération pourrait empêcher la suppression des serveurs ESXi.
* Lorsque vous retirez des serveurs ESXi, ceux-ci sont placés en mode maintenance, puis toutes les machines virtuelles qui s'exécutent sur les serveurs sont migrées avant d'être retirées de vCenter Server. Pour un contrôle maximum de la réimplantation des machines virtuelles, il est recommandé de placer les serveurs ESXi à supprimer en mode maintenance et de migrer manuellement les machines virtuelles qui s'exécutent sur ces serveur à l'aide du client Web VMware vSphere. Ensuite, retirez les serveurs ESXi à l'aide de la console {{site.data.keyword.vmwaresolutions_short}}.

## Procédure de retrait de serveurs ESXi

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le panneau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez réduire la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster sur lequel vous désirez retirer des serveurs ESXi.
5. Dans la section **Serveurs ESXi**, sélectionnez les serveurs que vous désirez supprimer et cliquez sur **Retirer**.

### Résultats après le retrait de serveurs ESXi

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande de retrait de serveurs ESXi est en cours de traitement. Sur la console, le statut du cluster qui est associé aux serveurs ESXi passe à **Modification en cours**.
3. Les serveurs ESXi sont complètement récupérés par l'infrastructure {{site.data.keyword.cloud_notm}} à la fin de son cycle de facturation, lequel est généralement de 30 jours.

   **Attention** : les serveurs ESXi retirés vous sont facturés jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.

### Liens connexes

* [Nomenclature de vCenter Server](vc_bom.html)
* [Exigences et planification pour les instances vCenter Server](vc_planning.html)
* [Ajout, affichage et suppression de clusters pour des instances vCenter Server](vc_addingviewingclusters.html)
* [Activer le mode maintenance sur un hôte](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
