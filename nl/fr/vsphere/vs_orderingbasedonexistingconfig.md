---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande de clusters vSphere on la base de configurations existantes

Vous pouvez commander un cluster VMware vSphere sur la base d'un modèle de configuration que vous avez sauvegardé. Cette procédure permet de définir une nouvelle configuration de cluster basée sur une configuration de cluster existante.

## Conditions requises

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud}} sur la page **Paramètres**. Pour plus d'informations, voir [Paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic/useraccount.html).
*  Vous avez passé en revue les exigences et les remarques énoncées dans [Exigences et planification pour les clusters vSphere](/docs/services/vmwaresolutions/vsphere/vs_planning.html).
*  Vous avez créé un modèle de configuration qui sera réutilisé.

## Procédure pour commander des clusters vSphere en fonction des configurations existantes

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **VMware vSphere** dans la section **Centres de données virtuels**.
2. Sur la page **VMware vSphere on IBM Cloud**, cliquez sur **Créer**.  
3. Cliquez sur l'onglet **Créer** et sélectionnez un modèle de configuration dans la liste **Configurations de cluster**.
4. Entrez le nom du nouveau cluster.
5. Passez en revue les paramètres de cluster renseignés automatiquement et mettez à jour les paramètres en fonction de vos besoins. Pour plus d'informations sur les paramètres, voir [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html).
6. Sur le panneau **Récapitulatif de la commande**, vérifiez la configuration de l'instance et le coût estimé.
   * Pour sauvegarder la configuration en tant que modèle sans passer de commande, cliquez sur **Sauvegarde de la configuration**.
   * Pour passer la commande, assurez-vous que le compte qui devra être facturé est correct, passez en revue et acceptez les conditions, puis cliquez sur **Mettre à disposition**.

   Seuls les serveurs {{site.data.keyword.baremetal_short}} sont installés. L'installation et la configuration de divers composants, comme VMware vCenter, VMware NSX ou VMware vSAN, après le déploiement, vous incombe.
   {:note}

## Résultats

Si vous avez sauvegardé la configuration de cluster en tant que modèle, vous recevez sur la console une notification vous indiquant que la configuration a été sauvegardée. Le modèle figure alors dans la liste **Configurations de cluster**.

Si vous avez passé commande, le déploiement du cluster démarre automatiquement. Une conformation par courrier électronique vous avise que la commande est en cours de traitement. Lorsque le cluster est prêt pour son utilisation, une notification vous en avertit.

Contrairement aux instances vCenter Server et Cloud Foundation, les clusters vSphere ne s'affichent pas sur la page **Instances déployées**.
{:note}

### Liens connexes

* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)
* [Mise à l'échelle de clusters vSphere existants](/docs/services/vmwaresolutions/vsphere/vs_scalingexistingclusters.html)
* [Mise à l'échelle de clusters créés en dehors de la console](/docs/services/vmwaresolutions/vsphere/vs_orderingforclustersoutside.html)
