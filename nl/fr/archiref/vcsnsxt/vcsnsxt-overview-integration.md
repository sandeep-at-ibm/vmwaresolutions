---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-03"

subcollection: vmware-solutions


---

# Intégration, adressage IP et flux réseau
{: #vcsnsxt-overview-integration}

## Intégration d'IBM Cloud Private et VMware vCenter Server on IBM Cloud
{: #vcsnsxt-overview-integration-icp-vcs-integration}

{{site.data.keyword.cloud}} Private est installé sur plusieurs machines virtuelles sur une instance vCenter Server. Dans l'instance vCenter Server, l'instance {{site.data.keyword.icpfull_notm}} est déployée avec une passerelle ESG (NSX Edge Services Gateway) dédiée et un routeur logique distribué (DLR) et elle utilisé un réseau VXLAN.

La passerelle ESG est configurée avec une règle SNAT pour autoriser le trafic sortant, activant ainsi la connectivité pour télécharger les prérequis {{site.data.keyword.icpfull_notm}} et la connectivité à GitHub et Docker. Vous pouvez aussi utiliser un proxy Web pour la connectivité Internet. La passerelle ESG est configurée avec une connectivité privée pour accéder aux services DNS et NTP. La passerelle ESG est également configurée avec une règle NAT pour permettre l'accès aux adresses IP virtuelles proxy et maître {{site.data.keyword.icpfull_notm}} à partir du réseau {{site.data.keyword.cloud_notm}} 10.x.

## Intégration d'IBM Cloud Kubernetes Service et vCenter Server
{: #vcsnsxt-overview-integration-iks-vcs-integration}

Actuellement, les scénarios suivants permettent d'intégrer la mise en réseau {{site.data.keyword.containerlong_notm}} et vCenter Server :
- **Réseau VLAN commun** - nécessite que les noeuds worker {{site.data.keyword.containerlong_notm}} soient déployés sur le même VLAN que l'instance vCenter Server. Avec un réseau VLAN, une passerelle ESG peut être un homologue BGP vers les noeuds worker.
- **Réseau privé virtuel strongSwan** – Ce scénario utilise la solution de connectivité {{site.data.keyword.containerlong_notm}} vers l'entreprise standard. Un conteneur strongSwan fournit une passerelle VPN pour le cluster qui réachemine les paquets vers les réseaux distants le long d'un tunnel IPSec vers la passerelle éloignée. Cette passerelle éloignée est une passerelle ESG sur l'instance vCenter Server. Sur les passerelles, les routes sont configurées en envoyant toutes les plages d'adresses IP de service et de cluster vers le conteneur strongSwan et toutes les adresses vCenter Server BYOIP vers la passerelle ESG. Les adresses IP cible pour les passerelles sont l'adresse IP portable privée du service d'équilibrage de charge qui est affecté au conteneur strongSwan et l'adresse IP portable privée de la passerelle ESG.
- **Routes statiques et NAT**.
- **Appairage BGP** – L'appairage BGP n'est pas une offre fournie par défaut dans {{site.data.keyword.cloud_notm}}. Elle doit être demandée et approuvée. Une fois activé, l'appairage BGP permet aux routeurs Calico vRouter et à la passerelle ESG de faire la promotion des routes vers le routeur BCR.

## Intégration d'IBM Cloud Kubernetes Service et IBM Cloud Private
{: #vcsnsxt-overview-integration-iks-icp-integration}

L'intégration {{site.data.keyword.containerlong_notm}} et {{site.data.keyword.icpfull_notm}} utilise la connectivité VPN strongSwan avec un conteneur strongSwan dans {{site.data.keyword.containerlong_notm}} et {{site.data.keyword.icpfull_notm}}.

## Affectation d'adresse IP
{: #vcsnsxt-overview-integration-ip-address-allocation}

D'un point de vue administratif, l'architecture de référence est dotée des plages réseau conceptuelles suivantes :
-	**Réseau de pods {{site.data.keyword.containerlong_notm}}** - Tous les pods qui sont déployés sur un noeud worker se voient affecter une adresse IP privée comprise dans la plage 172.30.0.0/16 et ils sont routés uniquement entre les noeuds worker. Pour éviter des conflits, n'utilisez pas cette plage d'adresses IP sur des noeuds qui communiquent avec vos noeuds worker. Les noeuds worker et les pods peuvent communiquer de manière sécurisée sur le réseau privé en utilisant des adresses IP privées. Toutefois, lorsqu'un pod tombe en panne ou qu'un noeud worker a besoin d'être recréé, une nouvelle adresse IP privée lui est affectée.
-	Réseau de service {{site.data.keyword.containerlong_notm}}** – **{{site.data.keyword.containerlong_notm}} utilise 172.21.0.0/16 pour les adresses de service au sein du cluster. Il existe deux autres plages d'adresses IP :
    - Public – Sous-réseau portable public avec une plage d'adresses IP fournie par {{site.data.keyword.cloud_notm}}. Cette plage d'adresses IP est utilisée pour exposer des applications sur internet via les services ALB ou Ingress.
    - Privé – Sous-réseau portable privé avec une plage d'adresses IP fournie par {{site.data.keyword.cloud_notm}}. Cette plage d'adresses IP est utilisée pour exposer des applications sur le réseau privé via les services ALB ou Ingress.
- **Réseau de noeuds worker {{site.data.keyword.containerlong_notm}}** - Il existe deux plages d'adresses IP pour le réseau de noeuds worker :
    - Public – Sous-réseau principal public avec une plage d'adresses IP fournie par {{site.data.keyword.cloud_notm}}.
    - Privé – Sous-réseau principal privé avec une plage d'adresses IP fournie par {{site.data.keyword.cloud_notm}}.
-	**Réseau d'hôtes vCenter Server** - Il existe deux plages d'adresses IP pour le réseau d'hôtes vCenter Server :
    - Public – Sous-réseau principal public avec une plage d'adresses IP fournie par {{site.data.keyword.cloud_notm}}.
    - Privé – Sous-réseau principal privé avec une plage d'adresses IP fournie par {{site.data.keyword.cloud_notm}}.
-	**Réseau ESG vCenter Server** - Il existe deux plages d'adresses IP pour le réseau ESG vCenter Server :
    - Public – Sous-réseau portable public avec une plage d'adresses IP fournie par {{site.data.keyword.cloud_notm}}.
    - Privé – Sous-réseau portable privé avec une plage d'adresses IP fournie par {{site.data.keyword.cloud_notm}}.
-	**Réseau MV vCenter Server** – Plage d'adresses IP d'entreprise utilisant une plage BYOIP qui n'est en conflit avec aucun des sous-réseaux fournis par {{site.data.keyword.cloud_notm}}.
-	**Réseau de pods {{site.data.keyword.icpfull_notm}} ** – Plage d'adresses IP d'entreprise utilisant une plage BYOIP qui n'est en conflit avec aucun des sous-réseaux fournis par {{site.data.keyword.cloud_notm}}. Les plages d'adresses IP de pod et de service peuvent être configurées dans cluster/config.yaml.
-	**Réseau de service {{site.data.keyword.icpfull_notm}}** – Plage d'adresses IP d'entreprise utilisant une plage BYOIP qui n'est en conflit avec aucun des sous-réseaux fournis par {{site.data.keyword.cloud_notm}}. Les plages d'adresses IP de pod et de service peuvent être configurées dans cluster/config.yaml.
-	**Réseau de noeuds worker {{site.data.keyword.icpfull_notm}} ** – Plage d'adresses IP d'entreprise utilisant une plage BYOIP qui n'est en conflit avec aucun des sous-réseaux fournis par {{site.data.keyword.cloud_notm}}.

## Flux de trafic réseau
{: #vcsnsxt-overview-integration-net-traffic-flows}

Les flux de trafic suivants sont décrits :
-	Utilisateur externe sur Internet vers un niveau Web hébergé dans un conteneur dans {{site.data.keyword.containerlong_notm}}.
-	Utilisateur externe sur Internet vers un niveau Web hébergé dans un conteneur dans {{site.data.keyword.icpfull_notm}}.
-	Niveau Web hébergé dans un conteneur dans {{site.data.keyword.containerlong_notm}} vers un groupe de serveurs d'application de base de données hébergé dans une machine virtuelle dans vCenter Server.
-	Niveau Web hébergé dans un conteneur dans {{site.data.keyword.icpfull_notm}} vers un groupe de serveurs d'application de base de données hébergé dans une machine virtuelle dans vCenter Server.
-	Utilisateur d'entreprise sur l'accès au réseau d'entreprise vers une machine virtuelle dans vCenter Server.

### Utilisateur externe sur Internet vers un niveau Web hébergé dans un conteneur dans IBM Cloud Kubernetes Service
{: #vcsnsxt-overview-integration-web-tier-iks}

1.	L'utilisateur externe émet une demande vers le niveau Web à l'aide de l'URL.
2.	Le serveur de noms de domaine est utilisé pour déterminer l'adresse IP. Cette adresse IP est une adresse publique {{site.data.keyword.cloud_notm}} sur un sous-réseau portable qui est affecté au service ALB ou Ingress.
3.	Le réseau public achemine automatiquement la demande vers le noeud worker qui héberge le service ALB ou Ingress.
4.	Le noeud worker achemine la demande vers l'adresse IP de cluster interne et le numéro de port du service ALB ou Ingress. Cette adresse IP de cluster interne est accessible uniquement dans le cluster.
5.	Au sein du noeud worker, le proxy kube achemine la demande vers l'ALB ou le service Ingress.
6.	Si l'application figure sur le même noeud worker, iptables est utilisé pour déterminer quelle interface interne est utilisée pour acheminer la demande. Si l'application figure sur un autre noeud worker, Calico vRouter est acheminé vers le noeud worker qui s'applique à l'aide de l'encapsulation IP-in-IP, uniquement si le noeud worker se trouve sur un autre sous-réseau.

### Utilisateur externe sur Internet vers un niveau Web hébergé dans un conteneur dans IBM Cloud Private.
{: #vcsnsxt-overview-integration-web-tier-icp}

1.	L'utilisateur externe émet une demande vers le niveau Web à l'aide de l'URL.
2.	Le serveur de noms de domaine est utilisé pour déterminer l'adresse IP. Cette adresse IP est une adresse publique {{site.data.keyword.cloud_notm}} sur un sous-réseau portable qui est affecté à l'instance vCenter Server.
3.	Le réseau public achemine automatiquement la demande vers l'hôte vSphere ESXi qui héberge la passerelle ESG.
4.	La passerelle ESG achemine la demande vers l'adresse IP de cluster interne et le numéro de port de l'ALB ou du service Ingress. Le paquet IP est encapsulé dans un cadre VXLAN si la passerelle ESG et l'ALB ou le service Ingress figurent sur des hôtes vSphere ESXi différents. Cette adresse IP de cluster interne est accessible uniquement dans le cluster.
5.	Au sein du noeud worker, le proxy kube achemine la demande vers l'ALB ou le service Ingress.
6.	Si l'application figure sur le même noeud worker, iptables est utilisé pour déterminer quelle interface interne est utilisée pour acheminer la demande. Si l'application figure sur un autre noeud worker, Calico vRouter est acheminé vers le noeud worker qui s'applique à l'aide de l'encapsulation IP-in-IP. Le paquet IP-in-IP est encapsulé dans un cadre VXLAN pour le transport vers l'hôte vSphere ESXi sur lequel figure le noeud worker.

### Niveau Web hébergé dans un conteneur dans IBM Cloud Kubernetes Service vers un groupe de serveurs d'application de base de données hébergé dans une machine virtuelle dans vCenter Server.
{: #vcsnsxt-overview-integration-iks-db-tier-vcs}

La façon dont les tables de routage dans la passerelle et les routeurs vRouter sont renseignées varient en fonction de la méthode d'intégration. Voir l'intégration {{site.data.keyword.containerlong_notm}} et vCenter Server.
1.	Le niveau Web qui s'exécute dans un conteneur dans {{site.data.keyword.containerlong_notm}} émet une demande vers une base de données qui s'exécute sur une machine virtuelle dans la même instance vCenter Server.
2.	Le serveur de noms de domaine est utilisé pour résoudre la demande vers l'adresse IP de la base de données.
3.	Le conteneur envoie la demande à Calico vRouter.
4.	La table de routage de vRouter est alimentée par les plages d'adresses IP hébergées sur l'instance vCenter Server.
5.	vRouter achemine la demande mais utilise SNAT pour remplacer l'adresse IP source, qui correspond à l'adresse IP du pod, par l'adresse IP du noeud worker.
6.	Le noeud worker qui héberge vRouter envoie la demande au routeur BCR.
7.	Le noeud BCR envoie la demande à la passerelle ESG.
8.	La passerelle ESG achemine ensuite la demande vers le routeur DLR.
9.	Le routeur DLR place la demande sur le réseau VXLAN requis.
10.	La machine virtuelle de base de données reçoit la demande.

### Niveau Web hébergé dans un conteneur dans IBM Cloud Private vers un groupe de serveurs d'application de base de données hébergé dans une machine virtuelle dans vCenter Server.
{: #vcsnsxt-overview-integration-icp-db-tier-vcs}

La façon dont les tables de routage dans la passerelle et les routeurs vRouter sont renseignées varient en fonction de la méthode d'intégration. Voir l'intégration {{site.data.keyword.icpfull_notm}} et vCenter Server.
1.	Le niveau Web qui s'exécute dans un conteneur dans {{site.data.keyword.icpfull_notm}} émet une demande vers une base de données qui s'exécute sur une machine virtuelle dans la même instance vCenter Server.
2.	Le serveur de noms de domaine est utilisé pour résoudre la demande vers l'adresse IP de la base de données.
3.	Le conteneur envoie la demande à Calico vRouter.
4.	La table de routage de vRouter est alimentée par les plages d'adresses IP hébergées sur l'instance vCenter Server.
5.	vRouter achemine la demande mais utilise SNAT pour remplacer l'adresse IP source, qui correspond à l'adresse IP du pod, par l'adresse IP du noeud worker.
6.	Le noeud worker qui héberge vRouter envoie la demande à la passerelle ESG.
7.	La passerelle ESG achemine ensuite la demande vers le routeur DLR.
8.	Le routeur DLR place la demande sur le réseau VXLAN requis.
9.	La machine virtuelle de base de données reçoit la demande.

### Utilisateur d'entreprise sur l'accès au réseau d'entreprise vers une machine virtuelle dans vCenter Server
{: #vcsnsxt-overview-integration-corporate-network-vcs}

1.	Un utilisateur d'entreprise connecté au réseau interne de l'entreprise émet une demande d'une ressource sur une machine virtuelle hébergée dans vCenter Server.
2.	Le serveur de noms de domaine est utilisé pour déterminer l'adresse IP de la machine virtuelle. Cette adresse IP figure sur un réseau qui a été étendu à {{site.data.keyword.cloud_notm}}.
3.	Le routeur local dirige le trafic vers l'hôte vSphere qui héberge le concentrateur L2.
4.	Le concentrateur L2 encapsule la demande dans un tunnel sécurisé et la transmet au concentrateur L2 distant qui est hébergé dans {{site.data.keyword.cloud_notm}} à l'aide de l'adresse IP de sous-réseau portable privé affectée à l'unité, via le routeur local.
5.	La route locale examine sa table de routage et s'aperçoit que l'adresse IP pour le concentrateur L2 distant doit être envoyé à l'interface WAN. L'acheminement vers l'interface WAN est réalisé par le biais du routeur {{site.data.keyword.cloud_notm}} XCR, via le routeur BCR.
6.	Le concentrateur L2 reçoit la demande et la place sur le réseau VXLAN qui héberge le réseau étendu.
7.	La machine virtuelle reçoit la demande.

## Liens connexes
{: #vcsnsxt-overview-integration-related}

* [Centres de données {{site.data.keyword.cloud_notm}} dans le monde](https://www.ibm.com/cloud/data-centers/)
* [Container white paper](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf) (téléchargement de fichier PDF)
* [Blogue VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [Feuille de données VMware HCX on {{site.data.keyword.cloud_notm}}](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [NSX for vSphere 6.4.3 configuration maximums](https://configmax.vmware.com/guest)
* [Documentation de la plateforme {{site.data.keyword.cloud_notm}}](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started#getting-started)
* [Projet Calico](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)
