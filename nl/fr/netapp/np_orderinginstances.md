---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande d'instances NetApp ONTAP Select
{: #np_orderinginstances}

Pour déployer une plateforme virtuelle VMware avec un dispositif de stockage défini par logiciel dédié et à haute disponibilité, commandez une instance NetApp ONTAP Select.

## Conditions requises
{: #np_orderinginstances-req}

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud}} sur la page **Paramètres**. Pour plus d'informations, voir [Gestion des paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Vous avez passé en revue les exigences et les remarques énoncées dans [Exigences et planification pour les instances NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning).

Ne modifiez aucune des valeurs définies lors de la commande ou du déploiement de l'instance. Cela rendrait votre instance inutilisable. Par exemple, si le réseau public s'arrête, si les serveurs et les instances de serveur virtuel passent derrière un mi-parcours Vyatta ou si l'instance de serveur virtuel IBM CloudBuilder s'arrête ou est supprimée.
{:important}

## Paramètres système
{: #np_orderinginstances-sys-settings}

Lorsque vous commandez une instance NetApp ONTAP Select, vous devez spécifier les paramètres de base suivants :

### Nom d'instance
{: #np_orderinginstances-instance-name}

Le nom de l'instance qui doit respecter les règles suivantes :
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Le nom d'instance doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique.
* Le nom d'instance ne doit pas dépasser 10 caractères.
* Le nom d'instance doit être unique au sein de votre compte.

## Paramètres d'interface réseau
{: #np_orderinginstances-network-interface-settings}

Vous devez spécifier les paramètres d'interface réseau suivants lorsque vous commandez une instance NetApp ONTAP Select.

### Préfixe de nom d'hôte
{: #np_orderinginstances-host-name-prefix}

Le préfixe du nom d'hôte qui doit respecter les règles suivantes :
*  Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
*  Le préfixe de nom d'hôte doit commencer et se terminer par un caractère alphanumérique.
*  Le préfixe de nom d'hôte ne doit pas dépasser 10 caractères.

### Libellé de sous-domaine
{: #np_orderinginstances-subdomain-label}

Le libellé du sous-domaine qui doit respecter les règles suivantes :
*  Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
*  Le libellé de sous-domaine doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique.
*  Le libellé de sous-domaine ne doit pas dépasser 10 caractères.
*  Le libellé de sous-domaine doit être unique au sein de votre compte.

### Nom de domaine
{: #np_orderinginstances-domain-name}

Le nom du domaine racine qui doit respecter les règles suivantes :
* Le nom de domaine doit être composé d'au moins deux chaînes séparées par un point (.)
* La première chaîne doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique.
* Toutes les chaînes, à l'exception de la dernière, ne peuvent contenir que des caractères alphanumériques et des tirets (-).
* La dernière chaîne ne peut contenir que des caractères alphabétiques.
* La dernière chaîne doit comporter entre 2 et 24 caractères.

La longueur maximale du nom de domaine complet des hôtes et des machines virtuelles est de 50 caractères. Les noms de domaine doivent respecter cette longueur maximale.
{:note}

## Paramètres d'octroi de licence
{: #np_orderinginstances-licensing-settings}

Vous devez télécharger quatre fichiers de licence NetApp, un pour chacun des quatre serveurs {{site.data.keyword.baremetal_short}}. Contactez l'équipe commerciale NetApp afin de vous procurer la licence appropriée pour votre déploiement hautes performances ou haute capacité.

## Paramètres de serveur bare metal
{: #np_orderinginstances-bare-metal-settings}

### Emplacement de centre de données
{: #np_orderinginstances-dc-location}

Vous devez sélectionner l'{{site.data.keyword.CloudDataCent_notm}} où l'instance doit être hébergée.

### Configuration de serveur bare metal
{: #np_orderinginstances-bare-metal-config}

Sélectionnez une configuration de serveur bare metal adaptée à vos besoins :
* **Hautes performances (Moyenne)** – Licence Premium/Dual Intel Xeon E5-2650 v4 (24 coeurs au total, 2,2 GHz)/128 Go de RAM/capacité de 22 unités SSD de 1,9 To par noeud/capacité effective d'un cluster de 4 noeuds – 59 To
* **Hautes performances (Grande)** – Licence Premium/Dual Intel Xeon E5-2650 v4 (24 coeurs au total, 2,2 GHz)/128 Go de RAM/capacité de 22 unités SSD de 3,8 To par noeud/capacité effective d'un cluster de 4 noeuds – 118 To
* **Haute capacité** – Licence Standard/Dual Intel Xeon E5-2650 v4 (24 coeurs au total, 2,2 GHz)/64 Go de RAM/capacité de trente-quatre unités SATA de 4 To par noeud/capacité effective d'un cluster de 4 noeuds – 190 To

Les unités SSD de 3,8 To sont prises en charge une fois qu'elles sont officiellement disponibles dans un {{site.data.keyword.CloudDataCent_notm}}.
{:note}

### Nombre de serveurs bare metal
{: #np_orderinginstances-bare-metal-number}

Le nombre de serveurs ESXi d'une instance NetApp ONTAP Select est de 4 par défaut. Vous ne pouvez pas modifier cette valeur. Tous les serveurs ESXi partagent la même configuration.

## Procédure à utiliser pour commander des instances NetApp ONTAP Select
{: #ordering-netapp-ontap-select-instances}

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **NetApp ONTAP Select** dans la section **Centres de données virtuels**.
2. Sur la page **NetApp ONTAP Select**, cliquez sur **Créer**.
3. Sur la page **NetApp ONTAP**, entrez le nom de l'instance.
4. Spécifiez les paramètres d'interface réseau **Préfixe de nom d'hôte**, **Libellé de sous-domaine** et **Nom de domaine**.
5. Spécifiez les paramètres d'octroi de licence en cliquant sur **Ajouter des fichiers de licence** pour télécharger les quatre fichiers de licence NetApp requis pour les quatre serveurs {{site.data.keyword.baremetal_short}}.
6. Spécifiez les paramètres de serveur bare metal :
   1. Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} qui doit héberger l'instance.
   2. Sélectionnez la configuration de serveur bare metal.
7. Sur la page **Récapitulatif de la commande**, vérifiez la configuration de l'instance avant de passer la commande.
    1. Passez en revue les paramètres de l'instance.
    2. Passez en revue le coût estimé de l'instance. Cliquez sur **Détails concernant la tarification** pour générer un récapitulatif au format PDF. Pour sauvegarder ou imprimer votre récapitulatif de commande, cliquez sur l'icône d'**impression** ou de **téléchargement** dans la fenêtre du PDF.
    3. Assurez-vous que le compte qui sera facturé est correct et cochez la case **Je comprends que le compte répertorié ci-dessous sera facturé**.
    4. Cliquez sur le ou les liens des conditions applicables à votre commande. Prenez soin d'accepter ces conditions, puis cochez la case **J'ai lu et j'accepte les accords de services tiers ci-dessous**.
    5. Cliquez sur **Mettre à disposition**.

## Résultats
{: #np_orderinginstances-results}

Le déploiement de l'instance commence automatiquement. Vous recevez une confirmation que la commande est en cours de traitement et vous pouvez vérifier l'état du déploiement en affichant les détails de l'instance.

Une fois l'instance correctement déployée, les composants décrits dans [Spécifications techniques relatives aux instances NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#technical-specifications-for-netapp-ontap-select-instances) sont installés sur votre plateforme virtuelle VMware.

Lorsque l'instance est prête pour utilisation, l'instance prend le statut **Prêt à l'emploi** et vous recevez une notification par courrier électronique.

## Etape suivante
{: #np_orderinginstances-next}

Affichez et gérez l'instance NetApp ONTAP Select que vous avez commandée.

Vous devez gérer les composants {{site.data.keyword.vmwaresolutions_short}} créés dans votre compte {{site.data.keyword.cloud_notm}} uniquement depuis la console {{site.data.keyword.vmwaresolutions_short}}, et non depuis le portail	{{site.data.keyword.slportal}} ou tout autre élément extérieur à la console. Si vous modifiez ces composants en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, les modifications ne sont pas synchronisées avec la console.
{:important}

**ATTENTION :** gérer des composants {{site.data.keyword.vmwaresolutions_short}} (installés dans votre compte {{site.data.keyword.cloud_notm}} lorsque vous avez commandé l'instance) en dehors de la console {{site.data.keyword.vmwaresolutions_short}} risque de rendre votre environnement instable. Ces activités de gestion incluent :
*  L'ajout, la modification, le retour ou la suppression de composants
*  La mise hors tension de composants

   Seules les activités de gestion des partages de fichiers du stockage partagé depuis le portail {{site.data.keyword.slportal}} font exception. Il s'agit des activités suivantes : commande, suppression (pouvant avoir un impact sur des magasins de données éventuellement montés), accord d'autorisation et montage de partages de fichiers de stockage partagé.

## Liens connexes
{: #np_orderinginstances-related}

* [Affichage des instances NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_viewinginstances)
* [Suppression d'instances NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_deletinginstance)
* [Centre de documentation NetApp ONTAP](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html)
* [Liaison d'un stockage dédié à des déploiements NetApp ONTAP Select](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
