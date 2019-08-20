---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: shared order resources, order reserved shared, order reserved resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande de la solution Shared - Reserved
{: #shared_ordering_reserved}

{{site.data.keyword.vmwaresolutions_full}} - Shared est fourni en tant qu'offre expérimentale.
{:note}

Pour Shared Reserved, les réservations de vCPU et de RAM des centres de données virtuels sont préallouées et leur disponibilité garantie.
* Le coût est calculé chaque mois pour la totalité de la réservation et il est basé sur la taille d'allocation du centre de données virtuel.
* Les ressources de vCPU et RAM peuvent, au besoin, être augmentées et diminuées ultérieurement.
* La quantité de mémoire pouvant être allouée et utilisée dans le centre de données virtuel n'est pas limitée. Les frais sont calculés à l'heure sur la base de la quantité en Go de stockage allouée.
* La capacité de réseaux publics entrants et sortants n'est pas limitée. La bande passante publique est facturée par Go.

## Exigences relatives aux solutions IBM Cloud for VMware - Shared
{: #shared_ordering_reserved-req}

### Compte d'infrastructure IBM Cloud
{: #shared_ordering_reserved-account-req}

Pour pouvoir utiliser {{site.data.keyword.vmwaresolutions_short}} afin de commander des solutions IBM Cloud for VMware - Shared, vous devez disposer d'un compte **Paiement à la carte** ou **Abonnement** {{site.data.keyword.cloud_notm}}. Le coût des ressources commandées est facturé sur ce compte {{site.data.keyword.cloud_notm}}.

### Exigences relatives au nom du centre de données virtuel
{: #shared_ordering_reserved-vdc-name-req}

Le nom du centre de données virtuel *doit* répondre aux exigences suivantes. Les exigences de dénomination seront appliquées à l'avenir.
* Seuls les caractères alphabétiques minuscules, numériques et tirets (-) sont autorisés.
* Le nom doit commencer par un caractère alphabétique minuscule.
* Le nom doit se terminer par un caractère alphabétique minuscule ou un caractère numérique.
* La longueur maximale du nom du centre de données virtuel est de 10 caractères.
* Le nom du centre de données virtuel doit être unique dans votre compte.

## Procédure de commande de la solution Shared - Reserved
{: #shared_ordering-procedure}

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur l'icône **VMware** dans le panneau de navigation de gauche, puis sur la carte **IBM Cloud for VMware Solutions Shared** dans la section **Centres de données virtuels VMWare**.
2. Sur la page **IBM Cloud for VMware Solutions Shared**, cliquez sur la carte **Reserved**, puis sur **Créer**.
3. Sur la page **IBM Cloud for VMware Solutions Shared - Reserved**, entrez le nom du centre de données virtuel.
4. Choisissez la durée d'engagement pour la réservation de ressources. Le {{site.data.keyword.CloudDataCent_notm}} où l'offre est disponible est présélectionné.
5. Indiquez la réservation de ressource :
    * Lorsque vous sélectionnez **Préconfiguré**, choisissez l'une des configurations prédéfinies.
    * Lorsque vous sélectionnez **Personnalisé**, indiquez les réservations de vCPU et de RAM.
6. Dans le panneau **Récapitulatif de la commande** , vérifiez la configuration et le coût estimé avant de passer la commande.
7. Cliquez sur **Mettre à disposition**.

## Résultats après commande de la solution Shared - Reserved
{: #shared_ordering_reserved-results}

* Le déploiement des ressources démarre automatiquement et vous recevez la confirmation que la commande est en cours de traitement. Vous pouvez vérifier l'état du déploiement, y compris les problèmes qui peuvent nécessiter votre attention, en affichant le **statut du centre de données virtuel**.
* Une fois les ressources correctement déployées, les composants décrits dans les [spécifications techniques pour {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs) sont installés sur votre plateforme virtuelle VMware.
* Une fois les ressources prêtes à l'emploi, le statut passe à l'état **Prêt à utiliser**.

## Liens connexes
{: #shared_ordering_reserved-related}

* [Présentation des solutions {{site.data.keyword.cloud_notm}} for VMware Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Commande de la solution Shared - On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Gestion des solutions {{site.data.keyword.cloud_notm}} for VMware - Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
