---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Commande d'IBM Spectrum Protect Plus on IBM Cloud

Vous pouvez commander le service {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} lors de la commande d'une nouvelle instance avec le service inclus ou vous pouvez ajouter le service à votre instance existante.

## Commande d'IBM Spectrum Protect Plus on IBM Cloud pour une nouvelle instance

Vous pouvez commander une nouvelle instance avec IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} à l'aide de l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, lorsque vous commandez une nouvelle instance, sélectionnez **IBM Spectrum Protect Plus on IBM Cloud** dans la section **Services**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **IBM Spectrum Protect Plus on IBM Cloud**, spécifiez les paramètres de service, puis choisissez **Ajouter à une nouvelle instance**.

## Commande d'IBM Spectrum Protect Plus on IBM Cloud pour une instance existante

Vous pouvez ajouter le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} dans une instance existante à l'aide de l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **IBM Spectrum Protect Plus on IBM Cloud**, spécifiez les paramètres de service, puis choisissez **Ajouter à une instance existante**.

## Configuration du service IBM Spectrum Protect Plus on IBM Cloud

Lorsque vous commandez le service, indiquez les paramètres suivants :

### Nombre de volumes de stockage

Nombre de volumes répondant à vos besoins en stockage.

### Taille de stockage par volume

Capacité de stockage par volume.

### Performances de stockage

Valeur IOPS (Input/output Operations Per Second) par Go adaptée à vos besoins en matière de charge de travail.
* Si vous voulez commander des licences pour IBM Spectrum Protect Plus, renseignez la zone **Nombre de machines virtuelles pour lesquelles concéder une licence** dans l'onglet **Commander des licences**.
* Si vous voulez fournir votre propre licence (BYOL, Bring Your Own License), cliquez sur l'onglet **Licence IBM Spectrum Protect Plus**, puis sur **Ajouter une licence** pour télécharger les fichiers de licence IBM Spectrum Protect Plus que vous possédez.

## Processus de déploiement du service IBM Spectrum Protect Plus on IBM Cloud

Le processus de déploiement du service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} est automatisé. Que vous commandiez une instance avec ce service inclus ou que vous déployez le service ultérieurement dans votre instance, les étapes suivantes sont réalisées par le processus d'automatisation de {{site.data.keyword.vmwaresolutions_short}} :

1. Selon les paramètres que vous spécifiez, le stockage NFS de type Endurance est commandé à partir de l'infrastructure {{site.data.keyword.cloud_notm}} pour le référentiel de sauvegarde IBM Spectrum Protect Plus.
2. Selon les paramètres que vous spécifiez, un certain nombre de licences est commandé à partir de l'infrastructure {{site.data.keyword.cloud_notm}} pour IBM Spectrum Protect Plus. Les licences sont commandées par paquets de 10 licences de machine virtuelle, en fonction du nombre de machines virtuelles que vous avez indiqué lors de la commande du service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. Si vous choisissez de fournir une licence IBM Spectrum Protect Plus existante, aucune commande de licence n'est passée à partir de l'infrastructure {{site.data.keyword.cloud_notm}}.
3. Le stockage NFS commandé pour ce service est monté sur tous les serveurs ESXi dans le cluster par défaut de l'instance, ce qui inclut l'ajout sur chaque serveur ESXi des routes statiques appropriées vers le sous-réseau privé de stockage.
4. Des magasins de données NFS sont créés dans vCenter Server pour tous les volumes de stockage NFS montés sur les serveurs ESXi.
5. Les machines virtuelles IBM Spectrum Protect Plus sont déployées, activées et configurées dans le cluster par défaut de l'instance.
6. Le stockage NFS qui a été commandé pour ce service est connecté à la machine virtuelle IBM Spectrum Protect Plus et le référentiel de sauvegarde est configuré.
7. Le nom d'hôte et l'adresse IP de la machine virtuelle IBM Spectrum Protect Plus sont enregistrés auprès du serveur DNS de l'instance.

### Liens connexes

* [Présentation d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_considerations.html)
* [Planification préventive du service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestion d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Documentation IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
