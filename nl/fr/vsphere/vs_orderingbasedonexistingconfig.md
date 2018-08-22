---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Commande de clusters vSphere on la base de configurations existantes

Vous pouvez commander un cluster VMware vSphere sur la base d'un modèle de configuration que vous avez sauvegardé. Cette procédure permet de définir une nouvelle configuration de cluster basée sur une configuration de cluster existante.

## Conditions requises

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud}} sur la page **Paramètres**. Pour plus d'informations, voir [Paramètres et comptes utilisateur](../vmonic/useraccount.html).
*  Vous avez passé en revue les exigences et les remarques énoncées dans [Exigences et planification pour les clusters vSphere](vs_planning.html).
*  Vous avez créé un modèle de configuration qui sera réutilisé.

## Procédure

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **VMware vSphere** dans la section **Centres de données virtuels**.
2. Sur la page **VMware vSphere on IBM Cloud**, cliquez sur **Créer**.  
3. Cliquez sur l'onglet **Créer** et sélectionnez un modèle de configuration dans la liste **Configurations de cluster**.
4. Entrez le nom du nouveau cluster.
5. Passez en revue ls paramètres de cluster qui sont automatiquement renseignés et mettez à jour les paramètres en fonction de vos besoins. Pour plus d'informations sur les paramètres, voir [Commande de nouveaux clusters vSphere](vs_orderinginstances.html).
6. Sur le panneau **Récapitulatif de la commande**, vérifiez la configuration de l'instance et le coût estimé.
   * Pour sauvegarder la configuration en tant que modèle sans passer de commande, cliquez sur **Sauvegarde de la configuration**.
   * Pour passer la commande, assurez-vous que le compte qui devra être facturé est correct, passez en revue et acceptez les conditions, puis cliquez sur **Mettre à disposition**.

   **Remarque** : seuls les serveurs {{site.data.keyword.baremetal_short}} sont installés. Vous êtes responsable de l'installation et de la configuration des divers composants après déploiement du cluster, tels que VMware vCenter, VMware NSX, VMware vSAN.

## Résultats

Si vous avez sauvegardé la configuration de cluster en tant que modèle, vous recevez sur la console une notification vous indiquant que la configuration a été sauvegardée. Le modèle figure alors dans la liste **Configurations de cluster**.

Si vous avez passé la commande, le déploiement du cluster démarre automatiquement et vous recevez par courrier électronique la confirmation que la commande est en cours de traitement. Lorsque le cluster est prêt pour utilisation, une notification vous en averti.

**Remarque :** contrairement aux instances vCenter Server et Cloud Foundation, les clusters vSphere ne s'affichent pas sur la page **Instances déployées**.

### Liens connexes

* [Commande de nouveaux clusters vSphere](vs_orderinginstances.html)
* [Mise à l'échelle de clusters vSphere existants](vs_scalingexistingclusters.html)
* [Mise à l'échelle de clusters créés en dehors de la console](vs_orderingforclustersoutside.html)
