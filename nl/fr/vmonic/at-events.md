---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-23"

keywords: IBM, activity tracker, LogDNA, event, security, VMware solutions events

subcollection: vmware-solutions


---

# Evénements du service Activity Tracker
{: #at-events}

Le service {{site.data.keyword.cloudaccesstrailfull}} vous permet de suivre la manière dont les utilisateurs et les applications interagissent avec {{site.data.keyword.vmwaresolutions_short}} dans {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.at_full_notm}} enregistre les activités initiées par l'utilisateur qui changent l'état d'un service dans {{site.data.keyword.cloud_notm}}. Vous pouvez utiliser ce service pour rechercher une activité anormale et des actions critiques, et pour vous conformer aux exigences d'audit réglementaires. De plus, vous pouvez être averti des actions à mesure qu'elles se produisent. Les événements collectés sont conformes à la norme CADF (Cloud Auditing Data Federation). Pour plus d'informations, voir [{{site.data.keyword.cloud_notm}} Activity Tracker avec LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).

## Suivi des événements de gestion des instances
{: #at-events-instance-mgmt}

Lorsque vous gérez des comptes utilisateur, des instances, des clusters et des services dans {{site.data.keyword.vmwaresolutions_short}}, un événement est généré et envoyé à un domaine global ou à une instance du service à l'emplacement où le service est mis à disposition. Pour plus d'informations, voir [Surveillance des événements dans le domaine global et par emplacement](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

Le tableau suivant répertorie les actions qui génèrent et envoient des événements de gestion à Activity Tracker.

| Action                                   | Description |
|:-----------------------------------------|:------------|
| `vmware-solutions.account-apikey.update` | La clé API d'infrastructure d'un compte est mise à jour. |
| `vmware-solutions.account-notification.update` | Le paramètre de notification pour un compte est mis à jour. |
| `vmware-solutions.instance-secure-data.wipe` | Les données sécurisées de l'instance sont effacées. |
| `vmware-solutions.instance-bss-account.migrate` |	Une instance est migrée vers un compte BSS. |
| `vmware-solutions.vcs.create` | Une instance de vCenter Server est créée. |
| `vmware-solutions.vcs.delete` | Une instance de vCenter Server est supprimée. |
| `vmware-solutions.vcs-host.add` | Un hôte est ajouté à une instance de vCenter Server. |
| `vmware-solutions.vcs-host.remove` | Un hôte est supprimé d'une instance de vCenter Server. |
| `vmware-solutions.vcs.update` | Une instance de vCenter Server est mise à jour. |
| `vmware-solutions.vcs-cluster.create` | Un cluster est créé pour une instance de vCenter Server. |
| `vmware-solutions.vcs-cluster.delete` | Un cluster est supprimé pour une instance de vCenter Server. |
| `vmware-solutions.vcs-nsx-license.update` | La licence NSX est mise à jour pour une instance de serveur vCenter. |
| `vmware-solutions.vcs-nfs-storage.add` | Le stockage NFS est ajouté à une instance de vCenter Server. |
| `vmware-solutions.vcs-nfs-storage.remove` | Le stockage NFS est retiré d'une instance de vCenter Server. |
| `vmware-solutions.vcs-plan.update` | Un plan d'instance de vCenter Server est mise à jour. |
| `vmware-solutions.vss.create` | Une instance de vSphere est créée. |
| `vmware-solutions.vss.update` | Une instance de vSphere est mise à jour. |
| `vmware-solutions.vss-template.remove` | Un modèle vSphere est supprimé. |
| `vmware-solutions.service.create` | Un service est créé. |
| `vmware-solutions.service.delete` | Un service est supprimé. |
{: caption="Tableau 1. Description des actions qui génèrent des événements de gestion" caption-side="top"}

## Suivi des événements pour le service KMIP for VMware on IBM Cloud
{: #at-events-kmip}

Lorsque vous gérez des clés pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}, un événement est généré et envoyé à un domaine global ou à une instance du service à l'emplacement où le service est mis à disposition. Pour plus d'informations, voir [Surveillance des événements dans le domaine global et par emplacement](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

Le tableau suivant répertorie les actions qui génèrent et envoient des événements pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}.

| Action                                      | Description                               |
|:--------------------------------------------|:------------------------------------------|
| `vmware-solutions.kmip-key.create` | Une clé KMIP est créée. |
| `vmware-solutions.kmip-key.retrieve` | Une clé KMIP est extraite. |
| `vmware-solutions.kmip-key-attributes.retrieve` | Les attributs d'une clé KMIP sont extraits. |
| `vmware-solutions.kmip-key.activate` | Une clé KMIP est activée. |
| `vmware-solutions.kmip-key.revoke` | Une clé KMIP est révoquée. |
| `vmware-solutions.kmip-key.destroy` | Une clé KMIP est détruite. |
{: caption="Tableau 2. Description des actions qui génèrent des événements pour le service KMIP for VMware on {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Où consulter les événements
{: #at-events-viewing}

Les événements sont disponibles à l'emplacement **Francfort**.

Il n'existe qu'une seule instance {{site.data.keyword.at_full_notm}} par emplacement. Pour afficher les événements, vous devez accéder à l'interface utilisateur Web du service {{site.data.keyword.at_full_notm}} à l'emplacement **EU-DE**. Pour plus d'informations, voir [Lancement de l'interface utilisateur Web via l'interface utilisateur IBM Cloud](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2).

## Liens connexes
{: #at-events-related}

* [Mise à disposition d'une instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [Accès à l'interface utilisateur Web](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [Présentation de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)
