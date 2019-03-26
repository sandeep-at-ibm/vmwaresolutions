---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestion de Caveonix RiskForesight on IBM Cloud
{: #managingcaveonix}

## Accès à la console Caveonix RiskForesight
{: #managingcaveonix-access-console}

Pour gérer le service Caveonix RiskForesight on {{site.data.keyword.cloud}}, vous devez accéder à la console Caveonix RiskForesight en procédant comme suit :

1. Utilisez le réseau privé virtuel de l'infrastructure IBM Cloud ou un serveur intermédiaire pour autoriser l'accès à l'adresse IP de la machine virtuelle Caveonix RiskForesight. Vous trouverez l'adresse IP sur la page des détails de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} dans la console {{site.data.keyword.vmwaresolutions_short}}. Plus spécifiquement : 
   1. Créez un mot de passe de réseau privé virtuel à partir du portail client de l'infrastructure {{site.data.keyword.cloud_notm}}.
   2. Connectez-vous au portail du réseau privé virtuel du centre de données à l'aide des données d'identification de réseau privé virtuel de l'infrastructure {{site.data.keyword.cloud_notm}}.
   3. Ajoutez le mappage d'adresse IP et de nom d'hôte dans le fichier hosts en respectant le format suivant :

      ```javascript
      IPAddress              HostName
      ```
2. Pour accéder à la console Caveonix RiskForesight, cliquez sur **Afficher la console RiskForesight** sur la page des détails de service de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}, puis connectez-vous à l'aide des données d'identification répertoriées sur cette même page des détails de service.

## Application de mises à jour à Caveonix RiskForesight on IBM Cloud
{: #managingcaveonix-update}

C'est à vous qu'il incombe de faire en sorte que le logiciel Caveonix RiskForesight soit toujours utilisé dans sa version la plus récente. Vous pouvez télécharger les mises à jour requises à partir de la page [Caveonix Service Provider Portal](https://support.caveonix.com).

## Mise à jour des licences Caveonix RiskForesight

La licence Caveonix RiskForesight est valide pendant un an. Vous pouvez mettre à jour la licence Caveonix RiskForesight lorsqu'elle arrive à expiration en utilisant la procédure suivante :
1. Commandez une nouvelle licence Caveonix RiskForesight et copiez-la dans la console Caveonix RiskForesight. Pour plus d'informations, voir [Procédure de commande de licences Caveonix RiskForesight](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_ordering#caveonix_license_ordering-procedure).
2. Supprimez la licence arrivée à expiration du tableau **Licences Caveonix RiskForesight** dans la console {{site.data.keyword.vmwaresolutions_short}}. Pour plus d'informations, voir [Procédure de suppression de licences Caveonix RiskForesight](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_managing#caveonix_license_managing_procedure-delete).

## Liens connexes
{: #managingcaveonix-related}

* [Présentation de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Commande de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
