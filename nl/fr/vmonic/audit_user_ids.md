---

copyright:

  years: 2016, 2019

lastupdated: "2019-05-31"

keywords: user IDs vCenter, PSC user, user ID service

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# ID utilisateur IBM
{: #audit_user_ids}

{{site.data.keyword.vmwaresolutions_short}} maintient un ensemble d'utilisateurs dans votre compte à utiliser par l'automatisation {{site.data.keyword.cloud_notm}} lorsque vous effectuez des opérations telles que l'ajout de serveurs, de clusters ou le stockage à votre instance VMware. Les ID utilisateur de votre compte peuvent également être utilisés pour l'installation et la configuration de services par l'automatisation des services {{site.data.keyword.cloud_notm}}. Passez en revue les sections suivantes relatives aux ID utilisateur utilisés par l'automatisation {{site.data.keyword.cloud_notm}}.

Les opérations des instances VMware échouent si les ID utilisateur IBM sont supprimés, désactivés ou si leurs mots de passe sont modifiés.
{:important}

## ID utilisateur du vCenter et de PSC (Platform Services Controller)
{: #audit_user_ids-vcenter-psc}

A partir de la version 2.5, {{site.data.keyword.vmwaresolutions_short}} utilise les ID utilisateur suivants pour ajouter une source d'identité, intégréé par défaut, dans vCenter.

Tableau 1. ID utilisateur de vCenter et PSC (Platform Services Controller)

| Utilisateur     | ID utilisateur      | Méthode | Description |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | Utilisé pour la configuration de VMware, par exemple pour la configuration de la haute disponibilité dans VMware et la création de commutateurs distribués. Utilisé après le déploiement pour coupler les instances principales et secondaires de vCenter Server. |
| Client | customerroot | SSH    | Créé uniquement pour l'utilisation par les clients. |
| IBM      | automation@``root_domain``<br/>(utilisateur Active Directory) | HTTP | Utilisé après le déploiement pour ajouter et supprimer des hôtes et des clusters et pour déployer et configurer des machines virtuelles pour les services complémentaires. |
| Client | Administrator@vsphere.local | HTTP | Créé uniquement pour l'utilisation par les clients. |

HTTP est utilisé pour l'installation et la configuration de vCenter, ainsi que pour les opérations VMware telles que l'ajout d'hôtes, de clusters ou de stockage pour la gestion des ressources de vCenter.
{:note}

## ID utilisateur de NSX Manager
{: #audit_user_ids-nsx-mgr}

Tableau 2. ID utilisateur de NSX Manager

| Utilisateur     | ID utilisateur      | Description |
|:---------|:-------------|:------------|
| IBM      | automation@``root_domain``<br/>(utilisateur Active Directory) | Utilisé après le déploiement pour gérer les adresses IP NSX VTEP, gérer la configuration des hôtes et des clusters lors de l'ajout et de la suppression d'hôtes et de clusters, et gérer la configuration ESG pour les services complémentaires qui nécessitent un accès au réseau public pour l'octroi de licence, l'activation ou les rapports d'utilisation. |
| Client | Administrateur        | Créé uniquement pour l'utilisation par les clients. |

## ID utilisateur des hôtes ESXi
{: #audit_user_ids-esxi}

Tableau 3. ID utilisateur des hôtes ESXi

| Utilisateur     | ID utilisateur      | Description |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | Utilisé après le déploiement pour ajouter un stockage NFS additionnel, configurer des routes pour ce stockage et exécuter tout le code de validation du serveur. |
| Client | root         | Créé uniquement pour l'utilisation par les clients. |

## ID utilisateur de Microsoft Active Directory
{: #audit_user_ids-ad}

Table 4. ID utilisateur d'Active Directory

| Utilisateur     | ID utilisateur       | Description |
|:---------|:------------- |:------------|
| IBM      | automation    | Permet d'ajouter un hôte, d'ajouter une machine virtuelle pour le service et pour configurer Active Directory et les entrées DNS. |
| Client | Administrateur | Créé uniquement pour l'utilisation par les clients. |

## ID utilisateur de service
{: #audit_user_ids-services}

Tableau 5. ID utilisateur de service

| ID utilisateur                                    | Description |
|:-------------------------------------------|:----------- |
| prod-BigIP-``dynamic_ID``-@``domain name`` | Utilisé pour l'installation et la configuration de F5 sur le service {{site.data.keyword.cloud_notm}}. |
| prod-Caveonix-``dynamic_ID``-@``domain name`` | Utilisé pour l'installation et la configuration de Caveonix RiskForesight sur le service {{site.data.keyword.cloud_notm}}. |
| prod-Fortigate-``dynamic_ID``-@``domain name`` | Utilisé pour l'installation et la configuration de FortiGate Security Appliance sur le service {{site.data.keyword.cloud_notm}}. |
| prod-FortigateVM-``dynamic_ID``-@``domain name`` | Utilisé pour l'installation et la configuration de FortiGate Virtual Appliance sur le service {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustCC-``5_letter_ID``-@``domain name`` | Utilisé pour l'installation et la configuration de HyTrust CloudControl sur le service {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustDC-``5_letter_ID``-@``domain name`` | Utilisé pour l'installation et la configuration de HyTrust DataControl sur le service {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustKC-``5_letter_ID``-@``domain name`` | Utilisé pour l'installation et la configuration de HyTrust KeyControl sur le service {{site.data.keyword.cloud_notm}}. |
| prod-KMIPAdapter-``dynamic_ID``-@``domain name`` | Utilisé pour l'installation et la configuration de KMIP for VMware sur le service {{site.data.keyword.cloud_notm}}. |
| prod-ICP-``dynamic_ID``-@``domain name`` | Utilisé pour l'installation et la configuration du service {{site.data.keyword.cloud_notm}} Private Hosted. |
| prod-SPPlus-``dynamic_ID``-@``domain name`` | Utilisé pour l'installation et la configuration d'IBM Spectrum Protect Plus sur le service {{site.data.keyword.cloud_notm}}. |
| prod-Veeam-``dynamic_ID``-@``domain name`` | Utilisé pour l'installation et la configuration de Veeam sur le service {{site.data.keyword.cloud_notm}}. |
| prod-HCX-``dynamic_ID``-@``domain name`` | Utilisé pour l'installation et la configuration de VMware HCX sur le service {{site.data.keyword.cloud_notm}}. |
| prod-Zerto-``dynamic_ID``-@``domain name`` | Utilisé pour l'installation et la configuration de Zerto sur le service {{site.data.keyword.cloud_notm}}. |

Les identificateurs dynamiques ont une longueur de huit à dix lettres.
{:note}

## Liens connexes
{: #audit_user_ids-related}

* [Remarques relatives à la modification des artefacts vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Evénements du service Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)
