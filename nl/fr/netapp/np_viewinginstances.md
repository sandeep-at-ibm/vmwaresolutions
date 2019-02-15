---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Affichage des instances NetApp ONTAP Select

Affichez les informations récapitulatives et détaillées des instances NetApp ONTAP Select qui sont mises à disposition pour différents comptes utilisateur.

## Procédure d'affichage du récapitulatif des instances NetApp ONTAP

Pour afficher un récapitulatif de toutes les instances NetApp ONTAP Select qui sont mises à disposition pour un compte utilisateur, procédez comme suit :

1. A partir de la console {{site.data.keyword.vmwaresolutions_full}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. A partir de la bannière de la console, cliquez sur l'icône de votre compte utilisateur, puis cliquez dans la zone **Compte** pour sélectionner le compte utilisateur dont vous souhaitez vérifier les instances.
3. Dans le tableau **Instances NetApp ONTAP Select**, affichez la liste des instances qui sont mises à disposition dans le compte utilisateur sélectionné.

Tableau 1. Eléments d'une instance NetApp ONTAP Select

| Elément        | Description       |  
|:------------- |:--------------- |
| Nom | Nom de l'instance. |
| Version | Version de l'instance. |  
| Emplacement | Centre de données dans lequel l'instance est hébergée. |
| Heure de création | Date et heure de création de l'instance. |   
| Statut | Statut de l'instance. Ce statut peut prendre l'une des valeurs suivantes :<ul><li>Création en cours : l'instance est en cours de création.</li><li>Génération en cours ; l'instance est en cours de configuration.</li><li>Prêt à l'emploi : l'instance est prête à l'emploi.</li><li>Modification en cours : l'instance est en cours de modification.</li><li>Echec : le processus de création, de configuration ou de modification a échoué.</li><li>Suppression en cours : l'instance est en cours de suppression.</li><li>Erreur de suppression : une erreur s'est produite au cours de la suppression de l'instance.</li><li>Supprimé : l'instance est supprimée.</li></ul>|

## Procédure d'affichage des détails des propriétés des instances NetApp ONTAP

Pour afficher les détails des propriétés d'une instance :

1. Dans le tableau **Instances NetApp ONTAP Select**, cliquez sur un nom d'instance.
2. Sous **Propriétés**, affichez les détails de l'instance.

Tableau 2. Propriétés d'instance NetApp ONTAP Select

| Propriété        | Description       |
|:--------------- |:----------------- |
| Nom | Nom de l'instance. |
| ID | ID de l'instance. |
| Emplacement | Centre de données dans lequel l'instance est hébergée. |
| Version déployée | Version déployée d'{{site.data.keyword.vmwaresolutions_short}}. |
| Version de vCenter | Version de VMware vCenter Server.<br><br>**Remarque** : la version vCenter Server affichée sur la console {{site.data.keyword.vmwaresolutions_short}} et celle sur le client Web VMware vSphere sont légèrement différentes. Les deux sont correctes. |
| NSX for vSphere | Version du produit VMware NSX for vSphere. |
| Edition de licence NSX | Version et édition de la licence VMware NSX. |
| Version de NetApp | Version de NetApp ONTAP Select. |
| Type de licence NetApp | Type de la licence NetApp ONTAP Select. |
| Domaine racine DNS | Le nom du domaine racine est le nom de domaine du serveur de noms de domaine (DNS) et le nom de l'approbation de la racine Microsoft Active Directory (AD) pour l'instance. |
| Domaine de connexion unique DNS | Il s'agit du domaine de connexion unique (Single Sign-On) vSphere. Le nom de domaine SSO est défini pour toutes les instances NetApp ONTAP Select déployées avec la valeur `vsphere.local`. |
| Sous-domaine DNS | Le sous-domaine est le nom du sous-domaine DNS du nom de domaine racine où résident les noms d'hôte des instances NetApp ONTAP Select locales. Le nom de sous-domaine est au format `<subdomain_label>.<root_domain>`. |
| Statut | Statut de l'instance. |

## Procédure d'affichage des informations d'accès aux instances NetApp ONTAP

Sous **Informations d'accès**, affichez les informations d'accès relatives aux composants d'instance. Les mots de passe affichés sont les mots de passe initiaux générés par le système. Si vous les modifiez en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, ils ne sont pas mis à jour sur la page récapitulative de l'instance.

Tableau 3. Informations d'accès relatives aux composants des instances NetApp ONTAP Select

| Composant        | Description       |
|:---------------- |:----------------- |
| AD/DNS IPs | Adresses IP des deux serveurs AD. |
| AD/DNS FQDN | Nom de domaine complet du serveur AD/DNS. |
| AD/DNS ADMIN (Remote Desktop) | Nom d'utilisateur et mot de passe que vous pouvez utiliser pour accéder au serveur AD via une connexion bureau à distance. |
| NSX Manager IP | Adresse IP de NSX Manager. |
| NSX Manager FQDN | Nom de domaine complet de NSX Manager. |
| NSX Manager HTTP | Nom d'utilisateur et mot de passe que vous pouvez utiliser pour accéder à la console Web de NSX Manager. |
| NetApp Cluster IP | Adresse IP du cluster NetApp ONTAP Select. |
| NetApp Cluster FQDN | Nom de domaine complet du cluster NetApp ONTAP. |
| NetApp Cluster HTTPS | Nom d'utilisateur et mot de passe que vous pouvez utiliser pour accéder au cluster NetApp ONTAP Select. |
| NetApp Deploy Tool IP | Adresse IP de la machine virtuelle NetApp ONTAP Select Deploy. |
| NetApp Deploy Tool FQDN | Nom de domaine complet de la machine virtuelle NetApp ONTAP Select Deploy. |
| NetApp Deploy Tool HTTPS | Nom d'utilisateur et mot de passe que vous pouvez utiliser pour accéder à la machine virtuelle NetApp ONTAP Select Deploy. |
| vCenter IP | Adresse IP du serveur vCenter Server. |
| vCenter FQDN | Nom de domaine complet du serveur vCenter Server. |
| vCenter ADMIN | Nom d'utilisateur et mot de passe de connexion unique VMware vCenter que vous pouvez utiliser pour vous connecter au serveur vCenter Server à l'aide du client Web vSphere. |
| vCenter SSH | Nom d'utilisateur et mot de passe que vous pouvez utiliser pour accéder à la machine virtuelle vCenter Server via une connexion SSH. |

## Procédure d'affichage de l'historique de déploiement des instances NetApp ONTAP

Cliquez sur **Historique de déploiement** dans le panneau de navigation de gauche pour afficher l'historique de déploiement de l'instance.

Tableau 4. Historique de déploiement d'une instance NetApp ONTAP Select

| Elément        | Description       |  
|:------------|:------------- |
| Date | Date et heure de changement du statut de l'instance |
| Récapitulatif | Détails du changement |

Si des erreurs se produisent lors du déploiement ou de la suppression d'une instance, l'équipe de support {{site.data.keyword.cloud_notm}} est automatiquement prévenue. Pour connaître le statut de votre ticket, vous pouvez [contacter le support IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html).

## Affichage des clusters NetApp ONTAP Select

1. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche.
2. Sous **CLUSTERS**, affichez le récapitulatif concernant les clusters NetApp ONTAP Select.

	Tableau 5. Eléments des clusters NetApp ONTAP Select

	 <table>
	   <tr>
	     <th>Elément</th>
	     <th>Description</th>
	   </tr>
	   <tr>
	     <td>Nom</td>
	     <td>Nom du cluster.</td>
	   </tr>
	   <tr>
	     <td>Serveurs ESXi</td>
	     <td>Nombre de serveurs ESXi dans le cluster.</td>
	   </tr>
	   <tr>
	      <td>UC</td>
	      <td>Spécification d'UC des serveurs ESXi du cluster.</td>
	   </tr>
	   <tr>
	      <td>Stockage effectif</td>
	      <td>Capacité disque totale des serveurs ESXi dans le cluster.</td>
	   </tr>
	   <tr>
	      <td>Mémoire</td>
	      <td>Taille de mémoire totale des serveurs ESXi du cluster.</td>
	   </tr>
	   <tr>
	      <td>Emplacement de centre de données</td>
	      <td>Centre de données dans lequel le cluster est hébergé. Il s'agit du même centre de données que pour l'instance.</td>
	   </tr>
		 <tr>
		   <td>Pod</td>
			 <td>Pod dans lequel le cluster est créé.</td>
		 </tr>
		 <tr>
		  <td>Statut</td>
			<td>Statut du cluster. Ce statut peut prendre l'une des valeurs suivantes :<ul><li>Initialisation en cours : le cluster est en cours de création et de configuration.</li><li>Modification en cours : le cluster est en cours de modification.</li><li>Prêt à l'emploi : le cluster est prêt à l'emploi.</li></ul></td>
		 </tr>
		 <tr>
		  <td>Actions</td>
			<td>Cliquez sur l'icône **Supprimer** pour supprimer le cluster.</td>
		 </tr>
	 </table>

3. Cliquez sur le nom du cluster pour afficher les détails de ses serveurs ESXi.

Tableau 6. Détails des serveurs ESXi d'un cluster NetApp ONTAP Select

| Elément        | Description       |  
|:------------|:----------------- |
| Nom | Nom du serveur ESXi au format `<host_prefix><n>.<subdomain_label>.<root_domain>`, où :<br><br>`host_prefix` est le préfixe de nom d'hôte, `n` est la séquence du serveur, `subdomain_label` est le libellé de sous-domaine et `root_domain` est le nom de domaine racine. |
| Version | Version du serveur ESXi. |
| Données d'identification | Nom d'utilisateur et mot de passe d'accès au serveur ESXi. |
| Adresse IP privée | Adresse IP privée du serveur ESXi. |
| Statut | Statut du serveur ESXi, qui peut avoir l'une des valeurs suivantes :<ul><li>Actif : le serveur ESXi est prêt à l'emploi.</li><li>Suppression en cours : le serveur ESXi est en cours de suppression.</li></ul> |

## Etape suivante

Gérez vos instances depuis la console {{site.data.keyword.vmwaresolutions_short}}, le client Web VMware vSphere ou la console NetApp.

Avant de cliquer sur **Console vCenter** sur la page récapitulative de l'instance pour accéder au client Web vSphere et commencer à gérer vos serveurs ESXi, vous devez vous connecter au portail VPN de l'{{site.data.keyword.CloudDataCent_notm}}. Survolez le bouton **Console vCenter** et suivez les instructions de manière à respecter toutes les exigences et à effectuer les étapes requises avant d'accéder au client Web vSphere.
{:important}

Consultez les rubriques suivantes pour plus d'informations sur l'exécution des instructions de connexion :

*  Pour les exigences et procédures à effectuer avant d'accéder au client vSphere Web Client, voir [Dépassement du délai d'attente lors de la connexion au client vSphere Web Client](/docs/services/vmwaresolutions/vmonic/trbl_timeout_vc_console.html).
*  Pour la liste des points d'accès de connexion au réseau privé de l'infrastructure {{site.data.keyword.cloud_notm}} à l'aide du réseau privé virtuel (VPN), voir [Accès VPN](http://www.softlayer.com/vpn-access){:new_window}.
*  Si vous rencontrez des problèmes lors du déploiement d'un fichier OVF (Open Virtualization Format) à l'aide du client vSphere Web Client, voir [Déploiement d'un fichier OVF à l'aide du client vSphere Web Client](/docs/services/vmwaresolutions/vmonic/trbl_deploy_ovf.html).

### Liens connexes

* [Commande d'instances NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp/np_orderinginstances.html)
* [Suppression d'instances NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp/np_deletinginstance.html)
* [Liaison d'un stockage dédié à des déploiements NetApp ONTAP Select](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
