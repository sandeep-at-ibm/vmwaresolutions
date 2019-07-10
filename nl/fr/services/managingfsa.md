---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: FortiGate Security console, FortiGate 300 console, login FortiGate console

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestion de FortiGate Security Appliance on IBM Cloud
{: #managingfsa}

Une fois le service FortiGate Security Appliance (FSA) on {{site.data.keyword.cloud}} correctement installé, vous pouvez gérer et configurer des règles de pare-feu pour le dispositif FSA à partir de la console FortiGate.

Vous devez vous assurer que les règles de pare-feu FSA sont définies de manière à autoriser les communications HTTPS sortantes (port TCP 443) initiées par des composants de gestion, tels que le gestionnaire virtuel Zerto, pour communiquer avec la base de données de gestion externe sur l'infrastructure {{site.data.keyword.cloud_notm}} via Internet. Les communications HTTPS sortantes (port TCP 443) proviennent de l'adresse IP publique des services de gestion VMware NSX Edge Services Gateway (ESG) de votre instance.
{:important}

## Accès à la console FortiGate série 300
{: #managingfsa-access-console}

Pour gérer le service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, vous devez accéder à la console FortiGate® série 300 de l'une des manières suivantes :
* Connectez-vous au client Web FortiOS à l'aide des données d'identification qui figurent sur la page des détails du service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}.
* Accédez à la console via une connexion SSH à l'aide des données d'identification qui figurent sur la page des détails du service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}.

Pour plus d'informations, voir[Commande, affichage et retrait de services pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Liens connexes
{: #managingfsa-related}

* [Présentation de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Site Web fortinet.com](https://www.fortinet.com/)
* [Bibliothèque de documents Fortinet](https://docs.fortinet.com/product/fortigate/6.2)
