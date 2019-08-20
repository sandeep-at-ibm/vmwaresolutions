---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Composants des services communs pour VMware et Skate Advisor Concept Car
{: #vcscar-commonservices}

Les services communs fournissent les services qui sont utilisés par d'autres services de la plateforme de gestion du cloud. Il s'agit notamment des services d'identité et d'accès, des services de nom de domaine et des services NTP (Network Time Protocol).

![{{site.data.keyword.icpfull_notm}} - Services communs](../../images/vcscar-common-services.svg "{{site.data.keyword.icpfull_notm}} - Services communs")

## Services d'identité et d'accès
{: #vcscar-commonservices-identity}

Dans le cadre de l'automatisation VMware vCenter Server on {{site.data.keyword.cloud_notm}}, un annuaire Microsoft Active Directory (AD) est utilisé pour la gestion des identités. Une seule instance de serveur virtuel AD est déployée. vCenter est configuré pour utiliser l'authentification AD et vous pouvez également configurer {{site.data.keyword.icpfull_notm}} pour l'authentification LDAP.

## Services de nom de domaine
{: #vcscar-commonservices-dns}

Le déploiement utilise les instances de serveur virtuel AD déployées comme serveurs DNS pour l'instance. Tous les composants déployés sont configurés pour pointer vers l'annuaire AD comme serveur DNS par défaut. Les composants déployés sont notamment vCenter, PSC, NSX et les hôtes ESXi.

## Services Network Time Protocol
{: #vcscar-commonservices-ntp}

Le déploiement vCenter Server utilise les serveurs NTP de l'infrastructure {{site.data.keyword.cloud_notm}}. Tous les composants déployés sont configurés pour utiliser ces serveurs NTP. Il est essentiel que tous les composants utilisent les mêmes serveurs NTP pour que les certificats et l'authentification AD puissent fonctionner correctement.
