---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations}

Le service Caveonix RiskForesight on {{site.data.keyword.cloud}} peut vous aider à gérer la cybersécurité et le risque de conformité à l'aide de contrôles de surveillance proactive et de défense automatisée destinés à assurer une protection contre les menaces et à permettre la conformité aux réglementations de l'industrie et du gouvernement. 

Ce service est disponible uniquement pour les instances VMware vCenter Server on {{site.data.keyword.cloud_notm}} qui sont déployées dans la version 2.9 ou ultérieure.
{:note}

## Spécifications techniques relatives à Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-specs}

Les composants suivants sont commandés et inclus dans le service Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}. 

### Ressources vCenter
{: #caveonix_considerations-tech-specs-vcenter}

* UC : 8 vCPU
* Mémoire RAM : 32 Go
* Disque : 80 Go

###  Réseau
{: #caveonix_considerations-tech-specs-network}

Un sous-réseau privé dédié avec 64 adresses IP est commandé. 

### Licences et frais
{: #caveonix_considerations-tech-specs-license-fee}

Une clé de licence Caveonix RiskForesight est commandée pour chaque instance du service.

## Remarques relatives à l'installation de Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-install}

Avant d'installer le service Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}, vérifiez que le nombre d'UC et la quantité de mémoire du cluster par défaut de votre instance de service suffisent pour la machine virtuelle Caveonix RiskForesight. 

## Remarques relatives au retrait de Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-remove}

Passez en revue les remarques suivantes avant de retirer le service Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} :
* Retirer le service Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} n'entraîne pas l'annulation de la licence Caveonix RiskForesight. Vous devez supprimer la licence Caveonix RiskForesight du tableau **Licences Caveonix RiskForesight** sur la page **Ressources** dans la console {{site.data.keyword.vmwaresolutions_short}}. 
* Lorsque vous retirez le service, l'automatisation {{site.data.keyword.vmwaresolutions_short}} supprime uniquement la seule machine virtuelle Caveonix "tout-en-un" qui a été déployée et le sous-réseau privé dédié qui a été commandé pour elle. Par conséquent,
   * si vous avez scindé la machine virtuelle Caveonix en plusieurs machines virtuelles, ces dernières ne sont pas retirées. 
   * Si vous avez utilisé les adresses IP du sous-réseau privé dédié sur des machines virtuelles supplémentaires, de nouvelles adresses IP doivent être affectées à ces dernières pour qu'elles puissent continuer à fonctionner.  
   * Si vous supprimez l'instance vCenter Server A avec le service Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} installé et que vous avez utilisé les adresses IP du sous-réseau privé dédié commandé pour le service dans l'instance vCenter Server B, le sous-réseau privé dédié est annulé lors de la suppression de l'instance vCenter Server A. 

## Liens connexes
{: #caveonix_considerations-related}

* [Commande de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Gestion de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingcaveonix)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
