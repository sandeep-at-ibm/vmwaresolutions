---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Processus de suppression du service Zerto on IBM Cloud

Le processus de retrait du service Zerto on {{site.data.keyword.cloud}} est automatisé. Les opérations suivantes sont effectuées pour retirer le service Zerto on {{site.data.keyword.cloud_notm}}. 

## Procédure de suppression de Zerto on IBM Cloud

1. Cliquez sur **Instances déployées** dans le panneau de navigation de gauche, puis cliquez sur l'instance sur laquelle vous voulez retirer le service.
2. Cliquez sur l'onglet **Services**.
3. Sur l'onglet **Services installés**, cliquez sur l'icône de menu déroulant dynamique dans l'angle supérieur droit de la carte de service, puis sur **Retirer un service**.
4. Dans la fenêtre **Retirer un service**, passez en revue, le cas échéant, les remarques ou avertissements. Cliquez sur **Je comprends**.
5. Une fois votre demande de retrait du service acceptée, le service prend le statut **Retrait en cours** et les opérations de retrait suivantes sont effectuées :   
   1. Suppression des dispositifs Zerto Virtual Replication Appliance déployés sur tous les serveurs ESXi.
   2. Désinstallation de la réplication virtuelle Zerto.
   3. Suppression de l'instance de service virtuel Windows sur laquelle la réplication virtuelle Zerto avait été installée.
   4. Retour du sous-réseau portable privé qui avait été commandé pour la communication de la réplication virtuelle Zerto avec l'infrastructure {{site.data.keyword.cloud_notm}}.    
   5. Suppression des frais liés au service de reprise après incident Zerto de votre relevé de facturation {{site.data.keyword.cloud_notm}}. 

      **Remarque** : le service de reprise après incident Zerto supprimé vous est facturé jusqu'à échéance du cycle de facturation.

## Résultats

Une fois le service correctement supprimé, vous recevez une notification par courrier électronique et le service ne s'affiche plus l'onglet **Services installés**.

### Liens connexes

* [Commande de Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [Gestion de Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Instances Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Instances vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Site Web zerto.com](https://www.zerto.com){:new_window}
* [Documentation technique Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
