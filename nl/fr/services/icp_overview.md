---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation d'IBM Cloud Private Hosted
{: #icp_overview}

Le service {{site.data.keyword.cloud}} Private Hosted déploie automatiquement {{site.data.keyword.cloud_notm}} Private Hosted sur vos instances VMware vCenter Server. Ce service fournit la puissance des microservices et des conteneurs à votre environnement VMware sur {{site.data.keyword.cloud_notm}}. Grâce à ce service, vous pouvez déployer le même modèle opérationnel et les mêmes outils VMware et {{site.data.keyword.cloud_notm}} locaux dans {{site.data.keyword.cloud_notm}}.

Ce service est disponible pour les instances suivantes :
* Les instances vCenter Server qui sont déployées dans ou mises à niveau vers la version 2.5 et des versions ultérieures
* Les instances vCenter Server with Hybridity Bundle qui sont déployées dans ou mises à niveau vers la version 2.7 et des versions ultérieures.
{:note}

## Spécifications techniques pour IBM Cloud Private Hosted
{: #icp_overview-specs}

Le tableau ci-après répertorie les exigences minimales requises pour commander le service IBM Cloud Private Hosted pour l'environnement **Prêt pour la production** et l'environnement **Développement/Test**.

Tableau 1. Exigences minimales requises pour les environnements Prêt pour la production et Développement/Test

|Environnement | Coeurs | Mémoire (Go) | Hôtes | Stockage (Go) |
|:---------- |:---- |:------ |:---- |:------- |
| Prêt pour la production | 52 | 640 | 3 | 8 000 |
| Développement/Test | 30 | 200 | 3 | 4 000 |

### Besoins en ressources d'IBM Cloud Private Hosted
{: #icp_overview-resource-req}

Les tableaux ci-après répertorient les besoins en ressources du service {{site.data.keyword.cloud_notm}} Private Hosted dans les environnements Prêt pour la production et Développement/Test.

Tableau 2. Besoins en ressources d'{{site.data.keyword.cloud_notm}} Private Hosted dans l'environnement Prêt pour la production

| Type de noeud  | Coeurs d'UC   |  Mémoire (Go) | Disque 1 (Go) | Disque 2 (Go) | Nombre de machines virtuelles |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Amorçage       | 12 | 24 | 100 | 1 | 1 |   
| Gestion | 8 | 64 | 500 | 3 | 3 |
| Maître     | 8 | 64 | 200 | 3 | 3 |  
| Proxy      | 2 | 4  | 150 | 3 | 3 |
| Worker     | 4 | 16 | 200 | 300 | 6 |
| Vulnerability Advisor | 8 | 16 | 500 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Amorçage {{site.data.keyword.icpfull_notm}}/CAM | 24 | 44 | 250 | 1 | 1 |
| Serveur NFS | 8 | 4  | 350 | 1 | 1 |
| Passerelle NSX ESG (Edge Services Gateway) | 2 | 1 | 0,5 | 0,5 | 2 |
| Contraintes documentées | 52 | 640 |  | 8 000 |   |

Tableau 3. Besoins en ressources d'{{site.data.keyword.cloud_notm}} Private Hosted dans l'environnement Développement/Test

| Type de noeud  | Coeurs d'UC   |  Mémoire (Go) | Disque 1 (Go) | Disque 2 (Go) | Nombre de machines virtuelles |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Amorçage       | 12 | 24 | 100 | 1 | 1 |   
| Gestion | 8 | 16 | 150 | 1 | 1 |
| Maître     | 8 | 16 | 200 | 1 | 1 |  
| Proxy      | 2 | 4  | 150 | 1 | 1 |
| Worker     | 4 | 16 | 200 | 300 | 3 |
| Vulnerability Advisor | 8 | 16 | 150 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Amorçage {{site.data.keyword.icpfull_notm}}/CAM | 24 | 44 | 250 | 1 | 1 |
| Serveur NFS | 8 | 4  | 350 | 1 | 1 |
| Passerelle NSX ESG (Edge Services Gateway) | 2 | 1 | 0,5 | 0,5 | 2 |
| Contraintes documentées | 30 | 200 |  | 4 000 |  |

### Formules de calcul des exigences d'espace pour IBM Cloud Private Hosted
{: #icp_overview-formulas}

Les formules suivantes sont utilisées pour calculer l'espace requis pour IBM Cloud Private et les surcharges de gestion :

#### Formule 1
{: #icp_overview-formulas-1}

`AvailableCores = [HostCoreCount - HostOverheadCores - (HostVSanOverheadCorePercentage * HostCoreCount)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadCores`

Tableau 4. Description des variables de la formule 1

| Variables	| Description |	Unité |	Exemple vSAN | Exemple NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |	Nombre de coeurs réels disponibles pour les charges de travail et les services dans l'environnement |	Coeurs |	38	| 43 |
| HostCount	| Nombre d'hôtes dans le cluster par défaut	| Hôtes | 4	| 4 |
| HostCoreCount	| Nombre de coeurs bruts disponibles dans chaque hôte dans le cluster par défaut |	Coeurs |	16 | 16 |
| HostOverheadCores	| Nombre de coeurs réservés par le serveur ESXi comme surcharge, égal à 0,1 coeur	| Coeurs	| 0,1 |	0,1 |
| MgmtOverheadCores | Nombre de coeurs réservés par les composants de gestion vCenter Server (vCenter Server, PSC, AD/DNS, Edges), égal à cinq coeurs	| Coeurs	| 5	| 5 |
| vSphereHAHostTolerance |	Nombre d'hôtes à tolérer dans la configuration vSphere HA, égal à un hôte |	Hôtes	 | 1 | 1 |
| HostVsanOverheadCorePercentage | Pourcentage de coeurs d'un hôte utilisé par vSAN, égal à 10 % ou à 0 % pour un hôte hors VSAN | % | 10 % |	0 % |

#### Formule 2
{: #icp_overview-formulas-2}

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

Tableau 5. Description des variables de la formule 2

| Variables	| Description |	Unité |	Exemple vSAN | Exemple NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory	| Nombre de Go de mémoire disponible pour les charges de travail et les services dans l'environnement | Go | 	693	| 860 |
| HostCount	| Nombre d'hôtes dans le cluster par défaut | Hôtes  | 6	| 6 |
| HostMemory |	Nombre de Go de mémoire bruts disponibles dans chaque hôte dans le cluster par défaut |	Go	| 192 |	192 |
| HostVsanCapacityDiskSize | Nombre de Go de capacité de chaque disque SSD vSAN sur cet hôte, égal à 960, 1946 ou 3891, ou égal à 0 Go pour un hôte hors VSAN | Go |	960 | 0 |
| HostOverheadMemory |	Nombre de Go de mémoire réservés par le serveur ESXi comme surcharge, égal à 4,6 Go |	Go	| 4,6 |	4,6 |
| MgmtOverheadMemory |	Nombre de Go de mémoire réservés par les composants de gestion vCenter Server (vCenter Server, PSC, AD/DNS, Edges), égal à 77 Go | Go | 77 | 77 |
| vSphereHAHostTolerance | Nombre d'hôtes à tolérer dans la configuration vSphere HA, égal à un hôte | Hôtes	| 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | Nombre de Go de mémoire réservés par les composants vSAN (représenté en tant que pourcentage de l'un des disques vSAN de capacité), égal à 2,75 % |	% | 2,75%	| 2,75% |
| HostVsanOverheadMemory | Nombre de Go de mémoire réservés par la gestion vSAN quelle que soit la taille du disque, égal à 7 Go ou à 0 Go pour un hôte hors VSAN	| Go |  7	| 0 |

## Remarques relatives à l'installation de IBM Cloud Private Hosted
{: #icp_overview-install}

* Procurez-vous la licence requise avant d'installer le service {{site.data.keyword.cloud_notm}} Private Hosted.Nous vous conseillons de vérifier que votre licence peut prendre en charge non seulement le déploiement {{site.data.keyword.cloud_notm}} Private Hosted initial, mais également la future extension de taille d'{{site.data.keyword.cloud_notm}} Private Hosted dans votre infrastructure.
* Pour les déploiements {{site.data.keyword.cloud_notm}} Private Hosted en environnement prêt pour la production, 64 Go de mémoire RAM par hôte ne sont pas pris en charge. Par conséquent, vous devez sélectionner une option de plus de 64 Go pour la mémoire **RAM**.
* Avant l'installation du service {{site.data.keyword.cloud_notm}} Private Hosted dans votre environnement, la capacité disponible sur le cluster par défaut dans l'environnement est vérifiée afin de s'assurer qu'il y aura suffisamment de place pour les composants de service. Si la vérification de la capacité échoue, le service n'est pas installé et l'état **La validation de la capacité a échoué** apparaît sur la console pour le service. De plus, un message de console contenant davantage de détails apparaît et vous êtes averti par courrier électronique. Pour installer le service, vous devez augmenter la capacité dans votre cluster par défaut en ajoutant d'autres hôtes ou en libérant de la mémoire RAM, de l'UC ou de l'espace disque, puis vous devez rajouter le service dans la console. Après cela, vous pouvez retirer le service qui est à l'état **La validation de la capacité a échoué** en cliquant sur l'icône **Supprimer** figurant en regard de son nom.

## Remarques relatives au retrait d'IBM Cloud Private Hosted
{: #icp_overview-remove}

* {{site.data.keyword.cloud_notm}} supprime uniquement les machines virtuelles qui ont été déployées durant l'installation initiale du service {{site.data.keyword.cloud_notm}} Private Hosted. Tout noeud qui est déployé après l'installation ne sera pas nettoyé.
* {{site.data.keyword.cloud_notm}} supprimera le réseau VXLAN, le routeur DLR et la passerelle de périphérie qui ont été créés durant le déploiement initial du service {{site.data.keyword.cloud_notm}} Private Hosted. Les machines virtuelles que vous avez déployées sur le réseau VXLAN perdent la connectivité une fois le retrait du service {{site.data.keyword.cloud_notm}} Private Hosted commencé.

## Liens connexes
{: #icp_overview-related}

* [Commande d'IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)
* [Guide vCenter Server et IBM Cloud Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [Ouvrir un ticket au sujet d'IBM Cloud Private](https://www.ibm.com/mysupport/s/?language=fr_FR)
