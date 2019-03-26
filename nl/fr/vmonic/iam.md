---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

# Gestion des accès utilisateur à l'aide d'IAM
{: #iam}

L'accès aux instances de service {{site.data.keyword.vmwaresolutions_full}} pour les utilisateurs de votre compte est contrôlé par {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Chaque utilisateur qui accède aux services {{site.data.keyword.vmwaresolutions_short}} de votre compte doit se voir attribuer une règle d'accès pour laquelle un rôle utilisateur IAM est défini.

La règle d'accès détermine les actions que l'utilisateur peut effectuer dans le contexte du service ou de l'instance que vous sélectionnez. Les actions autorisées sont personnalisées et définies par le service {{site.data.keyword.cloud_notm}} en tant qu'opérations pouvant être réalisées sur le service. Les actions sont ensuite mappées à des rôles utilisateur IAM.

Les règles permettent d'activer les accès à différents niveaux. Certaines des options incluent les accès suivants :

* Accès à toutes les instances de service de votre compte
* Accès à une instance de service individuelle de votre compte
* Accès à une ressource spécifique dans une instance
* Accès à tous les services activés par IAM dans votre compte

Après avoir défini la portée de la règle d'accès, vous lui affectez un rôle.

Consultez les informations ci-dessous afin de connaître les actions autorisées par chaque rôle au sein du service {{site.data.keyword.vmwaresolutions_short}}.

## Rôles et droits de gestion de plateforme
{: #iam-roles}

Les rôles de gestion de plateforme permettent aux utilisateurs d'effectuer des tâches sur des ressources de service au niveau de la plateforme. Par exemple, affecter un accès utilisateur au service, créer ou supprimer des ID de service, créer des instances et lier des instances à des applications.

Le tableau suivant fournit des informations sur les actions qui sont mappées aux rôles de gestion de plateforme.

Tableau 1. Rôles de gestion de plateforme et actions autorisées

| Rôle de gestion de plateforme | Actions | Exemples d'actions |
|:----------------- |:----------------- |:----------------- |
| Afficheur | Actions en lecture seule | <ul><li>Afficher le récapitulatif d'instances</li><li>Afficher les détails d'une instance</li></ul>|
| Editeur | Mettre à jour une instance spécifique |<ul><li>Ajouter ou retirer des serveurs ESXi</li><li>Ajouter ou retirer des clusters</li><li>Ajouter ou retirer des services</li><li>Mettre à niveau une instance vers une version ultérieure</li></ul> |
| Opérateur | Actions en lecture seule | <ul><li>Répertorier des instances</li><li>Afficher les détails d'une instance</li></ul> |
| Administrateur | Accès de gestion complet |<ul><li>Créer de nouvelles instances</li><li>Supprimer des instances</li><li>Accorder l'accès à une plateforme à d'autres utilisateurs</li></ul>|

Pour {{site.data.keyword.vmwaresolutions_short}}, les actions suivantes existent :

Tableau 2. Descriptions des actions et des rôles requis

| Action | Opération sur le service | Rôle |
|:------ |:-------------------- |:---- |
| vmware-solutions.instances.create | Créer de nouvelles instances | Administrateur |
| vmware-solutions.instances.delete | Supprimer des instances | Administrateur |
| vmware-solutions.instances.view | <ul><li>Répertorier des instances</li><li>Afficher les détails d'une instance</li></ul> | Afficheur, opérateur, éditeur et administrateur |
| vmware-solutions.instances.update | <ul><li>Ajouter ou retirer des serveurs ESXi</li><li>Ajouter ou retirer des clusters</li><li>Ajouter ou retirer des services</li><li>Mettre à niveau une instance vers une version ultérieure</li></ul> | Editeur et administrateur |
| vmware-solutions.account.update | Mettre à jour les paramètres de compte | Administrateur |

## Gestion de l'accès des utilisateurs
{: #iam-users}

Vous pouvez ajouter de nouveaux utilisateurs au compte {{site.data.keyword.cloud_notm}} afin que ces utilisateurs puissent partager les services et les ressources qui sont mis à disposition pour le compte. Pour plus d'informations, voir [Invitation des utilisateurs à accéder à des services et des ressources](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite).

Vous pouvez également gérer l'accès des utilisateurs existants, et notamment modifier l'accès existant, affecter un nouvel accès et vérifier l'accès affecté. Pour gérer l'accès des utilisateurs, vous devez être le propriétaire du compte ou vous devez disposer du rôle de gestion de plateforme **Administrateur**. Pour plus d'informations, voir [Gestion des accès aux ressources](/docs/iam?topic=iam-iammanidaccser).

## Migration d'instances existantes vers des comptes IBM Cloud
{: #iam-migrate}

En raison de l'intégration d'{{site.data.keyword.vmwaresolutions_short}} à IAM, les instances qui sont déployées dans la version 2.5 et dans les éditions ultérieures de votre compte {{site.data.keyword.cloud_notm}} sont ajoutées automatiquement à votre compte et sont gérées par IAM.

Quant aux instances existantes qui ont été déployées dans la version 2.4 et dans des éditions antérieures, vous pouvez les faire migrer vers des comptes {{site.data.keyword.cloud_notm}} spécifiés pour la gestion activée pour IAM. Pour plus d'informations, voir les rubriques suivantes :
* [Migration d'instances vCenter Server antérieures à la version 2.5 vers des comptes IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [Migration d'instances vCenter Server with Hybridity Bundle antérieures à la version 2.5 vers des comptes IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [Migration d'instances NetApp ONTAP Select antérieures à la version 2.5 vers des comptes IBM Cloud](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)

## Liens connexes
{: #iam-related}

* [Gestion de l'identité et de l'accès](/docs/iam?topic=iam-getstarted)
* [Invitation d'utilisateurs](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [Présentation d'IAM](/docs/iam?topic=iam-iamoverview)
