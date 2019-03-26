---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Application de mises à jour à des instances Cloud Foundation
{: #sd_applyingupdates}

La console {{site.data.keyword.vmwaresolutions_full}} détecte et répertorie régulièrement les mises à jour logicielles disponibles que vous pouvez appliquer à votre environnement virtuel VMware.

Une mise à jour disponible est un enregistrement dans la liste des mises à jour logicielles disponibles de l'instance, qui peut être appliquée immédiatement ou planifiée pour une application ultérieure. La mise à jour est une offre groupée qui contient un ou plusieurs packages pour la mise à jour des composants de gestion IBM et des composants VMware.

Les mises à jour IBM CloudDriver ne sont plus répertoriées car les mises à jour automatiques sont activées. Les actions telles que l'ajout d'un serveur ESXi, l'ajout d'un cluster et la commande d'un service entraînent la mise à jour automatique de l'instance vers la version la plus récente. Pour plus d'informations sur les mises à jour automatiques, voir la section *Résilience IBM CloudDriver* dans [Notes sur l'édition pour la version 2.5](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-relnotes_v25).
{:note}

## Avant de commencer
{: #sd_applyingupdates-prereq}

Avant d'appliquer une mise à jour, développez l'entrée de mise à jour en cliquant sur la flèche vers le bas et vérifiez les informations suivantes :
* La version de la mise à jour. Vous devez appliquer les mises à jour par ordre chronologique, c'est-à-dire de la plus ancienne à la plus récente. Assurez-vous d'avoir appliqué toutes les mises à jour précédentes avant d'appliquer la plus récente. Par exemple, vous devez appliquer la mise à jour V2.4 avant de tenter d'appliquer la mise à jour V2.5.
* Si un temps d'indisponibilité est nécessaire.
* Le temps total estimé pour effectuer la mise à jour.
* L'impact de la mise à jour sur l'environnement virtuel VMware. Le tableau 1 indique comment les différents niveaux des mises à jour affectent le système.
* Les détails de la mise à jour.

Tableau 1. Niveaux de mise à jour et impact

<table>
  <tr>
    <th>Niveau de mise à jour</th>
    <th>Impact</th>
  </tr>
  <tr>
    <td>Faible</td>
    <td>Cette mise à jour n'affecte aucun système. Vous n'avez pas à l'appliquer pendant un temps d'indisponibilité planifié.</td>
  </tr>
  <tr>
    <td>Moyen</td>
  <td>Cette mise à jour peut affecter certains systèmes. Il est recommandé de l'appliquer pendant un temps d'indisponibilité planifié.</td>
  </tr>
    <tr>
    <td>Majeur</td>
  <td>Cette mise à jour affecte certains ou tous les systèmes. Vous devez l'appliquer pendant un temps d'indisponibilité planifié.</td>
  </tr>
</table>

## Procédure d'application de mises à jour à des instances Cloud Foundation
{: #sd_applyingupdates-procedure}

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances Cloud Foundation**, cliquez sur l'instance à supprimer.
3. Sur la page **Récapitulatif**, vérifiez que tous les détails d'instance sont correctement affichés. Cliquez ensuite sur **Infrastructure** dans le panneau de navigation de gauche pour vérifier les détails sur la page **Infrastructure**.
   S'ils ne sont pas affichés, cela indique probablement un problème de connectivité avec l'instance de serveur virtuel IBM CloudDriver, lié à une règle de pare-feu ou à un autre problème de réseau. Résolvez le problème avant de passer à l'étape suivante, sinon la mise à jour risque d'échouer.
4. Cliquez sur **Mise à jour et module de correction** dans le panneau de navigation de gauche.
5. Cliquez sur la flèche vers le bas pour développer la mise à jour à appliquer, puis effectuez l'une des opérations suivantes :
   *  Pour lancer immédiatement la mise à jour, cliquez sur l'icône de menu déroulant dynamique dans la colonne **Actions** de l'entrée de mise à jour, puis cliquez sur **Mettre à jour maintenant**.
   *  Pour planifier une mise à jour ultérieure, cliquez sur l'icône de menu déroulant dynamique dans la colonne **Actions** de l'entrée de mise à jour, puis cliquez sur **Planifier la mise à jour**. Sélectionnez la date et l'heure ainsi que le fuseau horaire auxquels la mise à jour devra commencer. Cliquez sur **OK**.
6. Si vous appliquez des mises à jour à des instances Cloud Foundation dans une configuration de déploiement multisite, une section intitulée **Etapes de mise à jour obligatoires** s'affiche, dans laquelle sont répertoriées les opérations de mise à jour qui sont requises pour toutes les instances du déploiement multisite. Effectuez les étapes dans l'ordre en cliquant sur **Appliquer la mise à jour** pour chaque étape. Vous devez attendre la fin de chaque étape avant de passer à la suivante.

## Résultats
{: #sd_applyingupdates-results}

1. Avant le démarrage d'une opération de mise à jour, un diagnostic d'intégrité de l'instance est effectué. Si le diagnostic d'intégrité échoue, vous recevez une notification et vous pouvez corriger le problème avant d'appliquer la mise à jour.
2. Au cours des mises à jour qui incluent des mises à jour de composants VMware, il peut s'avérer nécessaire de migrer les machines virtuelles depuis les serveurs ESXi pour passer en mode maintenance. Si une machine virtuelle dispose d'un magasin de données local ou si un CD-ROM est monté, la migration de la machine virtuelle peut se révéler impossible.
3. Lors de la mise à disposition d'un nouvel environnement, {{site.data.keyword.vmwaresolutions_short}} crée l'ID **automationuser** qui est utilisé pour la gestion de l'instance, y compris l'application des mises à jour. Ne modifiez pas le mot de passe de cet ID utilisateur. La modification de ce mot de passe pourrait entraîner l'échec de la mise à jour.

4. Lorsque vous appliquez une mise à jour, un enregistrement s'affiche dans la liste des statuts de mise à jour logicielle, où vous pouvez visualiser la progression et le statut détaillés de la mise à jour. Lorsque la mise à jour a réussi, un enregistrement s'affiche dans la liste des mises à jour logicielles installées.

  Pour extraire le statut le plus récent d'un travail de mise à jour, cliquez sur l'icône d'actualisation dans l'angle supérieur droit de la page.
  {:tip}

5. Pour plus d'informations sur les statuts de mise à jour, voir le tableau suivant.

   Tableau 2. Détails relatifs aux statuts de mise à jour

    <table>
      <tr>
        <th>Statut</th>
        <th>Détails</th>
      </tr>
      <tr>
        <td>Disponible</td>
        <td>La mise à jour est disponible pour application. Vous ne pouvez pas sélectionner une mise à jour disponible tant que toutes ses mises à jour précédentes n'ont pas été appliquées.</td>
      </tr>
      <tr>
        <td>En cours</td>
      <td>L'opération de mise à jour a été lancée mais n'est pas encore terminée. Vous ne pouvez appliquer aucune autre mise à jour tant que l'opération de mise à jour en cours n'est pas terminée. </td>
      </tr>
        <tr>
        <td>Installé</td>
      <td>Le travail de mise à jour est terminé. Le composant correspondant de la plateforme VMware est mis à jour.</td>
      </tr>
        <tr>
        <td>Echec</td>
      <td>Le travail de mise à jour a échoué. La console signale l'échec de la mise à jour. Consultez l'erreur signalée et corrigez le problème avant d'appliquer de nouveau la mise à jour.</td>
      </tr>
          <tr>
        <td>Planifié</td>
      <td>Le travail de mise à jour est planifié pour une date ultérieure. Il commence automatiquement au moment planifié.</td>
      </tr>
          <tr>
        <td>Inconnu</td>
      <td>Le statut du travail de mise à jour est inconnu. Contactez le support IBM pour obtenir de l'aide.</td>
      </tr>
    </table>

6. Si le processus de mise à jour échoue à une étape spécifique, [contactez le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) pour obtenir de l'aide. Il vous expliquera comment résoudre le problème et vous aidera à reprendre la mise à niveau à partir de l'étape où elle a échoué.

## Liens connexes
{: #sd_applyingupdates-related}

* [Présentation de Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview)
* [Présentation de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
