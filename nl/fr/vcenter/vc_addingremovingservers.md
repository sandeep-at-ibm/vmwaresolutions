---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Extension et réduction de capacité pour des instances vCenter Server

Vous pouvez accroître ou réduire la capacité de votre instance VMware vCenter Server en fonction de vos besoins métier en ajoutant ou en supprimant des serveurs ESXi ou du stockage NFS.

Vous pouvez ajouter ou supprimer des partages de stockage NFS vers ou à partir d'un cluster NFS ou vSAN vCenter Server.
{:note}

Si votre cluster initial dispose d'un stockage vSAN, l'ajout d'un ou plusieurs serveurs ESXi après le déploiement permet d'accroître la capacité de stockage du cluster.

## Ajout de serveurs ESXi à des instances vCenter Server

### Avant d'ajouter des serveurs ESXi

* N'ajoutez pas de serveurs ESXi depuis le client Web VMware vSphere. Les modifications apportées sur le client Web vSphere ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_full}}.
* Une instance vCenter Server avec un stockage NFS doit disposer au minimum de 2 serveurs ESXi. Pour les instances déployées en version 2.1 ou ultérieure, vous pouvez développer le cluster par défaut jusqu'à contenir 51 serveurs ESXi. Chacun des autres clusters peut contenir jusqu'à 59 serveurs ESXi.
* Une instance vCenter Server avec un stockage vSAN doit disposer au minimum de 4 serveurs ESXi.
* Pour les instances vCenter Server déployées en version 2.0 ou antérieure, vous pouvez développer chaque cluster jusqu'à contenir 32 serveurs ESXi. Le nombre de serveurs {{site.data.keyword.baremetal_short}} que vous pouvez ajouter à la fois est le suivant :
   * Pour les configurations **Petite**, **Moyenne** et **Grande**, vous pouvez ajouter de 1 à 10 serveurs ESXi à la fois.
   * Pour les configurations **Skylake** et **Broadwell**, vous pouvez ajouter 1 à 20 serveurs ESXi à la fois. Pour plus d'informations sur le nombre minimum de serveurs ESXi, voir [Une instance vCenter Server à deux noeuds est-elle à haute disponibilité ?](/docs/services/vmwaresolutions/vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

### Procédure d'ajout de serveurs ESXi

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez accroître la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster auquel vous désirez ajouter des serveurs ESXi.
5. Dans la section **Serveurs ESXi**, cliquez sur **Ajouter un serveur**.
6. Dans la fenêtre **Ajouter un serveur**, indiquez le nombre de serveurs que vous voulez ajouter, passez en revue le coût estimé, puis cliquez sur **Ajouter**.

### Résultats après l'ajout de serveurs ESXi

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande d'ajout de serveurs ESXi est en cours de traitement. Sur la console, le statut du cluster qui est associé aux serveurs ESXi passe à **Modification en cours**.
3. Si vous ne voyez pas les serveurs ESXi ajoutés dans la liste du cluster, consultez vos courriers électroniques ou les notifications de la console pour obtenir plus de détails sur la cause de l'échec.

## Retrait de serveurs ESXi dans des instances vCenter Server

### Avant de retirer des serveurs ESXi

* Ne retirez pas de serveurs ESXi depuis le client Web VMware vSphere. Les modifications apportées sur le client Web vSphere ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}.
* Une instance vCenter Server avec stockage NFS doit disposer d'au moins 2 serveurs ESXi et une instance vCenter Server avec stockage vSAN d'au moins 4 serveurs ESXi.
* Avant de retirer des serveurs ESXi avec le service F5 on {{site.data.keyword.cloud_notm}} ou FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installé, vous devez faire migrer les machines virtuelles F5 BIG-IP et FortiGate vers un autre serveur ESXi que celui sur lequel elles sont hébergées.
* Avant de supprimer des serveurs ESXi sur lesquels le service IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} est installé, vérifiez qu'aucune opération de sauvegarde ou de restauration (en échec ou en cours) n'est active, car ce type d'opération pourrait empêcher la suppression des serveurs ESXi.
* Lorsque vous retirez des serveurs ESXi, ceux-ci sont placés en mode maintenance, puis toutes les machines virtuelles qui s'exécutent sur les serveurs sont migrées avant d'être retirées de vCenter Server. Pour un contrôle maximum de la réimplantation des machines virtuelles, il est recommandé de placer les serveurs ESXi à supprimer en mode maintenance et de migrer manuellement les machines virtuelles qui s'exécutent sur ces serveur à l'aide du client Web VMware vSphere. Ensuite, retirez les serveurs ESXi à l'aide de la console {{site.data.keyword.vmwaresolutions_short}}.

### Procédure de retrait de serveurs ESXi

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le panneau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez réduire la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster sur lequel vous désirez retirer des serveurs ESXi.
5. Dans la section **Serveurs ESXi**, sélectionnez les serveurs que vous désirez supprimer et cliquez sur **Retirer**.

### Résultats après le retrait de serveurs ESXi

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande de retrait de serveurs ESXi est en cours de traitement. Sur la console, le statut du cluster qui est associé aux serveurs ESXi passe à **Modification en cours**.
3. Les serveurs ESXi sont complètement récupérés par l'infrastructure {{site.data.keyword.cloud_notm}} à la fin de son cycle de facturation, lequel est généralement de 30 jours.

   Les serveurs ESXi retirés vous sont facturés jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.
   {:note}

## Ajout de stockage NFS à des instances vCenter Server

### Avant d'ajouter du stockage NFS

N'ajoutez pas de stockage NFS depuis le client Web VMware vSphere. Les modifications apportées sur le client Web vSphere ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}. IBM ne pourra pas gérer les partages de fichiers NFS que vous ajoutez manuellement à une instance.

### Procédure pour l'ajout de stockage NFS

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez accroître la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster auquel vous souhaitez ajouter du stockage NFS.
5. Dans la section **Stockage**, cliquez sur **Ajouter**.
6. Dans la fenêtre **Stockage**, configurez le stockage.
   * Si vous souhaitez ajouter et configurer les mêmes paramètres pour tous les partages de fichiers, renseignez les zones **Nombre de partages**, **Performances** et **Taille (Go)**.
   * Si vous souhaitez ajouter et configurer des partages de fichiers individuellement, renseignez les zones **Configurer les partages individuellement**, puis cliquez sur l'icône **+** en regard de l'option d'**ajout de stockage partagé**. Renseignez ensuite les zones **Performances** et **Taille (Go)** pour chaque partage de fichiers individuel. Vous devez sélectionner au moins un partage de fichiers.
7. Cliquez sur l'option d'**ajout de stockage NFS**.

### Résultats après l'ajout de stockage NFS

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande d'ajout de stockage NFS est en cours de traitement. Sur la console, le statut du cluster qui est associé au stockage NFS passe à **Modification en cours**.
3. Si vous ne voyez pas le stockage NFS ajouté dans la liste du cluster, consultez vos courriers électroniques ou les notifications de la console pour obtenir plus de détails sur la cause de l'échec.

## Retrait de stockage NFS dans des instances vCenter Server

### Avant de retirer du stockage NFS

* Ne retirez pas de stockage NFS depuis le client Web VMware vSphere. Les modifications apportées sur le client Web vSphere ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}.
* Avant de retirer le stockage NFS, assurez-vous d'avoir retiré toutes les machines virtuelles qui résident dans le stockage.
* Vérifiez que les partages que vous prévoyez de retirer sont associés à l'instance vCenter Server correcte.
* Le cluster doit être à l'état **Prêt à l'emploi**.

### Procédure pour le retrait de stockage NFS

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le panneau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez réduire la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster dont vous souhaitez retirer du stockage NFS.
5. Dans la section **Stockage**, sélectionnez le partage de stockage que vous voulez retirer et cliquez sur **Supprimer**.
6. Cliquez sur **Retirer** dans la fenêtre **Retirer le stockage**.

### Résultats après le retrait de stockage NFS

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande de retrait de stockage NFS est en cours de traitement. Sur la console, le statut du cluster qui est associé au stockage NFS passe à **Modification en cours**.
3. Le stockage NFS est complètement récupéré par l'infrastructure {{site.data.keyword.cloud_notm}} à la fin de son cycle de facturation, lequel est généralement de 30 jours.

   Les services retirés vous sont facturés jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.
   {:note}


### Liens connexes

* [Nomenclature de vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_bom.html)
* [Exigences et planification pour les instances vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_planning.html)
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [Ajout, affichage et suppression de clusters pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)
* [Activer le mode maintenance sur un hôte](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
