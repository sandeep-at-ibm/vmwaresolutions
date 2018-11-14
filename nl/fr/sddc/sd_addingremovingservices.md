---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

---

# Commande, affichage et retrait de services pour des instances Cloud Foundation

Vous pouvez commander des services pour vos instances VMware Cloud Foundation, telle une solution de reprise après incident. Lorsque vous n'avez plus besoin de ces services, vous pouvez les supprimer de vos instances.

## Services disponibles pour les instances Cloud Foundation

Le tableau suivant présente les services disponibles sur les instances Cloud Foundation, ainsi que les versions installées de ces services :

Tableau 1. Services disponibles pour les instances Cloud Foundation

| Nom de service | Version de service | Version d'instance |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud}}](../services/f5_considerations.html)                                 | BIG-IP VE v13.1 | A partir de V1.9 |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html)       | Série 300 | A partir de V1.8 |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html) | 6.0.3 | A partir de V2.0 |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html)              | 5.4.0 | A partir de V2.3 |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)              | 4.2.1 | A partir de V2.3 |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](../services/htkc_considerations.html)              | 4.2 | A partir de V2.5 |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](../services/spp_considerations.html)  | 10.1.1 Patch 1 | A partir de V2.2 |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_considerations.html)                  |   | A partir de V2.2 |
| [Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html)                          | 9.5u3 | A partir de V1.8 |
| [Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html)                                 | 6.0 update 3 | A partir de V1.2 |

## Procédure d'ajout de services à des instances Cloud Foundation

Pour ajouter un service à votre instance Cloud Foundation, cliquez sur le lien de service approprié dans le tableau précédent pour passer en revue les remarques relatives au service et vérifiez les composants qui sont déployés. Suivez ensuite les instructions de la rubrique appropriée sur les services de commande afin d'ajouter le service à votre instance.

### Résultats de l'installation d'un service

Lorsque l'installation du service est terminée, vous êtes prévenu par un courrier électronique, et le service s'affiche sur la page **Services** de l'instance avec le statut **Installé**.

## Procédure d'affichage de services pour des instances Cloud Foundation

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances Cloud Foundation**, cliquez sur l'instance pour laquelle vous souhaitez installer des services.
3. Cliquez sur **Services** dans le panneau de navigation de gauche.
4. Sur la page **Services**, cliquez sur un service pour passer en revue les informations le concernant, par exemple, le statut du service et d'autres détails.
5. Selon le service visualisé, vous pouvez accéder aux consoles de service à l'aide des données d'identification qui sont fournies sur la page des détails de service et vous pouvez gérer le service à partir de là.

## Procédure de retrait de services pour des instances Cloud Foundation

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances Cloud Foundation**, cliquez sur l'instance dont vous souhaitez retirer des services.
3. Cliquez sur **Services** dans le panneau de navigation de gauche.
4. Sur la page **Services**, localisez l'instance de service que vous souhaitez retirer et cliquez sur l'icône **Supprimer**.
5. Dans la fenêtre **Supprimer un service**, passez en revue, le cas échéant, les remarques ou avertissements. Sélectionnez **Je comprends** et cliquez sur **Supprimer**.

### Résultats du retrait d'un service

Une fois votre demande de retrait du service acceptée, le service prend le statut **Retrait en cours**.

Lorsque le retrait du service est terminé, vous êtes prévenu par un courrier électronique, et le service est retiré de la page **Services** de l'instance.

**Attention :** les services retirés vous sont facturés jusqu'à échéance du cycle de facturation d'{{site.data.keyword.cloud_notm}}.

### Liens connexes

* [Foire aux questions](../vmonic/faq.html)
