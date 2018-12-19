---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Cas d'utilisation

## Migration de charge de travail VMware vers IBM Cloud

L'entreprise Acme Skateboards souhaite étendre de façon transparente son environnement VMware SDDC sur site dans une instance VCS sur {{site.data.keyword.cloud}}. Elle doit faire en sorte de rester opérationnelle et de réduire le plus possible ses temps d'indisponibilité. Reconfigurer ses applications pour qu'elles s'exécutent dans le cloud n'est pas une solution optimale.

Le service {{site.data.keyword.cloud_notm}} vCenter Server with Hybridity Bundle permet la création d'une connexion ininterrompue entre des instances VCS et un centre de données virtuel VMware sur site. 

Les composants VMware HCX, qui sont déployés en tant que machines virtuelles sur le site cible VCS, permettent d'établir une connexion avec les composants VMware HCX installés sur le site source local homologue. 

Figure 1. Service VMware Hybrid Cloud Extension
![Service VMware Hybrid Cloud Extension](vcsnsxt-hcx-1.svg)

L'interconnectivité à couplage lâche entre le site local et {{site.data.keyword.cloud_notm}} active des fonctionnalités telles que :
-	**Interconnectivité simple** – Des connexions de réseau logique sont facilement établies sur n'importe quelle connexion physique, y compris l'Internet public, le réseau privé virtuel ou Direct Link.
-	**Extension de couche 2** – Les réseaux locaux sont étendus au cloud, y compris les sous-réseaux locaux et l'adressage IP.
-	**Chiffrement** – Le trafic réseau est chiffré entre les deux sites. 
-	**Réseau optimisé** – Sélectionne la meilleure connexion et achemine efficacement la connexion de sorte que le trafic réseau soit déplacé le plus rapidement possible.
-	**Dédoublonnage de données** – Jusqu'à 50 % de réduction de trafic réseau peut être réalisé.
-	**Routage intelligent** – Lorsqu'une charge de travail est déplacée, le routage de proximité peut modifier le chemin réseau (c'est-à-dire la passerelle) de sorte que le trafic réseau utilise la passerelle de site cible et ne dessine pas une "courbe en épingle à cheveux" vers le site d'origine.
-	**Migration sans interruption** – Un système en cours d'exécution peut être déplacé vers (ou depuis) le cloud à l'aide de vMotion.
-	**Migration planifiée** – N'importe quel nombre de machines virtuelles peut être répliqué vers le site de destination, puis activé sur ce site à une heure précise afin de remplacer les systèmes qui s'exécutent sur le site d'origine.
-	**Migration de règles de sécurité** – Si NSX est utilisé sur site, toutes les règles de sécurité, tous les pare-feu, etc. sont déplacés en même temps que la charge de travail.

## Déploiement d'architecture hybride

L'entreprise Acme Skateboards souhaite déployer une architecture hybride sur {{site.data.keyword.cloud_notm}} composée de vCenter et d'{{site.data.keyword.cloud_notm}} Private (ICP) pour son parcours vers la modernisation de ses applications. Ses exigences sont les suivantes : exécuter ses bases de données sur des machines virtuelles, les applications et les interfaces Web dans des conteneurs, et utiliser un jeu commun d'outils pour la gestion du réseau et de la sécurité.

{{site.data.keyword.vmwaresolutions_short}} fournit l'automatisation du déploiement des composants de technologie VMware dans les {{site.data.keyword.CloudDataCents_notm}} situés dans le monde entier. L'architecture est composée d'une région de cloud et a la capacité de s'étendre dans d'autres régions de cloud situées dans une autre zone géographique et/ou dans un autre pod {{site.data.keyword.cloud_notm}} au sein du même centre de données.

Les produits ICP et Cloud Automation Manager (CAM) peuvent être déployés manuellement dans votre plateforme de virtualisation sur site, permettant ainsi la gestion du cloud à partir des emplacements locaux. Sinon, ICP et CAM sont offerts en tant qu'extension de service à un déploiement VCS nouveau ou existant, permettant ainsi la gestion du cloud à partir d'{{site.data.keyword.cloud_notm}}. 

Le diagramme ci-dessous représente ICP s'exécutant sur une instance VCS. NSX-V est configuré avec un commutateur/réseau VXLAN dédié, un routeur DLR et une passerelle ESG spécifiquement pour le réseau dissocié ICP. Le routage est configuré via la passerelle ESG pour accéder au réseau dissocié. 

A l'aide de l'automatisation d'{{site.data.keyword.cloud_notm}}, l'entreprise Acme Skateboards peut mettre à disposition une solution hybride comprenant VCS afin d'exécuter ses machines virtuelles de base de données et ICP sur VCS pour exécuter ses applications et des services Web frontaux dans des conteneurs. NSX lui fournit un jeu commun d'outils de gestion pour la mise en réseau et la sécurité dans le réseau dissocié.

Pour plus d'informations sur NSX-V, voir [Présentation de NSX-V](vcsnsxt-overview-ic4vnsxv.html). Pour plus d'informations sur l'offre VCS et ICP, voir [vCenter Server et {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html).

Figure 2. VCS avec ICP
![VCS avec ICP](vcsnsxt-nsxvhl.svg)

Cela crée une interconnectivité à couplage lâche entre le site local et {{site.data.keyword.cloud_notm}} et active des fonctionnalités telles que :
-	**Interconnectivité simple** – Des connexions de réseau logique sont facilement établies sur n'importe quelle connexion physique, y compris l'Internet public, le réseau privé virtuel ou Direct Link.
-	**Extension de couche 2** – Les réseaux locaux sont étendus au cloud, y compris les sous-réseaux locaux et l'adressage IP.
-	**Chiffrement** – Le trafic réseau est chiffré entre les deux sites. 
-	**Réseau optimisé** – Sélectionne la meilleure connexion et achemine efficacement la connexion de sorte que le trafic réseau soit déplacé le plus rapidement possible.
-	**Dédoublonnage de données** – Jusqu'à 50 % de réduction de trafic réseau peut être réalisé.
-	**Routage intelligent** – Lorsqu'une charge de travail est déplacée, le routage de proximité peut modifier le chemin réseau (c'est-à-dire la passerelle) de sorte que le trafic réseau utilise la passerelle de site cible et ne dessine pas une "courbe en épingle à cheveux" vers le site d'origine.
-	**Migration sans interruption** – Un système en cours d'exécution peut être déplacé vers (ou depuis) le cloud à l'aide de vMotion.
-	**Migration planifiée** – N'importe quel nombre de machines virtuelles peut être répliqué vers le site de destination, puis activé sur ce site à une heure précise afin de remplacer les systèmes qui s'exécutent sur le site d'origine.
-	**Migration de règles de sécurité** – Si NSX est utilisé sur site, toutes les règles de sécurité, tous les pare-feu, etc. sont déplacés en même temps que la charge de travail.

Grâce à cette solution, Acme Skateboards a pu faire migrer ses charges de travail VMware locales vers {{site.data.keyword.cloud_notm}} tout en respectant ses deux exigences, à savoir réduire le plus possible ses temps d'indisponibilité et ne pas avoir à reconfigurer les applications. Pour plus d'informations sur vCenter Server with Hybridity Bundle, voir [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).

### Liens connexes

* [Présentation de VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
