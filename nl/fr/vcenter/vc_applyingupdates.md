---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Application des mises à jour de composants de gestion IBM aux instances vCenter Server
{: #vc_applyingupdates}

La procédure décrite dans cette section s'applique à la mise à jour des composants de gestion IBM pour les instances déployées dans les versions 2.1 à 2.4.

Pour les instances déployées dans (ou mises à niveau vers) la version 2.5 ou une version ultérieure, les mises à jour et les correctifs des composants de gestion IBM sont appliqués automatiquement, selon les besoins.

Pour les instances déployées dans la version 2.0 et les versions antérieures, vous devez appliquer les mises à jour manuellement.

De plus, notez le comportement suivant lorsque vous terminez certaines opérations sur votre instance :
* Lorsque vous commandez de nouveaux services, l'instance est mise à jour vers la dernière version.
* Lorsque vous ajoutez de nouveaux clusters, ces clusters sont fournis avec les derniers composants VMware, ce qui n'est pas le cas pour les clusters existants.
* Lorsque vous ajoutez de nouveaux serveurs ESXi, ces serveurs ESXi sont équipés des derniers composants VMware, ce qui n'est pas le cas pour les serveurs ESXi existants.

{{site.data.keyword.vmwaresolutions_short}} ne prend pas en charge l'application des mises à jour et correctifs pour les composants VMware. Vous devez surveiller et appliquer ces mises à jour vous-même.
{:important}

## Avant d'appliquer les mises à jour des composants de gestion IBM
{: #vc_applyingupdates-prereq}

Développez l'entrée de mise à jour en cliquant sur la flèche vers le bas et vérifiez les informations suivantes :
* La version de la mise à jour. Vous devez appliquer les mises à jour par ordre chronologique, c'est-à-dire de la plus ancienne à la plus récente. Assurez-vous d'avoir appliqué toutes les mises à jour précédentes avant d'appliquer la plus récente. Par exemple, vous devez appliquer la mise à jour de la version 2.3 avant de tenter d'appliquer la mise à jour de la version 2.4.
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

## Procédure de mise à jour des composants de gestion IBM (instances de la version 2.1 à la version 2.4)
{: #vc_applyingupdates-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance à mettre à jour.
3. Sur la page **Récapitulatif**, vérifiez que tous les détails d'instance sont correctement affichés. Cliquez ensuite sur **Infrastructure** dans le panneau de navigation de gauche pour vérifier les détails sur la page **Infrastructure**.

   S'ils ne sont pas affichés, cela indique probablement un problème de connectivité avec l'instance de serveur virtuel IBM CloudDriver, lié à une règle de pare-feu ou à un problème de réseau. Résolvez le problème avant de passer à l'étape suivante, sinon la mise à jour risque d'échouer.

4. Cliquez sur **Mise à jour et module de correction** dans le volet de navigation de gauche et cliquez sur la flèche vers le bas pour développer la mise à jour de gestion IBM que vous souhaitez appliquer, puis suivez l'une des étapes suivantes :
   * Pour lancer immédiatement la mise à jour, cliquez sur l'icône de menu déroulant dynamique dans la colonne **Actions** de l'entrée de mise à jour, puis cliquez sur **Mettre à jour maintenant**.
   * Pour planifier une mise à jour ultérieure, cliquez sur l'icône de menu déroulant dynamique dans la colonne **Actions** de l'entrée de mise à jour, puis cliquez sur **Planifier la mise à jour**. Sélectionnez la date et l'heure ainsi que le fuseau horaire auxquels la mise à jour devra commencer. Cliquez sur **OK**.
5. Si vous appliquez des mises à jour à des instances dans une configuration de déploiement multisite, une section intitulée **Etapes de mise à jour obligatoires** s'affiche. Cette section répertorie les opérations de mise à jour requises pour toutes les instances du déploiement multisite. Effectuez les étapes dans l'ordre en cliquant sur **Appliquer la mise à jour** pour chaque étape. Vous devez attendre la fin de chaque étape avant de passer à la suivante.

## Résultats de l'application des mises à jour des composants de gestion IBM
{: #vc_applyingupdates-results}

1. Lorsque vous appliquez une mise à jour, un enregistrement s'affiche dans la liste des statuts de mise à jour logicielle, où vous pouvez visualiser la progression et le statut détaillés de la mise à jour. Lorsque la mise à jour a réussi, un enregistrement s'affiche dans la liste des mises à jour logicielles installées.

  Pour extraire le statut le plus récent d'une tâche de mise à jour, cliquez sur l'icône d'actualisation dans l'angle supérieur droit de la page.
  {:tip}

2. Pour plus d'informations sur les statuts de mise à jour, voir le tableau suivant.

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

3. Si le processus de mise à jour échoue à une étape spécifique, [contactez le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) pour obtenir de l'aide. Il vous expliquera comment résoudre le problème et vous aidera à appliquer les mises à jour et les correctifs à partir de l'étape où elle a échoué.

## Liens connexes
{: #vc_applyingupdates-related}

* [Présentation de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Mise à niveau des licences pour les instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_upgrade-lic)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
