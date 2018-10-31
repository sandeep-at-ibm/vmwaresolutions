---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Présentation de F5 on IBM Cloud

Le service F5 on {{site.data.keyword.cloud}} (F5 BIG-IP® Virtual Edition) fournit des services intelligents d'équilibrage de charge L4-L7 et de gestion du trafic à l'échelle locale et globale, une protection maximale via pare-feu des applications Web et réseau et un accès sécurisé aux applications fédérées.

Vous pouvez installer plusieurs instances de ce service si besoin.

**Disponibilité :** ce service est disponible uniquement sur les instances déployées en version 1.9 ou dans des éditions ultérieures.

## Spécifications techniques relatives à F5 on IBM Cloud

Les composants suivants sont inclus avec le service F5 on {{site.data.keyword.cloud_notm}} :

### Machines virtuelles
* Deux machines virtuelles avec toutes les options disponibles.
* 2, 4 ou 8 UC virtuelles par machine virtuelle en fonction de l'option de l'octroi de licence
* 4, 8 ou 16 Go de mémoire RAM par machine virtuelle en fonction de l'option de l'octroi de licence

### Utilisation en réseau
* VXLAN (Private Virtual Extensible LAN) pour la synchronisation haute disponibilité.
* Accès à TMSH (Traffic Management Shell) et à la console de gestion via un réseau de gestion privé.

### Licences et frais
Des frais de licence sont appliqués pour chaque machine virtuelle à chaque cycle de facturation en fonction de l'option d'octroi de licence (Bien, Mieux ou Meilleur) et de la bande passante choisie.

**Important: ** vous ne pouvez pas modifier le niveau d'octroi de licence près installation du service. Pour modifier le niveau d'octroi de licence, vous devez supprimer le service existant, puis le réinstaller en sélectionnant une autre option d'octroi de licence.

## Remarques relatives à l'installation du service F5 on IBM Cloud

Avant d'installer le service F5 on {{site.data.keyword.cloud_notm}}, passez en revue les remarques suivantes.

En fonction du modèle de licence et de la bande passante que vous sélectionnez, deux machines virtuelles BIG-IP VE sont déployées avec la configuration suivante :

Tableau 1. Déploiements d'UC et de RAM selon la bande passante et le modèle de licence sélectionnés

| Bande passante maximale | Modèle de licence : Bien | Modèle de licence : Mieux | Modèle de licence : Meilleur |
|:------------------|:--------------------|:----------------------|:--------------------|
| 25 Mbit/s           | 2 UC virtuelles, 4 Go de RAM    | 4 UC virtuelles, 8 Go de RAM      | 8 UC virtuelles, 16 Go de RAM   |
| 200 Mbit/s          | 2 UC virtuelles, 4 Go de RAM    | 4 UC virtuelles, 8 Go de RAM      | 8 UC virtuelles, 16 Go de RAM   |
| 1 Gbit/s            | 2 UC virtuelles, 4 Go de RAM    | 4 UC virtuelles, 8 Go de RAM      | 8 UC virtuelles, 16 Go de RAM   |
| 3 Gbit/s            | 8 UC virtuelles, 16 Go de RAM   | 8 UC virtuelles, 16 Go de RAM     | 8 UC virtuelles, 16 Go de RAM   |
| 5 Gbit/s            | 8 UC virtuelles, 16 Go de RAM   | 8 UC virtuelles, 16 Go de RAM     | 8 UC virtuelles, 16 Go de RAM   |
| 10 Gbit/s           | 8 UC virtuelles, 16 Go de RAM   | 8 UC virtuelles, 16 Go de RAM     | 8 UC virtuelles, 16 Go de RAM   |

**Remarques :**

* F5 BIG–IP limite le débit du dispositif en fonction de la bande passante maximale sélectionnée. Etant donnée que de nombreux facteurs affectent les performances réseau, toutes les configurations et topologies ne sont pas à même d'offrir la bande passante maximale sélectionnée.
* La paire de machines virtuelles BIG-IP VE à haute disponibilité ne sera déployée que dans le cluster par défaut.

  De plus, 100% de l'UC et de la RAM des deux machines virtuelles BIG-IP VE est également réservé car ces machines virtuelles se trouvent dans le plan de données des communications réseau et il est essentiel que des ressources soient disponibles pour ces machines.

  Pour calculer la réservation d'UC et de RAM pour une seule machine virtuelle BIG-IP VE, utilisez la formule suivante :

  `réservation d'UC = vitesse d'UC du serveur ESXi * nombre d'UC virtuelles` (voir Tableau 1)

  `réservation de RAM = taille de la RAM` (voir Tableau 1)

### Remarques relatives à la planification
Vous devez respecter les exigences suivantes afin d'éviter les incidents avec le service F5 on {{site.data.keyword.cloud_notm}} :
* Au moins deux serveurs ESXi actifs sont disponibles pour les deux machines virtuelles BIG-IP VE à déployer avec la règle d'anti-affinité de conservation des machines virtuelles sur des serveurs distincts.
* Les deux serveurs ESXi actifs disposent de suffisamment de ressources pour héberger une machine virtuelle BIG-IP VE sur chaque serveur ESXi avec une réservation de 100 % d'UC et de RAM.
* VMware vSphere HA dispose de suffisamment de ressources pour héberger les deux machines virtuelles BIG-IP avec 100 % d'UC et de RAM.

Compte tenu de ces exigences, vous devez prévoir l'espace requis pour F5 on {{site.data.keyword.cloud_notm}}. Au besoin, avant de commander F5 on {{site.data.keyword.cloud_notm}}, ajoutez 1 à 2 serveurs ESXi à votre instance et/ou réduisez la réservation d'UC de vSphere HA pour basculement.

## Exemple de commande de F5 on IBM Cloud

Vous commandez une instance VMware vCenter Server **Petite** avec 2 serveurs ESXI et la configuration suivante : seize coeurs à 2,10 GHz avec chacun 128 Go de RAM. Pour F5 on {{site.data.keyword.cloud_notm}}, vous sélectionnez le modèle de licence **Meilleur** et une valeur de 5 Gbit/s pour la **bande passante maximale**.

Dans ce cas, une unique machine virtuelle BIG-IP requiert, sur chaque serveur :
* 2,1 GHz * 8 UC virtuelles = 16,8 GHz d'UC et
* 16 Go de RAM

Au total, 33,6 GHz d'UC et 32 Go de RAM pour les deux machines virtuelles BIG-IP.

Chaque serveur ESXi a une capacité de 16 coeurs * 2,1 GHz = 33,6 GHz, de sorte que nous respectons les deux exigences si les deux serveurs sont actifs et qu'au moins 16,8 GHz d'UC et 16 Go de RAM sont disponibles sur chaque serveur.

Toutefois, par défaut, vSphere HA réserve 50 % d'UC et de mémoire RAM pour le basculement sur les instances vCenter Server initialement déployées avec 2 serveurs ESXi. Pour cet exemple, la disponibilité est la suivante :

`50 % de 2 * 16 coeurs * 2,1 GHz = 33,6 GHz disponibles`

Etant donné que d'autres charges de travail figureront sur les serveurs ESXi (par exemple, VMware vCenter Server, VMware NSX Controller, VMware NSX Edge), en utilisant ces ressources, nous ne respectons pas la troisième exigence puisque nous avons besoin d'une UC cadencée à 33,6 GHz et de 32 Go de mémoire RAM pour les deux machines virtuelles BIG-IP.

Dans ce cas, l'installation de F5 on {{site.data.keyword.cloud_notm}} risque d'échouer, sauf si au moins un serveur ESXi est ajouté à l'environnement et que les réservations de vSphere HA pour basculement sont mises à jour de manière à garantir un nombre suffisant de ressources disponibles pour les deux machines virtuelles BIG-IP VE. Si des ressources supplémentaires sont nécessaires pour exécuter le service F5 on {{site.data.keyword.cloud_notm}}, vous pouvez ajouter d'autres serveurs ESXi avant d'installer F5 on {{site.data.keyword.cloud_notm}}.

## Remarques relatives au retrait de F5 on IBM Cloud

Avant de supprimer le service F5 on {{site.data.keyword.cloud_notm}}, vérifiez que la configuration BIG-IP VE existante a été correctement supprimée. Plus précisément, que le trafic réseau a été routé de manière à contourner BIG-IP VE au lieu de traverser BIG-IP VE. Sinon, le trafic de données existant à partir de votre environnement risque d'être impacté.

### Liens connexes

* [Commande de F5 on {{site.data.keyword.cloud_notm}}](f5_ordering.html)
* [Gestion de F5 on {{site.data.keyword.cloud_notm}}](managing_f5.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web de F5](https://f5.com/){:new_window}
