---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Extension et réduction de capacité pour des instances vCenter Server with Hybridity Bundle

Vous pouvez accroître ou réduire la capacité de votre instance VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle en fonction de vos besoins métier, en ajoutant ou en retirant des serveurs ESXi.

Etant donné que votre cluster initial dispose d'un stockage vSAN, l'ajout d'un ou de plusieurs serveurs ESXi après le déploiement peut permettre d'augmenter la capacité de stockage du cluster.

## Ajout de serveurs ESXi à des instances vCenter Server avec Hybridity Bundle

### Avant d'ajouter des serveurs ESXi

* N'ajoutez pas de serveurs ESXi depuis le client Web VMware vSphere. Les modifications apportées sur le client Web vSphere ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}.
* Le stockage vSAN nécessite au moins 4 serveurs ESXi.

## Procédure d'ajout de serveurs ESXi

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez accroître la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster auquel vous désirez ajouter des serveurs ESXi.
5. Dans le tableau **Serveurs ESXi**, cliquez sur **Ajouter**.
6. Dans la fenêtre **Ajouter un serveur**, indiquez le nombre de serveurs que vous voulez ajouter, cliquez sur le lien correspondant au prix pour passer en revue le coût estimé, puis cliquez sur **Ajouter**.

### Résultats après l'ajout de serveurs ESXi

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande d'ajout de serveurs ESXi est en cours de traitement. Sur la console, le statut du cluster qui est associé aux serveurs ESXi passe à **Modification en cours**.
3. Si vous ne voyez pas les nouveaux serveurs ESXi ajoutés dans la liste du cluster, consultez vos courriers électroniques ou les notifications de la console pour obtenir plus de détails sur la cause de l'échec.

## Retrait de serveurs ESXi sur des instances vCenter Server avec Hybridity Bundle

### Avant de retirer des serveurs ESXi

* Ne retirez pas de serveurs ESXi depuis le client Web VMware vSphere. Les modifications apportées sur le client Web vSphere ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}.
* Le stockage vSAN nécessite au moins 4 serveurs ESXi.
* Avant de retirer des serveurs ESXi avec le service F5 on {{site.data.keyword.cloud_notm}} ou FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installé, vous devez faire migrer les machines virtuelles F5 BIG-IP et FortiGate vers un autre serveur ESXi que celui sur lequel elles sont hébergées.
* Avant de retirer des serveurs ESXi sur lesquels le service IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} est installé, vérifiez qu'aucune opération de sauvegarde ou de restauration (en échec ou en cours) n'est active, car ce type d'opération pourrait empêcher le retrait des serveurs ESXi.
* Lorsque vous retirez des serveurs ESXi, ceux-ci sont placés en mode maintenance, puis toutes les machines virtuelles qui s'exécutent sur les serveurs sont migrées avant d'être retirées de vCenter Server. Pour un contrôle maximum de la réimplantation des machines virtuelles, il est recommandé de placer les serveurs ESXi à supprimer en mode maintenance et de migrer manuellement les machines virtuelles qui s'exécutent sur ces serveur à l'aide du client Web VMware vSphere. Ensuite, supprimez les serveurs ESXi à l'aide de la console {{site.data.keyword.vmwaresolutions_short}}.

## Procédure de retrait de serveurs ESXi

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le panneau **Instances vCenter Server**, cliquez sur l'instance dont vous désirez réduire la capacité.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
4. Dans le tableau **CLUSTERS**, cliquez sur le cluster sur lequel vous désirez retirer des serveurs ESXi.
5. Dans le tableau **Serveurs ESXi**, sélectionnez les serveurs que vous désirez supprimer et cliquez sur **Retirer**.

### Conséquences du retrait de serveurs ESXi

1. Un bref délai peut être observé sur la console entre le passage du statut **Prêt à l'emploi** au statut **Modification en cours**. Laissez l'opération s'exécuter complètement avant d'apporter d'autres modifications à l'instance.
2. Un courrier électronique vous avise que votre demande de retrait de serveurs ESXi est en cours de traitement. Sur la console, le statut du cluster associé aux serveurs ESXi passe à **Modification en cours**.
3. Les serveurs ESXi sont complètement récupérés par l'infrastructure {{site.data.keyword.cloud_notm}} à la fin de son cycle de facturation, lequel est généralement de 30 jours.

   Les serveurs ESXi retirés vous sont facturés jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.{:note}

### Liens connexes

* [Nomenclature de vCenter Server](vc_bom.html)
* [Exigences et planification pour les instances vCenter Server with Hybridity Bundle](vc_hybrid_planning.html)
* [Ajout, affichage et suppression de clusters pour des instances vCenter Server with Hybridity Bundle](vc_hybrid_addingviewingclusters.html)
* [Activer le mode maintenance sur un hôte](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
