---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Extension et réduction de capacité pour des instances vCenter Server with NSX-T
{: #vc_nsx-t_addingremovingservers}

Vous pouvez accroître ou réduire la capacité de votre instance VMware vCenter Server with NSX-T en fonction de vos besoins métier en ajoutant ou en supprimant des serveurs ESXi ou du stockage NFS.

* A compter de l'édition V3.0, vous pouvez ajouter ou retirer simultanément le stockage NFS et des serveurs ESXi sur des clusters qui sont à l'état **Prêt à l'emploi**. Par exemple, vous pouvez ajouter ou retirer un serveur ESXi dans un cluster et ajouter ou retirer le stockage NFS dans un autre cluster. 
* A compter de l'édition V2.9, vous pouvez ajouter de nouveaux serveurs ESXi à un cluster tandis que ces serveurs sont en mode maintenance. De plus, vous pouvez ajouter ou retirer simultanément des serveurs ESXi sur plusieurs clusters.

**Remarques** :
* Si votre cluster initial dispose d'un stockage vSAN, l'ajout d'un ou plusieurs serveurs ESXi après le déploiement permet d'accroître la capacité de stockage du cluster.
* Vous pouvez ajouter ou retirer des partages de stockage NFS à/d'un cluster vCenter Server with NSX-T NFS ou vSAN existant.

## Ajout de serveurs ESXi à des instances vCenter Server with NSX-T
{: #vc_nsx-t_addingremovingservers-adding}

### Avant d'ajouter des serveurs ESXi
{: #vc_nsx-t_addingremovingservers-adding-prereq}

* Dans la mesure du possible, vous devez ajouter les serveurs ESXi à l'aide de la console {{site.data.keyword.vmwaresolutions_full}} car les modifications apportées au client VMware vSphere Web Client ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}. Par conséquent, ajoutez des serveurs ESXi à vCenter Server uniquement pour les serveurs ESXi sur site ou pour les serveurs ESXi que vous ne pouvez ou ne voulez pas gérer dans la console {{site.data.keyword.vmwaresolutions_short}}.
* Une instance vCenter Server with NSX-T avec un stockage NFS doit disposer au minimum de 3 serveurs ESXi. Vous pouvez développer le cluster par défaut jusqu'à contenir 51 serveurs ESXi. Chacun des autres clusters peut contenir jusqu'à 59 serveurs ESXi.
* Une instance vCenter Server with NSX-T avec un stockage vSAN doit disposer au minimum de 4 serveurs ESXi.

### Procédure d'ajout de serveurs ESXi
{: #vc_nsx-t_addingremovingservers-adding-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez accroître la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster auquel vous désirez ajouter des serveurs ESXi.
5. Dans la section **Serveurs ESXi**, cliquez sur **Ajouter**.
6. Dans la fenêtre **Ajouter un serveur**, entrez le nombre de serveurs que vous voulez ajouter.
7. Le cas échéant, cochez la case permettant d'ajouter des serveurs alors que le mode maintenance est actif.
8. Passez en revue le coût estimé et cliquez sur **Ajouter**.

### Résultats après l'ajout de serveurs ESXi
{: #vc_nsx-t_addingremovingservers-adding-results}

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande d'ajout de serveurs ESXi est en cours de traitement. Sur la console, le statut du cluster qui est associé aux serveurs ESXi passe à **Modification en cours**.
3. Si vous ne voyez pas les serveurs ESXi ajoutés dans la liste du cluster, consultez vos courriers électroniques ou les notifications de la console pour obtenir plus de détails sur la cause de l'échec.

Si vous ajoutez des serveurs ESXi alors que le mode maintenance est actif, les machines virtuelles ne sont pas migrées vers les nouveaux serveurs tant que le mode maintenance n'est pas désactivé pour le cluster.   
{:important}

## Retrait de serveurs ESXi sur des instances vCenter Server with NSX-T
{: #vc_nsx-t_addingremovingservers-removing}

### Avant de retirer des serveurs ESXi
{: #vc_nsx-t_addingremovingservers-removing-prereq}

* Dans la mesure du possible, vous devez retirer les serveurs ESXi à l'aide de la console {{site.data.keyword.vmwaresolutions_full}} car les modifications apportées au client vSphere Web Client ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}. Par conséquent, retirez des serveurs ESXi de vCenter Server uniquement en cas de serveurs ESXi sur site ou pour les serveurs ESXi que vous ne pouvez ou ne voulez pas gérer dans la console {{site.data.keyword.vmwaresolutions_short}}.
* Une instance vCenter Server with NSX-T avec stockage NFS doit disposer d'au moins 3 serveurs ESXi et une instance vCenter Server with NSX-T avec stockage vSAN doit disposer d'au moins 4 serveurs ESXi.
* Lorsque vous retirez des serveurs ESXi, ceux-ci sont placés en mode maintenance, puis toutes les machines virtuelles qui s'exécutent sur les serveurs sont migrées avant d'être retirées de vCenter Server. Pour un contrôle maximum de la réimplantation des machines virtuelles, il est recommandé de placer les serveurs ESXi à supprimer en mode maintenance et de migrer manuellement les machines virtuelles qui s'exécutent sur ces serveur à l'aide du client Web VMware vSphere. Ensuite, retirez les serveurs ESXi à l'aide de la console {{site.data.keyword.vmwaresolutions_short}}.

### Procédure de retrait de serveurs ESXi
{: #vc_nsx-t_addingremovingservers-removing-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le panneau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez réduire la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster sur lequel vous désirez retirer des serveurs ESXi.
5. Dans la section **Serveurs ESXi**, sélectionnez les serveurs que vous désirez supprimer et cliquez sur **Retirer**.

### Résultats après le retrait de serveurs ESXi
{: #vc_nsx-t_addingremovingservers-removing-results}

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande de retrait de serveurs ESXi est en cours de traitement. Sur la console, le statut du cluster qui est associé aux serveurs ESXi passe à **Modification en cours**.
3. Les serveurs ESXi sont complètement récupérés par l'infrastructure {{site.data.keyword.cloud_notm}} à la fin de son cycle de facturation, lequel est généralement de 30 jours.

   Les serveurs ESXi retirés vous sont facturés jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.
   {:note}

## Ajout de stockage NFS à des instances vCenter Server with NSX-T
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-to-vcs-nsx-t}

### Avant d'ajouter du stockage NFS
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-prereq}

N'ajoutez pas de stockage NFS depuis le client Web VMware vSphere. Les modifications apportées sur le client Web vSphere ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}. IBM ne pourra pas gérer les partages de fichiers NFS que vous ajoutez manuellement à une instance.

### Procédure pour l'ajout de stockage NFS
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez accroître la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster auquel vous souhaitez ajouter du stockage NFS.
5. Dans la section **Stockage**, cliquez sur **Ajouter**.
6. Dans la fenêtre **Stockage**, configurez le stockage.
   * Si vous souhaitez ajouter et configurer les mêmes paramètres pour tous les partages de fichiers, renseignez les zones **Nombre de partages**, **Performances** et **Taille (Go)**.
   * Si vous souhaitez ajouter et configurer des partages de fichiers individuellement, renseignez les zones **Configurer les partages individuellement**, puis cliquez sur l'icône **+** en regard de l'option d'**ajout de stockage partagé**. Renseignez ensuite les zones **Performances** et **Taille (Go)** pour chaque partage de fichiers individuel. Vous devez sélectionner au moins un partage de fichiers.
7. Cliquez sur l'option d'**ajout de stockage NFS**.

### Résultats après l'ajout de stockage NFS
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-results}

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande d'ajout de stockage NFS est en cours de traitement. Sur la console, le statut du cluster qui est associé au stockage NFS passe à **Modification en cours**.
3. Si vous ne voyez pas le stockage NFS ajouté dans la liste du cluster, consultez vos courriers électroniques ou les notifications de la console pour obtenir plus de détails sur la cause de l'échec.

## Retrait de stockage NFS sur des instances vCenter Server with NSX-T
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage}

### Avant de retirer du stockage NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-prereq}

* Ne retirez pas de stockage NFS depuis le client Web VMware vSphere. Les modifications apportées sur le client Web vSphere ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}.
* Avant de retirer le stockage NFS, assurez-vous d'avoir retiré toutes les machines virtuelles qui résident dans le stockage.
* Vérifiez que les partages que vous prévoyez de retirer sont associés à l'instance vCenter Server correcte.
* Le cluster doit être à l'état **Prêt à l'emploi**.

### Procédure pour le retrait de stockage NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le panneau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez réduire la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster dont vous souhaitez retirer du stockage NFS.
5. Dans la section **Stockage**, sélectionnez le partage de stockage que vous voulez retirer et cliquez sur **Supprimer**.
6. Cliquez sur **Retirer** dans la fenêtre **Retirer le stockage**.

### Résultats après le retrait de stockage NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-results}

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande de retrait de stockage NFS est en cours de traitement. Sur la console, le statut du cluster qui est associé au stockage NFS passe à **Modification en cours**.
3. Le stockage NFS est complètement récupéré par l'infrastructure {{site.data.keyword.cloud_notm}} à la fin de son cycle de facturation, lequel est généralement de 30 jours.

   Les services retirés vous sont facturés jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.
   {:note}

## Liens connexes
{: #vc_nsx-t_addingremovingservers-related}

* [Nomenclature de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Exigences et planification pour les instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Commande d'instances vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [Ajout, affichage et suppression de clusters pour des instances vCenter Server with NSX-T](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_addingviewingcluster#vc_nsx-t_addingviewingcluster)
* [Place a host in maintenance mode](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/s/article/1003212){:new_window}
