---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-08"

subcollection: vmware-solutions


---

# Notes sur l'édition pour la version 2.8
{: #relnotes_v28}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Instances de la version d'essai à noeud unique pour la migration et la modernisation des applications
{: #relnotes_v28-single-node-trial}

La version d'essai à noeud unique pour la migration et la modernisation des applications permet de tester rapidement comment utiliser {{site.data.keyword.cloud_notm}} pour migrer les charges de travail VMware dans {{site.data.keyword.cloud_notm}}, puis moderniser ces charges de travail à l'aide de conteneurs. Il s'agit d'une version d'essai de {{site.data.keyword.icpfull_notm}} Hosted sur VMware vCenter Server on {{site.data.keyword.cloud_notm}} qui fournit la plateforme de gestion Kubernetes pour les conteneurs et la plateforme VMware à service exclusif qui peut être gérée à l'aide des mêmes outils connus que dans les environnements locaux.

Pour plus d'informations, voir [Présentation de la version d'essai à noeud unique pour la migration et la modernisation des applications](/docs/services/vmwaresolutions?topic=vmware-solutions-cloud_modern_bundle_overview#cloud_modern_bundle_overview).

## Ajout et suppression de stockage de système NFS
{: #relnotes_v28-nfs}

Dans la version 2.8, vous pouvez désormais ajouter des partages de stockage NFS sur un cluster NFS ou vSAN vCenter Server existant, mais également supprimer des partages de fichiers NFS d'un cluster vCenter Server existant.

Les options suivantes pour le stockage de niveau fichier personnalisé sont maintenant disponibles :

* Tailles de partage NFS à partir de 20 Go jusqu'à 12 To, par incréments de 1 Go
* 0,25 IOPS/Go

Pour plus d'informations, voir les sections *Ajout de stockage NFS aux instances vCenter Server* et *Suppression de stockage NFS des instances vCenter Server* dans [Extension et réduction de capacité pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances).

## Prise en charge du serveur Broadwell E5-2690 et E7-8890 certifié SAP
{: #relnotes_v28-broadwell-e5-e7}

A compter de la version 2.8, les nouveaux modèles d'UC de serveur {{site.data.keyword.baremetal_short_sing}} {{site.data.keyword.cloud_notm}} sont disponibles pour déploiement pour les instances et les clusters VMware vCenter Server on {{site.data.keyword.cloud_notm}} et VMware vSphere on {{site.data.keyword.cloud_notm}} :

* Processeur Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,60 GHz/512 Go de mémoire RAM
* Processeur Quad Intel Xeon E7-8890 v4/96 coeurs au total, 2,20 GHz/1024 Go de mémoire RAM
* Processeur Quad Intel Xeon E7-8890 v4/96 coeurs au total, 2,20 GHz/2048 Go de mémoire RAM
* Processeur Quad Intel Xeon E7-8890 v4/96 coeurs au total, 2,20 GHz/4096 Go de mémoire RAM

Pour plus d'informations, voir la section *Paramètres de serveur {{site.data.keyword.baremetal_short_sing}}* dans :
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Prise en charge du serveur Broadwell E7-4820 et E7-4850
{: #relnotes_v28-broadwell-e7}

A compter de la version 2.8, les nouveaux modèles d'UC de serveur {{site.data.keyword.baremetal_short_sing}} {{site.data.keyword.cloud_notm}} sont disponibles pour déploiement pour les instances et les clusters vCenter Server, vCenter Server with Hybridity Bundle, Cloud Foundation et vSphere on {{site.data.keyword.cloud_notm}} :

* Quad Intel Xeon E7-4820 v4/40 coeurs au total, 2,0 GHz
* Quad Intel Xeon E7-4850 v4/64 coeurs au total, 2,1 GHz

Pour plus d'informations, voir la section *Paramètres de serveur {{site.data.keyword.baremetal_short_sing}}* dans :
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [Commande d'instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance#bare-metal-server-settings)
* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Platform Services Controller intégré
{: #relnotes_v28-psc}

A compter de la version 2.8, vCenter Server est déployé avec une version intégrée de PSC (Platform Services Controller), ce qui signifie que vCenter Server, les composants vCenter Server et PSC sont déployés sur une machine virtuelle unique. Cette modification concerne toutes les instances de vCenter Server, vCenter Server with Hybridity et NetApp nouvellement déployées.

Pour les instances qui sont mises à niveau à partir d'une version antérieure à la version 2.8, PSC n'est pas intégré dans vCenter Server. Si vous voulez utiliser la version intégrée de PSC, vous devez procéder vous-même à une conversion en externe vers la version PSC intégrée.

Dans une configuration multisite où l'instance principale est une instance mise à niveau pour laquelle PSC a été converti manuellement en externe vers une version intégrée, les instances secondaires en version 2.8 nouvellement déployées intégreront PSC.

Pour plus d'informations, voir la section *Architecture vCenter Server* dans [Présentation de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#vcenter-server-architecture).

## Mises à jour des instances VMware vCenter Server
{: #relnotes_v28-vcs}

Cette édition applique les mises à niveau et améliorations suivantes :

* vSphere ESXi 6.5 Update EP11 (build 6.5.0-10719125)
* vCenter Server 6.5 U2d (build 6.5.0-10964411)
* Platform Services Controller 6.5 U2d (build 6.5.0-10964411)

## Mises à jour des instances VMware Cloud Foundation
{: #relnotes_v28-cf}

Cette édition applique les mises à niveau et améliorations suivantes :

* vSphere ESXi 6.5 Update EP11 (build 6.5.0-10719125)
* vCenter Server 6.5 U2c (build 6.5.0-9451637)
* Platform Services Controller 6.5 U2c (build 6.5.0-9451637)

## Mises à jour apportées aux services complémentaires
{: #relnotes_v28-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v28-spp}

L'édition en cours installe IBM Spectrum Protect™ Plus V10.1.2 sur toutes les instances nouvellement déployées. Pour plus d'informations sur les nouvelles fonctions dans IBM Spectrum Protect Plus V10.1.2, voir [Mises à jour d'IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.2/spp/r_techchg_spp.html){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v28-kmip}

Auparavant, vous pouviez commander une instance Cloud Foundation ou vCenter Server avec le service KMIP for VMware on {{site.data.keyword.cloud_notm}} inclus ou ajouter le service à une instance Cloud Foundation ou vCenter Server existante après le déploiement initial.

A compter de la version 2.8, le service est disponible en tant que service autonome sans être associé à une instance VMware. Chaque instance du service peut servir une ou plusieurs instances Cloud Foundation, vCenter Server ou clusters vSphere.

Pour plus d'informations, voir [Présentation de KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations).

## Documentation d'architecture de référence
{: #relnotes_v28-ref}

(mis à jour le 8 février 2019) Les documents techniques suivants nouveaux ou mis à jour dans la section *Référence* de la documentation utilisateur :

* [Architecture {{site.data.keyword.vmwaresolutions_short}} (avec NSX-V et NSX-T)
](/docs/services/vmwaresolutions/services?topic=vmware-solutions-solution_overview#solution_overview)
* [Architecture de référence de Caveonix RiskForesight](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-on-vcs)
* [VMware HCX on {{site.data.keyword.cloud_notm}} for VMware Solutions](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-intro)

## Améliorations et mises à jour apportées à l'interface utilisateur
{: #relnotes_v28-ui}

L'interface utilisateur a été mise à jour et présente les améliorations suivantes :

* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.
