---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: Zerto, request Zerto Orchestrated, Zerto managed service

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# Services gérés pour Zerto on IBM Cloud
{: #managing_zerto_services}

Le service Zerto on {{site.data.keyword.cloud}} fournit des fonctions de réplication et de reprise après incident. Ces fonctions peuvent être intégrées aux offres de déploiement de manière à assurer la protection et la récupération des données dans votre environnement virtuel VMware sur {{site.data.keyword.cloud_notm}}.

Lorsque vous demandez Services gérés pour Zerto on {{site.data.keyword.cloud_notm}}, un environnement de reprise après incident totalement géré peut être déployé en utilisant le logiciel de reprise après incident (DR, Disaster Recovery) Zerto et IBM Resiliency Services.

Les modèles ci-après pour Services gérés pour Zerto on {{site.data.keyword.cloud_notm}} sont disponibles.

## IBM Orchestrated Managed Services for Zerto
{: #managing_zerto_services-orchestrated}

Ce modèle convient si vous utilisez l'offre Zerto on {{site.data.keyword.cloud_notm}}.

Avec ce modèle, le service {{site.data.keyword.cloud_notm}} Resiliency Orchestration est mis à disposition pour Zerto on {{site.data.keyword.cloud_notm}}. Ce modèle permet une protection en continu des machines virtuelles, des systèmes d'exploitation et des données sur {{site.data.keyword.cloud_notm}}, avec test de reprise après incident sans provoquer d'interruption, visibilité des objectifs de délai de récupération/de point de récupération, fonctionnalité de basculement et de reprise par restauration.

Toutes les fonctions sont gérées à partir du tableau de bord {{site.data.keyword.cloud_notm}} Resiliency Orchestration par le centre de commande global d'IBM Resiliency Services.

Pour plus d'informations, voir [IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration){:external}.

## Services gérés par IBM pour Zerto (sans Orchestration)
{: #managing_zerto_services-without-orchestrated}

Avec ce modèle, une solution de reprise après incident totalement gérée est mise à disposition pour Zerto on {{site.data.keyword.cloud_notm}}. Ce modèle est adapté si vous voulez disposer d'un service géré pour la réplication virtuelle Zerto uniquement, sans le service {{site.data.keyword.cloud_notm}} Resiliency Orchestration sur {{site.data.keyword.cloud_notm}}.

Pour plus d'informations, voir [IBM Resiliency Disaster Recovery as a Service](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top){:external}.

## Procédure de demande de Services gérés pour Zerto on IBM Cloud
{: #managing_zerto_services-procedure}

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Initiation** dans le panneau de navigation de gauche.
2. Faites défiler la page vers le bas et sous **Services gérés VMware**, cliquez sur la carte **Services gérés pour Zerto on IBM Cloud**.
3. Sur la page **Zerto on IBM Cloud**, passez en revue la description et les spécifications techniques concernant Zerto on {{site.data.keyword.cloud_notm}} en tant que service géré, puis cliquez sur **Créer**.
4. Spécifiez les paramètres de configuration en fonction de vos exigences ou acceptez les valeurs par défaut.
5. Cliquez sur **vCenter Server** pour ajouter le service à l'une de vos instances.
6. Pour ajouter le service pendant que vous commandez une nouvelle instance, cliquez sur **Ajouter à une nouvelle instance** et poursuivez votre commande d'instance [vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance) ou [vCenter Server with Hybridity](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance).
7. Pour ajouter le service à une instance existante, cliquez sur l'option **Ajouter à une instance existante**, sélectionnez dans la liste l'instance à laquelle vous voulez ajouter le service, puis confirmez que vous souhaitez poursuivre la commande en cliquant sur **Mettre à disposition**.

## Liens connexes
{: #managing_zerto_services-related}

* [Commande, affichage et retrait de services pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
