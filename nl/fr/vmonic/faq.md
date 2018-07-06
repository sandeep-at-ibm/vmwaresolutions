---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# Foire aux questions sur IBM Cloud for VMware Solutions

Trouvez les réponses aux questions fréquemment posées concernant {{site.data.keyword.vmwaresolutions_full}}.

## De quels comptes utilisateur ai-je besoin pour IBM Cloud for VMware Solutions ?

* **Compte IBMid**. Ce compte est nécessaire pour accéder à la console {{site.data.keyword.vmwaresolutions_short}}. La console est une interface utilisateur autonome distincte du portail {{site.data.keyword.slportal_full}}. Pour plus d'informations, voir [Initiation](../index.html).
* **Compte {{site.data.keyword.cloud_notm}}**. Ce compte est nécessaire pour la mise à disposition. Vous pouvez vous inscrire pour obtenir un compte {{site.data.keyword.cloud_notm}} en effectuant une mise à niveau de votre **compte IBMid** vers un compte de paiement à la carte. Le compte {{site.data.keyword.cloud_notm}} que vous utilisez doit répondre à certaines exigences. Pour plus d'informations, voir [Inscription pour un compte {{site.data.keyword.cloud_notm}}](signing_softlayer_account.html) et [Exigences liées au compte {{site.data.keyword.cloud_notm}}](slaccountrequirement.html).

## Comment associer mes données d'identification d'infrastructure IBM Cloud à la console IBM Cloud for VMware Solutions ?

A la première commande de votre instance, suivez les instructions de la page des données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} afin de localiser et de copier la clé d'API et le nom d'utilisateur {{site.data.keyword.cloud_notm}} qui figurent sur le portail {{site.data.keyword.slportal}}. Les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sont stockées sur la console {{site.data.keyword.vmwaresolutions_short}} une fois la première commande passée. Les commandes ultérieures utilisent automatiquement les données d'identification stockées.

## Comment sont facturées mes consommations de plateforme virtuelle VMware ?

Tous les coûts d'infrastructure physique et virtuelle ainsi que des licences issues de l'instance sont facturés sur votre compte {{site.data.keyword.cloud_notm}}. Lorsque vous commandez une instance, vous devez disposer d'un compte {{site.data.keyword.cloud_notm}} et fournir la clé {{site.data.keyword.slapi_short}} associée au compte.

## Quelles sont les différences entre une instance vCenter Server, une instance Cloud Foundation et un cluster VMware vSphere ?

Tous les types d'instance fournissent différentes options de déploiement pour les environnements virtuels VMware. Toutefois, la différence entre ces types réside dans l'étendue des possibilités de personnalisation et d'automatisation.

* Lorsque vous commandez une instance VMware vCenter Server, vous déployez un environnement virtuel VMware avec des ressources de calcul, de stockage et de réseau personnalisées. Pour plus d'informations sur les composants déployés, voir la section _Spécifications techniques de vCenter Server_ dans la rubrique [Présentation de vCenter Server](../vcenter/vc_vcenterserveroverview.html).
* Lorsque vous commandez une instance VMware Cloud Foundation, vous déployez une plateforme unifiée de centre de données défini par les logiciels (SDDC, Software-Defined Data Center). Pour plus d'informations sur les composants déployés, voir [Composants d'instance Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#cloud-foundation-instance-components).
* Lorsque vous commandez un cluster VMware vSphere, vous obtenez un maximum de souplesse pour concevoir et créer votre environnement VMware hébergé tout en intégrant du matériel compatible avec VMware. Cela dit, {{site.data.keyword.cloud_notm}} n'automatise pas l'installation, la configuration et l'apport des composants VMware facultatifs pour le cluster VMware vSphere.
* Les fonctions qui sont prises en charge poru les instances vCenter Server, les instances Cloud Foundation et les clusters vSphere sont différentes. Pour plus d'informations, voir [Graphique de comparaison des offres](inst_comp_chart.html).

## Qu'inclut une instance vCenter Server ?

Pour plus d'informations, voir la section _Spécifications techniques de vCenter Server_ dans la rubrique [Présentation de vCenter Server](../vcenter/vc_vcenterserveroverview.html).

## Qu'inclut une instance Cloud Foundation ?

Pour plus d'informations, voir [Composants d'instance Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

## Qu'inclut un cluster vSphere ?
Pour plus d'informations, voir [Composants de VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html).

## Une instance vCenter Server à deux noeuds est-elle à haute disponibilité ?

Il est vivement recommandé de déployer les charges de travail de production dans des environnements dotés d'au moins trois noeuds.

Bien que le planificateur de ressources distribuées (DRS, Distributed Resource Scheduler) VMware vSphere et la haute disponibilité VMware soient activés par défaut, les meilleures pratiques VMware suggèrent de placer chacun des trois contrôleurs NSX sur un noeud distinct.

Dans le déploiement minimum à deux noeuds, l'un des noeuds reçoit un contrôleur NSX et le second, deux contrôleurs NSX. Si le noeud où se trouvent les deux contrôleurs NSX vient à s'arrêter, les opérations du contrôleur NSX sont placées dans un noeud en mode lecture seule et les nouvelles machines virtuelles ou machines virtuelles vMotion risquent d'être confrontées à des problèmes de réseau.

Lorsqu'un troisième noeud est ajouté à un cluster à deux noeuds, vCenter Server rééquilibre automatiquement les trois contrôleurs NSX entre les trois noeuds et crée un environnement à haute disponibilité.

## Puis-je définir une configuration VMware vCenter 6.5 à haute disponibilité ?

Non, ce n'est pas recommandé. Vous risquez des incidents au niveau des fonctions {{site.data.keyword.vmwaresolutions_short}}.

## Les clusters peuvent-ils être renommés ?

Pour les instances vCenter Server, le premier cluster créé lors du déploiement est, par défaut, nommé **cluster1**. Vous pouvez le renommer dans le client VMware vSphere. Lorsque vous ajoutez un cluster à une instance vCenter Server, vous pouvez indiquer le nom qui vous convient sur la console {{site.data.keyword.vmwaresolutions_short}}.

**Remarque**:  pour les instances Cloud Foundation, le nom du cluster par défaut n'est pas modifiable.

##Comment sont gérés les correctifs ?

IBM fournit des mises à jour permanentes du composant IBM CloudDriver, qui sont mises à disposition via {{site.data.keyword.cloud_notm}} pour la console VMware Solutions. IBM ne fournit pas de mises à jour permanentes pour les services complémentaires tels que Zerto on {{site.data.keyword.cloud_notm}} ou Veeam on {{site.data.keyword.cloud_notm}}. L'obtention et l'installation de ces mises à jour est de votre responsabilité.

Les mises à jour de VMware sont appliquées différemment selon le type d'instance VMware que vous avez déployée :

* Pour les instances VMware Cloud Foundation, les mises à jour des composants vSphere ESXi, NSX, vCenter, contrôleur PSC (Platform Services Controller) et gestionnaire SDDC sont fournies via la console {{site.data.keyword.vmwaresolutions_short}}.
* Pour les instances VMware vCenter Server :
  * Pour les instances déployées en ou mise à niveau vers la version 2.1 ou ultérieure, les nouveaux clusters et serveurs ESXi déployés reçoivent de VMware des mises à jour ESXi récentes, mais pas nécessairement les toutes dernières.
  * Vous êtes responsable de toutes les autres mises à jour des composants VMware, y compris de vous assurer que les nouveaux clusters et serveurs ESXi déployés disposent de toutes les mises à jour les plus récentes dont vous avez besoin.
  * Pour les instances déployées en version 2.0 ou ultérieure, le gestionnaire de mises à jour VMware (VUM, VMware Update Manager) est intégré à votre serveur vCenter Server. Vous pouvez configurer VUM de manière à télécharger les mises à jour ESXi depuis VMware.

Pour plus d'informations, voir :
* [Support VMware](https://www.vmware.com/support.html)
* [Application de mises à jour à des instances vCenter Server](../vcenter/vc_applyingupdates.html)
* [Application de mises à jour à des instances Cloud Foundation](../sddc/sd_applyingupdates.html)

## La passerelle NSX Edge des services de gestion présente-t-elle un risque pour la sécurité ?

Bien que la passerelle VMware NSX Edge des services de gestion se trouve sur un sous-réseau public, des mesures de sécurité ont été prises afin de garantir qu'elle ne présente aucun risque pour la sécurité. Ces mesures sont les suivantes :
*  Le pare-feu NSX Edge est configuré de manière à n'autoriser que le trafic HTTPS sortant (port TCP 443) initié par les machines virtuelles de gestion.
*  Le conversion d'adresses réseau (SNAT) est utilisée de sorte que les adresses IP privées ne soient pas visibles à l'extérieur du réseau privé.
*  L'accès distant pour le dispositif NSX Edge des services de gestion est désactivé.
*  Les mots de passe d'accès à la passerelle NSX Edge des services de gestion depuis le réseau privé sont rendus aléatoires et chiffrés.

## La passerelle NSX Edge présente-t-elle un risque pour la sécurité ?

Bien que la passerelle NSX Edge gérée par le client soit connectée au VLAN public, des mesures de sécurité ont été prises afin de garantir qu'elle ne présente aucun risque pour la sécurité. Ces mesures sont les suivantes :
*  Une règle de pare-feu est en vigueur afin de n'autoriser que le trafic sortant issu de la plage d'adresses IP du sous-réseau privé.
*  Une règle SNAT (désactivée par défaut) est en vigueur afin de convertir toutes les adresses IP issues du sous-réseau privé en une unique adresse IP sur le sous-réseau public.
*  L'accès distant pour le dispositif NSX Edge géré par le client est désactivé.
*  Les mots de passe d'accès à la passerelle NSX Edge gérée par le client depuis le réseau privé sont rendus aléatoires et chiffrés.

## Comment choisir les centres de données pour mes instances ?

Les déploiements d'instance sont soumis à des exigences strictes en matière d'infrastructure physique, qui varient en fonction des {{site.data.keyword.CloudDataCents_notm}}. Lorsque vous commandez votre instance, les centres de données disponibles sont répertoriés dans des régions et vous pouvez en sélectionner un dans la liste.

Pour plus d'informations, voir les sections _Disponibilité d'IBM Cloud Data Center_ dans :
* [Exigences et planification pour les instances vCenter Server](../vcenter/vc_planning.html)
* [Exigences et planification pour les instances vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_planning.html)
* [Exigences et planification pour les instances Cloud Foundation](../sddc/sd_planning.html)
* [Exigences et planification pour VMware vSphere on IBM Cloud](../vsphere/vs_planning.html)
* [Exigences et planification pour les instances NetApp ONTAP Select](../netapp/np_planning.html)
* [Exigences et planification pour les instances VMware Federal](../vcenter/vc_fed_planning.html)

## Combien de temps faut-il pour déployer mon instance ?

Vous pouvez vérifier le statut du déploiement de l'instance en affichant l'historique de déploiement sur la page des détails de l'instance depuis la console {{site.data.keyword.vmwaresolutions_short}}.

## Est-ce que VMware vSphere on IBM Cloud utilise l'automatisation pour installer, configurer et apporter la pile VMware ?

Non. VMware vSphere on {{site.data.keyword.cloud_notm}} n'utilise pas l'automatisation avancée des plateformes Cloud Foundation et vCenter Server. Selon les éléments commandés, la plateforme distribue des licences VMware facultatives, des serveurs ESXi et, en option, une paire à haute disponibilité de pare-feu physiques FortiGate. Si un nouveau cluster est créé, trois nouveaux VLAN sont également mis à disposition : un public et deux privés.

VMware ESXi est automatiquement installé sur chaque serveur bare metal, mais c'est à vous d'installer les composants VMware supplémentaires, tels que vCenter Server ou NSX. Etant donné que vSphere on {{site.data.keyword.cloud_notm}} garantit que le matériel compatible VMware est commandé sur les composants VMware sélectionnés, aucune automatisation n'est mise en oeuvre pour configurer et installer l'environnement VMware. Vous êtes responsable de la conception et de l'architecture de l'environnement hébergé IBM.

## Comment afficher la liste de toutes les notifications ?

Pour afficher l'historique complet des notifications, cliquez sur **Notifications** dans le panneau de navigation de gauche.

## Que faire en cas de problème avec IBM Cloud for VMware Solutions ?

Si vous avez besoin d'aide concernant {{site.data.keyword.vmwaresolutions_short}}, contactez le support IBM via l'un des canaux de support. Pour plus d'informations, voir [Contacter le support IBM](trbl_support.html).

### Liens connexes

* [Notifications](notifications.html)
* [Instances Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Instances vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Accès à la console](loginmethod.html)
* [Paramètres et comptes utilisateur](useraccount.html)
