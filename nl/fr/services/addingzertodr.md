---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de Zerto on IBM Cloud
{: #addingzertodr}

Le service Zerto on {{site.data.keyword.cloud}} fournit des fonctions de réplication et de reprise après incident, qui peuvent être intégrées aux offres de déploiement de manière à assurer la protection et la récupération des données dans votre environnement virtuel VMware sur {{site.data.keyword.cloud_notm}}.

Ce service est disponible uniquement sur les instances qui sont déployées en version 1.2 ou dans des versions ultérieures. La version de Zerto en cours qui est installée est 6.5 update 3.
{:note}

## Spécifications techniques relatives à Zerto on IBM Cloud
{: #addingzertodr-specs}

Les composants suivants sont commandés et inclus dans le service Zerto on {{site.data.keyword.cloud_notm}} :

Les composants Zerto Virtual Replication Appliance (VRA) ne sont déployés que dans le cluster par défaut.
{:note}

### Instances de serveur virtuel
{: #addingzertodr-specs-vsi}

* Une instance de serveur virtuel - Zerto Virtual Manager
* 2 coeurs de 2 GHz
* 4 Go de mémoire RAM
* Windows Server 2016 Standard Edition (64 bits)

### Stockage
{: #addingzertodr-specs-storage}

Disque (SAN) 100 Go

### Utilisation en réseau
{: #addingzertodr-specs-network}

* Une adresse IP privée principale
* Liaison montante de réseau privé 1 Gbps

### Licences et frais
{: #addingzertodr-specs-licenses}

Licence Zerto Replication V6.5 update 3

## Liens connexes
{: #addingzertodr-related}

* [Commande de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Gestion de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Demande de services gérés pour Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Site Web zerto.com](https://www.zerto.com){:new_window}
* [Documentation technique Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
