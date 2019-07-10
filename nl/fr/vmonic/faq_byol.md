---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: FAQ, license, BYOL

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Foire aux questions sur l'octroi de licence et le mode BYOL
{: #faq_byol}

Trouvez des réponses aux questions concernant l'octroi de licence, y compris la fonction BYOL d'{{site.data.keyword.vmwaresolutions_full}}.

## Qu'est-ce que BYOL ?
{: #faq_byol-def}
{: faq}

Bring Your Own License (BYOL) est une fonction disponible dans les clusters VMware vCenter Server et VMware vSphere dans la version 2.0 et dans des éditions ultérieures. La fonction BYOL vous permet d'utiliser vos propres licences VMware pour un ou plusieurs des composants logiciels VMware suivants :
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

Si vous choisissez d'utiliser votre propre licence pour un composant VMware et de fournir une clé de licence valide pour celui-ci, aucune licence n'est commandée auprès d'IBM pour ce composant et aucun frais de licence mensuel n'est facturé sur votre compte d'infrastructure {{site.data.keyword.cloud_notm}} pour ce composant.

La fonction BYOL n'est pas disponible pour les partenaires commerciaux.
{:note}

## Où puis-je gérer les licences et les composants commandés via VMware vSphere on IBM Cloud ?
{: #faq_byol-license-mgmt}
{: faq}

Une fois que vous avez passé une commande de création d'un nouveau cluster pour VMware vSphere on {{site.data.keyword.cloud_notm}}, les licences VMware, les serveurs ESXi et les autres composants de réseau sont distribués et peuvent être gérés depuis {{site.data.keyword.slportal}}.

Après le déploiement, accédez à la console {{site.data.keyword.vmwaresolutions_short}} afin de mettre à l'échelle le nouveau cluster à l'aide de la configuration enregistrée. Pour plus d'informations, voir [Mise à l'échelle de clusters existants](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters).

## Quelles éditions de licence et UC sont nécessaires pour BYOL ?
{: #faq_byol-license-cpu-reqs}
{: faq}

Les exigences suivantes s'appliquent aux éditions de licence pour BYOL.

### Exigences de BYOL pour les instances vCenter Server
{: #faq_byol-vcs-reqs}

Tableau 1. Exigences pour les éditions de licence et le minimum d'UC pour les instances vCenter Server

  | Composant VMware | Edition de licence requise | Nombre minimum d'UC requis
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard                | Non applicable |
  | vSphere        | Entreprise Plus | 8 UC |
  | vSAN           | Advanced ou Enterprise | 8 UC |
  | NSX            | Standard, Advanced ou Enterprise | 8 UC |

## Que se passe-t-il si la clé de licence fournie est incorrecte ?
{: #faq_byol-incorrect-license}
{: faq}

Toutes les clés de licence que vous fournissez sont validées afin de garantir qu'elles sont correctes pour les composants VMware correspondants et qu'elles respectent les exigences en matière d'édition et d'UC minimum des composants VMware. Si la validation de l'une des clés de licence échoue, vous recevez une notification et vous ne pouvez pas poursuivre la commande de l'instance.

## Puis-je fournir une clé de licence avec plus de 8 UC ?
{: #faq_byol-license-key}
{: faq}

Oui. Pour chaque composant VMware, une licence par UC est requise. Actuellement, tous les serveurs vCenter Server disposent de deux UC. Par conséquent, deux licences sont requises pour chaque serveur. Il est recommandé de fournir une clé de licence à même de prendre en charge l'instance de base ainsi que tous les noeuds d'extension que vous pourriez vouloir ajouter ultérieurement à l'instance.

## Puis-je utiliser la fonction BYOL pour certains composants VMware et acheter des licences mensuelles pour d'autres ?
{: #faq_byol-mthly-license}
{: faq}

Oui. Vous pouvez utiliser la fonction BYOL ou acheter des licences pour toute combinaison des quatre composants VMware. La console {{site.data.keyword.vmwaresolutions_short}} vous simplifie la sélection de l'option de licence lorsque vous commandez une instance. Votre option de licence lors de la commande de l'instance initiale s'applique à toute la durée de vie de cette instance.

## Pour un composant VMware spécifique, puis-je utiliser BYOL pour certaines licences et acheter les autres licences à IBM ?
{: #faq_byol-purchase}
{: faq}

Oui. Si vous avez sélectionné BYOL pour un composant VMware spécifique lors de la création d'un cluster, vous disposez des options suivantes :
* Entrer une nouvelle clé BYOL
* Continuer à utiliser une clé BYOL existante
* Acheter une licence IBM pour ce cluster.

Actuellement, seuls VMware vSphere Enterprise et VMware vSAN peuvent être utilisés sous licence par cluster.

## Puis-je utiliser BYOL lors de la création d'un cluster ?
{: #faq_byol-cluster}
{: faq}

Oui. Vous pouvez utiliser BYOL à partir de licences BYOL existantes ou entrer une nouvelle BYOL lors de la création d'un cluster. Vous avez également la possibilité d'acquérir une licence d'abonnement IBM lors de la création d'un cluster.

Actuellement, seuls VMware vSphere Enterprise et VMware vSAN peuvent être utilisés sous licence par cluster.

## Comment puis-je gérer mes licences BYOL ?
{: #faq_byol-mgmt}
{: faq}

Vous pouvez gérer vos licences BYOL à l'aide du client Web VMware vSphere une fois le déploiement de l'instance terminé.

## Si j'ajoute d'autres serveurs ESXi à mon instance ultérieurement, est-ce que l'instance vérifie si mes licences BYOL ont suffisamment de capacité ?
{: #faq_byol-add-esxi}
{: faq}

Oui. Lorsque vous ajoutez des serveurs ESXi à une instance déployée, la capacité de vos licences BYOL est automatiquement vérifiée par rapport au nombre de serveurs ESXi spécifié. Si cette capacité n'est pas suffisante, les serveurs ESXi ne sont pas ajoutés et vous recevez une notification sur la console.

## Comment savoir de quelle capacité de licence je dispose sur un cluster avec BYOL ?
{: #faq_byol-capacity}
{: faq}

Pour identifier le nombre d'UC utilisables avec votre clé de licence, procédez comme suit :
1. Accédez à la page **Ressources**.
2. Localisez et cliquez sur l'instance.
3. Sur l'onglet **Infrastructure**, cliquez sur le cluster pour lequel vous désirez vérifier la capacité de licence.
   Le nombre d'UC disponibles est indiqué dans le tableau **Licence fournie par l'utilisateur**.

## Est-ce que je bénéficie du support IBM lorsque je sélectionne l'option de licence BYOL ?
{: #faq_byol-support}
{: faq}

Le support IBM reste votre point de contact pour tout ce qui concerne la configuration d'instance. Toutefois, si le problème signalé concerne un composant VMware avec BYOL, vous êtes dirigé vers le support VMware.

## Pourquoi les frais de licence vSphere apparaissent-ils dans la liste d'estimation du prix lorsque j'utilise BYOL ? Suis-je facturé ?
{: #faq_byol-vsphere}
{: faq}

Les serveurs {{site.data.keyword.baremetal_short}} sont mise à disposition avec VMware vSphere déjà installé et avec des licences vSphere déjà incluses. Si vous avez sélectionné BYOL pour vSphere, un processus est automatiquement initié au moment du déploiement de l'instance afin de supprimer les licences vSphere incluses. Les frais de licences sont alors crédités sur votre compte {{site.data.keyword.cloud_notm}}. Vous n'avez rien à faire concernant ce processus.

## Puis-je toujours utiliser le processus manuel existant pour BYOL ?
{: #faq_byol-manual-process}
{: faq}

Avec l'introduction de la fonction BYOL, il n'est pas recommandé de continuer à utiliser le processus manuel. Si vous voulez utiliser BYOL, fournissez vos propres licences lorsque vous commandez l'instance.

## Est-ce que BYOL est pris en charge pour d'autres produits VMware tels que VMware vRealize Automation, VMware vRealize Operations ou VMware vRealize Log Insight ?
{: #faq_byol-other-support}
{: faq}

Non, parce que ces produits VMware ne font pas partie du déploiement de l'instance. Ces produits VMware peuvent être installés en sus du déploiement initial, ce qui implique que les clients ou leurs agents procèdent à l'installation et à l'octroi de licence.

## Puis-je commander un stockage NFS avec vCenter Server with Hybridity Bundle ?
{: #faq_byol-nfs}
{: faq}

Pour les instances nouvellement déployées, seul le stockage vSAN All-Flash est pris en charge. L'offre vCenter Server with Hybridity Bundle inclut l'octroi de licence vSAN Advanced ou Enterprise.

Si vous possédez une instance vCenter Server dotée de stockage NFS, vous pouvez mettre à niveau votre instance existante vers vCenter Server with Hybridity Bundle. Bien que l'octroi de licence vSAN Advanced soit commandé durant la mise à niveau, vous n'êtes pas tenu de mettre à disposition un cluster All-flash vSAN.

## Puis-je utiliser le mode BYOL avec vCenter Server with Hybridity Bundle ?
{: #faq_byol-hybridity}
{: faq}

Vous ne pouvez pas utiliser votre propre licence VMware (BYOL) sur {{site.data.keyword.cloud_notm}}. vCenter Server with Hybridity Bundle exige que toutes les licences VMware soient fournies par IBM.

## Quelle est la différence entre l'octroi de licence vCenter Server with Hybridity Bundle et l'octroi de licence vCenter Server ?
{: #faq_byol-hybridity-vcs}
{: faq}

Les licences VMware individuelles disponibles dans vCenter Server sont facturées par unité centrale. Comme avec toutes les licences VMware facturées par unité centrale fournies par IBM, le prix est majoré de 1.3x sur tous les serveurs dotés de plus de 16 coeurs par unité centrale, pour Dual Intel Xeon Gold 6140.

vCenter Server with Hybridity Bundle est un ensemble prescrit de licences et d'éditions VMware soumis à une licence par coeur et non par unité centrale. Par conséquent, le prix de la licence pour ces instances ne change pas.

## Quels sont les composants et éditions de licence VMware fournis par IBM disponibles pour vCenter Server with Hybridity Bundle ?
{: #faq_byol-hybridity-avail}
{: faq}

Les nouvelles instances de vCenter Server with Hybridity Bundle incluent VMware vSphere Enterprise Plus, VMware vCenter Standard, VMware NSX Advanced ou Enterprise, VMware vSAN Advanced ou Enterprise et VMware Hybrid Cloud Extension (HCX).

Si vous disposez d'une instance vCenter Server avec une édition NSX Base, une mise à niveau vers l'édition NSX Advanced est effectuée automatiquement lorsque vous commandez vCenter Server with Hybridity Bundle.

## Puis-je mettre à niveau l'édition NSX Advanced qui est incluse dans vCenter Server with Hybridity Bundle vers l'édition NSX Enterprise ?
{: #faq_byol-nsx-upgrade}
{: faq}

Bien que vCenter Server with Hybridity Bundle inclut l'édition NSX Advanced, vous pouvez effectuer une mise à niveau vers l'édition NSX Enterprise après avoir commandé vCenter Server with Hybridity Bundle. Pour ce faire, utilisez l'onglet **Mise à jour et module de correction** de la page des détails d'instance sur la console {{site.data.keyword.vmwaresolutions_short}}.

## Liens connexes
{: #faq_byol-related}

* [Accès à la console](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-loginmethod)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
