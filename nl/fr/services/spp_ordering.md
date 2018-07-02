---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-13"

---

# Commande d'IBM Spectrum Protect Plus on IBM Cloud

Vous pouvez commander le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} lors de la commande d'une nouvelle instance avec le service inclus ou vous pouvez ajouter le service à votre instance existante. 

## Commande d'IBM Spectrum Protect Plus on IBM Cloud pour une nouvelle instance

Vous pouvez commander une nouvelle instance avec IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} à l'aide de l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_full}}, lorsque vous commandez une nouvelle instance, sélectionnez **IBM Spectrum Protect Plus on IBM Cloud** dans la section **Services**. 
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}**, spécifiez les paramètres de service, puis choisissez **Ajouter à une nouvelle instance**.

## Commande d'IBM Spectrum Protect Plus on IBM Cloud pour une instance existante

Vous pouvez ajouter le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} dans une instance existante à l'aide de l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter un service**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **IBM Spectrum Protect Plus on IBM Cloud**, spécifiez les paramètres de service, puis choisissez **Ajouter à une nouvelle instance**.

## Configuration du service IBM Spectrum Protect Plus on IBM Cloud

Lorsque vous commandez le service, indiquez les paramètres suivants :

### Nombre de volumes de stockage

Nombre de volumes répondant à vos besoins en stockage. 

### Taille de stockage par volume

Capacité de stockage par volume. Un minimum de 500 Go par volume est nécessaire pour la gestion.

### Performances de stockage

Valeur IOPS (Input/output Operations Per Second) par Go adaptée à vos besoins en matière de charge de travail. 
* Si vous voulez commander des licences pour IBM Spectrum Protect Plus, renseignez la zone **Nombre de machines virtuelles pour lesquelles concéder une licence** dans l'onglet **Commander des licences**. Un minimum de 10 machines virtuelles est nécessaire pour la gestion des licences.
* Si vous voulez fournir votre propre licence (BYOL, Bring Your Own License), cliquez sur l'onglet **Licence IBM Spectrum Protect Plus**, puis sur **Ajouter une licence** pour télécharger les fichiers de licence IBM Spectrum Protect Plus que vous possédez.

## Processus de déploiement du service IBM Spectrum Protect Plus on IBM Cloud

Le processus de déploiement du service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} est automatisé. Que vous commandiez une instance avec ce service inclus ou que vous déployez le service ultérieurement dans votre instance, les étapes suivantes sont réalisées par le processus d'automatisation de {{site.data.keyword.vmwaresolutions_short}} : 

1. Commande d'un stockage NFS Endurance depuis l'infrastructure {{site.data.keyword.cloud_notm}} pour le référentiel de sauvegarde IBM Spectrum Protect Plus basé sur des entrées utilisateur.
2. Commande d'un nombre spécifique de licences pour IBM Spectrum Protect Plus depuis l'infrastructure {{site.data.keyword.cloud_notm}} sur la base des entrées utilisateur. Les licences sont commandées par paquets de 10 licences de machine virtuelle, en fonction du nombre de machines virtuelles que l'utilisateur indique lors de la commande du service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. Si l'utilisateur choisit de fournir une licence IBM Spectrum Protect Plus existante, aucune commande de licence n'est passée à l'infrastructure {{site.data.keyword.cloud_notm}}.
3. Montage de tous les stockages NFS commandés pour ce service sur tous les serveurs ESXi du cluster par défaut de l'instance, en incluant sur chaque serveur ESXi les routes statiques appropriées vers le sous-réseau privé de stockage.
4. Création de magasins de données NFS dans vCenter Server pour tous les volumes de stockage NFS montés sur les serveurs ESXi.
5. Déploiement, activation et configuration de la machine virtuelle IBM Spectrum Protect Plus dans le cluster par défaut de l'instance.
6. Association de tous les stockages NFS commandés pour ce service à la machine virtuelle IBM Spectrum Protect Plus et configuration du référentiel de sauvegarde.
7. Inscription du nom d'hôte et de l'adresse IP de la machine virtuelle IBM Spectrum Protect Plus auprès du serveur DNS de l'instance.
8. (Pour les instances V2.3 et ultérieures) Création d'une tâche de sauvegarde de gestion par défaut dans IBM Spectrum Protect Plus. Pour plus d'informations, voir [Gestion d'IBM Spectrum Protect Plus on IBM Cloud](managingspp.html).

## Liens connexes

* [Présentation d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_considerations.html)
* [Planification préventive du service IBM Spectrum Protect Plus on IBM Cloud](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestion d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Documentation IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
