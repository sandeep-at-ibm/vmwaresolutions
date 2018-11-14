---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-10"

---

# Conception détaillée

## Composants des services communs
Les services communs fournissent les services utilisés par d'autres services de la plateforme de gestion du cloud. Il s'agit notamment des services d'identité et d'accès, des services de nom de domaine et des services NTP. 

Figure 1. Services communs ICP

![Services communs ICP](vcsicp-icp-commonservices.svg)

### Services d'identité et d'accès
Dans le cadre de l'automatisation VCS, un annuaire Microsoft Active Directory (AD) est utilisé pour la gestion des identités. Une seule instance de serveur virtuel AD est déployée. vCenter est configuré pour utiliser l'authentification MS AD et ICP peut également être configuré pour l'authentification LDAP. 

###	Services de noms de domaine
Le déploiement VCS utilise les instances de serveur virtuel Microsoft Active Directory (AD) déployées en tant que serveurs DNS pour l'instance. Tous les composants déployés (vCenter, PSC, NSX, hôtes ESXi) sont configurés pour pointer vers l'annuaire MS AD comme serveur DNS par défaut.

###	Services NTP
Le déploiement VCS utilise les serveurs NTP de l'infrastructure IBM Cloud. Tous les composants déployés seront configurés pour utiliser ces serveurs NTP. Le fait que tous les composants de la conception utilisent les mêmes serveurs NTP est essentiel pour que les certificats et l'authentification MS AD puissent fonctionner correctement.

## Mise en réseau

### Mise en réseau NSX-V

L'architecture de NSX-V est telle qu'une plateforme NSX-V Manager est associée à une instance vCenter Server. NSX-V fournit des services de mise en réseau aux applications qui s'exécutent dans un environnement vSphere. 

En utilisant la mise en réseau NSX-V incluse dans le déploiement VCS, nous pouvons déployer ICP dans un réseau dissocié VXLAN. 

ICP est déployé avec la pile de mise en réseau Calico par défaut pour Kubernetes, ce qui fournit l'isolement réseau dans votre cluster.

Figure 2. ICP avec mise en réseau NSX-V

![ICP avec mise en réseau NSX-V](vcsicp-nsxv-networking.svg)

Pour plus d'informations, voir [Architecture de référence de la mise en réseau VCS pour IBM Cloud](../vcsnsxt/vcsnsxt-intro.html).

### Mise en réseau NSX-T

L'architecture de NSX-T est telle qu'une plateforme de mise en réseau pouvant se connecter à n'importe quel type d'application, reposant sur une machine virtuelle ou un conteneur, s'exécute dans ou en dehors d'un environnement vSphere. 

ICP fournit une option permettant de remplacer la mise en réseau Calico par une instance NSX-T, fournissant ainsi un emplacement unique pour la gestion de la mise en réseau et de la sécurité. 

Figure 3. ICP avec mise en réseau NSX-T

![ICP avec mise en réseau NSX-T](vcsicp-icp-nsxt-networking.svg)

### Liens connexes

* [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
