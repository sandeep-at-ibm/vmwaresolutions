---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# Foire aux questions sur l'octroi de licence et le mode BYOL

Trouvez des réponses aux questions concernant l'octroi de licence, y compris la fonction BYOL d'{{site.data.keyword.vmwaresolutions_full}}.

## Qu'est-ce que BYOL ?

Bring Your Own License, ou BYOL, est une fonction disponible pour les instances VMware Cloud Foundation en V1.8 et dans des éditions ultérieures et pour les clusters vCenter Server et vSphere en V2.0 et dans des éditions ultérieures. La fonction BYOL vous permet d'utiliser vos propres licences VMware pour un ou plusieurs des composants logiciels VMware suivants lorsque vous commandez des instances :
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

Si vous choisissez d'utiliser votre propre licence pour un composant VMware et de fournir une clé de licence valide pour celui-ci, aucune licence n'est commandée auprès d'IBM pour ce composant et aucun frais de licence mensuel n'est facturé sur votre compte d'infrastructure {{site.data.keyword.cloud}} pour ce composant. 

**Remarque :** cette fonction BYOL n'est pas disponible pour les partenaires commerciaux.

## Où puis-je gérer les licences et les composants commandés via VMware vSphere on IBM Cloud ?

Une fois que vous avez passé une commande de création d'un nouveau cluster pour VMware vSphere on {{site.data.keyword.cloud_notm}}, les licences VMware, les serveurs ESXi et les autres composants de réseau sont distribués et peuvent être gérés depuis le portail {{site.data.keyword.slportal}}.

Après le déploiement, accédez à la console {{site.data.keyword.vmwaresolutions_short}} afin de mettre à l'échelle le nouveau cluster à l'aide de la configuration enregistrée. Pour plus d'informations sur la mise à l'échelle, voir [Mise à l'échelle de clusters vSphere existants](../vsphere/vs_scalingexistingclusters.html).

## Quelles éditions de licence et quantités d'UC sont nécessaires pour BYOL ?

Les exigences suivantes s'appliquent aux éditions de licence pour BYOL.

### Exigences de BYOL pour les instances vCenter Server

Tableau 1. Exigences pour les éditions de licence et le minimum d'UC pour les instances vCenter Server

  | Composant VMware | Edition de licence requise | Nombre minimum d'UC requis
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard                | Non applicable |
  | vSphere        | Entreprise Plus | 8 UC |
  | vSAN           | Advanced ou Enterprise | 8 UC |
  | NSX            | Standard, Advanced ou Enterprise | 8 UC |

### Exigences de BYOL pour les instances Cloud Foundation

Tableau 2. Exigences pour les éditions de licence et le minimum d'UC pour les instances Cloud Foundation

  | Composant VMware | Edition de licence requise | Nombre minimum d'UC requis
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard | Non applicable |
  | vSphere        | Entreprise Plus | 8 UC |
  | vSAN           | Advanced ou Enterprise | 8 UC |
  | NSX            | Enterprise | 8 UC |

## Que se passe-t-il si la clé de licence fournie est incorrecte ?

Toutes les clés de licence que vous fournissez sont validées afin de garantir qu'elles sont correctes pour les composants VMware correspondants et qu'elles respectent les exigences en matière d'édition et d'UC minimum des composants VMware. Si la validation de l'une des clés de licence échoue, vous recevez une notification et vous ne pouvez pas poursuivre la commande de l'instance.

## Puis-je fournir une clé de licence avec plus de 8 UC ?

Oui. Pour chaque composant VMware, une licence par UC est requise. Actuellement, tous les serveurs vCenter Server et Cloud Foundation disposent de deux UC et deux licences sont requises pour chaque serveur. Il est recommandé de fournir une clé de licence à même de prendre en charge l'instance de base ainsi que tous les noeuds d'extension que vous pourriez vouloir ajouter ultérieurement à l'instance.

## Puis-je fournir la licence du gestionnaire SDDC lorsque j'utilise la fonction BYOL ?

Non. Notre accord avec VMware implique que vous devez accepter la clé de licence actuelle du client. Même si le déploiement de Cloud Foundation inclut des licences pour le gestionnaire SDDC, nous ne pouvons accepter et valider aucun fichier de clé de licence de gestionnaire SDDC pour BYOL. Par conséquent, les licences du gestionnaire SDDC sont facturées par IBM pour toutes les instances. Les licences du gestionnaire SDDC constituent une toute petite portion de l'ensemble des frais de licence pour une instance Cloud Foundation.

## Puis-je utiliser la fonction BYOL pour certains composants VMware et acheter des licences mensuelles pour d'autres ?

Oui. Vous pouvez utiliser la fonction BYOL ou acheter des licences pour toute combinaison des quatre composants VMware. La console {{site.data.keyword.vmwaresolutions_short}} vous simplifie la sélection de l'option de licence lorsque vous commandez une instance vCenter Server ou Cloud Foundation. Votre option de licence lors de la commande de l'instance initiale s'applique à toute la durée de vie de cette instance.

## Pour un composant VMware spécifique, puis-je utiliser BYOL pour certaines licences et acheter les autres licences à IBM ?

Oui. Si vous avez sélectionné BYOL pour un composant VMware spécifique, vous avez la possibilité lors de la création d'un nouveau cluster d'entrer une nouvelle clé BYOL, de continuer à utiliser une clé BYOL existante ou d'acheter une licence fournie par IBM pour ce cluster.  Actuellement, seuls VMware vSphere Enterprise et VMware vSAN sont disponibles pour l'octroi de licence par cluster.

## Puis-je utiliser BYOL lors de la création d'un nouveau cluster ?

Oui. Vous pouvez utiliser BYOL à partir de licences BYOL existantes ou entrer une nouvelle BYOL lors de la création d'un nouveau cluster. Vous avez également la possibilité d'acheter une licence d'abonnement fournie par IBM lors de la création d'un nouveau cluster. Actuellement, seuls VMware vSphere Enterprise et VMware vSAN sont disponibles pour l'octroi de licence par cluster.

## Comment puis-je gérer mes licences BYOL ?

Vous pouvez gérer vos licences BYOL à l'aide du client Web VMware vSphere une fois le déploiement de l'instance terminé.

## Si j'ajoute d'autres serveurs ESXi à mon instance ultérieurement, est-ce que l'instance vérifie si la capacité de mes licences BYOL est suffisante ?

Oui. Lorsque vous ajoutez des serveurs ESXi à une instance déployée, la capacité de vos licences BYOL est automatiquement vérifiée par rapport au nombre de serveurs ESXi spécifié. Si cette capacité n'est pas suffisante, les serveurs ESXi ne sont pas ajoutés et vous recevez une notification sur la console.

## Comment savoir de quelle capacité de licence je dispose sur un cluster avec BYOL ?

Pour connaître le nombre d'UC disponibles dans votre clé de licence, accédez à la page **Instances déployées**, localisez l'instance et cliquez dessus, puis sur l'onglet **Infrastructure**, cliquez sur le cluster pour lequel vous voulez vérifier la capacité de licence. Le nombre d'UC disponibles est indiqué dans le tableau **Licence fournie par l'utilisateur**.

## Est-ce que je bénéficie du support IBM lorsque je sélectionne l'option de licence BYOL ?

Le support IBM reste votre point de contact pour tout ce qui concerne la configuration d'instance. Toutefois, si le problème signalé concerne un composant VMware avec BYOL, vous êtes dirigé vers le support VMware.

## Pourquoi les frais de licence vSphere apparaissent-ils dans la liste d'estimation du prix lorsque j'utilise BYOL ? Suis-je facturé ?

Les serveurs {{site.data.keyword.baremetal_short}} sont mise à disposition avec VMware vSphere déjà installé et avec des licences vSphere déjà incluses. Si vous avez sélectionné BYOL pour vSphere, un processus est automatiquement initié au moment du déploiement de l'instance afin de supprimer les licences vSphere incluses. Les frais de licences sont ensuite crédités sur votre compte {{site.data.keyword.cloud_notm}}. Vous n'avez rien à faire concernant ce processus.

## Puis-je toujours utiliser le processus manuel existant pour BYOL ?

Avec l'introduction de la fonction BYOL, il n'est pas recommandé de continuer à utiliser le processus manuel. Si vous voulez utiliser BYOL, fournissez vos propres licences lorsque vous commandez l'instance.

## Est-ce que BYOL est pris en charge pour d'autres produits VMware tels que VMware vRealize Automation, VMware vRealize Operations ou VMware vRealize Log Insight ?

Non, parce que ces produits VMware ne font pas partie du déploiement de l'instance. Ces produits VMware peuvent être installés au-dessus du déploiement initial, ce qui implique que les clients ou leurs agents doivent effectuer l'installation et l'octroi de licence.

## Puis-je commander un stockage NFS avec vCenter Server with Hybridity Bundle ?

Pour les instances nouvellement déployées, seul le stockage vSAN All-Flash est pris en charge. L'offre vCenter Server with Hybridity Bundle inclut l'octroi de licence vSAN Advanced ou Enterprise. 

Si vous possédez une instance vCenter Server dotée de stockage NFS, vous pouvez mettre à niveau votre instance existante vers vCenter Server with Hybridity Bundle. Bien que l'octroi de licence vSAN Advanced soit commandé durant la mise à niveau, vous n'êtes pas tenu de mettre à disposition un cluster All-flash vSAN. 

## Puis-je utiliser le mode BYOL avec vCenter Server with Hybridity Bundle ?

Vous ne pouvez pas utiliser votre propre licence VMware (BYOL) sur {{site.data.keyword.cloud_notm}}. vCenter Server with Hybridity Bundle exige que toutes les licences VMware soient fournies par IBM. 

## Quelle est la différence entre l'octroi de licence vCenter Server with Hybridity Bundle et l'octroi de licence vCenter Server ?

Les licences VMware individuelles disponibles dans vCenter Server sont facturées par unité centrale. Comme avec toutes les licences VMware facturées par unité centrale fournies par IBM, le prix est majoré de 1.3x sur tous les serveurs dotés de plus de 16 coeurs par unité centrale, pour Dual Intel Xeon Gold 6140.

vCenter Server with Hybridity Bundle est un ensemble prescrit de licences et d'éditions VMware soumis à une licence par coeur et non par unité centrale. Par conséquent, le prix de la licence pour ces instances ne change pas.

## Quels sont les composants et éditions de licence VMware fournis par IBM disponibles pour vCenter Server with Hybridity Bundle ?

Les nouvelles instances de vCenter Server with Hybridity Bundle incluent VMware vSphere Enterprise Plus, VMware vCenter Standard, VMware NSX Advanced ou Enterprise, VMware vSAN Advanced ou Enterprise et VMware Hybrid Cloud Extension (HCX).

Si vous possédez une instance vCenter Server dotée d'une édition NSX Base, une mise à niveau vers l'édition NSX Advanced s'effectuera automatiquement lorsque vous commanderez vCenter Server with Hybridity Bundle. 

## Puis-je mettre à niveau l'édition NSX Advanced qui est incluse dans vCenter Server with Hybridity Bundle vers l'édition NSX Enterprise ?

Bien que vCenter Server with Hybridity Bundle inclut l'édition NSX Advanced, vous pouvez effectuer une mise à niveau vers l'édition NSX Enterprise après avoir commandé vCenter Server with Hybridity Bundle. Pour ce faire, utilisez l'onglet **Mise à jour et module de correction** de la page des détails d'instance sur la console {{site.data.keyword.vmwaresolutions_short}}. 

### Liens connexes

* [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Instances Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Accès à la console](loginmethod.html)
* [Contacter le support IBM](trbl_support.html)
* [vRealize Automation](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/vRealizeAutomation){:new_window}
