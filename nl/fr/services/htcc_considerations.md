---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: HyTrust CloudControl, HTCC, tech specs HTCC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de HyTrust CloudControl on IBM Cloud
{: #htcc_considerations}

Le service HyTrust CloudControl on {{site.data.keyword.cloud}} applique et contrôle la conformité par rapport aux normes de sécurité standard, notamment le contrôle d'accès à base de rôles (RBAC) et les fonctions d'approbation et d'audit. Combiné à HyTrust DataControl, ce service garantit que les machines virtuelles et les données de charge de travail ne sortent pas d'une région, d'un cluster ou d'un serveur ESXi spécifique au sein de l'{{site.data.keyword.CloudDataCent_notm}}.

Ce service n'est disponible que pour les instances qui exécutent vSphere 6.5 et qui sont déployées dans ou mises à niveau vers la version 2.3 ou des éditions ultérieures. La version de HyTrust CloudControl en cours qui est installée est la version 5.5.1.
{:note}

## Spécifications techniques relatives à HyTrust CloudControl on IBM Cloud
{: #htcc_considerations-specs}

Les composants suivants sont commandés et inclus dans le service HyTrust CloudControl on {{site.data.keyword.cloud_notm}} :

### Dispositif HyTrust CloudControl
{: #htcc_considerations-appliance}

* UC : 4 vCPU
* Mémoire RAM : 16 Go
* Disque : VMDK 70 Go résident sur vSAN dans un cluster convergé
* Réseau : Placé sur un réseau portable privé VLAN spécifié pour la gestion

### Haute disponibilité
{: #htcc_considerations-ha}

Deux dispositifs CloudControl déployés dans une configuration active-passive

### Licences et frais
{: #htcc_considerations-licenses}

Licence par hôte : une licence HyTrust CloudControl est commandée pour chaque hôte de l'environnement

## Remarques relatives au retrait de HyTrust CloudControl on IBM Cloud
{: #htcc_considerations-remove}

Avant de retirer le service HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, prenez soin de désactiver la **mise en lieu sûr par mot de passe root**, si elle est configurée, et de supprimer tous les hôtes protégés sur HyTrust CloudControl.

## Liens connexes
{: #htcc_considerations-related}

* [Commande de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [Gestion de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Site Web HyTrust](https://www.hytrust.com/)
