---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations}

Le service FortiGate Security Appliance on {{site.data.keyword.cloud}} déploie une paire de dispositifs FortiGate Security Appliance (FSA) série 300 en mode haute disponibilité, qui fournissent des services de pare-feu, de routage, de conversion d'adresses réseau (NAT) et de réseau privé virtuel (VPN) afin de protéger tous les serveurs et machines virtuelles sur le réseau local virtuel (VLAN) de vos instances.

Vous pouvez gérer ce service à l'aide du client Web FortiOS ou de l'interface de ligne de commande via SSH.

Ce service est disponible uniquement sur les instances déployées en version 1.8 ou dans des éditions ultérieures.
{:note}

## Spécifications techniques relatives à FortiGate Security Appliance on IBM Cloud
{: #technical-specifications-for-fortigate-security-appliance-on-ibm-cloud}

Les composants suivants sont commandés et inclus dans le service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} :

### Matériel
{: #fsa_considerations-hardware}

Dispositif FortiGate Security Appliance série 300

### Haute disponibilité
{: #fsa_considerations-ha}

Deux dispositifs sont déployés dans une configuration active-passive

### Utilisation en réseau
{: #fsa_considerations-networking}

* Liaison Dual 1 GbE sur les réseaux en amont et en aval
* Un nouveau VLAN public {{site.data.keyword.cloud_notm}} en amont
* Un VLAN public {{site.data.keyword.cloud_notm}} en aval existant

## Considérations à prendre en compte lorsque vous installez FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-install}

Passez en revue les remarques suivantes avant d'installer le service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} :
* Vérifiez que le compte {{site.data.keyword.cloud_notm}} que vous utilisez dispose du droit **Pare-feu matériel**. Ce droit est nécessaire pour éditer ou afficher les paramètres et journaux de pare-feu du service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} de votre instance.
* Si vous voulez ajouter le service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} à une instance déployée, vérifiez qu'aucun autre pare-feu de l'infrastructure {{site.data.keyword.cloud_notm}} n'est déjà en place pour le VLAN public de l'instance.
* L'installation du service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} ajoute un nouveau VLAN public.
* Lors du déploiement du service, il est possible que votre instance ne puisse temporairement pas accéder à Internet.
* Une fois le service FortiGate Security Appliance (FSA) on {{site.data.keyword.cloud_notm}} correctement installé, vous pouvez gérer et configurer des règles de pare-feu pour le dispositif FSA à partir de la console FortiGate. Vous devez vous assurer que les règles de pare-feu FSA sont définies de sorte à autoriser les communications HTTPS sortantes (port TCP 443) initiées par des composants de gestion tels le gestionnaire virtuel Zerto pour communiquer avec la base de données de gestion externe sur {{site.data.keyword.cloud_notm}} via Internet. Les communications HTTPS sortantes (port TCP 443) proviennent de l'adresse IP publique des services de gestion VMware NSX Edge Services Gateway (ESG) de votre instance.
* Vous devez gérer la configuration du service FortiGate Security Appliance avec la plus grande attention de manière à n'autoriser que les communications nécessaires et à refuser toutes les autres communications.
* Si vous commandez d'autres clusters, les VLAN publics pour ces clusters nouvellement ajoutés ne disposeront pas de la paire à haute disponibilité de dispositifs Security Appliance.

## Considérations à prendre en compte lorsque vous retirez FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-remove}

Passez en revue les remarques suivantes avant de supprimer le service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} :
* La suppression du service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} supprime le VLAN public qui avait été ajouté.
* Lors de la suppression du service, il est possible que votre instance ne puisse temporairement pas accéder à Internet.
* Toutes les règles FortiGate d'autorisation, d'inspection, de blocage et de routage du trafic NAT sont supprimées en même temps que le service Fortinet. Si vous aviez des règles NAT, vous devez les reconfigurer.

## Liens connexes
{: #fsa_considerations-related}

* [Commande de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [Gestion de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfsa)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Site Web Fortinet](https://www.fortinet.com/){:new_window}
* [Bibliothèque de documents Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
