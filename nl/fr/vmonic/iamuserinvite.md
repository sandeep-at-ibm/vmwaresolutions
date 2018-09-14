---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# Invitation des utilisateurs à accéder à des services et des ressources

{{site.data.keyword.vmwaresolutions_full}} est intégré à {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) pour permettre à plusieurs utilisateurs de collaborer. Après vous être inscrit à un compte {{site.data.keyword.cloud_notm}} et vous être connecté à la console {{site.data.keyword.vmwaresolutions_short}}, vous pouvez ajouter des utilisateurs au compte {{site.data.keyword.cloud_notm}}. Les utilisateurs que vous ajoutez peuvent partager les services et les ressources qui sont mises à disposition pour le compte.

## Avant de commencer

* Vérifiez que vous êtes le propriétaire du compte ou que votre rôle de gestion de plateforme pour le service **VMware Solutions** est **Administrateur**.
* Prenez soin de passer en revue les rôles et les droits utilisateur décrits dans [Gestion des accès utilisateur à l'aide d'IAM](iam.html).

## Procédure

1. Sur le côté gauche de la bannière, cliquez sur **Gestion > Sécurité > Identity and access**.
2. Sur la page **Utilisateurs**, cliquez sur **Inviter des utilisateurs**.
3. Sur la page **Inviter des utilisateurs**, dans la section **Utilisateurs**, entrez les adresses électroniques des utilisateurs que vous souhaitez inviter dans la zone **Adresse électronique**.
4. Dans la section **Accès**, développez **Services** et exécutez les tâches suivantes :
   1. Sélectionnez **Ressource** dans la liste **Affecter l'accès à**.
   2. Sélectionnez **VMware Solutions** dans la liste **Services**.
   3. Sélectionnez le rôle d'accès à la plateforme que vous désirez affecter aux utilisateurs. Il peut s'agir du rôle **Administrateur**, **Editeur**, **Opérateur** ou **Afficheur**.
5. Cliquez sur **Inviter des utilisateurs**.

## Résultats

Une fois que les utilisateurs ajoutés ont accepté votre invitation, ils peuvent se connecter à la console {{site.data.keyword.vmwaresolutions_short}} et basculer sur votre compte. Pour ce faire, dans leurs paramètres de profil, ils doivent cliquer sur leur avatar à l'angle supérieur droit de la console {{site.data.keyword.vmwaresolutions_short}}. Les utilisateurs ajoutés peuvent alors collaborer et partager les services et les ressources disponibles dans votre compte spécifié.

### Liens connexes

* [Invitation d'utilisateurs et affectation d'accès](../../../iam/iamuserinv.html)
* [Gestion de l'identité et de l'accès](../../../iam/quickstart.html)
* [Gestion des utilisateurs et de l'accès](../../../iam/iamusermanage.html)
* [Présentation d'IAM](../../../iam/index.html)
* [Migration d'instances vCenter Server antérieures à la version 2.5 vers des comptes IBM Cloud](../vcenter/vc_addinstancetousraccount.html)
* [Migration d'instances vCenter Server with Hybridity Bundle antérieures à la version 2.5 vers des comptes IBM Cloud](../vcenter/vc_hybrid_addinstancetousraccount.html)
* [Migration d'instances Cloud Foundation Select antérieures à la version 2.5 vers des comptes IBM Cloud](../sddc/sd_addinstancetousraccount.html)
* [Migration d'instances NetApp ONTAP Select antérieures à la version 2.5 vers des comptes IBM Cloud](../netapp/np_addinstancetousraccount.html)
* [Migration d'instances VMware Federal antérieures à la version 2.5 vers des comptes IBM Cloud](../vcenter/vc_fed_addinstancetousraccount.html)
