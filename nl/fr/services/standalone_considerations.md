---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: VMware HCX standalone, HCX on-premises, tech specs HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Remarques relatives aux instances VMware HCX on IBM Cloud locales
{: #standalone_considerations}

Passez en revue les remarques suivantes avant d'installer ou de supprimer des instances HCX on {{site.data.keyword.cloud}} que vous avez commandées pour une utilisation locale :

Une instance vCenter Server avec HCX on {{site.data.keyword.cloud_notm}} est limitée à trois connexions simultanées à partir des sites locaux.
{:note}

## Remarques relatives à l'installation d'instances HCX on IBM Cloud locales
{: #standalone_considerations-install}

Les composants HCX on {{site.data.keyword.cloud_notm}} doivent être installés à la fois sur {{site.data.keyword.cloud_notm}} et dans votre environnement vSphere local. Il est recommandé d'installer le service HCX on {{site.data.keyword.cloud_notm}} dans votre instance vCenter Server sur {{site.data.keyword.cloud_notm}} avant d'installer l'instance HCX on {{site.data.keyword.cloud_notm}} locale. Pour plus d'informations, voir [Remarques relatives à l'installation de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-hcx_considerations#hcx_considerations-install).

### Exigences liées aux adresses IP
{: #standalone_considerations-ip}

Pour que HCX fonctionne parfaitement, vous avez besoin d'au moins cinq adresses IP privées ayant un accès à Internet.

### Processus de déploiement des instances HCX on IBM Cloud locales
{: #standalone_considerations-deploy}

Vous devez effectuer les tâches suivantes pour installer correctement l'instance HCX on {{site.data.keyword.cloud_notm}} locale :
1. Depuis la console {{site.data.keyword.vmwaresolutions_short}}, commandez l'instance HCX locale sur {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [Commande d'instances HCX locales](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances).
2. Dans **Console HCX Cloud**, procédez comme suit :
    1. Cliquez sur l'onglet **Administration**.
    2. Sur l'onglet **Mises à jour système**, cliquez sur **Demander le lien de téléchargement**.
    3. Cliquez sur **Copier le lien**, puis utilisez ce lien pour télécharger le client HCX Enterprise sur un environnement local avec accès à votre environnement vSphere local.
3. Dans le client VMware vSphere Web Client, déployez le client HCX Enterprise en tant que dispositif virtuel HCX Manager dans votre environnement local.

   Vous devez déployer le gestionnaire HCX Manager local dans un réseau privé et l'autoriser à accéder au réseau public. Vous pouvez utiliser une passerelle NSX Edge, Vyatta ou autre pour accorder l'accès Internet au gestionnaire HCX Manager local. Si les passerelles utilisées pour l'accès au réseau privé et l'accès au réseau public sont différentes, il est recommandé d'utiliser la passerelle par défaut pour autoriser l'accès au réseau public et permettre, depuis la **console d'administration de HCX Manager**, de créer une route statique pour l'accès au réseau privé.
   {:note}
4. Une fois le déploiement de HCX Manager terminé, utilisez la **console d'administration de HCX Manager** pour activer le gestionnaire HCX Manager local. Pour obtenir une clé d'activation pour le gestionnaire HCX Manager local, commandez une instance HCX on {{site.data.keyword.cloud_notm}} locale dans la console {{site.data.keyword.vmwaresolutions_short}}. Pour plus d'informations, voir [Commande d'instances HCX locales](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances).
5. Si vous utilisez un certificat SSL autosigné lors de la commande du service HCX on {{site.data.keyword.cloud_notm}}, vous devez importer le certificat dans le gestionnaire HCX Manager local en procédant comme suit :
    1. Sur la **console d'administration de HCX Manager**, cliquez sur l'onglet **Administration**.
    2. Dans le panneau de navigation de gauche, cliquez sur **Certificat d'autorité de certification digne de confiance**, puis sur **Importer** sur la droite.
    3. Cliquez sur **URL**, puis entrez l'adresse URL du certificat que vous souhaitez appliquer, c'est-à-dire l'**adresse IP HCX Cloud** (``https://<cloud-side public IP>``) que vous trouverez sur la page des détails du service HCX on {{site.data.keyword.cloud_notm}} dans la console {{site.data.keyword.vmwaresolutions_short}}.
    4. Cliquez sur **Appliquer**.

La configuration de base du gestionnaire HCX Manager local est terminée. Vous pouvez poursuivre l'appariement du site HCX on {{site.data.keyword.cloud_notm}} local avec le site HCX côté cloud.

Pour plus d'informations, voir [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx){:external}.

## Remarques relatives à la suppression des instances HCX on IBM Cloud locales
{: #standalone_considerations-delete}

Passez en revue les remarques suivantes avant de supprimer une instance CX on {{site.data.keyword.cloud_notm}} qui a été commandée pour une utilisation locale :
1. Dans le client VMware vSphere Web Client, accédez à l'interface utilisateur de HCX et vérifiez que :
    1. aucune opération de reprise après incident ou de migration HCX n'est en cours d'exécution ;
    2. tous les réseaux étendus ont été supprimés ;
    3. tous les composants interconnectés aux sites de cloud appariés ont été supprimés.

   Vous devez avoir effectué toutes les étapes précédentes avant de passer à l'étape suivante. Sinon, la licence de l'instance HCX on {{site.data.keyword.cloud_notm}} locale sera annulée. Si la licence est annulée, aucune migration ne pourra être effectuée et des erreurs seront susceptibles de se produire au niveau des composants HCX.  
   {:important}
2. Dans la console {{site.data.keyword.vmwaresolutions_short}}, supprimez l'instance HCX on {{site.data.keyword.cloud_notm}} HCX locale qui avait été commandée pour obtenir la clé d'activation pour le gestionnaire HCX Manager local. Vérifiez que l'instance supprimée n'est plus disponible sur la console avant de passer à l'étape suivante.

   Pour plus d'informations, voir [Suppression d'instances HCX on {{site.data.keyword.cloud_notm}} locales](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_deletingserviceinstances).
3. Dans le client VMware vSphere Web Client, supprimez le gestionnaire HCX Manager local.

## Liens connexes
{: #standalone_considerations-related}

* [Affichage d'instances HCX on {{site.data.keyword.cloud_notm}} locales](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_viewingserviceinstances)
* [Glossaire des termes HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Documentation VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources){:external}
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
