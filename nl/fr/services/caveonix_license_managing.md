---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: Caveonix view license, Caveonix manage license, delete Caveonix license

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestion des licences Caveonix RiskForesight
{: #caveonix_license_managing}

Vous pouvez afficher, éditer des notes ou supprimer les licences Caveonix RiskForesight que vous avez commandées pour une utilisation autonome.

## Procédure d'affichage des licences Caveonix RiskForesight
{: #caveonix_license_managing_procedure-view}

1. Cliquez sur **Ressources** dans le panneau de navigation de gauche, puis faites défiler l'écran jusqu'au tableau **Licences Caveonix RiskForesight**.

   | Elément | Description |
   |:-----|:------------|
   | Nom | Nom de la licence. |
   | Heure de création | Date et heure de création de la licence. |
   | Statut | Statut de la licence : <br>Modification en cours : le licence est en cours de création.<br>Installé : la licence est prête à être utilisée.<br>Retrait en cours : la licence est en cours de suppression. |
   {: caption="Tableau 1. Description des éléments de licence Caveonix RiskForesight" caption-side="top"}

2. Pour afficher les informations relatives à une licence spécifique, cliquez sur celle-ci.

## Procédure d'édition des notes relatives aux licences Caveonix RiskForesight
{: #caveonix_license_managing_procedure-edit}

1. Cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Faites défiler l'écran vers le tableau **Licences Caveonix RiskForesight** et cliquez sur la licence dont vous souhaitez éditer les remarques.
3. Sur la page des détails de la licence, éditez les remarques de cette dernière, puis cliquez sur **Confirmer**.

## Problèmes connus relatifs à l'affichage de la date de licence
{: #caveonix_license_considerations-date}

Si vous utilisez Mozilla Firefox comme navigateur, il se peut qu'aucune valeur ne s'affiche pour les dates de début et de fin de la licence sur la console Caveonix RiskForesight. Pour résoudre ce problème, affichez les informations de licence dans un autre navigateur, tel que Google Chrome.

Si vous rencontrez ce problème et si le seul navigateur dont vous disposez est Firefox, contactez le [support Caveonix](https://www.caveonix.com/support/){:external} pour obtenir de l'aide.
{:note}

## Procédure de suppression de licences Caveonix RiskForesight
{: #caveonix_license_managing_procedure-delete}

Supprimer une licence Caveonix RiskForesight n'entraîne pas le retrait du service Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} qui est installé sur une instance vCenter Server.La suppression du service doit être effectuée dans la console {{site.data.keyword.vmwaresolutions_short}}. Pour plus d'informations, voir [Procédure de retrait de services pour des instances vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-removing-procedure).
{:note:}

1. Cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Faites défiler l'écran vers le tableau **Licences Caveonix RiskForesight** et localisez la licence à supprimer.
3. Dans la colonne **Actions**, cliquez sur l'icône de suppression.
4. Dans la fenêtre **Supprimer une licence**, cliquez sur **OK**.
   La licence prend le statut **Retrait en cours**. Lorsque la suppression de la licence est terminée, celle-ci n'est plus disponible dans le tableau **Licences Caveonix RiskForesight**.

## Liens connexes
{: #caveonix_license_managing-related}

* [Présentation de Caveonix RiskForesight]()
* [Commande de licences Caveonix RiskForesight](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)
