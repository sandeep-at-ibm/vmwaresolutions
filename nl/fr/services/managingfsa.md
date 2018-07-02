---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# Gestion de FortiGate Security Appliance on IBM Cloud

Une fois le service FortiGate Security Appliance (FSA) on {{site.data.keyword.cloud_notm}} correctement installé, vous pouvez gérer et configurer des règles de pare-feu pour le dispositif FSA à partir de la console FortiGate.

**Important** : vous devez vous assurer que les règles de pare-feu de FortiGate Security Appliance (FSA) sont définies de manière à autoriser les communications HTTPS sortantes (port TCP 443) initiées par des composants de gestion, tels que la machine virtuelle IBM CloudDriver ou le gestionnaire virtuel Zerto, à communiquer avec la base de données de gestion externe sur l'infrastructure IBM Cloud via Internet. Les communications HTTPS sortantes (port TCP 443) proviennent de l'adresse IP publique des services de gestion VMware NSX Edge Services Gateway (ESG) de votre instance.

## Accès à la console FortiGate série 300

Pour gérer le service FortiGate Security Appliance on {{site.data.keyword.cloud}}, vous devez accéder à la console FortiGate® série 300 de l'une des manières suivantes :
* Connectez-vous au client Web FortiOS à l'aide des données d'identification qui figurent sur la page des détails du service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}.
* Accédez à la console via une connexion SSH à l'aide des données d'identification qui figurent sur la page des détails du service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}.

Pour plus d'informations, voir les rubriques suivantes :
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html)

## Liens connexes

* [Présentation de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](fsa_considerations.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web fortinet.com](https://www.fortinet.com/)
* [Documentation technique Fortinet](http://docs.fortinet.com/fortigate/admin-guides)
