---

copyright:

  years:  2016

lastupdated: "2016-11-04"

subcollection: vmwaresolutions


---

# Notes sur l'édition pour la version 1.1
{: #relnotes_v11}

Cette édition inclut de nouvelles fonctionnalités, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Exigences liées au spanning VLAN
{: #relnotes_v11-vlan-spanning}

Si vous utilisez un compte SoftLayer® classique (non VRF), le spanning VLAN doit être activé. S'il ne l'est pas pour les comptes classiques, les divers composants de l'environnement de virtualisation VMware risquent de ne pas pouvoir communiquer entre eux. Pour activer le spanning VLAN dans votre compte SoftLayer, voir [Activation ou désactivation du spanning VLAN](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}.

## Paramètres de courrier électronique et notifications
{: #relnotes_v11-email}

Vous pouvez configurer des notifications par courrier électronique sur la page **Paramètres**. Ce paramètre est activé par défaut, ce qui signifie que vous recevez une notification par courrier électronique pour chaque nouvelle commande d'instance, lorsque l'instance est mise à disposition et prête pour utilisation. Vous pouvez également désactiver les notifications par courrier électronique sur la page **Paramètres**. Pour plus d'informations, voir [Paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).

## Informations de statut détaillées
{: #relnotes_v11-status-info}

Des informations de statut détaillées sont maintenant disponibles pour les instances Cloud Foundation. Lorsque vous cliquez sur le nom d'une instance, les informations relatives à son statut qui s'affichent désormais donnent plus de détails concernant la progression du déploiement. Si une erreur se produit, des messages s'affichent afin de vous aider à résoudre le problème.
