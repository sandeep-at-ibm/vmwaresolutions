---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Présentation de FortiGate Security Appliance on IBM Cloud

Le service FortiGate Security Appliance on {{site.data.keyword.cloud}} déploie une paire de dispositifs FortiGate Security Appliance (FSA) série 300 en mode haute disponibilité, qui fournissent des services de pare-feu, de routage, de conversion d'adresses réseau (NAT) et de réseau privé virtuel (VPN) afin de protéger tous les serveurs et machines virtuelles sur le réseau privé virtuel (VLAN) de vos instances.

Vous pouvez gérer ce service à l'aide du client Web FortiOS ou de l'interface de ligne de commande via SSH.

**Disponibilité** : ce service est disponible uniquement sur les instances qui sont déployées en version 1.8 ou dans des éditions ultérieures.

## Composants de FortiGate Security Appliance on IBM Cloud

Lorsque vous commandez le service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} pour votre instance, une paire à haute disponibilité de dispositifs FortiGate Security série 300 est déployée sur le VLAN public par défaut de l'instance ou du cluster d'origine. L'ensemble du trafic vers le VLAN public de votre instance est acheminé via le dispositif FortiGate Security Appliance.

**Remarque :** si vous commandez d'autres clusters, les VLAN publics pour ces derniers ne disposeront pas de la paire à haute disponibilité de dispositifs Security Appliances.

## Remarques relatives à l'installation du service FortiGate Security Appliance on IBM Cloud

Passez en revue les remarques suivantes avant d'installer le service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} :
* Vérifiez que le compte {{site.data.keyword.cloud_notm}} que vous utilisez dispose du droit **Pare-feu matériel**. Ce droit est nécessaire pour éditer ou afficher les paramètres et journaux de pare-feu du service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} de votre instance.
* Si vous voulez ajouter le service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} à une instance déployée, vérifiez qu'aucun autre pare-feu de l'infrastructure {{site.data.keyword.cloud_notm}} n'est déjà en place pour le réseau local virtuel (VLAN) de l'instance.
* L'installation du service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} ajoutera un nouveau réseau local virtuel (VLAN) public.
* Lors du déploiement du service, il est possible que votre instance ne puisse temporairement pas accéder à Internet.
* Une fois le service FortiGate Security Appliance (FSA) on {{site.data.keyword.cloud_notm}} correctement installé, vous pouvez gérer et configurer des règles de pare-feu pour le dispositif FSA à partir de la console FortiGate. Vous devez vous assurer que les règles de pare-feu de FortiGate Security Appliance (FSA) sont définies de manière à autoriser les communications HTTPS sortantes (port TCP 443) initiées par des composants de gestion, tels que la machine virtuelle IBM CloudDriver ou le gestionnaire virtuel Zerto, pour communiquer avec la base de données de gestion externe sur {{site.data.keyword.cloud_notm}} sur Internet. Les communications HTTPS sortantes (port TCP 443) proviennent de l'adresse IP publique des services de gestion VMware NSX Edge Services Gateway (ESG) de votre instance.
* Si vous déployez une paire de dispositifs FortiGate Security Appliance dans le cadre d'une nouvelle instance, ces dispositifs sont configurés de manière à n'autoriser que les communications sortantes requises depuis votre instance vers le réseau public et à refuser toutes les autres communications.
* Si vous déployez une paire de dispositifs FortiGate Security Appliance dans le cadre d'une instance existante, ces dispositifs sont configurés avec une règle explicite de manière à n'autoriser que les communications de gestion sortantes requises depuis votre instance vers le réseau public. De plus, les dispositifs sont configurés avec une règle supplémentaire pour autoriser toutes les autres communications de sorte que votre trafic d'application existant ne soit pas interrompu. Vous devez gérer la configuration du service FortiGate Security Appliance avec la plus grande attention de manière à n'autoriser que les communications nécessaires et à refuser toutes les autres communications.

## Remarques relatives au retrait du service FortiGate Security Appliance on IBM Cloud

Passez en revue les remarques suivantes avant de supprimer le service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} :
* La suppression du service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} supprime le réseau local virtuel (VLAN) public qui avait été ajouté.
* Lors de la suppression du service, il est possible que votre instance ne puisse temporairement pas accéder à Internet.
* Toutes les règles FortiGate d'autorisation, d'inspection, de blocage et de routage du trafic NAT sont supprimées en même temps que le service Fortinet. Si vous aviez des règles NAT, vous devez les reconfigurer.

## Liens connexes

* [Commande de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](fsa_ordering.html)
* [Gestion de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](managingfsa.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web Fortinet](https://www.fortinet.com/){:new_window}
* [Bibliothèque de documents Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
