---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-06"

---

{:tip: .tip}

# Application de mises à jour à des instances vCenter Server

Le processus d'application de modules de correction et de mises à jour aux instances vCenter Server est automatisé uniquement pour les composants de gestion. Les mises à jour VMware doivent être appliquées manuellement.

## Avant de commencer

**Important :** lors de la mise à niveau d'une instance vCenter Server vers une instance vCenter Server with Hybridity Bundle, vous devez d'abord appliquer la mise à jour logicielle vCenter Server V2.3 de base avant de pouvoir effectuer la mise à niveau de licence vers Hybridity Bundle.

Avant d'appliquer une mise à jour, développez l'entrée de mise à jour en cliquant sur la flèche vers le bas et vérifiez les informations suivantes :
* La version de la mise à jour. Vous devez appliquer les mises à jour par ordre chronologique, c'est-à-dire de la plus ancienne à la plus récente. Assurez-vous d'avoir appliqué toutes les mises à jour précédentes avant d'appliquer la plus récente. Par exemple, vous devez appliquer la mise à jour V2.3 avant de tenter d'appliquer la mise à jour V2.4.
* Si un temps d'indisponibilité est nécessaire.
* Le temps total estimé pour effectuer la mise à jour.
* L'impact de la mise à jour sur l'environnement virtuel VMware. Le tableau 1 indique comment les différents niveaux d'impact affectent le système.
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

## Application de mises à jour et de modules de correction à des instances vCenter Server

Cette procédure s'applique aux instances déployées en version 2.1 et ultérieures. Pour les instances déployées en version 2.0 et antérieures, vous devez appliquer les mises à jour VMware manuellement.

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance à mettre à jour.
3. Sur la page **Récapitulatif**, vérifiez que tous les détails d'instance sont correctement affichés. Cliquez ensuite sur **Infrastructure** dans le panneau de navigation de gauche pour vérifier les détails sur la page **Infrastructure**.
   S'ils ne sont pas affichés, cela indique probablement un problème de connectivité avec la machine virtuelle IBM CloudDriver, lié à une règle de pare-feu ou autre problème de réseau. Résolvez le problème avant de passer à l'étape suivante, sinon la mise à jour risque d'échouer.
4. Cliquez sur **Mise à jour et module de correction** dans le panneau de navigation de gauche.

   **Remarque** : la page **Mise à jour et module de correction** pour une instance ne contient que les packages de mise à jour des composants de gestion IBM, pas les mises à jour VMware. Les mises à jour VMware doivent être appliquées manuellement.

   {{site.data.keyword.vmwaresolutions_short}} applique les mises à jour VMware dans les circonstances suivantes :
   * Lorsqu'une nouvelle instance vCenter Server est déployée
   * Lorsque de nouveaux serveurs ESXi sont ajoutés
   * Lorsque de nouveaux clusters sont ajoutés

5. Pour des mises à niveau de licence NSX, cliquez sur **Mettre à niveau la licence**. Sélectionnez l'édition vers laquelle vous souhaitez effectuer une mise à niveau, puis cliquez sur **Mettre à niveau**. Les rétromigrations d'édition de licence ne sont pas disponibles.

   **Remarque** : la mise à niveau de licence remplace toutes les licences NSX existantes sur l'instance. Des frais supplémentaires peuvent découler d'un chevauchement entre les anciennes et les nouvelles licences si vous effectuez la mise à niveau en cours de cycle de facturation. Pour éviter des frais supplémentaires, il est recommandé d'effectuer la mise à niveau de la licence à la fin du cycle de facturation.

6. Pour les mises à jour logicielles, cliquez sur la flèche vers le bas afin de développer la mise à jour que vous voulez appliquer, puis effectuez l'une des opérations suivantes :
   *  Pour lancer immédiatement la mise à jour, cliquez sur l'icône de menu déroulant dynamique dans la colonne **Actions** de l'entrée de mise à jour, puis cliquez sur **Mettre à jour maintenant**.
   *  Pour planifier une mise à jour ultérieure, cliquez sur l'icône de menu déroulant dynamique dans la colonne **Actions** de l'entrée de mise à jour, puis cliquez sur **Planifier la mise à jour**. Sélectionnez la date et l'heure ainsi que le fuseau horaire auxquels la mise à jour devra commencer. Cliquez sur **OK**.
7. Si vous appliquez des mises à jour à des instances de serveurs vCenter dans une configuration de déploiement multisite, une section intitulée **Etapes de mise à jour obligatoires** s'affiche. Cette section répertorie les opérations de mise à jour requises pour toutes les instances du déploiement multisite. Effectuez les étapes dans l'ordre en cliquant sur **Appliquer la mise à jour** pour chaque étape. Vous devez attendre la fin de chaque étape avant de passer à la suivante.   

## Mise à niveau vers l'instance vCenter Server with Hybridity Bundle

Durant la mise à niveau de licence vers Hybridity Bundle, une mise à niveau vers l'édition VMware NSX Advanced s'effectue immédiatement si votre instance vCenter Server utilise l'édition VMware NSX Base.

Procédez comme suit pour mettre à niveau d'une instance vCenter Server vers vCenter Server with Hybridity Bundle :

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance à mettre à niveau.
3. Sur la page **Récapitulatif**, vérifiez que tous les détails d'instance sont correctement affichés. Cliquez ensuite sur **Infrastructure** dans le panneau de navigation de gauche pour vérifier les détails sur la page **Infrastructure**.
   S'ils ne sont pas affichés, cela indique probablement un problème de connectivité avec la machine virtuelle IBM CloudDriver, lié à une règle de pare-feu ou autre problème de réseau. Résolvez le problème avant de passer à l'étape suivante, sinon la mise à jour risque d'échouer.
4. Cliquez sur **Mise à jour et module de correction** dans le panneau de navigation de gauche.
5. Appliquez la mise à niveau de licence Hybridity Bundle. Dans le tableau **Mises à niveau de licence**, cliquez sur **Mettre à niveau** dans la colonne **Action**, passez en revue le coût estimé, puis cliquez sur **Mettre à niveau**.
6. Déployez éventuellement le service VMware HCX on {{site.data.keyword.cloud_notm}}. Lorsque Hybridity Bundle est activé dans le tableau **Mises à niveau de licence**, procédez comme suit :
  1. Dans le tableau **Mises à niveau de licence**, cliquez sur **Déployer HCX on {{site.data.keyword.cloud_notm}}** dans la colonne **Action**.
  2. Faites défiler l'écran jusqu'à la carte **HCX on {{site.data.keyword.cloud_notm}}** et cliquez sur **Sélectionner un service**.
  3. Faites défiler l'écran et spécifiez les paramètres requis pour le service, puis cliquez sur **Suivant**.
  4. Passez en revue les conditions qui s'appliquent au service, ainsi que le coût estimé, puis cliquez sur **Passer une commande**.

## Résultats

1. Avant le démarrage d'une opération de mise à jour, une sauvegarde des machines virtuelles de gestion est automatiquement effectuée, si un service de sauvegarde est installé sur votre instance. Une fois la sauvegarde terminée, la mise à jour est appliquée.

2. Lorsque vous appliquez une mise à jour, un enregistrement s'affiche dans la liste des statuts de mise à jour logicielle, où vous pouvez visualiser la progression et le statut détaillés de la mise à jour. Lorsque la mise à jour a réussi, un enregistrement s'affiche dans la liste des mises à jour logicielles installées.

  Pour extraire le statut le plus récent d'une tâche de mise à jour, cliquez sur l'icône d'actualisation dans l'angle supérieur droit de la page.
  {:tip}

3. Pour plus d'informations sur les statuts de mise à jour, voir le tableau suivant.

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

4. Si le processus de mise à jour échoue à une étape spécifique, [contactez le support IBM](../vmonic/trbl_support.html) pour obtenir de l'aide. Il vous expliquera comment résoudre le problème et vous aidera à relancer la mise à niveau à partir de l'étape où elle a échoué.

## Liens connexes

* [Présentation de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
