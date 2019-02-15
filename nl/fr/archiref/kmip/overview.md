---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de KMIP for VMware

Cette architecture de solution décrit l'architecture KMIP on VMware pour la protection de vos instances VMware on {{site.data.keyword.cloud_notm}}. De nombreuses options de chiffrement de stockage sont disponibles pour protéger votre charge de travail VMware. KMIP for VMware peut être utilisé avec le chiffrement VMware natif vSphere et le chiffrement vSAN pour offrir une gestion du chiffrement de stockage simplifiée avec la sécurité et la flexibilité des clés gérées par le client {{site.data.keyword.cloud_notm}} Key Protect.

**Remarque **: Dans cette édition, KMIP for VMware on {{site.data.keyword.cloud_notm}} est limité au chiffrement vSphere uniquement.

Cette solution est considérée comme un composant supplémentaire et une extension des solutions vCenter Server et VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}. Par conséquent, ce document n'aborde pas la configuration existante de ces solutions de base dans {{site.data.keyword.cloud_notm}}. Pour en savoir plus sur l'architecture des solutions de base, voir [Architecture de la solution VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html).

## Principaux avantages

Tandis que de nombreuses solutions de chiffrement de stockage sont disponibles pour votre charge de travail VMware, KMIP for VMware présente les avantages suivants :

* Intégration au chiffrement VMware vSAN et au chiffrement vSphere, lesquels sont implémentés dans la couche de l'hyperviseur et non dans la couche de stockage ou dans la couche de la machine virtuelle. Cette approche garantit une gestion facile et la transparence pour votre solution et application de stockage.
* Serveur de gestion des clés entièrement géré et disponible dans de nombreuses régions multi-zone (MZR) IBM Cloud.
* Avec l'intégration de votre cluster VMware à IBM Cloud Key Protect, vous disposez de clés entièrement gérées par le client et que vous pouvez révoquer à tout moment.

### Liens connexes

* [Conception de la solution](/docs/services/vmwaresolutions/archiref/kmip/design.html)
* [Implémentation et gestion](/docs/services/vmwaresolutions/archiref/kmip/implementation.html)
