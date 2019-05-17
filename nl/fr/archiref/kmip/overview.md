---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de KMIP for VMware
{: #kmip-overview}

Cette architecture de solution décrit l'architecture KMIP on VMware pour la protection de vos instances VMware on {{site.data.keyword.cloud_notm}}. De nombreuses options de chiffrement de stockage sont disponibles pour protéger votre charge de travail VMware. KMIP for VMware fonctionne avec le chiffrement vSphere et le chiffrement vSAN natifs de VMware pour fournir une gestion simplifiée du chiffrement du stockage ainsi que la sécurité et la flexibilité des clés gérées par le client de {{site.data.keyword.cloud_notm}} Key Protect ou de {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services.

Cette solution est considérée comme un composant supplémentaire et une extension de l'offre vCenter Server on {{site.data.keyword.cloud_notm}}. Par conséquent, ce document n'aborde pas la configuration existante de ces solutions de base dans {{site.data.keyword.cloud_notm}}. Pour en savoir plus sur l'architecture des solutions de base, voir [Architecture de la solution VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

## Principaux avantages
{: #kmip-overview-benefits}

Tandis que de nombreuses solutions de chiffrement de stockage sont disponibles pour votre charge de travail VMware, KMIP for VMware présente les avantages suivants :

* Intégration au chiffrement VMware vSAN et au chiffrement vSphere, lesquels sont implémentés dans la couche de l'hyperviseur et non dans la couche de stockage ou dans la couche de la machine virtuelle. Cette approche garantit une gestion facile et la transparence pour votre solution et application de stockage.
* Serveur de gestion des clés entièrement géré et disponible dans de nombreuses régions multi-zone (MZR) {{site.data.keyword.cloud_notm}}.
* L'intégration de votre cluster VMware avec {{site.data.keyword.cloud_notm}} Key Protect ou {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services vous fournit des clés entièrement gérées par le client que vous pouvez révoquer à tout moment.

## Liens connexes
{: #kmip-overview-related}

* [Conception de la solution](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [Implémentation et gestion](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-implementation)
