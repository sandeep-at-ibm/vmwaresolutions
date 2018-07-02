---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# Commande de FortiGate Virtual Appliance on IBM Cloud

Vous pouvez commander le service FortiGate Virtual Appliance on {{site.data.keyword.cloud}} lors de la commande d'une nouvelle instance avec le service inclus ou vous pouvez ajouter le service à votre instance existante. 

## Commande de FortiGate Virtual Appliance on IBM Cloud pour une nouvelle instance

Vous pouvez commander une nouvelle instance avec FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} à l'aide de l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_full}}, lorsque vous commandez une nouvelle instance, sélectionnez **FortiGate Virtual Appliance on IBM Cloud** dans la section **Services**. 
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **FortiGate Virtual Appliance on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une nouvelle instance**.

## Commande de FortiGate Virtual Appliance on IBM Cloud pour une instance existante

Vous pouvez ajouter le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} dans une instance existante à l'aide de l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter un service**.
* Depuis le catalogue {{site.data.keyword.cloud_notm}}, sélectionnez **FortiGate Virtual Appliance on IBM Cloud**, spécifiez les paramètres de service et sélectionnez **Ajouter à une instance existante**.

## Configuration du service FortiGate Virtual Appliance on IBM Cloud

Lorsque vous commandez le service, indiquez les paramètres suivants :

### Nom

Entrez le nom du service.

### Taille de déploiement

IBM Cloud fournit les options de taille de déploiement suivantes :
- **Petite (2 UC virtuelles/4 Go de RAM)**
- **Moyenne (4 UC virtuelles/6 Go de RAM)**
- **Grande (8 UC virtuelles/12 Go de RAM)**

### Modèle de licence

Le modèle de licence pour le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} propose les options suivantes :
<dl class="dl">
        <dt class="dt dlterm">Pare-feu standard</dt>
        <dd class="dd">Cette offre groupée inclut Stateful Packet Inspection, VLAN Protection and Advanced Logging, Ingress/Egress Firewall Rules, SSL/IPSec VPN Termination et le support 24 heures sur 24, 7 jours sur 7. </dd>
        <dt class="dt dlterm">Pare-feu standard + UTM</dt>
        <dd class="dd">Cette offre groupée inclut tous les services de pare-feu standard en plus de IPS NGFW et filtrage Web, Antivirus et antispam, Réputation de l'adresse IP et du domaine et les services de sécurité FortiGate principaux. </dd>
        <dt class="dt dlterm">Pare-feu standard + Enterprise</dt>
        <dd class="dd">Cette offre groupée inclut tous les services UTM et de pare-feu standard en plus de FortiSandbox Cloud et Mobile Security.</dd>
</dl>

**Important** : vous ne pouvez pas modifier le modèle de licence après l'installation du service. Pour modifier le modèle de licence, vous devez retirer le service existant, puis le réinstaller en sélectionnant une autre option de licence.

## Liens connexes

* [Présentation de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](fortinetvm_considerations.html)
* [Gestion de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web Fortinet](https://www.fortinet.com/){:new_window}
* [Bibliothèque de documents Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
