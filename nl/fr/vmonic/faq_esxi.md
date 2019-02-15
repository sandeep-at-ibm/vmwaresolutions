---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Foire aux questions sur les serveurs ESXi

Trouvez les réponses aux questions fréquemment posées au sujet des serveurs ESXi gérés sur la console {{site.data.keyword.vmwaresolutions_full}}.

## Combien de serveurs ESXi puis-je ajouter à mon instance ?
{: faq}

* Pour les instances vCenter Server, vous pouvez développer le cluster par défaut jusqu'à contenir 51 serveurs ESXi. Chacun des autres clusters peut contenir jusqu'à 59 serveurs ESXi. Etant donné que vous pouvez ajouter jusqu'à 10 clusters à une instance, chaque instance déployée peut avoir un maximum de 51 + 9x59 = 582 serveurs ESXi pour l'ensemble des clusters.
* Pour les instances Cloud Foundation, la configuration standard contient quatre serveurs ESXi. Vous pouvez ajouter jusqu'à 28 serveurs au maximum (soit un total de 32 serveurs). Pour les instances Cloud Foundation d'une configuration multisite, vous pouvez avoir jusqu'à 128 serveurs ESXi au maximum pour toutes les instances.

  Si votre configuration Cloud Foundation nécessite un déploiement multisite de plus de 128 serveurs ESXi, [contactez le support IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html) pour obtenir de l'aide.
  {:note}

## Combien de serveurs ESXi puis-je ajouter à un cluster ?

Pour les instances déployés dans la version 2.2 et les versions suivantes, vous pouvez ajouter jusqu'à 51 serveurs ESXi au maximum au cluster initial et jusqu'à 59 serveurs ESXi au maximum aux clusters additionnels.

Pour les instances déployées dans la version 2.1 ou des éditions antérieures, vous devez activer la prise en charge vSAN nécessaire pour augmenter la taille du cluster au-delà de 32 éléments. Pour activer la prise en charge vSAN nécessaire, procédez comme suit :

1. Sur chaque serveur ESXi déployé, exécutez les commandes suivantes :

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. Redémarrez chaque serveur ESXi. Pour plus d'informations, voir [Création d'un cluster vSAN 6.x avec jusqu'à 64 hôtes](https://kb.vmware.com/s/article/2110081).
3. Vous serez peut-être amené à augmenter la taille du vCenter Server pour tenir compte des machines virtuelles et des serveurs ESXi supplémentaires.
4. Ouvrez un ticket de demande de service IBM pour indiquer que vous avez appliqué manuellement les modifications vSAN en exécutant les étapes 1 à 3. Dans le ticket, demandez à ce que votre instance mise à niveau puisse gérer plus de 32 serveurs ESXi.

## Puis-je modifier les noms et les adresses IP des serveurs ESXi ?

Vous ne pouvez pas modifier les noms et les adresses IP des serveurs ESXi car ils sont enregistrés pour la résolution DNS Windows. Toute modification pourrait entraîner des échecs durant le déploiement ou dans les fonctions de vCenter Server.

N'utilisez pas la fonction **Renommer unité** de l'interface utilisateur {{site.data.keyword.cloud_notm}} pour modifier des noms de serveur ESXi. Cette fonction modifie le nom de domaine complet du serveur ESXi, mais le centre vCenter configuré et les enregistrements d'hôte d'instance de serveur virtuel Windows VSI seront incorrects et risquent de provoquer des incidents.
{:note}

## Puis-je désactiver l'accès racine sur mes serveurs ESXi ?

Il est recommandé de maintenir activé l'accès racine sur les serveurs ESXi, faute de quoi des échecs des fonctions d'{{site.data.keyword.vmwaresolutions_short}} pourraient survenir.

Si nécessaire, vous pouvez désactiver l'accès racine une fois que le statut des serveurs ESXi indique **Prêt à l'emploi** sur la console {{site.data.keyword.vmwaresolutions_short}}.

Vous devez réactiver l'accès racine pour les opérations d'automatisation ultérieures, par exemple lorsque vous ajoutez ou retirez des partages de fichiers ou installez des services complémentaires, tels que Zerto on {{site.data.keyword.cloud_notm}}.

## Puis-je ajouter des routes statiques sur mes serveurs ESXi afin de monter du stockage depuis d'autres emplacements ?

Vous pouvez ajouter des routes statiques pour le stockage mais vous devez le faire avec précaution. Sinon, les partages existants risquent d'être démontés.

L'ajout de routes statiques n'est pas pris en charge pour vMotion. Une modification de la configuration de sous-réseau vMotion pourrait entraîner des échecs des fonctions d'{{site.data.keyword.vmwaresolutions_short}}.
{:note}

### Liens connexes

* [Extension et réduction de capacité pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservers.html)
* [Extension et réduction de capacité pour des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_addingremovingservers.html)
* [Ajout, affichage et suppression de clusters pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)
* [Ajout, affichage et suppression de clusters pour des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_addingviewingclusters.html)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
