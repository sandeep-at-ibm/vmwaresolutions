---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Accès réseau et flux
{: #vcsicp-detail-design-network}

## Accès d'application conteneur – IBM Cloud Private
{: #vcsicp-detail-design-network-container-icp}

Il existe trois méthodes principales pour obtenir un trafic et accès externes dans vos applications en cluster Kubernetes :

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Private
{: #vcsicp-detail-design-network-nodeport-icp}

Les ports Nodeport permettent d'exposer facilement l'accès externe à une charge de travail à des fins de développement initial et de tests, mais ils ne sont pas recommandés pour la production. La fonction Ingress ou l'équilibreur de charge sont recommandés.

### LoadBalancer - IBM Cloud Private
{: #vcsicp-detail-design-network-loadbalancer-icp}

Actuellement, la plateforme {{site.data.keyword.icpfull_notm}} prend en charge un équilibreur de charge externe pour la charge de travail d'application.

### Ingress - IBM Cloud Private
{: #vcsicp-detail-design-network-ingress-icp}

La fonction Ingress est une collection de règles qui permettent aux connexions entrantes d'atteindre les services de cluster. La fonction Ingress peut être configurée afin d'octroyer aux services des URL accessibles en externe, d'effectuer l'équilibrage de charge pour le trafic, de terminer SSL, d'offrir un hébergement virtuel basé sur le nom, etc.  Le noeud proxy dans l'infrastructure {{site.data.keyword.icpfull_notm}} exécute cette fonction.

## Accès d'application conteneur – IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-network-container-iks}

Il existe trois méthodes principales pour obtenir un trafic et accès externes dans vos applications en cluster Kubernetes :

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-network-nodeport-iks}

Les ports Nodeport permettent d'exposer facilement l'accès externe à une charge de travail à des fins de développement initial et de tests, mais ils ne sont pas recommandés pour la production. La fonction Ingress ou l'équilibreur de charge sont recommandés.

### LoadBalancer - IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-network-loadbalancer-iks}

Chaque cluster {{site.data.keyword.containerlong_notm}} est mis à disposition avec un équilibreur de charge d'application (ALB) public ou privé. L'ALB utilise un point d'entrée public ou privé unique et sécurisé pour acheminer les demandes entrantes vers vos applications.

### Ingress - IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-network-ingress-iks}

La fonction Ingress est une collection de règles qui permettent aux connexions entrantes d'atteindre les services de cluster. La fonction Ingress peut être configurée afin d'octroyer aux services des URL accessibles en externe, d'effectuer l'équilibrage de charge pour le trafic, de terminer SSL, d'offrir un hébergement virtuel basé sur le nom, etc.

## Flux de trafic
{: #vcsicp-detail-design-network-traffic-flows}

Les flux de trafic suivants sont décrits :

- Utilisateur externe sur Internet vers un niveau Web hébergé dans un conteneur dans {{site.data.keyword.icpfull_notm}}.
- Niveau Web hébergé dans un conteneur dans {{site.data.keyword.icpfull_notm}} vers un groupe de serveurs d'application de base de données hébergé dans une machine virtuelle dans VMware vCenter Server on {{site.data.keyword.cloud_notm}}.
- Utilisateur d'entreprise sur l'accès au réseau d'entreprise vers une machine virtuelle dans vCenter Server.

### Utilisateur externe sur Internet vers un niveau Web hébergé dans un conteneur dans IBM Cloud Private.
{: #vcsicp-detail-design-network-external-user}

1. L'utilisateur externe émet une demande vers le niveau Web à l'aide de l'URL.
2.	Le serveur de noms de domaine est utilisé pour déterminer l'adresse IP. Cette adresse IP est une adresse publique {{site.data.keyword.cloud_notm}} sur un sous-réseau portable qui est affecté à l'instance vCenter Server.
3.	Le réseau public achemine automatiquement la demande vers l'hôte vSphere ESXi qui héberge la passerelle ESG.
4.	La passerelle ESG achemine la demande vers l'adresse IP de cluster interne et le numéro de port de l'ALB ou du service Ingress. Le paquet IP est encapsulé dans un cadre VXLAN si la passerelle ESG et l'ALB ou le service Ingress figurent sur des hôtes vSphere ESXi différents. Cette adresse IP de cluster interne est accessible uniquement dans le cluster.
5.	Au sein du noeud worker, le proxy kube achemine la demande vers l'ALB ou le service Ingress.
6.	Si l'application figure sur le même noeud worker, iptables est utilisé pour déterminer quelle interface interne est utilisée pour acheminer la demande. Si l'application figure sur un autre noeud worker, Calico vRouter est acheminé vers le noeud worker qui s'applique à l'aide de l'encapsulation IP-in-IP. Le paquet IP-in-IP est encapsulé dans un cadre VXLAN pour le transport vers l'hôte vSphere ESXi sur lequel figure le noeud worker.

### Niveau Web hébergé dans un conteneur dans IBM Cloud Private vers un groupe de serveurs d'application de base de données hébergé dans une machine virtuelle dans vCenter Server.
{: #vcsicp-detail-design-network-web-tier}

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
{: #vcsicp-detail-design-network-enterprise-user}

1.	Un utilisateur d'entreprise connecté au réseau interne de l'entreprise émet une demande d'une ressource sur une machine virtuelle hébergée dans vCenter Server.
2.	Le serveur de noms de domaine est utilisé pour déterminer l'adresse IP de la machine virtuelle. Cette adresse IP figure sur un réseau qui a été étendu à {{site.data.keyword.cloud_notm}}.
3.	Le routeur local dirige le trafic vers l'hôte vSphere qui héberge le concentrateur L2.
4.	Le concentrateur L2 encapsule la demande dans un tunnel sécurisé et la transmet au concentrateur L2 distant qui est hébergé dans {{site.data.keyword.cloud_notm}} à l'aide de l'adresse IP de sous-réseau portable privé affectée à l'unité, via le routeur local.
5.	La route locale examine sa table de routage et s'aperçoit que l'adresse IP pour le concentrateur L2 distant doit être envoyé à l'interface WAN. L'acheminement vers l'interface WAN est réalisé par le biais du routeur {{site.data.keyword.cloud_notm}} XCR, via le routeur BCR.
6.	Le concentrateur L2 reçoit la demande et la place sur le réseau VXLAN qui héberge le réseau étendu.
7.	La machine virtuelle reçoit la demande.

## Réseau d'accès public
{: #vcsicp-detail-design-network-public-access-net}

Par défaut, {{site.data.keyword.icpfull_notm}} et CAM nécessitent une connectivité Internet pour extraire des images Docker, des chartes Helm, des modèles Terraform et des gestionnaires de packages de système d'exploitation.
Dans les dernières éditions, des installations basées sur un proxy sont prises en charge pour les installations qui ne sont pas directement connectées à Internet et qui proposent des options d'installation en mode hors ligne.

###	Pare-feu NSX
{: #vcsicp-detail-design-network-nsx-firewall}

Le pare-feu {{site.data.keyword.icpfull_notm}} NSX Edge est configuré avec des règles permettant :
*	d'activer l'accès des réseaux VXLAN à un accès public ;
*	d'activer l'accès des réseaux VXLAN à un accès réseau {{site.data.keyword.cloud_notm}} privé ;
*	d'activer l'accès réseau {{site.data.keyword.cloud_notm}} privé à des réseaux VXLAN.

### NSX NAT
{: #vcsicp-detail-design-network-nsx-nat}

{{site.data.keyword.icpfull_notm}} NSX NAT est configuré avec les NAT suivants :
*	SNAT pour l'accès des réseaux VXLAN à un accès public
*	SNAT pour l'accès des réseaux VXLAN à un accès réseau {{site.data.keyword.cloud_notm}} privé
*	DNAT pour des adresses IP virtuelles de cluster {{site.data.keyword.icpfull_notm}}

## Liens connexes
{: #vcsicp-detail-design-network-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
