---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-02"

keywords: vmware solutions events, activity tracker, event details

subcollection: vmware-solutions


---

# Evénements du service Activity Tracker
{: #at-events}

Le service {{site.data.keyword.cloudaccesstrailfull}} vous permet de suivre la manière dont les utilisateurs et les applications interagissent avec {{site.data.keyword.vmwaresolutions_short}} dans {{site.data.keyword.cloud_notm}}.

Le service {{site.data.keyword.cloudaccesstrailfull_notm}} enregistre les activités initiées par l'utilisateur qui changent l'état d'un service dans {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [A propos d'IBM® Cloud Activity Tracker avec LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#gs_ov).

## Tableau Evénements du service Activity Tracker
{: #at-events-table}

Consultez le tableau suivant pour obtenir une description des colonnes du tableau Evénements du service Activity Tracker.

| Colonne                | Type de valeur | Description |
|:----------------------|:-----------|:------------|
| Time                  | Non applicable        | Date et heure de création de l'événement. |
| initiator.name        | Chaîne     | IBMid de l'utilisateur qui initie l'action. |
| target_name           | Chaîne     | Ressource sur laquelle l'action est exécutée. |
| target.typeURI        | Chaîne     | UUID de la cible sur laquelle l'action est exécutée. |
| action                | Chaîne     | Action qui déclenche l'événement. Les valeurs valides sont `create`, `update` et `delete`. |
| outcome               | Chaîne     | Résultat de l'action. La valeur est `success`, `failure` ou `pending`. |
| reason_reasonCode     | Entier    | Code raison du résultat. |
| initiator_host_address| Chaîne     | Adresse IP d'où provient la demande. |
{: caption="Table 1. Description du tableau Evénements du service Activity Tracker" caption-side="top"}

Pour plus d'informations, voir [Zones d'événement](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-event).

## Suivi des événements de gestion des instances
{: #at-events-instance-mgmt}

Lorsque vous gérez des comptes utilisateur, des instances, des clusters et des services dans {{site.data.keyword.vmwaresolutions_short}}, un événement est généré et envoyé au **domaine de compte** dans Activity Tracker.

Consultez le tableau suivant pour plus de détails sur les actions qui génèrent et envoient des événements de gestion à Activity Tracker.

| Action                                   | Description | Résultat |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.account-apikey.update` | La clé API d'infrastructure d'un compte est mise à jour. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.account-notification.update` | Le paramètre de notification pour un compte est mis à jour. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-secure-data.wipe` | Les données sécurisées de l'instance sont effacées. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-bss-account.migrate` |	Une instance est migrée vers un compte BSS. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.create` | Une instance de vCenter Server est créée. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.delete` | Une instance de vCenter Server est supprimée. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.add` | Un hôte est ajouté à une instance de vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.remove` | Un hôte est supprimé d'une instance de vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.update` | Une instance de vCenter Server est mise à jour. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.create` | Un cluster est créé pour une instance de vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.delete` | Un cluster est supprimé pour une instance de vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nsx-license.update` | La licence NSX est mise à jour pour une instance de serveur vCenter. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.add` | Le bundle hybridity est mis à niveau pour une instance de vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.remove` | Le bundle hybridity est supprimé d'une instance de serveur vCenter. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.add` | Le stockage NFS est ajouté à une instance de vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.remove` | Le stockage NFS est retiré d'une instance de vCenter Server. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-plan.update` | Un plan d'instance de vCenter Server est mise à jour. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.create` | Une instance de vSphere est créée. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.update` | Une instance de vSphere est mise à jour. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss-template.remove` | Un modèle vSphere est supprimé. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.create` | Un service est créé. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.delete` | Un service est supprimé. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service-hybridity.upgrade` | Un bundle hybridity est mis à niveau vers `version`. | `pending`<br>`success`<br>`failure` |
{: caption="Table 2. Description des actions qui génèrent des événements de gestion" caption-side="top"}

## Suivi des événements pour le service KMIP for VMware on IBM Cloud
{: #at-events-kmip}

Lorsque vous gérez des clés pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}, un événement est généré et envoyé au **domaine de compte** dans Activity Tracker.

Consultez le tableau suivant pour plus de détails sur les actions qui génèrent et envoient des événements pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}.

| Action                                      | Description                               | Résultat |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.kmip-key.create` | Une clé KMIP est créée. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.retrieve` | Une clé KMIP est extraite. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key-attributes.retrieve` | Les attributs d'une clé KMIP sont extraits. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.activate` | Une clé KMIP est activée. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.revoke` | Une clé KMIP est révoquée. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.destroy` | Une clé KMIP est détruite. | `pending`<br>`success`<br>`failure` |
{: caption="Table 3. Description des actions qui génèrent des événements pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Où consulter les événements
{: #at-events-viewing}

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}} qui se trouve dans la région {{site.data.keyword.cloud_notm}} où les événements sont générés.

Utilisez {{site.data.keyword.cloud_notm}} Activity Tracker avec LogDNA pour afficher l'instance. Pour plus d'informations, voir [Affichage des événements](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-view_events).

## Liens connexes
{: #at-events-related}

* [Mise à disposition d'une instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [Accès à l'interface utilisateur Web](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [Présentation de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
