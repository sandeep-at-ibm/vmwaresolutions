---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Affichage d'instances Cloud Foundation

Affichez les informations récapitulatives et détaillées des instances VMware Cloud Foundation qui sont mises à disposition pour différents comptes utilisateur.

## Affichage du récapitulatif des instances Cloud Foundation

Pour afficher un récapitulatif de toutes les instances Cloud Foundation qui sont mises à disposition pour un compte utilisateur, procédez comme suit :

1. Dans la console {{site.data.keyword.vmwaresolutions_full}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans l'angle supérieur droit de la console, cliquez sur votre avatar, puis cliquez dans la zone **Compte** pour sélectionner le compte utilisateur dont vous souhaitez vérifier les instances. 
3. Dans le tableau **Instances Cloud Foundation Select**, affichez la liste de vos instances :

Tableau 1. Eléments d'une instance Cloud Foundation

| Elément        | Description       |  
|:------------- |:------------- |
| Nom | Nom de l'instance |
| Version | Version d'édition dans laquelle l'instance a été déployée ou vers laquelle elle a été mise à niveau |
| Emplacement | {{site.data.keyword.CloudDataCent_notm}} où l'instance est hébergée |
| Heure de création | Date et heure de création de l'instance |
| Statut | Statut de l'instance |

L'instance peut prendre différents statuts.

Tableau 2. Description des statuts des instances Cloud Foundation

| Statut        | Description       |
|:------------- |:------------- |
| Création en cours | L'instance est en cours de création. |
| Génération en cours | L'instance est en cours de configuration. |
| Prêt à l'emploi | L'instance est prête pour utilisation. |
| Modification en cours | L'instance est en cours de modification. |
| Echec | Le processus de création, de configuration ou de modification a échoué. |
| Suppression en cours | L'instance est en cours de suppression. |
| Erreur de suppression | Une erreur s'est produite au cours du processus de suppression de l'instance. |
| Supprimé | L'instance a été supprimée. |

## Affichage des détails des propriétés d'une instance Cloud Foundation

Pour afficher les détails des propriétés d'une instance :

1. Dans le tableau **Instances Cloud Foundation**, cliquez sur nom d'instance.
2. Sous **Propriétés**, affichez les détails de l'instance.

Tableau 3. Propriétés d'instance Cloud Foundation

| Propriété        | Description       |
|:------------- |:------------- |
| Nom | Nom de l'instance |
| ID | ID de l'instance |
| Emplacement | {{site.data.keyword.CloudDataCent_notm}} où l'instance est hébergée |
| Version en cours | Version en cours d'{{site.data.keyword.vmwaresolutions_short}} |
| Version de vCenter | Version de VMware vCenter Server<br><br>**Remarque** : la version vCenter Server affichée sur la console {{site.data.keyword.vmwaresolutions_short}} et celle sur le client Web VMware vSphere sont légèrement différentes. Les deux sont correctes. |
| NSX for vSphere | Version du produit VMware NSX for vSphere |
| Licence de _composant VMware_ | Si vous avez sélectionné d'utiliser votre propre licence VMware pour tous les composants VMware sur la page **Octroi de licence** lors de la commande de l'instance, le nom du composant VMware et la clé de licence entrée pour le composant sont affichés.<br><br>**Licence vCenter Server** et **License NSX** sont des exemple de licences de composant VMware. |
| Edition de licence NSX | Version et édition de la licence VMware NSX |
| Domaine racine DNS | Il s'agit du nom de domaine du serveur de noms de domaine (DNS, Domain Name System) et du nom de l'approbation de la racine Microsoft Active Directory (AD). |
| Domaine de connexion unique DNS | Il s'agit du domaine de connexion unique (Single Sign-On) vSphere. Le nom de domaine SSO est défini pour toutes les instances Cloud Foundation déployées avec la valeur <samp class="ph codeph">vsphere.local</samp>. |
| Sous-domaine DNS | Il s'agit du sous-domaine DNS du nom de domaine racine où résident les noms d'hôte des instances Cloud Foundation locales. Le nom de sous-domaine est au format <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>. |
| Version de SDDC Manager  |  Version du gestionnaire SDDC Manager de l'instance |
| Statut  | Statut de l'instance<br><br>Les informations affichées fournissent une mise à jour de la progression du déploiement ou de l'action appliquée à l'instance. En cas de problème, un message peut s'afficher pour vous aider à identifier et résoudre le problème. |

## Affichage des informations d'accès relatives aux instances Cloud Foundation

Sous **Informations d'accès**, affichez les informations d'accès relatives aux composants d'instance. Les mots de passe affichés sont les mots de passe initiaux générés par le système. Si vous les modifiez en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, ils ne sont pas mis à jour sur la page récapitulative de l'instance.

Tableau 4. Informations d'accès Cloud Foundation pour les composants liés à l'instance

| Composant        | Description       |
|:------------- |:------------- |
| AD/DNS IP | Les adresses IP des deux serveurs AD |
| AD/DNS FQDN | Les noms de domaine complets des serveurs AD/DNS<br><br>**Remarque :** le même mot de passe administrateur peut être utilisé pour établir une connexion à tous les serveurs AD/DNS via une connexion bureau à distance. |
| AD/DNS ADMIN (Remote Desktop)  | Pour les instances principales, affiche le nom d'utilisateur et le mot de passe d'accès au serveur AD avec une connexion bureau à distance.<br><br>Pour les instances secondaires, cliquez sur le lien **Afficher sur l'instance principale** afin d'être dirigé vers les informations de nom d'utilisateur et de mot de passe sur l'instance principale.<br><br>**Remarque** : une fois l'instance secondaire ajoutée au domaine DNS principal et la réplication lancée, le mot de passe administrateur local sur l'instance principale est susceptible de remplacer le mot de passe administrateur local sur l'instance secondaire. En cliquant sur le lien **Afficher sur l'instance principale**, vous obtiendrez le mot de passe administrateur correct.  |
| NSX Manager IP  | L'adresse IP de NSX Manager  |
| NSX Manager FQDN  | Le nom de domaine complet de NSX Manager  |
| NSX Manager HTTP  | Le nom d'utilisateur et mot de passe utilisés pour accéder à la console Web de NSX Manager |
| NSX Manager SSH | Le nom d'utilisateur et le mot de passe que vous pouvez utiliser pour accéder à NSX Manager via une connexion SSH |
| PSC IP  | L'adresse IP du contrôleur PSC ( Platform Services Controller)  |
| PSC FQDN  | Le nom de domaine complet du contrôleur PSC  |    
| PSC SSH  | Le nom d'utilisateur et le mot de passe que vous pouvez utiliser pour accéder à la machine virtuelle PSC via une connexion SSH  |
| PSC ADMIN  | Le nom d'utilisateur et le mot de passe de connexion unique VMware vCenter que vous pouvez utiliser pour accéder à la console Web du PSC  |
| vCenter IP  | L'adresse IP du serveur vCenter Server  |
| vCenter FQDN  | Le nom de domaine complet du serveur vCenter Server  |
| vCenter SSH  | Le nom d'utilisateur et le mot de passe que vous pouvez utiliser pour accéder à la machine virtuelle vCenter Server via une connexion SSH |
| vCenter ADMIN  | Le nom d'utilisateur et le mot de passe de connexion unique VMware vCenter que vous pouvez utiliser pour vous connecter au serveur vCenter Server à l'aide du client Web vSphere  |

## Affichage de l'historique de déploiement des instances Cloud Foundation

Cliquez sur **Historique de déploiement** dans le panneau de navigation de gauche pour afficher l'historique de déploiement de l'instance.

Tableau 5. Historique de déploiement d'une instance Cloud Foundation

| Elément        | Description       |  
|:------------- |:------------- |
| Date | La date et l'heure de changement du statut de l'instance |
| Récapitulatif | Les détails du changement |

## Que faire en cas d'erreurs

Si des erreurs se produisent lors du déploiement ou de la suppression d'une instance, l'équipe de support {{site.data.keyword.cloud_notm}} est automatiquement prévenue. Pour connaître le statut de votre ticket, vous pouvez [contacter le support IBM](../vmonic/trbl_support.html).

## Etape suivante

Gérez vos instances depuis la console {{site.data.keyword.vmwaresolutions_short}} ou le client Web vSphere.

**Important** : avant de cliquer sur **Console vCenter** sur la page récapitulative de l'instance pour accéder au client Web vSphere et commencer à gérer vos serveurs ESXi, vous devez vous connecter au portail VPN de l'{{site.data.keyword.CloudDataCent_notm}}. Survolez le bouton de la console vCenter et suivez les instructions de manière à respecter toutes les exigences et à effectuer les étapes requises avant d'accéder au client Web vSphere.

Passez en revue les rubriques suivantes pour obtenir des informations qui vous aideront à exécuter les instructions de connexion :

* Pour les exigences et procédures à effectuer avant d'accéder au client Web vSphere, voir [Dépassement du délai d'attente lors de la connexion au client Web vSphere](../vmonic/trbl_timeout_vc_console.html).
* Pour la liste des points d'accès de connexion au réseau privé {{site.data.keyword.cloud_notm}} à l'aide du réseau privé virtuel (VPN), voir [Accès VPN](http://www.softlayer.com/vpn-access){:new_window}.
* Si vous rencontrez des problèmes lors du déploiement d'un fichier OVF (Open Virtualization Format) à l'aide du client Web vSphere, voir [Déploiement d'un fichier OVF à l'aide du client Web vSphere](../vmonic/trbl_deploy_ovf.html).

### Liens connexes

* [Commande d'instances Cloud Foundation](sd_orderinginstance.html)
* [Extension et réduction de capacité pour des instances Cloud Foundation](sd_addingremovingservers.html)
* [Suppression d'instances Cloud Foundation](sd_deletinginstance.html)
