---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-16"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Foire aux questions sur IBM Cloud for VMware Solutions
{: #faq}

Trouvez les réponses aux questions fréquemment posées concernant {{site.data.keyword.vmwaresolutions_full}}.

## De quels comptes utilisateur ai-je besoin pour IBM Cloud for VMware Solutions ?
{: #faq-user-accts}
{: faq}

* **Compte IBMid**. Ce compte est nécessaire pour accéder à la console {{site.data.keyword.vmwaresolutions_short}}. La console est une interface utilisateur autonome distincte du portail {{site.data.keyword.slportal}}. Pour plus d'informations, voir [Initiation](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started).
* **Compte {{site.data.keyword.cloud_notm}}**. Ce compte est nécessaire pour la mise à disposition. Vous pouvez vous inscrire pour obtenir un compte {{site.data.keyword.cloud_notm}} en effectuant une utilisant un **IBMid** existant ou en créant un nouvel **IBMid**.
* **Compte d'infrastructure {{site.data.keyword.cloud_notm}}**. Ce compte est utilisé pour se connecter à portail client d'infrastructure {{site.data.keyword.cloud_notm}} qui fournit des fonctions supplémentaires pour gérer des produits et des services d'infrastructure. Vous pouvez obtenir un compte d'infrastructure {{site.data.keyword.cloud_notm}} en effectuant une mise à niveau de votre **compte {{site.data.keyword.cloud_notm}}** vers un compte de paiement à la carte ou en établissant un lien entre votre compte d'infrastructure {{site.data.keyword.cloud_notm}} et votre compte {{site.data.keyword.cloud_notm}}. Le compte d'infrastructure {{site.data.keyword.cloud_notm}} que vous utilisez doit répondre à certaines exigences. Pour plus d'informations, voir [Inscription à des comptes requis](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account) et [Exigences concernant le compte d'infrastructure {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).

## Comment associer mes données d'identification d'infrastructure IBM Cloud à la console IBM Cloud for VMware Solutions ?
{: #faq-associate-credentials}
{: faq}

A la première commande de votre instance, suivez les instructions de la page **Paramètres** dans la console afin de localiser et de copier la clé d'API et le nom d'utilisateur d'infrastructure {{site.data.keyword.cloud_notm}} qui figurent sur le portail {{site.data.keyword.slportal}}. Les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sont stockées sur la console {{site.data.keyword.vmwaresolutions_short}} une fois la première commande passée. Les commandes ultérieures utilisent automatiquement les données d'identification stockées.

## Comment sont facturées mes consommations de plateforme virtuelle VMware ?
{: #faq-billing}
{: faq}

Tous les coûts d'infrastructure physique et virtuelle, ainsi que des licences associées à l'instance, sont facturés sur votre compte {{site.data.keyword.cloud_notm}}. Lorsque vous commandez une instance, vous devez disposer d'un compte {{site.data.keyword.cloud_notm}} et fournir la clé {{site.data.keyword.slapi_short}} associée au compte.

## Quelles sont les différences entre une instance vCenter Server et un cluster VMware vSphere ?
{: #faq-vcs-cf-vss}
{: faq}

Tous les types d'instance fournissent différentes options de déploiement pour les environnements virtuels VMware. Toutefois, la différence entre ces types réside dans l'étendue des possibilités de personnalisation et d'automatisation.

* Lorsque vous commandez une instance VMware vCenter Server, vous déployez un environnement virtuel VMware avec des ressources de calcul, de stockage et de réseau personnalisées. Pour plus d'informations sur les composants déployés, voir [Spécifications techniques relatives aux instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs).
* Lorsque vous commandez un cluster VMware vSphere, vous obtenez un maximum de souplesse pour concevoir et créer votre environnement VMware hébergé tout en intégrant du matériel compatible VMware. Cela dit, {{site.data.keyword.cloud_notm}} n'automatise pas l'installation, la configuration et l'apport des composants VMware facultatifs pour le cluster VMware vSphere.
* Les fonctions qui sont prises en charge par les instances vCenter Server et les clusters vSphere sont différentes. Pour plus d'informations, voir [Graphique de comparaison des offres](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart).

## Qu'inclut une instance vCenter Server ?
{: #faq-vcs}
{: faq}

Pour plus d'informations, voir [Spécifications techniques relatives aux instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs).

## Qu'inclut un cluster vSphere ?
{: #faq-vss}
{: faq}

Pour plus d'informations, voir [Composants de VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview).

## Une instance vCenter Server à deux noeuds est-elle à haute disponibilité ?
{: #is-a-two-node-vcenter-server-instance-highly-available}
{: faq}

Il est recommandé de déployer les charges de travail de production dans des environnements dotés d'au moins trois noeuds.

VMware vSphere DRS (Distributed Resource Scheduler) et VMware HA (High Availability) sont activés par défaut. Les pratiques VMware recommandées suggèrent toutefois de placer chacun des trois contrôleurs NSX sur un noeud distinct.

Dans le déploiement minimum à deux noeuds, l'un des noeuds reçoit un contrôleur NSX et le second, deux contrôleurs NSX. Si le noeud où se trouvent les deux contrôleurs NSX vient à s'arrêter, les opérations du contrôleur NSX sont placées dans un noeud en mode lecture seule et les nouvelles machines virtuelles ou machines virtuelles vMotion risquent d'être confrontées à des problèmes de réseau.

Lorsqu'un troisième noeud est ajouté à un cluster à deux noeuds, vCenter Server rééquilibre automatiquement les trois contrôleurs NSX entre les trois noeuds et crée un environnement à haute disponibilité.

## Puis-je définir une configuration VMware vCenter 6.5 à haute disponibilité ?
{: #faq-ha}
{: faq}

Non, ce n'est pas recommandé. Vous risquez des incidents au niveau des fonctions {{site.data.keyword.vmwaresolutions_short}}.

## Les clusters peuvent-ils être renommés ?
{: #faq-rename-cluster}
{: faq}

Pour une nouvelle instance vCenter Server, le premier cluster créé lors du déploiement est, par défaut, nommé **cluster1**. Vous pouvez le renommer dans le client VMware vSphere. Lorsque vous ajoutez un cluster à une instance vCenter Server, vous pouvez spécifier le nom de votre choix sur la console {{site.data.keyword.vmwaresolutions_short}}.

## Comment sont gérés les modules de correction ?
{: #faq-patches}
{: faq}

IBM fournit des mises à jour permanentes du code en déployant l'instance de serveur virtuel (VSI) IBM CloudDriver (VSI) à la demande. IBM ne fournit pas de mises à jour permanentes pour les services complémentaires tels que Zerto on {{site.data.keyword.cloud_notm}} ou Veeam on {{site.data.keyword.cloud_notm}}. L'obtention et l'installation de ces mises à jour est de votre responsabilité.

Pour les instances VMware vCenter Server déployées dans ou mises à niveau vers la version 2.1 ou une version ultérieure, les nouveaux clusters et serveurs ESXi déployés reçoivent de VMware des mises à jour ESXi récentes, mais pas nécessairement les toutes dernières.

Vous êtes responsable de toutes les autres mises à jour des composants VMware, y compris de vous assurer que les nouveaux clusters et serveurs ESXi déployés disposent de toutes les mises à jour les plus récentes dont vous avez besoin.
{:important}

Pour les instances déployées en version 2.0 ou ultérieure, le gestionnaire de mises à jour VMware (VUM, VMware Update Manager) est intégré à votre serveur vCenter Server. Vous pouvez configurer VUM afin de télécharger des mises à jour ESXi depuis VMware.

Pour plus d'informations, consultez les ressources suivantes :
* [Support VMware](https://www.vmware.com/support.html)
* [Application de mises à jour à des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates)
* [Application de mises à jour à des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_applyingupdates)

## La passerelle NSX Edge des services de gestion présente-t-elle un risque pour la sécurité ?
{: #faq-mgmt-nsx}
{: faq}

Bien que la passerelle VMware NSX Edge des services de gestion se trouve sur un sous-réseau public, des mesures de sécurité ont été prises afin de garantir qu'elle ne présente aucun risque pour la sécurité:
*  Le pare-feu NSX Edge est configuré de manière à n'autoriser que le trafic HTTPS sortant (port TCP 443) initié par les machines virtuelles de gestion.
*  La conversion d'adresses réseau (SNAT) est utilisée afin que les adresses IP privées ne soient pas visibles à l'extérieur du réseau privé.
*  L'accès distant pour le dispositif NSX Edge des services de gestion est désactivé.
*  Les mots de passe d'accès à la passerelle NSX Edge des services de gestion depuis le réseau privé sont rendus aléatoires et chiffrés.

## La passerelle NSX Edge présente-t-elle un risque pour la sécurité ?
{: #faq-customer-nsx}
{: faq}

Bien que la passerelle NSX Edge gérée par le client soit connectée au VLAN public, des mesures de sécurité ont été prises afin de garantir qu'elle ne présente aucun risque pour la sécurité. Les mesures de sécurité suivantes sont en place :
*  Une règle de pare-feu est en vigueur afin de n'autoriser que le trafic sortant issu de la plage d'adresses IP du sous-réseau privé.
*  Une règle SNAT (désactivée par défaut) est en place pour convertir toutes les adresses IP du sous-réseau privé en une seule adresse IP sur le sous-réseau public.
*  L'accès distant pour le dispositif NSX Edge géré par le client est désactivé.
*  Les mots de passe d'accès à la passerelle NSX Edge gérée par le client depuis le réseau privé sont rendus aléatoires et chiffrés.

## Comment choisir les centres de données pour mes instances ?
{: #faq-data-center}
{: faq}

Les déploiements d'instance sont soumis à des exigences strictes en matière d'infrastructure physique, qui varient en fonction des {{site.data.keyword.CloudDataCents_notm}}. Lorsque vous commandez votre instance, les centres de données disponibles sont répertoriés dans des régions et vous pouvez en sélectionner un dans la liste.

Pour plus d'informations, voir les sections _Disponibilité d'IBM Cloud Data Center_ dans :
* [Exigences et planification pour les instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Exigences et planification pour les instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Exigences et planification pour VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)
* [Exigences et planification pour les instances NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning)

## Combien de temps faut-il pour déployer mon instance ?
{: #faq-deploy}
{: faq}

Vous pouvez vérifier le statut du déploiement de l'instance en affichant l'historique de déploiement sur la page des détails de l'instance depuis la console {{site.data.keyword.vmwaresolutions_short}}.

## Est-ce que VMware vSphere on IBM Cloud utilise l'automatisation pour installer, configurer et apporter la pile VMware ?
{: #faq-vss-automation}
{: faq}

Non. VMware vSphere on {{site.data.keyword.cloud_notm}} n'utilise pas l'automatisation avancée de la plateforme vCenter Server. Selon les éléments commandés, la plateforme distribue des licences VMware facultatives, des serveurs ESXi et, en option, une paire à haute disponibilité de pare-feu physiques FortiGate. Si un nouveau cluster est créé, trois nouveaux VLAN sont également mis à disposition : un VLAN public et deux privés.

VMware ESXi est automatiquement installé sur chaque serveur bare metal, mais c'est à vous d'installer les composants VMware supplémentaires, tels que vCenter Server ou NSX. Bien que vSphere sur {{site.data.keyword.cloud_notm}} veille à ce que le matériel commandé soit compatible avec VMware compte tenu des composants VMware sélectionnés, aucune automatisation ne permet de configurer et d'installer l'environnement VMware. Vous êtes responsable de la conception et de l'architecture de l'environnement hébergé IBM.

## Comment afficher la liste de toutes les notifications ?
{: #faq-notification}
{: faq}

Pour afficher l'historique complet des notifications, cliquez sur **Notifications** dans le panneau de navigation de gauche.

## Que faire en cas de problème avec IBM Cloud for VMware Solutions ?
{: #faq-support}
{: faq}

Si vous avez besoin d'aide concernant {{site.data.keyword.vmwaresolutions_short}}, contactez le support IBM via l'un des canaux de support. Pour plus d'informations, voir [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).

## Liens connexes
{: #faq-related}

* [Notifications](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [Instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Accès à la console](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-loginmethod)
* [Paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
