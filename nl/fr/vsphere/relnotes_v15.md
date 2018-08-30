---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-30"

---

# Notes sur l'édition pour la version 1.5

Cette édition inclut de nouvelles fonctionnalités, des améliorations d'utilisation et des corrections d'erreur. Pour la liste des erreurs rectifiées dans les différentes éditions, les problèmes connus concernant le produit et des conseils supplémentaires pour l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Exigences relatives à un compte VRF par rapport à un compte SoftLayer classique

Pour les comptes SoftLayer® classiques, le spanning VLAN est un paramètre qui peut être activé au niveau du compte. Pour {{site.data.keyword.vmwaresolutions_short}}, le spanning VLAN doit obligatoirement être activé.

Pour les comptes SoftLayer de réacheminement et de routage virtuels (VRF, Virtual Routing and Forwarding), l'équivalent du spanning VLAN est un paramètre permanent non modifiable. Aucune configuration utilisateur n'est nécessaire pour les comptes VRF.

Avant de passer une commande d'instance, vérifiez que votre compte SoftLayer est soit un compte VRF soit un compte classique (non VRF) pour lequel le spanning VLAN est activé. Sinon, la commande risque d'échouer.

Pour confirmer que votre compte SoftLayer est un compte VRF, interrogez le support IBM Bluemix. Pour les comptes classiques, vous devez activer le spanning VLAN en suivant les instructions de la rubrique [Activation ou désactivation du spanning VLAN](../../../infrastructure/vlans/vlan-spanning.html){:new_window}.

## Mises à jour du modèle de frais de service

Pour les instances Cloud Foundation, une nouvelle licence de _gestionnaire SDDC_ a été instaurée. Elle est appliquée à chaque noeud et perçue mensuellement. Pour plus d'informations, voir [Spécifications techniques relatives aux instances Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).

## Améliorations de la convivialité

Des améliorations ont été apportées à l'interface utilisateur, à savoir :

* La disponibilité des divers centres de données et leur capacité à honorer la commande sont clairement indiquées sur l'interface utilisateur de sorte que vous puissiez prendre une décision éclairée concernant le centre de données à sélectionner lors de la commande de l'instance. Pour plus d'informations, voir [Exigences et planification pour les instances Cloud Foundation](../sddc/sd_planning.html) et [Exigences et planification pour les instances vCenter Server](../vcenter/vc_planning.html).
* Pour les instances Cloud Foundation, des informations telles que le nom de l'instance, les noms de domaine et de sous-domaine et l'emplacement du centre de données sont automatiquement affichées dans un format graphique tandis que vous entrez les informations requises dans les zones de saisie. Pour plus d'informations, voir [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html).
