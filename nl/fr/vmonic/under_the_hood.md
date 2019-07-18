---

copyright:

  years:  2019

lastupdated: "2019-06-28"

keywords: about vmware solutions, product overview, benefits

subcollection: vmware-solutions

---
{:external: target="_blank" .external}

# IBM Cloud for VMware Solutions : Jetons un coup d'oeil sous le capot
{: #under_the_hood}

## Déploiement et gestion d'environnements virtualisés VMware
{: #under_the_hood-deploy}

Procédons  un examen approfondi de l'architecture d'{{site.data.keyword.vmwaresolutions_full}}, qui est une offre {{site.data.keyword.cloud_notm}} permettant de déployer et gérer des environnements virtualisés VMware. Dans ce tutoriel, vous allez découvrir les différents composants de l'offre et la façon dont ils s'articulent pour mettre à disposition et gérer l'environnement dans le cloud public. 

## Deux sociétés, une solution rationalisée
{: #under_the_hood-two-companies}

Depuis un certain temps déjà, les utilisateurs déploient des environnements virtualisés VMware sur IBM Public Cloud, par eux-mêmes ou en faisant appel à des services professionnels. En février 2016, [IBM et VMware ont annoncé un partenariat](https://www-03.ibm.com/press/us/en/pressrelease/49154.wss){:external} destiné à automatiser le processus de déploiement des logiciels VMware et des environnements VMware dans {{site.data.keyword.cloud_notm}}. Dans un premier temps, ce partenariat a permis de commander différents déploiements et licences de produit VMware à partir de la console {{site.data.keyword.vmwaresolutions_short}}, puis il a mis à disposition l'offre [VMware Horizon Air](https://www-03.ibm.com/press/us/en/pressrelease/49932.wss){:external} dans {{site.data.keyword.cloud_notm}}. En outre, IBM et VMware ont collaboré afin de produire conjointement une [architecture de référence standard et une prescription de déploiement pour VMware](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture){:external} dans IBM Public Cloud.

A l'automne 2016, IBM et VMware ont publié conjointement {{site.data.keyword.vmwaresolutions_short}}. Cet ensemble d'offres est basé sur les technologies de virtualisation de VMware, notamment le calcul virtualisé (VMware vSphere), la mise en réseau (VMware NSX) et le cas échéant, le stockage virtualisé (VMware vSAN). Ces environnements sont opportunément appelés centres de données définis par les logiciels. 

{{site.data.keyword.vmwaresolutions_short}} s'appuie sur la technologie VMware pour rationaliser de façon significative le déploiement et la gestion de ces centres de données définis par les logiciels dans IBM Public Cloud. Grâce à {{site.data.keyword.vmwaresolutions_short}}, il est désormais possible de déployer automatiquement des portions de l'architecture de référence standard sur {{site.data.keyword.cloud_notm}} et non plus manuellement. Les environnements dont le déploiement et la configuration duraient deux semaines peuvent désormais être mis à disposition en quelques heures. 

Cette souplesse de déploiement vous permet de vous concentrer sur l'implémentation de solutions par dessus VMware et non sur la génération de votre environnement. Avec des environnements rapidement utilisables, vous pouvez construire non seulement des solutions de cloud hybrides sur votre cloud privé et IBM Public Cloud, mais également des solutions natives pour le cloud dans IBM Public Cloud. En combinant plusieurs déploiements, vous pouvez facilement ajouter des fonctions de reprise après incident ou de haute disponibilité à vos solutions. 

A présent, jetons un coup d'oeil sous le capot de l'architecture {{site.data.keyword.vmwaresolutions_short}}. Cela vous permettra de comprendre les différents composants qui constituent la solution, ainsi que la façon dont ils s'articulent pour mettre à disposition et gérer votre centre de données défini par les logiciels dans {{site.data.keyword.cloud_notm}}. Vous découvrirez également la topologie de réseau et plusieurs méthodes vous permettant d'établir une connexion à votre environnement. 

## Fondements d'IBM Cloud for VMware Solutions

Vos centres de données définis par les logiciels sont mis à disposition et gérés à l'aide de la [console {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}. Vous vous connectez à la console à l'aide de votre compte IBMid. 

A partir du catalogue VMware Solutions, vous pouvez mettre à disposition l'un des nombreux types d'environnement de virtualisation. La solution de virtualisation présentée est *VMware vCenter Server on {{site.data.keyword.cloud_notm}}*, qui offre l'hyperviseur vSphere de VMware, VMware vCenter Server, VMware NSX et, le cas échéant, VMware vSAN. Vous pouvez également mettre à disposition cet environnement avec davantage de modules complémentaires qui fournissent des services de sauvegarde, de reprise après incident, de migration, de conformité et de mise en réseau. 

Avant de commander une instance vCenter Server, vous devez configurer votre clé d'API d'infrastructure {{site.data.keyword.cloud_notm}} dans le catalogue VMware Solutions. Pour cela, cliquez sur le lien [Paramètres](https://cloud.ibm.com/infrastructure/vmware-solutions/console/settings){:external} dans le menu de gauche de la console, puis tapez votre nom d'utilisateur et votre clé d'API lorsque vous êtes invité à saisir des données d'identification d'infrastructure {{site.data.keyword.cloud_notm}}. Le système vérifie que votre clé d'API et votre compte disposent des droits et paramètres appropriés pour déployer votre instance. 

Lorsque vous commandez votre instance vCenter Server, vous commencez par choisir son nom et la version de VMware vSphere. Toutes les instances VMware sont déployées avec des contrôleurs de domaine Microsoft Active Directory, et pour la connexion unique, vous devez désigner votre instance comme site principal ou secondaire. Une instance principale est la première ou la seule instance dans votre domaine de connexion unique. Vous pouvez déployer d'autres instances secondaires et les associer au même domaine de connexion unique qu'une instance principale existante. Ensuite, vous choisissez d'utiliser vos propres licences VMware ou vous choisissez l'édition de licence que vous souhaitez louer à partir d'{{site.data.keyword.cloud_notm}}. Enfin, vous choisissez la région et le centre de données {{site.data.keyword.cloud_notm}} pour votre instance, ainsi que les caractéristiques d'unité centrale et de mémoire pour les hôtes de votre cluster. 

Dans la partie suivante de la page de commande, vous entrez les caractéristiques de stockage et de mise en réseau de votre instance. Vous avez le choix entre le stockage vSAN et le stockage NFS pour votre cluster, avec la possibilité de choisir la taille et le nombre de disques vSAN Flash et l'édition de licence vSAN ou la taille, le nombre et les performances de volumes de stockage NFS. Pour la mise en réseau, vous choisissez le préfixe de nom d'hôte pour vos hôtes, et le sous-domaine et le domaine pour le cluster. Vous avez la possibilité de déployer les contrôleurs Active Directory sous la forme d'une instance de serveur virtuel {{site.data.keyword.cloud_notm}} ou de deux machines virtuelles dans votre cluster pour lesquelles vous devez fournir des licences et une activation. 

Au bas de la page de commande de vCenter Server, vous pouvez effectuer une sélection parmi différents services complémentaires que vous pouvez déployer pour votre instance VMware et qui sont facturés sur votre compte {{site.data.keyword.cloud_notm}}. Certains services requièrent des tâches de configuration supplémentaires que vous spécifiez dans le formulaire de commande. 

Le formulaire de commande calcule et affiche une estimation de prix basée sur vos sélections. Vous avez la possibilité d'examiner cette estimation, ainsi que différentes dispositions avant de passer votre commande. 

### Options de déploiement
{: #under_the_hood-deploy-options}

Le formulaire de commande de vCenter Server contient différentes options d'unité centrale, de mémoire et de stockage pour votre instance. De nouvelles options sont régulièrement mises à disposition, par conséquent, consultez dans le catalogue {{site.data.keyword.cloud_notm}} les dernières informations en matière de disponibilité. 

{{site.data.keyword.cloud_notm}} déploie votre instance vCenter Server à l'aide de trois VLAN, un public et deux privés. Le VLAN public est connecté à des interfaces double 10 GbE, il vous est en grande partie réservé et vous pouvez l'utiliser à votre gré à des fins de connectivité publique ou de tunnellisation pour vos propres déploiements de charge de travail. Toutefois, lors du déploiement, une paire de passerelles NSX Edge Services Gateway est déployée sur le VLAN public pour permettre à des services complémentaires de se connecter au réseau public à des fins d'octroi de licence et de facturation. Les VLAN privés sont connectés à des interfaces double 10 GbE distinctes : le premier VLAN privé est utilisé pour les communications de gestion et NSX VTEP, et le second est utilisé pour vMotion et pour le trafic de stockage NFS. 

Des instances VMware peuvent être mises à disposition dans 35 {{site.data.keyword.CloudDataCents_notm}} différents. De temps en temps, {{site.data.keyword.cloud_notm}} met à disposition de nouveaux centres de données. Recherchez dans le catalogue {{site.data.keyword.cloud_notm}} la liste la plus récente répertoriant les emplacements disponibles. 

### Déploiement d'instance
{: #under_the_hood-inst-deploy}

Lorsque vous commandez une nouvelle instance VMware vCenter, vous choisissez l'emplacement et la spécification de cette instance. {{site.data.keyword.vmwaresolutions_short}} utilise ensuite le nom d'utilisateur et la clé d'API {{site.data.keyword.cloud_notm}} que vous avez précédemment sélectionnés pour orchestrer l'ensemble du processus de commande, d'installation et de configuration de votre environnement de virtualisation. Cela comprend :

1. La commande de VLAN et de sous-réseaux pour la mise en réseau. 
2. La commande d'{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} avec vSphere Hypervisor installé.
3. Le déploiement et la configuration de VMware vCenter Server avec Platform Services Controller intégré, VMware NSX Manager, des contrôleurs et des passerelles Edge Services Gateway. 
4. La commande et la configuration de votre stockage de cluster, y compris VMware vSAN ou le stockage {{site.data.keyword.cloud_notm}} Endurance. 
5. Le déploiement d'un composant de gestion IBM appelé IBM CloudDriver.
6. Le déploiement et la configuration des services complémentaires que vous avez sélectionnés pour votre instance. 
7. La validation de l'installation et de la configuration de l'environnement. 

Vous sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} où vous souhaitez mettre à disposition votre instance. Si le matériel est disponible dans l'{{site.data.keyword.CloudDataCent_notm}} que vous avez sélectionné, le processus de mise à disposition d'instance dure généralement moins de 24 heures. 

Une fois votre instance mise à disposition, si vous êtes connecté à votre compte {{site.data.keyword.cloud_notm}} via un VPN, vous pouvez vous connecter à votre serveur vCenter directement depuis votre navigateur Web de poste de travail. 

Les composants de votre instance sont généralement accessibles par leur nom d'hôte au lieu de leur adresse IP. Pour pouvoir vous connecter à et vous authentifier auprès de vCenter, assurez-vous que le nom d'hôte vCenter et PSC (Platform Services Controller) peut être résolu par votre poste de travail en l'ajoutant au fichier hosts de votre poste de travail, comme indiqué dans la liste 1. Le nom d'hôte et l'adresse IP figurent dans la console {{site.data.keyword.vmwaresolutions_short}}, sur l'onglet **Récapitulatif** de votre instance. Vous souhaiterez peut-être ajouter également les noms d'hôte et les adresses IP de vos hôtes vSphere à votre fichier hosts. 

*Liste 1. Fichiers hosts*

<pre># Dallas site vCenter and Platform Services Controller (PSC)
10.208.85.196  vcenter-dallas.dallas.example.com
# Dallas site hosts
10.208.85.171  host0.dallas.example.com
10.208.85.153  host1.dallas.example.com
10.208.85.137  host2.dallas.example.com</pre>

Une fois votre instance déployée, vous pouvez la gérer à partir de la console. Les fonctions de gestion incluent la possibilité d'effectuer chacune des actions suivantes :

* Déployer et retirer des nodes de votre cluster
* Déployer et retirer des clusters supplémentaires dans le même centre de données et le même pod ou dans d'autres centres de données et d'autres pods
* Déployer et retirer des services complémentaires pour votre instance
* Mettre à niveau certaines éditions de licence pour votre instance

La console {{site.data.keyword.vmwaresolutions_short}} fournit une vue détaillée de chacune de vos instances vCenter Server. Pour chaque instance, l'onglet **Récapitulatif** inclut un lien vers la console vCenter et d'autres détails sur l'instance et les composants de gestion. L'onglet **Infrastructure** affiche les détails sur les clusters, les hôtes, le stockage et la mise en réseau de l'instance et vous permet d'ajouter ou retirer des clusters, des hôtes et du stockage. Sur l'onglet **Mise à jour et module de correction**, vous pouvez mettre à niveau certaines éditions de licence. Sur l'onglet **Services**, vous pouvez visualiser et gérer les services complémentaires qui sont déployés pour votre instance. L'onglet **Historique de déploiement** affiche un historique de toutes les actions qui sont effectuées sur votre instance. 

## Composants d'IBM Cloud for VMware Solutions
{: #under_the_hood-comp}

Un certain nombre de différents composants s'articulent pour mettre à disposition et gérer votre environnement. La plupart de ces composants est déployée dans votre compte {{site.data.keyword.cloud_notm}}. Dans la mesure où la solution dépend de l'articulation de tous ces composants, vous ne devez modifier ou annuler aucun d'eux sur votre compte {{site.data.keyword.cloud_notm}}. La méthode appropriée pour retirer une instance en cours d'exécution consiste à utiliser la console et non à annuler les composants individuels. 

Bien qu'il s'agisse d'un environnement de virtualisation intégré, le coût lié aux différents composants de virtualisation (par exemple, les licences VMware), composants d'infrastructure (serveurs bare metal, VLAN, sous-réseaux et stockage) et composants de gestion est précisé de manière détaillée dans la facture que vous recevez de la part d'{{site.data.keyword.cloud_notm}}.

### Console IBM Cloud for VMware Solutions
{: #under_the_hood-console}

Vous vous connectez à la [console {{site.data.keyword.vmwaresolutions_short}} ](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external} pour créer et gérer vos instances. Cette partie de la solution est chargée du processus de commande et de mise à disposition initial de votre environnement, et aussi de la gestion en continu de votre environnement. Vos instances déployées communiquent avec la console à l'aide du réseau privé {{site.data.keyword.cloud_notm}}. 

### Composant IBM CloudBuilder
{: #under_the_hood-ibm-cb}

Lorsque vous mettez à disposition une nouvelle instance, la console déploie une instance de serveur virtuel sur votre compte {{site.data.keyword.cloud_notm}}. Ce serveur virtuel est également appelé IBM CloudBuilder. Il effectue l'installation et la configuration de tous les composants de l'instance, ainsi que la validation de l'environnement. Une fois la mise à disposition terminée, CloudBuilder est supprimé. 

### Composant IBM CloudDriver
{: #under_the_hood-ibm-cd}

Un peu comme IBM CloudBuilder, IBM CloudDriver est une instance de serveur virtuel temporaire déployée dans votre compte {{site.data.keyword.cloud_notm}} pour effectuer des opérations sur votre instance. Il est déployé si besoin pour configurer ou retirer des hôtes, des clusters, du stockage ou des services dans votre instance.

### Composants VMware
{: #under_the_hood-vmware-comp}

Pour toutes les instances, vSphere Hypervisor est installé sur les serveurs bare metal. {{site.data.keyword.cloud_notm}} déploie ensuite un dispositif vCenter Server Appliance avec Platform Services Controller (PSC) intégré, un gestionnaire NSX Manager, trois contrôleurs NSX et deux paires de passerelles NSX Edge Services Gateway dans le cluster de gestion VMware. 

### Composants supplémentaires
{: #under_the_hood-add-comp}

En fonction de votre sélection, une instance de serveur virtuel Microsoft Windows ou deux machines virtuelles Microsoft Windows sont déployées en parallèle de votre cluster ou dans votre cluster en tant que serveurs Active Directory pour les composants de gestion. Vous pouvez ajouter vos propres serveurs Active Directory en tant que sources d'identité supplémentaires à des fins d'accès pour gestion. 

Quelle que soit la méthode que vous avez choisie afin d'assurer la continuité des opérations pour vos charges de travail, {{site.data.keyword.cloud_notm}} vous recommande fortement de sauvegarder les composants de gestion de votre instance. La console {{site.data.keyword.vmwaresolutions_short}} vous permet de déployer un serveur de sauvegarde IBM Spectrum Protect Plus intégré ou un serveur de sauvegarde Veeam Backup & Replication en même temps que votre instance. Ces services de sauvegarde peuvent être utilisés dans le cadre d'une [solution de sauvegarde complète](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup) pour votre instance.

### Licences
{: #under_the_hood-licenses}

{{site.data.keyword.cloud_notm}} fournit un certain nombre de licences VMware (par exemple, vCenter Server et NSX), qui sont installées dans votre instance et facturées sur votre compte {{site.data.keyword.cloud_notm}}. 

## Architecture de réseau IBM Cloud for VMware Solutions
{: #under_the_hood-network}

Votre instance vCenter Server se connecte à un VLAN public et vous pouvez l'utiliser avec vos charges de travail déployées. Le VLAN public vous est en grande partie réservé et vous pouvez l'utiliser à votre gré, toutefois, lors du déploiement, une paire de passerelles NSX Edge Services Gateway est connectée au VLAN public pour permettre à certains services complémentaires de communiquer avec l'extérieur à des fins d'octroi de licence et de facturation. Il est possible de déployer une instance sans utiliser le réseau public, dans ce cas, les services complémentaires ne sont pas tous pris en charge et vous pouvez être amené à fournir un proxy Web pour activer l'utilisation des services complémentaires non pris en charge. 

Votre instance vCenter Server est dotée de deux VLAN privés qui sont joints sur l'interface de réseau privé pour vos hyperviseurs. Le premier VLAN privé est utilisé pour la connectivité de gestion (par exemple, les communications vCenter avec des hyperviseurs) et par NSX pour la tunnellisation de tout le trafic VXLAN pour vos charges de travail déployées. Le second VLAN privé est utilisé pour vMotion et pour le trafic de stockage. Le trafic de stockage peut correspondre aux protocoles NFS ou vSAN. 

{{site.data.keyword.cloud_notm}} fournit certains services complémentaires sur ces VLAN privés. Vos serveurs Active Directory communiquent avec des serveurs DNS {{site.data.keyword.cloud_notm}} via le VLAN de gestion privé. Vos systèmes hôte et vos autres composants communiquent avec des serveurs NTP {{site.data.keyword.cloud_notm}} via le VLAN de gestion privé. Les composants IBM CloudBuilder et CloudDriver communiquent avec la console {{site.data.keyword.vmwaresolutions_short}} via ce VLAN également. Vos systèmes hôte se connectent au stockage {{site.data.keyword.cloud_notm}} Endurance via le VLAN de stockage privé.

### Connexion à votre instance
{: #under_the_hood-connect-inst}

Vous disposez d'un certain nombre de possibilités pour vous connecter à vos instances. Vous pouvez vous connecter directement à des adresses IP privées dans votre instance (par exemple, vCenter) en utilisant le [VPN {{site.data.keyword.cloud_notm}}](https://www.softlayer.com/VPN-Access){:external}. Vous pouvez également commander des [dispositifs réseau {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/network-appliances){:external} et des [pare-feu virtuels ou matériels {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/network-security), tels que FortiGate et vSRX pour votre compte. {{site.data.keyword.cloud_notm}} offre également des [liens directs](https://www.ibm.com/cloud/direct-link){:external} entre votre réseau et les VLAN dans votre compte {{site.data.keyword.cloud_notm}}. 

Pour accéder à vos machines virtuelles déployées, vous pouvez appliquer des adresses IP publiques directement à vos machines virtuelles. Toutefois, vous pouvez aussi utiliser les fonctions de dispositif réseau et de pare-feu d'{{site.data.keyword.cloud_notm}} pour configurer un accès public plus sécurisé à vos machines virtuelles à l'aide de la conversion d'adresses réseau et de pare-feu. Vous pouvez également déployer des serveurs NSX Edge et utiliser ces serveurs afin de configurer la connectivité VPN ou NAT pour vos machines virtuelles. 

## Conclusion
{: #under_the_hood-conclusion}

Ce tutoriel vous a présenté les fonctions de base d'{{site.data.keyword.vmwaresolutions_short}} pour le déploiement et la gestion d'environnements de virtualisation VMware standardisés dans le cloud public. Etant donné que la mise à disposition de ces environnements est plus rapide que jamais, vous pouvez vous concentrer vos efforts sur le déploiement de vos applications et solutions sur ces environnements et sur l'établissement de connexion entre des clouds pour assurer la reprise après incident et la haute disponibilité. 

Nous avons examiné les différents composants déployés dans votre compte {{site.data.keyword.cloud_notm}}, qui apparaissent sur votre relevé de facturation {{site.data.keyword.cloud_notm}} et s'articulent pour assurer le bon fonctionnement de votre environnement. Enfin, nous avons pris en compte l'architecture de réseau de la solution et certaines options pour établir une connectivité à l'environnement, soit en utilisant différentes options de connectivité sécurisées de sorte que vos communications conservent leur caractère privé, soit en utilisant différentes options pour la connectivité Internet publique. 

A présent que vous avec tout ce qu'il vous faut pour commencer, lancez-vous et déployez dès aujourd'hui votre prochain environnement de virtualisation VMware sur {{site.data.keyword.cloud_notm}}. 

## Liens connexes
{: #under_the_hood-related}

* [Initiation](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [Architecture VMware Solutions](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)
