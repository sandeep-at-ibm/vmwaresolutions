---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle

Vous pouvez commander des services pour vos instances VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle, par exemple, une solution de reprise après incident. Lorsque vous n'avez plus besoin de ces services, vous pouvez les supprimer de vos instances.

## Services disponibles pour les instances vCenter Server with Hybridity Bundle

Les services suivants sont disponibles pour les instances vCenter Server with Hybridity Bundle :

Tableau 1. Services disponibles pour les instances vCenter Server with Hybridity Bundle

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
| [VMware HCX on IBM Cloud](../services/hcx_considerations.html)                         | Oui              |
| [Zerto on IBM Cloud](../services/addingzertodr.html)                                 | Oui              |


## Ajout de services à des instances vCenter Server with Hybridity Bundle

Afin d'appliquer un service à votre instance vCenter Server with Hybridity Bundle, cliquez sur les liens dans le tableau pour passer en revue les remarques relatives au service, vérifiez les composants qui sont déployés et suivez les instructions décrites dans les rubriques de commande pour passer votre commande. 

### Résultats de l'installation d'un service

Lorsque l'installation du service est terminée, vous êtes prévenu par un courrier électronique, et le service s'affiche sur l'onglet **Services** de la page des détails de l'instance avec le statut **Installé**. 

## Affichage des services pour les instances vCenter Server with Hybridity Bundle

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous souhaitez afficher les services.
3. Cliquez sur **Services** dans le panneau de navigation de gauche. 
4. Sur la page **Services**, cliquez sur un service pour passer en revue les informations le concernant, par exemple, le statut du service et d'autres détails. 
5. Selon le service visualisé, vous pouvez accéder aux consoles de service à l'aide des données d'identification fournies sur la page des détails de service et vous pouvez gérer le service à partir de là.

## Retrait de services pour les instances vCenter Server with Hybridity Bundle

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous souhaitez retirer des services.
3. Cliquez sur **Services** dans le panneau de navigation de gauche. 
4. Sur la page **Services**, localisez l'instance de service que vous souhaitez retirer et cliquez sur l'icône **Supprimer**.
5. Dans la fenêtre **Supprimer un service**, passez en revue, le cas échéant, les remarques ou avertissements. Sélectionnez **Je comprends** et cliquez sur **Supprimer**.

### Résultats du retrait d'un service

Une fois votre demande de retrait du service acceptée, le service prend le statut **Retrait en cours**.

Lorsque le retrait du service est terminé, vous êtes prévenu par un courrier électronique, et le service est retiré de la page **Services** de l'instance. 

**Attention** : les services retirés vous sont facturés jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.

## Liens connexes

* [Foire aux questions](../vmonic/faq.html)
