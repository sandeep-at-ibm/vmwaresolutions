---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: vCenter Server Hybridity delete instance, delete vCenter Server Hybridity, remove vCenter Server Hybridity

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Retrait d'Hybridity Bundle d'une instance vCenter Server
{: #vc_hybrid_deletingbundle}

Pour retirer la licence Hybridity Bundle de votre instance vCenter Server, vous devez remplacer les clés de licence locative VMware NSX et VMware vSAN par des clés BYOL (Bring Your Own License) dans le client Web VMware vSphere. De plus, vous devez ouvrir un ticket de demande de service pour annuler les frais liés aux licences locatives.

Le fait de rétromigrer votre licence peut provoquer l'échec de votre instance vCenter Server. Vous pouvez choisir de rétromigrer une licence à vos risques et périls, mais avant, examinez attentivement les fonctions qui ne seront plus disponibles à l'issue de cette opération. Pour plus d'informations, voir [Graphique de comparaison des éditions de composant VMware](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution-appendix).
{:important}

## Considérations importantes à prendre en compte lorsque vous retirez Hybridity Bundle d'un environnement multisite
{: #vc_hybrid_deletingbundle-considerations}

Voici les considérations que vous devez prendre en compte avant de retirer Hybridity Bundle d'un environnement multisite :

* Vous devez appliquer des licences BYOL à tous les déploiements multi-site avant de retirer les licences locatives.
* Vous devez combiner les licences VMware NSX et disposer d'une capacité d'utilisation suffisante sur tous les déploiements multisite.
* Vous devez créer un seul ticket de demande de service pour retirer Hybridity Bundle de tous les déploiements multisite.

Lors du retrait de Hybridity Bundle d'un environnement multisite, les licences BYOL sont appliquées. Il vous incombe de vous assurer que les éditions de licence sont cohérentes sur tous les sites d'une configuration multisite.
{:note}

## Avant de retirer Hybridity Bundle
{: #vc_hybrid_deletingbundle-prereq}

Vérifiez que les conditions requises suivantes sont respectées avant de retirer Hybridity Bundle :

* Vous disposez d'une instance V2.4 ou de niveau ultérieur avec Hybridity Bundle activé.
* Le service VMware HCX on {{site.data.keyword.cloud_notm}} n'est pas installé sur votre instance vCenter Server.
* Vous avez accès au client Web VMware vSphere en tant qu'administrateur.
* Vous avez déjà appliqué des clés BYOL pour VMware NSX et chaque cluster VMware vSAN ou vous possédez des clés BYOL prêtes à être appliquées.
* Vous pouvez éventuellement appliquer des clés BYOL pour les licences VMware vCenter Server et VMware vSphere Enterprise Plus.

## Procédure de retrait d'Hybridity Bundle
{: #vc_hybrid_deletingbundle-procedure}

1. Connectez-vous en tant qu'**Administrateur** au client VMware vSphere Web Client sur lequel vous voulez retirer Hybridity Bundle.
2. Cliquez sur **Accueil > Administration > Octroi de licence > Licences**.
3. Cliquez sur l'onglet **Actifs**.
4. Procédez comme suit pour installer une licence BYOL pour VMware NSX :
   1. Cliquez sur l'onglet **Solutions**.
   2. Sélectionnez NSX for vSphere et cliquez sur **Toutes les actions > Affecter une licence**.
   3. Cliquez sur l'icône **Ajouter** et saisissez la clé de licence. Cliquez sur **Suivant**.
   4. Tapez le nom de la licence et cliquez sur **Suivant**. Cliquez sur **Terminer** pour ajouter la licence.
   5. Sélectionnez la nouvelle clé de licence.
   6. Notez les clés de licence complètes de la licence qui est appliquée et de la licence qui est remplacée.

   Vous devez disposer des détails de licence afin de pouvoir les utiliser ultérieurement dans cette procédure.
   {:important}
   7. Cliquez sur **OK** pour affecter la licence.
5. Procédez comme suit pour installer une licence BYOL pour VMware vSAN :
   1. Cliquez sur l'onglet **Clusters**.
   2. Procédez comme suit pour chaque cluster vSAN associé à votre instance vCenter Server :
    1. Sélectionnez un cluster vSAN et cliquez sur **Toutes les actions > Affecter une licence**.
    2. Cliquez sur l'icône **Ajouter** et saisissez la clé de licence. Cliquez sur **Suivant**.
    3. Tapez le nom de la licence et cliquez sur **Suivant**. Cliquez sur **Terminer** pour ajouter la licence.
    4. Sélectionnez la nouvelle clé de licence.
    5. Notez le nom de cluster et les clés de licence complètes de la licence qui est appliquée et de la licence qui est remplacée.

    Vous devez disposer des détails de licence afin de pouvoir les utiliser ultérieurement dans cette procédure.
    {:important}
    6. Cliquez sur **OK** pour affecter la licence.
6. Procédez éventuellement comme suit pour installer une licence BYOL pour VMware vCenter Server :
   1. Cliquez sur l'onglet **Systèmes vCenter Server**.
   2. Sélectionnez vCenter Server et cliquez sur **Toutes les actions > Affecter une licence**.
   3. Cliquez sur l'icône **Ajouter** et saisissez la clé de licence. Cliquez sur **Suivant**.
   4. Tapez le nom de la licence et cliquez sur **Suivant**. Cliquez sur **Terminer** pour ajouter la licence.
   5. Sélectionnez la nouvelle clé de licence.
   6. Notez les clés de licence complètes de la licence qui est appliquée et de la licence qui est remplacée.

   Vous devez disposer des détails de licence afin de pouvoir les utiliser ultérieurement dans cette procédure.
   {:important}

   7. Cliquez sur **OK** pour affecter la licence.
7. Procédez éventuellement comme suit pour installer une licence BYOL pour VMware vSphere Enterprise Plus :
  1. Cliquez sur l'onglet **Hôtes**.
  2. Procédez comme suit pour chaque cluster associé à votre instance vCenter Server ou pour tous les clusters à la fois si la même licence est appliquée à tous les clusters associés à votre serveur vCenter :
    1. Sélectionnez les hôtes qui sont associés au cluster et cliquez sur **Toutes les actions > Affecter une licence**.
    2. Cliquez sur l'icône **Ajouter** et saisissez la clé de licence. Cliquez sur **Suivant**.
    3. Tapez le nom de la licence et cliquez sur **Suivant**. Cliquez sur **Terminer** pour ajouter la licence.
    4. Sélectionnez la nouvelle clé de licence.
    5. Notez le nom de cluster et les clés de licence complètes de la licence qui est appliquée et de la licence qui est remplacée.

    Vous devez disposer des détails de licence afin de pouvoir les utiliser ultérieurement dans cette procédure. Si les clés de licence ne sont pas identiques d'un cluster à l'autre, prenez soin de noter le nom de cluster associé à chacune d'elles.
    {:important}

    6. Cliquez sur **OK** pour affecter la licence.
8. Retirez les licences locatives.
   1. Cliquez sur l'onglet **Licences**.
   2. Sélectionnez les licences que vous avez remplacées dans les étapes 4 à 7.
   3. Cliquez sur l'icône **Retirer des licences**.
9. Ouvrez un ticket de demande de service et indiquez les informations suivantes pour annuler les frais liés aux licences locatives :
  * Le nom d'une ou plusieurs de vos instances vCenter Server.
  * L'ID associé à une ou plusieurs de vos instances vCenter Server.
  * La liste des clés de licence BYOL que vous avez installées au cours de cette procédure. Le cas échéant, indiquez le nom de l'instance et du cluster avec les clés de licence pour vSphere et les clusters vSAN.
  * La liste des clés de licence locative que vous avez retirées au cours de cette procédure. Le cas échéant, indiquez le nom de l'instance et du cluster avec les clés de licence pour vSphere et les clusters vSAN.

  Avant d'annuler les frais liés à la licence locative Hybridity Bundle, les équipes chargées du support et des opérations IBM accèdent à la couche de gestion vCenter de votre compte d'infrastructure {{site.data.keyword.cloud_notm}} pour s'assurer que les licences locatives ont été retirées.
  {:note}

## Liens connexes
{: #vc_hybrid_deletingbundle-related}

* [Commande d'instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Affichage des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
