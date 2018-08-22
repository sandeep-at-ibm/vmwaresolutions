---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-24"

---

# Remarques relatives à la mise en réseau des instances Cloud Foundation

Passez en revue les informations suivantes pour des détails relatifs aux remarques et exigences concernant la mise en réseau de vos instances Cloud Foundation. Prenez soin de respecter les exigences de sorte que vos instances puissent fonctionner correctement.

## Composants de mise en réseau pour les instances Cloud Foundation

Pour passer en revue les composants de mise en réseau inclus dans votre instance Cloud Foundation, voir [Spécifications techniques relatives aux instances Cloud Foundation](sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances). 

## Remarques relatives au pare-feu NSX

Si vous utilisez des pare-feu DFW NSX, vous devez configurer des règles pour toutes les communications établies à partir de l'instance de serveur virtuel {{site.data.keyword.IBM}} CloudDriver et des machines virtuelles SDDC Manager de manière à autoriser tous les protocoles à communiquer sur les adresses IP `10.0.0.0/8` et `161.26.0.0/16`.

## Utilisation de VMware NSX avec vos machines virtuelles

Lors du déploiement d'une instance Cloud Foundation, VMware NSX est commandé, installé, mis sous licence et configuré dans votre instance. De même, NSX Manager, des contrôleurs NSX et la zone de transport NSX sont configurés et chaque serveur ESXi est configuré avec les composants NSX.

Cependant, si vos machines virtuelles de charge de travail ont besoin de communiquer entre elles eet d'accéder à Internet, c'est à vous de configurer NSX pour que vos machines virtuelles l'utilisent.

Pour plus d'informations sur la configuration de NSX :
* Pour une instance Cloud Foundation principale (unique), voir [Configuration de NSX pour des machines virtuelles de charge de travail sur VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/).
* Pour une instance Cloud Foundation multisite, voir [Connexion sécurisée à vos charges de travail VMware privées dans {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html).

## Remarques relatives à la modification de mots de passe pour des composants NSX

Passez en revue les remarques suivantes avant de modifier les mots de passe de NSX Manager, des contrôleurs NSX et de NSX Edge :
* Ne modifiez pas le mot de passe de NSX Manager. Ce mot de passe figure sur la page **Récapitulatif** de l'instance dans la console {{site.data.keyword.vmwaresolutions_short}}.
* Ne modifiez pas les mots de passe des contrôleurs NSX. Pour savoir comment modifier les mots de passe des contrôleurs NSX, voir [Modification du mot de passe d'un contrôleur](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html).
* Ne modifiez pas le mot de passe de la passerelle de services de gestion VMware NSX Edge Services Gateway (ESG).

### Liens connexes

* [Présentation de NSX](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [Passerelle NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [Gestion des règles de conversion d'adresses réseau](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
