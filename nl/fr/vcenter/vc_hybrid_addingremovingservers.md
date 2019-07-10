---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: vCenter Server Hybridity add host, add server vCenter Server Hybridity, remove host vCenter Server Hybridity

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Extension et réduction de capacité pour des instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservers}

Vous pouvez accroître ou réduire la capacité de votre instance VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle en fonction de vos besoins métier, en ajoutant ou en retirant des serveurs ESXi.

À partir de la version V3.1, vous pouvez ajouter de nouveaux serveurs ESXi à un cluster existant en sélectionnant une configuration existante ou une autre configuration que les hôtes existants du cluster. Les configurations existantes sont disponibles pour une sélection instantanée lorsque vous commandez votre nouveau serveur. Pour éviter les problèmes de performances ou de stabilité, il est recommandé que les clusters utilisent la même configuration ou une configuration similaire en ce qui concerne le processeur, la mémoire vive et le stockage. Cette fonctionnalité est utile pour les mises à jour matérielles au sein du même cluster.Un cluster ne peut posséder qu'un seul ype de stockage.

A compter de l'édition V2.9, vous pouvez ajouter de nouveaux serveurs ESXi à un cluster tandis que celui-ci est en mode maintenance. De plus, vous pouvez ajouter ou retirer simultanément des serveurs ESXi sur plusieurs clusters. Les opérations simultanées suivantes sont disponibles :

* Ajout d'hôtes à un cluster et ajout d'hôtes à d'autres clusters.
* Retrait d'hôtes d'un cluster et retrait d'hôtes d'autres clusters.
* Ajout d'hôtes à un cluster et retrait d'hôtes d'autres clusters.
* Retrait d'hôtes d'un cluster et ajout d'hôtes à d'autres clusters.

Etant donné que votre cluster initial dispose d'un stockage vSAN, l'ajout d'un ou de plusieurs serveurs ESXi après le déploiement peut permettre d'augmenter la capacité de stockage du cluster.

## Ajout de serveurs ESXi à des instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservers-adding}

### Avant d'ajouter des serveurs ESXi
{: #vc_hybrid_addingremovingservers-adding-prereq}

* Dans la mesure du possible, vous devez ajouter les serveurs ESXi à l'aide de la console {{site.data.keyword.vmwaresolutions_full}} car les modifications apportées au client VMware vSphere Web Client ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}. Par conséquent, ajoutez des serveurs ESXi à vCenter Server uniquement pour les serveurs ESXi sur site ou pour les serveurs ESXi que vous ne pouvez ou ne voulez pas gérer dans la console {{site.data.keyword.vmwaresolutions_short}}.
* Le stockage vSAN nécessite au moins 4 serveurs ESXi.

## Procédure d'ajout de serveurs ESXi
{: #vc_hybrid_addingremovingservers-adding-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez accroître la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster auquel vous désirez ajouter des serveurs ESXi.
5. Dans le tableau **Serveurs ESXi**, cliquez sur **Ajouter**.
6. Dans la fenêtre **Ajouter un serveur**, entrez le nombre de serveurs que vous voulez ajouter.
7. Le cas échéant, cochez la case permettant d'ajouter des serveurs alors que le mode maintenance est actif. La case à cocher est sélectionnée par défaut. 

   Lorsque vous mettez à disposition le nouveau serveur ESXi, les machines virtuelles (VM) sont immédiatement migrées vers les nouveaux serveurs si vous ne cochez pas la case **Mode maintenance**. Vous ne recevez pas de message de confirmation avant le début de la migration.
{:important}

8. Procédez à la configuration du serveur bare metal.
   * Sélectionnez une configuration parmi les hôtes existants du cluster. 
   * Sélectionnez une nouvelle configuration {{site.data.keyword.baremetal_short_sing}}, puis spécifiez le modèle d'UC et la taille de mémoire RAM. 
9. Procédez à la configuration du stockage. Spécifiez les types de disque pour les disques de cache et de capacité, le nombre de disques et l'édition de licence vSAN. Si vous souhaitez obtenir davantage de stockage, cochez la zone **Hautes performances avec Intel Optane**.
10. Passez en revue le coût estimé et cliquez sur **Ajouter**.

  Vous pouvez également ajouter les ressources mises à disposition à l’outil d’estimation {{site.data.keyword.cloud_notm}} en cliquant sur **Ajouter à l'estimation**. Cela est utile si vous souhaitez estimer le coût des ressources {{site.data.keyword.vmwaresolutions_short}} sélectionnées avec d'autres ressources {{site.data.keyword.cloud_notm}} que vous pourriez envisager d'acheter.

### Que se passe-t-il après l'ajout de serveurs ESXi ?  
{: #vc_hybrid_addingremovingservers-adding-results}

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande d'ajout de serveurs ESXi est en cours de traitement. Sur la console, le statut du cluster qui est associé aux serveurs ESXi passe à **Modification en cours**.
3. Si vous ne voyez pas les nouveaux serveurs ESXi ajoutés dans la liste du cluster, consultez vos courriers électroniques ou les notifications de la console pour obtenir plus de détails sur la cause de l'échec.

Si vous ajoutez des serveurs ESXi alors que le mode maintenance est actif, les machines virtuelles ne sont pas migrées vers les nouveaux serveurs tant que le mode maintenance n'est pas désactivé pour le cluster.   
{:important}

## Retrait de serveurs ESXi sur des instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservers-removing}

### Avant de retirer des serveurs ESXi
{: #vc_hybrid_addingremovingservers-removing-prereq}

* Dans la mesure du possible, vous devez retirer les serveurs ESXi à l'aide de la console {{site.data.keyword.vmwaresolutions_full}} car les modifications apportées au client vSphere Web Client ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}. Par conséquent, retirez des serveurs ESXi de vCenter Server uniquement en cas de serveurs ESXi sur site ou pour les serveurs ESXi que vous ne pouvez ou ne voulez pas gérer dans la console {{site.data.keyword.vmwaresolutions_short}}.
* Le stockage vSAN nécessite au moins 4 serveurs ESXi.
* Avant de retirer des serveurs ESXi avec le service F5 on {{site.data.keyword.cloud_notm}} ou FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installé, vous devez faire migrer les machines virtuelles F5 BIG-IP et FortiGate vers un autre serveur ESXi que celui sur lequel elles sont hébergées.
* Avant de retirer des serveurs ESXi sur lesquels le service IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} est installé, vérifiez qu'aucune opération de sauvegarde ou de restauration (en échec ou en cours) n'est active, car ce type d'opération pourrait empêcher le retrait des serveurs ESXi.
* Lorsque vous retirez des serveurs ESXi, ceux-ci sont placés en mode maintenance, puis toutes les machines virtuelles qui s'exécutent sur les serveurs sont migrées avant d'être retirées de vCenter Server. Pour un contrôle maximum de la réimplantation des machines virtuelles, il est recommandé de placer les serveurs ESXi à supprimer en mode maintenance et de migrer manuellement les machines virtuelles qui s'exécutent sur ces serveur à l'aide du client Web VMware vSphere. Ensuite, supprimez les serveurs ESXi à l'aide de la console {{site.data.keyword.vmwaresolutions_short}}.

## Procédure de retrait de serveurs ESXi
{: #vc_hybrid_addingremovingservers-removing-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le panneau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez réduire la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster sur lequel vous désirez retirer des serveurs ESXi.
5. Dans le tableau **Serveurs ESXi**, sélectionnez les serveurs que vous désirez supprimer et cliquez sur **Retirer**.

### Conséquences du retrait de serveurs ESXi
{: #vc_hybrid_addingremovingservers-removing-results}

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande de retrait de serveurs ESXi est en cours de traitement. Sur la console, le statut du cluster associé aux serveurs ESXi passe à **Modification en cours**.
3. Les serveurs ESXi sont complètement récupérés par l'infrastructure {{site.data.keyword.cloud_notm}} à la fin de son cycle de facturation, lequel est généralement de 30 jours.

   Les serveurs ESXi retirés vous sont facturés jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.
   {:note}

## Liens connexes
{: #vc_hybrid_addingremovingservers-related}

* [Nomenclature de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Exigences et planification pour les instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Ajout, affichage et suppression de clusters pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [Place a host in maintenance mode](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/s/article/1003212){:new_window}
