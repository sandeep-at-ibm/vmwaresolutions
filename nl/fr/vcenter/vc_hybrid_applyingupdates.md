---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Application de mises à jour à des instances vCenter Server with Hybridity Bundle

Le processus d'application de modules de correction et de mises à jour aux instances vCenter Server with Hybridity Bundle est automatisé uniquement pour les composants de gestion. Les mises à jour VMware doivent être appliquées manuellement.

## Avant de commencer

A compter de la version 2.5, les mises à jour d'IBM CloudDriver ne sont plus répertoriées car les mises à jour automatiques sont activées. Les actions telles que l'ajout d'un hôte, l'ajout d'un cluster et la commande d'un service entraînent la mise à jour automatique de l'instance vers la version la plus récente. Pour plus d'informations sur les mises à jour automatiques, voir la section *Résilience IBM CloudDriver* dans [Notes sur l'édition pour la version 2.5](/docs/services/vmwaresolutions/vmonic/relnotes_v25.html).
{:note}

Avant d'appliquer une mise à jour, développez l'entrée de mise à jour en cliquant sur la flèche vers le bas et vérifiez les informations suivantes :
* La version de la mise à jour. Vous devez appliquer les mises à jour par ordre chronologique, c'est-à-dire de la plus ancienne à la plus récente. Assurez-vous d'avoir appliqué toutes les mises à jour précédentes avant d'appliquer la plus récente. Par exemple, vous devez appliquer la mise à jour V2.3 avant de tenter d'appliquer la mise à jour V2.4.
* Si un temps d'indisponibilité est nécessaire.
* Le temps total estimé pour effectuer la mise à jour.
* L'impact de la mise à jour sur l'environnement virtuel VMware.
* Les détails de la mise à jour.

Le tableau suivant indique comment les différents niveaux d'impact affectent le système .

Tableau 1. Niveaux de mise à jour et impact

| Niveau de mise à jour  | Impact        |  
|:------------- |:------------- |
| Faible    | Cette mise à jour n'affecte aucun système. Vous n'avez pas à l'appliquer pendant un temps d'indisponibilité planifié. |  
| Moyen | Cette mise à jour peut affecter certains systèmes. Il est recommandé de l'appliquer pendant un temps d'indisponibilité planifié. |  
| Majeur  | Cette mise à jour affecte certains ou tous les systèmes. Vous devez l'appliquer pendant un temps d'indisponibilité planifié. |  

## Procédure d'application de mises à jour à des instances vCenter Server with Hybridity Bundle

1. A partir de la console {{site.data.keyword.vmwaresolutions_full}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance à mettre à jour.
3. Sur la page **Récapitulatif**, vérifiez que tous les détails d'instance sont correctement affichés. Cliquez ensuite sur **Infrastructure** dans le panneau de navigation de gauche pour vérifier les détails sur la page **Infrastructure**.
   S'ils ne sont pas affichés, cela indique probablement un problème de connectivité avec l'instance de serveur virtuel IBM CloudDriver, lié à une règle de pare-feu ou à un autre problème de réseau. Résolvez le problème avant de passer à l'étape suivante, sinon la mise à jour risque d'échouer.
4. Cliquez sur **Mise à jour et module de correction** dans le panneau de navigation de gauche.

   La page **Mise à jour et module de correction** ne contient que les packages de mise à jour des composants de gestion IBM, pas les mises à jour VMware. {{site.data.keyword.vmwaresolutions_short}} applique les mises à jour VMware dans les circonstances suivantes :
   * Lorsqu'une nouvelle instance vCenter Server est déployée
   * Lorsque de nouveaux serveurs ESXi sont ajoutés, ils sont mis à disposition avec des mises à jour VMware, mais les serveurs ESXi existants ne sont pas mis à jour.
   * Lorsque de nouveaux clusters sont ajoutés, ils sont mis à disposition avec des mises à jour VMware, mais les clusters existants ne sont pas mis à jour.
   {:note}

5. Pour des mises à niveau de licence, cliquez sur **Mettre à niveau**. Sélectionnez dans la liste l'édition vers laquelle vous souhaitez effectuer une mise à niveau, puis cliquez sur **Mettre à niveau**. Les rétromigrations d'édition de licence ne sont pas disponibles.

   La mise à niveau de licence remplace toutes les licences NSX existantes sur l'instance. Des frais supplémentaires peuvent découler d'un chevauchement entre les anciennes et les nouvelles licences si vous effectuez la mise à niveau en cours de cycle de facturation. Pour éviter des frais supplémentaires, il est recommandé d'effectuer la mise à niveau de la licence à la fin du cycle de facturation.
   {:note}

6. Pour les mises à jour logicielles, cliquez sur la flèche vers le bas afin de développer la mise à jour que vous voulez appliquer, puis effectuez l'une des opérations suivantes :
   *  Pour lancer immédiatement la mise à jour, cliquez sur l'icône de menu déroulant dynamique dans la colonne **Actions** de l'entrée de mise à jour, puis cliquez sur **Mettre à jour maintenant**.
   *  Pour planifier une mise à jour ultérieure, cliquez sur l'icône de menu déroulant dynamique dans la colonne **Actions** de l'entrée de mise à jour, puis cliquez sur **Planifier la mise à jour**. Sélectionnez la date et l'heure ainsi que le fuseau horaire auxquels la mise à jour devra commencer. Cliquez sur **OK**.
7. Si vous appliquez des mises à jour à des instances vCenter Server dans une configuration de déploiement multisite, une section intitulée **Etapes de mise à jour obligatoires** s'affiche. Cette section répertorie les opérations de mise à jour requises pour toutes les instances du déploiement multisite. Effectuez les étapes dans l'ordre en cliquant sur **Appliquer la mise à jour** pour chaque étape. Vous devez attendre la fin de chaque étape avant de passer à la suivante.   

## Résultats

2. Lorsque vous appliquez une mise à jour, un enregistrement s'affiche dans la liste des statuts de mise à jour logicielle, où vous pouvez visualiser la progression et le statut détaillés de la mise à jour. Lorsque la mise à jour a réussi, un enregistrement s'affiche dans la liste des mises à jour logicielles installées.

  Pour extraire le statut le plus récent d'un travail de mise à jour, cliquez sur l'icône d'actualisation dans l'angle supérieur droit de la page.
  {:tip}

3. Pour des détails sur les statuts de mise à jour, voir la liste suivante :
<dl class="dl">
<dt class="dt dlterm">Disponible</dt>
<dd class="dd">La mise à jour est disponible pour application. Vous ne pouvez pas sélectionner une mise à jour disponible tant que toutes ses mises à jour précédentes n'ont pas été appliquées.
</dd>
<dt class="dt dlterm">En cours</dt>
<dd class="dd">L'opération de mise à jour a été lancée mais n'est pas encore terminée. Vous ne pouvez appliquer aucune autre mise à jour tant que l'opération de mise à jour en cours n'est pas
terminée.</dd>
<dt class="dt dlterm">Installé</dt>
<dd class="dd">Le travail de mise à jour est terminé. Le composant correspondant de la plateforme VMware est mis à jour.</dd>
<dt class="dt dlterm">Echec</dt>
<dd class="dd">Le travail de mise à jour a échoué. La console signale l'échec de la mise à jour. Consultez l'erreur signalée et corrigez le problème
avant d'appliquer de nouveau la mise à jour.</dd>
<dt class="dt dlterm">Planifié</dt>
<dd class="dd">Le travail de mise à jour est planifié pour une date ultérieure. Il commence automatiquement au moment planifié.</dd>
<dt class="dt dlterm">Inconnu</dt>
<dd class="dd">Le statut du travail de mise à jour est inconnu. Contactez le support IBM pour obtenir de l'aide.</dd>
</dl>

4. Si le processus de mise à jour échoue à une étape spécifique, [contactez le support IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html) pour obtenir de l'aide. Il vous expliquera comment résoudre le problème et vous aidera à relancer la mise à niveau à partir de l'étape où elle a échoué.

### Liens connexes

* [Présentation de vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter/vc_hybrid_overview.html)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic/faq.html)
