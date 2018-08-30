---

copyright:

  years:  2016, 2018

lastupdated: "2017-01-23"

---

# Notes sur l'édition pour la version 1.3

Cette édition inclut de nouvelles fonctionnalités, des améliorations d'utilisation et des corrections d'erreur. Pour la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des conseils supplémentaires pour l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Stockage de niveau fichier partagé pour les instances vCenter Server

Vous pouvez désormais ajouter un stockage NAS (Network Attached Storage) partagé aux instances vCenter Server. L'ajout de cette fonctionnalité vous permet d'exécuter des charges de travail de production sur vCenter Server et d'éviter toute perte de données en cas d'incident sur des noeuds. Le stockage de fichiers NFS (Network File System) est fourni en option dans le processus de commande des instances vCenter Server. Pour plus d'informations, voir [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html).

## Suppression de la reprise après incident Zerto

Que vous ayez commandé la reprise après incident Zerto dans le cadre de votre instance ou l'ayez ajoutée à une instance existante, vous pouvez désormais supprimer ce service lorsque vous n'en avez plus besoin. Après que vous avez demandé le retrait du service à partir de la console, le support IBM vous guide lors de la finalisation du processus de retrait.

Pour plus d'informations, voir les rubriques suivantes :

* [Suppression de la reprise après incident](../services/removingzertodr.html)
* [Affichage d'instances Cloud Foundation](../sddc/sd_viewinginstances.html)
* [Affichage des instances vCenter Server](../vcenter/vc_viewinginstances.html)

## VMware NSX Edge pour les instances Cloud Foundation

NSX Edge est désormais inclus en tant qu'élément des nouvelles instances Cloud Foundation que vous commandez. NSX Edge offre des services de passerelle et de sécurité périphériques permettant d'isoler un réseau virtuel.

Lors du déploiement d'une instance, IBM déploie une passerelle NSX ESG (Edge Services Gateway) de gestion. Les machines virtuelles de gestion IBM utilisent cette passerelle ESG pour communiquer avec des composants de gestion IBM externes spécifiques liés à l'automatisation. La passerelle ESG est déployée de manière à inclure deux interfaces : une pour la connexion au réseau local virtuel {{site.data.keyword.cloud_notm}} privé et l'autre pour la connexion au réseau local virtuel {{site.data.keyword.cloud_notm}} public.

Pour garantir la sécurité, des règles de pare-feu sont instaurées afin d'autoriser uniquement les communications HTTPS sortantes initiées par les machines virtuelles de gestion. Cette passerelle ESG est déployée dans une Grande configuration et seul le support IBM est habilité à modifier la configuration.

Pour plus d'informations, voir les rubriques suivantes :

* [Spécifications techniques relatives aux instances Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)
* [La passerelle NSX Edge des services de gestion présente-t-elle un risque pour la sécurité ?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [Documentation VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Processus de commande d'instance

Le processus de commande d'instance a été amélioré pour les instances Cloud Foundation comme pour les instances and vCenter Server :

* La page de récapitulatif affiche toutes les dispositions et termes applicables à tous les composants et services commandés afin de vous faciliter l'accès et la révision de ces dispositions avant de passer la commande.
* Vous pouvez sauvegarder et imprimer le récapitulatif de commande de votre instance avant de passer la commande. Avec cette nouvelle fonction, vous pouvez passer en revue les paramètres et le coût de l'instance, modifier au besoin les composants commandés, obtenir une approbation, puis revenir à votre commande.

Pour plus d'informations, voir les rubriques suivantes :

* [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html)

## Gestion d'instances

De nouvelles fonctions et améliorations ont été apportées au processus de gestion des instances :

* Pour les instances Cloud Foundation et vCenter Server, vous pouvez afficher et passer en revue le coût estimé de vos serveurs ESXi avant de les ajouter à votre instance. Une fois que vous avez indiqué le nombre de serveurs que vous voulez ajouter, le coût estimé par serveur, par mois, s'affiche sur la console. Pour plus d'informations, voir [Extension et réduction de capacité pour des instances Cloud Foundation](../sddc/sd_addingremovingservers.html) et [Extension et réduction de capacité pour des instances vCenter Server](../vcenter/vc_addingremovingservers.html).
* Pour les instances Cloud Foundation et vCenter Server, le nombre total d'instances s'affiche en haut de la page de récapitulatif. De plus, vous pouvez commander une instance en un seul clic à partir des page de récapitulatif des instances. Dans la page de récapitulatif, vous pouvez également afficher le statut détaillé de la commande au cours de la mise à disposition. Lorsque vous survolez le statut affiché, vous obtenez d'autres détails concernant l'étape en cours ou l'erreur, le cas échéant.
* Pour les instances Cloud Foundation, la page des détails de l'instance affiche l'historique de déploiement de l'instance, accompagné d'informations relatives au statut du déploiement étape par étape. Pour plus d'informations, voir [Affichage d'instances Cloud Foundation](../sddc/sd_viewinginstances.html).
* Pour les instances Cloud Foundation, la convivialité du processus de mise à jour et d'application de correctif a été améliorée par l'ajout de détails concernant la mise à jour sur la page **Mise à jour et module de correction**, tels que la durée d'indisponibilité nécessaire pour appliquer le correctif, le moment planifié pour la mise à jour et une indication visuelle pour signaler qu'un correctif obligatoire doit être appliqué avant celui en cours. Pour plus d'informations, voir [Application de mises à jour et de correctifs à des instances Cloud Foundation](../sddc/sd_applyingupdates.html).

## Notification par courrier électronique

Vous recevez une notification par courrier électronique lorsqu'une nouvelle commande de déploiement d'instance a été passée et lorsqu'un service a été ajouté, déployé ou supprimé de votre instance. Les paramètres de notification sont activés par défaut. En fonction de vos préférences, vous pouvez définir sur la page **Paramètres** les notifications que vous voulez recevoir. Pour plus d'informations, voir [Paramètres et comptes utilisateur](useraccount.html).
