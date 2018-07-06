---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Présentation de FortiGate Virtual Appliance on IBM Cloud

Le service FortiGate Virtual Appliance on {{site.data.keyword.cloud}} déploie dans votre environnement une paire de dispositifs FortiGate Virtual Appliance qui vous permettent de réduire les risques en implémentant des contrôles de sécurité critiques au sein de votre infrastructure virtuelle.

Vous pouvez installer plusieurs instances de ce service si besoin. Vous pouvez gérer ce service à l'aide du client Web FortiOS ou de l'interface de ligne de commande via SSH.

**Disponibilité** : Ce service est disponible uniquement pour les instances déployées en version 2.0 ou dans des éditions ultérieures.

## Composants de FortiGate Virtual Appliance on IBM Cloud

Lorsque vous commandez le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, une paire de dispositifs FortiGate Virtual Appliance est déployée avec les éléments suivants :
* Une interface réseau configurée pour le réseau de gestion. 
* Neuf interfaces réseau supplémentaires que vous pouvez configurer pour protéger le trafic de données, si besoin.

Les dispositifs FortiGate Virtual Appliance ne sont pas préconfigurés en tant que paire de dispositifs à haute disponibilité. Après le déploiement, vous pouvez configurer des paramètres à haute disponibilité, à savoir Virtual Router Redundancy Protocol (VRRP) et FortiGate Cluster Protocol (FGCP), en fonction de vos besoins.

## Remarques relatives à l'installation du service FortiGate Virtual Appliance on IBM Cloud

Passez en revue les remarques suivantes avant d'installer le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} :
* Les machines virtuelles FortiGate ne seront déployées que dans le cluster par défaut.
* Selon le modèle de licence et la taille du déploiement sélectionnés, les deux machines virtuelles FortiGate sont déployées dans l'une des configurations suivantes :
    * Petite (2 UC virtuelles/4 Go de RAM)
    * Moyenne (4 UC virtuelles/6 Go de RAM)
    * Grande (8 UC virtuelles/12 Go de RAM)

  De plus, 100 % de l'UC et de la mémoire RAM des deux machines virtuelles FortiGate sont également réservés car ces machines virtuelles se trouvent dans le plan de données des
  communications réseau et il est essentiel que des ressources soient disponibles pour ces machines.

  Pour calculer la réservation d'UC et de RAM pour une seule machine virtuelle FortiGate VE, utilisez la formule suivante :
   * `réservation d'UC = vitesse d'UC du serveur ESXi * nombre d'UC virtuelles`
   * `réservation de RAM = taille de la RAM`
* Lorsque vous déployez une paire à haute disponibilité de dispositifs FortiGate Virtual Appliance dans votre instance, des règles de pare-feu et SNAT sont définies sur la passerelle NSX ESG (Edge Services Gateway) de gestion ainsi que des routes statiques sur le service FortiGate Virtual Appliance afin de permettre les communications HTTPS sortantes depuis votre instance vers le réseau public pour l'activation des licences et l'acquisition des règles de sécurité et des contenus les plus récents.
* Vous ne pouvez pas modifier le niveau de licence après installation du service. Pour modifier le niveau de licence, vous devez supprimer le service existant, puis le réinstaller en sélectionnant une autre option de licence.
* Vous devez respecter les exigences suivantes afin d'éviter les incidents avec le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} :
   * Au moins deux serveurs ESXi actifs sont disponibles pour les deux machines virtuelles FortiGate à déployer avec la règle d'anti-affinité de conservation des machines virtuelles sur des serveurs distincts.
   * Les deux serveurs ESXi actifs disposent de suffisamment de ressources pour héberger une machine virtuelle FortiGate sur chaque serveur ESXi avec une réservation de 100% d'UC et de RAM.
   * VMware vSphere HA dispose de suffisamment de ressources pour héberger les deux machines virtuelles FortiGate avec 100% d'UC et de RAM.

  Compte tenu de ces exigences, vous devez soigneusement prévoir l'espace requis pour le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}. Au besoin, avant de commander le dispositif FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, ajoutez 1 à 2 serveurs ESXi à votre instance et/ou réduisez la réservation d'UC de vSphere HA pour basculement. 

## Exemple de commande de dispositif FortiGate Virtual Appliance on IBM Cloud

Vous commandez une instance VMware vCenter Server **Petite** avec 2 serveurs ESXi et la configuration suivante : 16 coeurs à 2,10 GHz avec chacun 128 Go de RAM. Pour le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, vous sélectionnez **Grande** (8 UC virtuelles/12 Go de RAM) comme taille de déploiement et n'importe quel modèle de licence d'abonnement.

Dans ce cas, une seule machine virtuelle FortiGate par serveur est requise :
* 2,1 GHz * 8 UC virtuelles = 16,8 GHz d'UC et
* 12 Go de RAM

Au total, 33,6 GHz d'UC et 24 Go de RAM pour deux machines virtuelles FortiGate.

Chaque serveur ESXi a une capacité de 16 coeurs * 2,1 GHz = 33,6 GHz, de sorte que nous respectons les deux exigences si les deux serveurs sont actifs et qu'au moins 16,8 GHz d'UC et 12 Go de RAM sont disponibles sur chaque serveur.

vSphere HA réserve toutefois par défaut 50% d'UC et de RAM pour le basculement sur les instances vCenter Server initialement déployées avec 2 serveurs ESXi, de sorte que nous avons uniquement :

`50% de 2 * 16 coeurs * 2,1 GHz = 33,6 GHz disponibles`

Etant donné que d'autres charges de travail se trouveront sur les serveurs ESXi (par exemple, IBM CloudDriver, VMware NSX Controller ou VMware NSX Edge), en utilisant ces ressources, nous ne respectons pas la troisième exigence. En effet, nous avons besoin de 33,6 GHz d'UC et de 24 Go de mémoire RAM pour les deux machines virtuelles FortiGate. 

Dans ce cas, l'installation de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} risque d'échouer, sauf si au moins un serveur ESXi est ajouté à l'environnement et que les réservations de vSphere HA pour basculement sont mises à jour de manière à garantir un nombre suffisant de ressources disponibles pour les deux machines virtuelles FortiGate. 

Si des ressources supplémentaires sont nécessaires pour exécuter le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, vous pouvez ajouter d'autres serveurs ESXi avant d'installer le service.

## Remarques relatives au retrait du service FortiGate Virtual Appliance on IBM Cloud

Avant de retirer le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, vérifiez que la configuration des dispositifs FortiGate Virtual Appliance existants a été correctement retirée. Plus précisément, que le trafic réseau a été routé de manière à contourner les dispositifs FortiGate Virtual Appliance au lieu de les traverser. Sinon, le trafic de données existant au sein de votre environnement risque d'être impacté.

## Liens connexes

* [Commande de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](fortinetvm_ordering.html)
* [Gestion de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web Fortinet](https://www.fortinet.com/){:new_window}
* [Bibliothèque de documents Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
