---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Exigences relatives au compte d'infrastructure IBM Cloud

Pour pouvoir utiliser {{site.data.keyword.vmwaresolutions_full}} en vue de commander des instances, vous devez disposer d'un compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer). Le coût des composants commandés dans vos instances est facturé sur ce compte {{site.data.keyword.cloud_notm}}.

**Remarque :** auparavant, le compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) était appelé compte IBM SoftLayer.

## Autorisations pour le compte d'infrastructure IBM Cloud

Le compte d'infrastructure {{site.data.keyword.cloud_notm}} que vous utilisez doit détenir certaines autorisations pour être à même de commander les composants de vos instances et d'effectuer des opérations en votre nom. Les autorisations requises sont applicables à tous les types d'instances et services que vous commandez depuis la console {{site.data.keyword.vmwaresolutions_short}}.

Les utilisateurs autorisés peuvent vérifier et mettre à jour les autorisations d'un compte d'infrastructure {{site.data.keyword.cloud_notm}} sur le portail {{site.data.keyword.slportal}}. Pour plus d'informations, voir _Edition des autorisations de portail client d'un utilisateur_ dans [Gestion d'un profil utilisateur](../../../customer-portal/cpmanuserprof.html){:new_window}.

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

## Spanning de réseaux locaux virtuels (VLAN) pour les comptes classiques (non VRF)

Si vous utilisez un compte d'infrastructure {{site.data.keyword.cloud_notm}} classique (non VRF), le spanning VLAN doit être activé. S'il ne l'est pas pour les comptes classiques, les divers composants de l'environnement de virtualisation VMware risquent de ne pas pouvoir communiquer entre eux. Pour activer le spanning VLAN dans votre compte d'infrastructure {{site.data.keyword.cloud_notm}}, voir [Activation ou désactivation du spanning VLAN](../../../infrastructure/vlans/vlan-spanning.html){:new_window}.

### Liens connexes

* [Exigences pour les instances Cloud Foundation](../sddc/sd_planning.html)
* [Exigences pour les instances vCenter Server](../vcenter/vc_planning.html)
* [Paramètres et comptes utilisateur](useraccount.html)
