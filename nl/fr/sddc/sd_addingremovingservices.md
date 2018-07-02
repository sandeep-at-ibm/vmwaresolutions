---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# Commande, affichage et retrait de services pour des instances Cloud Foundation

Vous pouvez commander des services pour vos instances VMware Cloud Foundation, telle une solution de reprise après incident. Lorsque vous n'avez plus besoin de ces services, vous pouvez les supprimer de vos instances.

## Services disponibles pour les instances Cloud Foundation

Le tableau suivant présente les services disponibles sur les instances Cloud Foundation :

Tableau 1. Services disponibles pour les instances Cloud Foundation

|Nom de service                                                                          | Disponibilité |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on IBM Cloud](../services/f5_considerations.html)                                 | Oui              |
| [FortiGate Security Appliance on IBM Cloud](../services/fsa_considerations.html)       | Oui              |
| [FortiGate Virtual Appliance on IBM Cloud](../services/fortinetvm_considerations.html) | Oui              |
| [HyTrust CloudControl on IBM Cloud](../services/htcc_considerations.html)              | Oui              |
| [HyTrust DataControl on IBM Cloud](../services/htdc_considerations.html)              | Oui              |
| [IBM Spectrum Protect Plus on IBM Cloud](../services/spp_considerations.html)         | Oui              |
| [KMIP for VMware on IBM Cloud](../services/kmip_considerations.html)                  | Oui              |
| [Veeam on IBM Cloud](../services/veeam_considerations.html)                           | Oui              |
| [VMware HCX on IBM Cloud](../services/hcx_considerations.html)                         | Non             |
| [Zerto on IBM Cloud](../services/addingzertodr.html)                                 | Oui              |

## Ajout de services à des instances Cloud Foundation

Pour ajouter un service à votre instance Cloud Foundation, cliquez sur le lien de service approprié dans le tableau précédent pour passer en revue les remarques relatives au service et vérifiez les composants qui sont déployés. Suivez ensuite les instructions décrites dans la rubrique sur la commande de service afin d'ajouter le service à votre instance. 

### Résultats de l'installation d'un service

Lorsque l'installation du service est terminée, vous êtes prévenu par un courrier électronique, et le service s'affiche sur la page **Services** de l'instance avec le statut **Installé**. 

## Affichage des services des instances Cloud Foundation

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances Cloud Foundation**, cliquez sur l'instance pour laquelle vous souhaitez installer des services.
3. Cliquez sur **Services** dans le panneau de navigation de gauche. 
4. Sur la page **Services**, cliquez sur un service pour passer en revue les informations le concernant, par exemple, le statut du service et d'autres détails. 
5. Selon le service visualisé, vous pouvez accéder aux consoles de service à l'aide des données d'identification fournies sur la page des détails de service et vous pouvez gérer le service à partir de là.

## Suppression de services des instances Cloud Foundation

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances Cloud Foundation**, cliquez sur l'instance dont vous souhaitez retirer des services.
3. Cliquez sur **Services** dans le panneau de navigation de gauche. 
4. Sur la page **Services**, localisez l'instance de service que vous souhaitez retirer et cliquez sur l'icône **Supprimer**.
5. Dans la fenêtre **Supprimer un service**, passez en revue, le cas échéant, les remarques ou avertissements. Sélectionnez **Je comprends** et cliquez sur **Supprimer**.

### Résultats du retrait d'un service

Une fois votre demande de retrait du service acceptée, le service prend le statut **Retrait en cours**.

Lorsque le retrait du service est terminé, vous êtes prévenu par un courrier électronique, et le service est retiré de la page **Services** de l'instance. 

**Attention** : les services retirés vous sont facturés jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.

## Liens connexes

* [Foire aux questions](../vmonic/faq.html)
