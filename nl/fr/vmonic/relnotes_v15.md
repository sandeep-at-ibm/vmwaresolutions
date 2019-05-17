---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-30"

subcollection: vmware-solutions


---

# Notes sur l'édition pour la version 1.5
{: #relnotes_v15}

Cette édition inclut de nouvelles fonctionnalités, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Exigences relatives à un compte VRF par rapport à un compte SoftLayer classique
{: #relnotes_v15-vrf}

Pour les comptes SoftLayer® classiques, le spanning VLAN est un paramètre qui peut être activé au niveau du compte. Pour {{site.data.keyword.vmwaresolutions_short}}, le spanning VLAN doit obligatoirement être activé.

Pour les comptes SoftLayer de réacheminement et de routage virtuels (VRF, Virtual Routing and Forwarding), l'équivalent du spanning VLAN est un paramètre permanent non modifiable. Aucune configuration utilisateur n'est nécessaire pour les comptes VRF.

Avant de passer une commande d'instance, vérifiez que votre compte SoftLayer est soit un compte VRF soit un compte classique (non VRF) pour lequel le spanning VLAN est activé. Sinon, la commande risque d'échouer.

Pour confirmer que votre compte SoftLayer est un compte VRF, interrogez le support IBM Bluemix. Pour les comptes classiques, vous devez activer le spanning VLAN en suivant les instructions de la rubrique [Activation ou désactivation du spanning VLAN](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}.

## Mises à jour du modèle de frais de service
{: #relnotes_v15-svc-charge}

Pour les instances Cloud Foundation, une nouvelle licence de _gestionnaire SDDC_ a été instaurée. Elle est appliquée à chaque noeud et perçue mensuellement.

## Améliorations de la convivialité
{: #relnotes_v15-ui}

Des améliorations ont été apportées à l'interface utilisateur, à savoir :

* La disponibilité des divers {{site.data.keyword.CloudDataCents_notm}} et leur capacité à honorer la commande sont clairement indiquées sur l'interface utilisateur. Utilisez ces informations pour prendre une décision éclairée concernant l'{{site.data.keyword.CloudDataCent_notm}} à sélectionner lorsque vous commandez une instance. Pour plus d'informations, voir [Exigences et planification pour les instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).
* Pour les instances Cloud Foundation, des informations telles que le nom de l'instance, les noms de domaine et de sous-domaine et l'emplacement du centre de données sont automatiquement affichées dans un format graphique à mesure que vous entrez les informations requises dans les zones de saisie.
