---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-26"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Exigences relatives au compte d'infrastructure IBM Cloud
{: #slaccountrequirement}

Pour pouvoir utiliser {{site.data.keyword.vmwaresolutions_full}} en vue de commander des instances, vous devez disposer d'un compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer). Le coût des composants commandés dans vos instances est facturé sur ce compte {{site.data.keyword.cloud_notm}}.

Auparavant, le compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) était appelé compte IBM SoftLayer.
{:note}

## Autorisations pour le compte d'infrastructure IBM Cloud
{: #slaccountrequirement-permissions}

Le compte d'infrastructure {{site.data.keyword.cloud_notm}} que vous utilisez doit détenir certaines autorisations pour être à même de commander les composants de vos instances et d'effectuer des opérations en votre nom. Les autorisations requises sont applicables à tous les types d'instances et services que vous commandez depuis la console {{site.data.keyword.vmwaresolutions_short}}.

Les utilisateurs autorisés peuvent vérifier et mettre à jour les autorisations d'un compte d'infrastructure {{site.data.keyword.cloud_notm}} sur le portail {{site.data.keyword.slportal}}. Pour plus d'informations, voir [Edition des autorisations de portail client d'un utilisateur](/docs/customer-portal?topic=customer-portal-customerportal_accuserprof#cp_editusercpperm){:new_window}.

Tableau 1. Autorisations requises pour le compte d'infrastructure {{site.data.keyword.cloud_notm}}

| Droit         | Détails                                 |
|:------------------ |:--------------------------------------- |
| Ajout de serveur | Ce droit est nécessaire pour les opérations suivantes : commande de serveurs {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} sur lesquels s'exécute VMware ESXi et mise à disposition de serveurs virtuels horaires qui sont utilisés pour des opérations de configuration, de maintenance et de prise en charge d'instance. |
| Annulation de serveur | Ce droit est nécessaire pour libérer et récupérer des serveurs {{site.data.keyword.baremetal_short}} sur lesquels s'exécute VMware ESXi. Si vous supprimez votre instance, les composants commandés sont automatiquement libérés selon la séquence de dépendance appropriée. |
| Affichage des détails du serveur virtuel | Ce droit est nécessaire pour extraire les détails de mise à disposition du serveur, requis pour la validation de la commande et la configuration automatique. |
| Ajout de stockage | Ce droit est nécessaire pour commander du stockage de sauvegarde et du stockage partagé pour l'instance. |
| Gestion du stockage | Ce droit est nécessaire pour gérer le stockage de sauvegarde et le stockage partagé de l'instance. |
| Pare-feu matériel | Ce droit est nécessaire pour éditer ou afficher les fichiers journaux et les paramètres du service Fortinet on {{site.data.keyword.cloud_notm}}, s'il est installé sur votre instance. |
| Ajouter la fonction de calcul avec le port réseau public | Ce droit est nécessaire pour commander du matériel et des instances de serveur virtuel avec les ports du réseau public. |
| Ajout d'adresses IP | Ce droit est nécessaire pour commander des plages de sous-réseaux privés portables en votre nom, opération obligatoire pour gérer les machines virtuelles qui s'exécutent dans un cluster vSphere. Lorsque d'autres services sont ajoutés à votre instance, les adresses IP privées portables sont affectées au serveurs VMware ESXi afin d'isoler et d'allouer de la bande passante. |
| Ajout de tickets | Ce droit est nécessaire pour ouvrir des tickets de demande de service en votre nom. Des tickets peuvent être créés pour les opérations suivantes : initier des opérations de restauration et initier des processus de résolution des incidents automatiquement si des problèmes sont détectés. |
| Edition de tickets | Ce droit est nécessaire pour éditer les tickets de demande de service créés en votre nom. |
| Affichage de tickets | Ce droit est nécessaire pour surveiller les tickets de demande de service associés à des composants de votre instance relatifs à des problèmes et délais au niveau de la mise à disposition de l'infrastructure {{site.data.keyword.cloud_notm}}. |
| Affichage des détails matériels | Ce droit est nécessaire pour extraire les détails matériels, requis pour la validation de la commande et la configuration automatique. |
| Affichage des licences | Ce droit est nécessaire pour extraire et valider les licences utilisées par votre instance. |
| Affichage des mots de passe | Ce droit est nécessaire pour pouvoir administrer les instances de serveur virtuel commandées. |
| Gestion de la surveillance du serveur | Ce droit n'est pas nécessaire pour passer une commande mais il l'est pour extraire et valider le statut de surveillance des serveurs {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} sur lesquels les serveurs VMware ESXi exécutent votre instance. |

## VRF avec noeuds finaux de service activés
{: #slaccountrequirement-vrf-se}

Votre compte d'infrastructure {{site.data.keyword.cloud_notm}} doit être un compte VRF (Virtual Routing and Forwarding) avec des noeuds finaux de service activés. Si votre compte n'est pas de type VRF, vous devez le convertir en un compte VRF. De plus, vous devez activer votre compte VRF pour l'utilisation de noeuds finaux de service.

Pour plus d'informations, voir :
* [Présentation de VRF on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [Activation de votre compte pour l'utilisation de noeuds finaux de service](/docs/services/service-endpoint?topic=services/service-endpoint-cs_cli_install_steps#cs_cli_install_steps)

## Fin du support du spanning VLAN
{: #slaccountrequirement-vlan-eos}

Le spanning VLAN cessera d'être pris en charge en août 2019. D'ici la fin juillet 2019, vous devez convertir votre compte d'infrastructure {{site.data.keyword.cloud_notm}} en un compte VRF et activer les points finaux de service.
{:important}

## Liens connexes
{: #slaccountrequirement-related}

* [Exigences pour les instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
* [Présentation de VRF on IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
