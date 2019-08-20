---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestion des ressources partagées
{: #shared_managing}

{{site.data.keyword.vmwaresolutions_full}} - Shared est fourni en tant qu'offre expérimentale.
{:note}

Les clients gèrent le cycle de vie des centres de données virtuels à l'aide de l'offre {{site.data.keyword.vmwaresolutions_short}}.

Les fonctions suivantes sont prises en charge, soit à l'aide de l'interface utilisateur Web ou de l'API publique :
- Affichage d'instances de centre de données virtuel
- Accès à la console de gestion vCloud
- Redimensionnement d'instances de centre de données virtuel
- Suppression d'instances de centre de données virtuel
- Ajout et suppression de services VMware dans des instances de centre de données virtuel (**Futur**)

## Affichage d'instances de centre de données virtuel
{: #shared_managing-viewing}

Pour afficher un récapitulatif de toutes les instances de centre de données virtuel mises à disposition pour un compte utilisateur, procédez comme suit :

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. A partir de la bannière de la console, cliquez sur l'icône de votre compte utilisateur, puis cliquez dans la zone **Compte** pour sélectionner le compte utilisateur dont vous souhaitez vérifier les instances.  
3. Dans le tableau **IBM Cloud VMware Solutions Shared**, affichez la liste des instances mises à disposition dans le compte utilisateur sélectionné.

| Elément        | Description       |  
|:------------- |:------------- |
| Nom | Nom de l'instance |
| Type | Type de centre de données virtuel |
| Emplacement | {{site.data.keyword.CloudDataCent_notm}} où l'instance est hébergée |  
| Heure de création | Date et heure de création de l'instance |
| Statut | Statut de l'instance |

{: caption="Tableau 1. Eléments d'instance de centre de données virtuel" caption-side="top"}

L'instance peut prendre différents statuts.

| Statut        | Description       |
|:------------- |:------------- |
| Création en cours | L'instance est en cours de création. |
| Prêt à l'emploi | L'instance est prête pour utilisation. |
| Modification en cours | L'instance est en cours de modification. |
| Suppression en cours | L'instance est en cours de suppression. |
| Supprimé | L'instance a été supprimée. |

{: caption="Tableau 2. Descriptions du statut des instances de centre de données virtuel" caption-side="top"}

## Procédure d'affichage des détails du centre de données virtuel
{: #vc_viewinginstances-procedure-view-vdc-details}

Pour afficher les détails des propriétés d'une instance :

1. Dans le tableau **IBM Cloud VMware Solutions Shared**, cliquez sur un nom d'instance.
2. Sous **Propriétés**, affichez les détails de l'instance.

| Propriété        | Description       |
|:------------- |:------------- |
| Nom | Nom de l'instance. |
| Type | Type du centre de données virtuel. |
| Emplacement | {{site.data.keyword.CloudDataCent_notm}} où l'instance est hébergée. |
| ID | ID de l'instance. |
| Heure de création | Date et heure de création de l'instance, qui correspond également au démarrage de la facturation. |
| vCPU | Limite ou quantité d'UC réservée pouvant être utilisée à tout moment par le centre de données virtuel.  |
| RAM | Limite ou quantité de mémoire réservée pouvant être utilisée à tout moment par le centre de données virtuel.  |
| IP publique | Chaque centre de données virtuel est fourni avec cinq adresses IP publiques qui peuvent être utilisées pour connecter des vApp et des machines virtuelles à Internet. |

{: caption="Tableau 3. Propriétés du centre de données virtuel" caption-side="top"}

## Accès à la console de gestion vCloud Director
{: #shared_managing-accessing}

Gérez le centre de données virtuel via la console de gestion vCloud Director.

Le premier accès à la console de gestion vCloud Director est effectué à l'aide des données d'identification **admin**. Générez un mot de passe dans la page des détails du centre de données virtuel à l'aide du lien **Reset Location Password**. 
Cette action génère un mot de passe aléatoire complexe initial, qui peut être réinitialisé à tout moment.

L'offre {{site.data.keyword.vmwaresolutions_short}} ne stocke pas le mot de passe **admin**. Une fois le mot de passe généré, vous devez le capturer. 
Si vous perdez le mot de passe, un nouveau mot de passe doit être généré.

Tous les centres de données virtuels du même emplacement ont le même mot de passe **admin**. 
La réinitialisation du mot de passe sur une instance de centre de données virtuel réinitialise le mot de passe **admin** d'accès à la console de gestion vCloud Director pour toutes les instances de centre de données virtuel au même emplacement.

Une fois le premier mot de passe **admin** généré, le bouton **vCloud Director Portal** est disponible dans l'angle supérieur droit de la page des détails. 
Cliquez sur **vCloud Director Portal** pour accéder à la console de gestion vCloud Director. 
Pour vous connecter, utilisez le nom d'utilisateur **admin** et le mot de passe obtenu avec le lien **Reset Location Password** .

## Redimensionnement d'instances de centre de données virtuel
{: #shared_managing-resizing}

A tout moment, lorsqu'une instance de centre de données virtuel est à l'état **Prêt à utiliser**, vous pouvez modifier la quantité de ressources affectées à un centre de données virtuel. 

Redimensionner les ressources vCPU ou RAM d'une instance de centre de données virtuel dans la page des détails du centre de données virtuel. 
Cliquez sur l'icône en forme de crayon en regard de **Ressources** dans la page des détails et modifiez les valeurs des propriétés vCPU ou RAM.

Enfin, vérifiez la configuration et le coût estimé avant de passer la commande.

  Le changement de configuration échoue si les ressources vCPU et RAM sont en cours d'utilisation lorsque vous les réduisez car les ressources de centre de données virtuel ne peuvent pas être réduites à un niveau inférieur à l'utilisation des ressources actuellement actives.
{:note}

L'instance de centre de données virtuel passe à l'état **Modification** pendant le changement. 
Une fois les ressources prêtes à l'emploi, le statut passe à l'état **Prêt à utiliser**.

## Suppression d'instances de centre de données virtuel
{: #shared_managing-deleting}

Une instance de centre de données virtuel peut être supprimée lorsqu'elle est à l'état **Prêt à utiliser**. Effectuez l'opération de suppression depuis la page des détails du centre de données virtuel ou depuis le tableau IBM Cloud VMware Solutions Shared Resource.

Dans la page des détails, cliquez sur l'icône **Supprimer** dans l'option de menu déroulant dynamique en haut à droite de la page des détails. 
Ensuite, confirmez que vous voulez supprimer l'instance.

Dans le tableau IBM Cloud VMware Solutions Shared Resource, recherchez l'instance que vous voulez supprimer, puis cliquez sur l'icône **Supprimer** dans la colonne **Actions**. Ensuite, confirmez que vous voulez supprimer l'instance.

## Liens connexes
{: #shared_managing-related}

* [Présentation des solutions {{site.data.keyword.cloud_notm}} for VMware Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Commande de la solution Shared - On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Commande de la solution Shared - Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
