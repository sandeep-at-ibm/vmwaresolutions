---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-12"

---

# Evénements d'Activity Tracker
{: #at-events}

Le service {{site.data.keyword.cloudaccesstrailfull}} vous permet de suivre la manière dont les utilisateurs et les applications interagissent avec {{site.data.keyword.vmwaresolutions_short}} dans {{site.data.keyword.Bluemix_notm}}.

Le service {{site.data.keyword.cloudaccesstrailfull_notm}} enregistre les activités initiées par l'utilisateur qui changent l'état d'un service dans {{site.data.keyword.Bluemix_notm}}. Pour plus d'information, voir le document [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla).

## Tableau d'événements d'Activity Tracker
{: #at-events-table}

Consultez le tableau suivant pour obtenir une description des colonnes du tableau Evénements du service Activity Tracker.

Table 1. Description du tableau Evénements du service Activity Tracker

| Colonne                | Type de valeur | Description |
|:----------------------|:-----------|:------------|
| Time                  | Non applicable        | Date et heure de création de l'événement. |
| initiator.name        | Chaîne     | IBMid de l'utilisateur qui initie l'action. |
| target_name           | Chaîne     | Ressource sur laquelle l'action est exécutée. |
| target.typeURI        | Chaîne     | UUID de la cible sur laquelle l'action est exécutée. |
| action                | Chaîne     | Action qui déclenche l'événement. Les valeurs valides sont `create`, `update` et `delete`. |
| outcome               | Chaîne     | Résultat de l'action. La valeur est `réussite`, `échec` ou `en attente`. |
| reason_reasonCode     | Entier    | Code raison du résultat. |
| initiator_host_address| Chaîne     | Adresse IP d'où provient la demande. |

Pour plus d'informations, voir [Zones des événements du service Activity Tracker](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event).

## Suivi des événements de gestion des instances
{: #at-events-instance-mgmt}

Lorsque vous gérez des comptes utilisateur, des instances, des clusters et des services dans {{site.data.keyword.vmwaresolutions_short}}, un événement est généré et envoyé au **domaine de compte** dans Activity Tracker.

Consultez le tableau suivant pour plus de détails sur les actions qui génèrent et envoient des événements de gestion à Activity Tracker.

Table 2. Description des actions qui génèrent des événements de gestion

| Action                                   | Description | Résultat |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.user_account.update`    | <ul><li>La demande de mise à jour du compte utilisateur est reçue.</li><li>La demande de mise à jour du compte utilisateur reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.notification.update` | <ul><li>La demande de mise à jour des notification est reçue.</li><li>La demande de mise à jour des notification reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.secure_data.wipe`       | <ul><li>La demande de nettoyage des données sécurisées est reçue.</li><li>La demande de nettoyage des données sécurisées reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.bss_account.migrate` | <ul><li>La demande de migration vers le compte bss compte est reçue.</li><li>La demande de migration vers le compte bss reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcf.delete`                | <ul><li>La demande de suppression d'une instance Cloud Foundation est reçue.</li><li>La demande de suppression d'une instance Cloud Foundation reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcf.add_hosts`             | <ul><li>La demande d'ajout de serveurs ESXi à une instance Cloud Foundation est reçue.</li><li>La demande d'ajout de serveurs ESXi à une instance Cloud Foundation reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcf.remove_hosts`          | <ul><li>La demande de suppression de serveurs ESXi d'une instance Cloud Foundation est reçue.</li><li>La demande de suppression de serveurs ESXi d'une instance Cloud Foundation reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcf.create_cluster`        | <ul><li>La demande de création d'un cluster pour une instance Cloud Foundation est reçue.</li> <li>La demande de création d'un cluster pour une instance Cloud Foundation reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcf.delete_cluster`        | <ul><li>La demande de suppression d'un cluster pour une instance Cloud Foundation est reçue.</li><li>La demande de suppression d'un cluster pour une instance Cloud Foundation reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcf.schedule_update`       | <ul><li>La demande d'une planification de mise à jour pour une instance Cloud Foundation est reçue.</li><li>La demande d'une planification de mise à jour pour une instance Cloud Foundation reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcs.order`                 | <ul><li>La demande de commande d'une instance vCenter Server est reçue.</li><li>La demande de commande d'une instance vCenter Server reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcs.delete`                | <ul><li>La demande de suppression d'une instance vCenter Server est reçue.</li><li>La demande de suppression d'une instance vCenter Server reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcs.add_host`              | <ul><li>La demande d'ajout de serveurs ESXi à une instance vCenter Server est reçue.</li><li>La demande d'ajout de serveurs ESXi à une instance vCenter Server reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcs.remove_hosts`          | <ul><li>La demande de suppression de serveurs ESXi d'une instance vCenter Server est reçue.</li><li>La demande de suppression de serveurs ESXi d'une instance vCenter Server reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcs.schedule_update`       | <ul><li>La demande d'une planification de mise à jour pour une instance vCenter Server est reçue.</li><li>La demande d'une planification de mise à jour pour une instance vCenter Server reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcs.create_cluster`        | <ul><li>La demande de création d'un cluster pour une instance vCenter Server est reçue.</li><li>La demande de création d'un cluster pour une instance vCenter Server reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcs.delete_cluster`        | <ul><li>La demande de suppression d'un cluster d'une instance vCenter Server est reçue.</li> <li>La demande de suppression d'un cluster d'une instance vCenter Server reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcs.update_nsx_license`        | <ul><li>La demande de mise à jour de la licence VMware NSX est reçue.</li><li>La demande de mise à jour de la licence VMware NSX reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vcs.upgrade_to_hybridity`   | <ul><li>La demande de mise à niveau d'une instance vCenter Server vers un vCenter Server avec une instance Hybridity Bundle est reçue.</li><li>La demande de mise à niveau d'une instance vCenter Server vers un vCenter Server avec une instance Hybridity Bundle reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vsphere.order`              | <ul><li>La demande de commande d'un cluster vSphere est reçue.</li><li>La demande de commande d'un cluster vSphere reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vsphere.update`             | <ul><li>La demande de mise à jour d'un cluster vSphere est reçue.</li><li>La demande de mise à jour d'un cluster vSphere reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.vsphere.save_template`      | <ul><li>La demande de sauvegarde de la configuration d'un cluster vSphere est reçue.</li><li>La demande de sauvegarde de la configuration d'un cluster vSphere reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.netapp.order`               | <ul><li>La demande de commande d'une instance NetApp ONTAP Select est reçue.</li><li>La demande de commande d'une instance NetApp ONTAP Select reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.netapp.delete`              | <ul><li>La demande de suppression d'une instance NetApp ONTAP Select est reçue.</li><li>La demande de suppression d'une instance NetApp ONTAP Select reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.service_variable.update`    | <ul><li>La demande de mise à jour de la configuration d'un service est reçue.</li><li>La demande de mise à jour de la configuration d'un service reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.service.order`              | <ul><li>La demande de commande d'un service pour une instance est reçue.</li><li>La demande de commande d'un service pour une instance reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.service.delete_by_id`       | <ul><li>La demande de commande d'un service pour une instance reçoit une réponse.</li><li>La demande de suppression d'un service d'une instance reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.service.upgrade_to_hybridity` | <ul><li>La demande de mise à niveau d'une instance vCenter Server existante vers un vCenter Server avec une instance Hybridity Bundle est reçue.</li><li>La demande de mise à niveau d'une instance vCenter Server existante vers un vCenter Server avec une instance Hybridity Bundle reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.service.deploy` | L'action de déploiement d'un service est exécutée. | `réussite` |
| `vmware-solutions.service.undeploy` | L'action de retrait d'un service d'une instance est exécutée. | `réussite` |

## Suivi des événements pour le service KMIP for VMware on IBM Cloud
{: #at-events-kmip}

Lorsque vous gérez des clés pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}, un événement est généré et envoyé au **domaine de compte** dans Activity Tracker.

Consultez le tableau suivant pour plus de détails sur les actions qui génèrent et envoient des événements pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Table 3. Description des actions qui génèrent des événements pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Action                                      | Description                               | Résultat |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.key.create`               | <ul><li>La demande de création d'une clé est reçue.</li><li>La demande de création d'une clé reçoit une réponse.</li></ul> | <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.key.get`                  | <ul><li>La demande d'obtention du contenu d'une clé est reçue.</li><li>La demande d'obtention du contenu d'une clé reçoit une réponse.</li></ul> |  <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.key.get_attributes`       | <ul><li>La demande d'obtention des attributs d'une clé est reçue.</li><li>La demande d'obtention des attributs d'une clé reçoit une réponse.</li></ul> |  <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.key.activate`             | <ul><li>La demande d'activation d'une clé est reçue.</li><li>La demande d'activation d'une clé reçoit une réponse.</li></ul> |  <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.key.revoke`               | <ul><li>La demande de révocation d'une clé est reçue.</li><li>La demande de révocation d'une clé reçoit une réponse.</li></ul> |  <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.key.destroy`              | <ul><li>La demande de destruction d'une clé est reçue.</li><li>La demande de destruction d'une clé reçoit une réponse.</li></ul> |  <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |
| `vmware-solutions.key.discover_versions`    | <ul><li>La demande de recherche de la version du service KMIP for VMware on {{site.data.keyword.cloud_notm}} est reçue.</li><li>La demande de recherche de la version du service KMIP for VMware on {{site.data.keyword.cloud_notm}} reçoit une réponse.</li></ul> |  <ul><li>`en attente`</li><li>`réussite` ou `échec`</li></ul> |

## Où consulter les événements
{: #at-events-viewing}

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}} qui se trouve dans la région {{site.data.keyword.Bluemix_notm}} où les événements sont générés.

## Liens connexes
{: #at-events-related}

* [Mise à disposition d'Activity Tracker](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [Accès au tableau de bord Activity Tracker dans la console {{site.data.keyword.cloud_notm}}](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [Présentation de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
