---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vCenter Server NSX-T networking, networking components, networking NSX-T

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}

# Remarques relatives à la mise en réseau des instances vCenter Server with NSX-T
{: #vc_nsx-t_networkingonvcenterserver}

Passez en revue les informations suivantes pour obtenir des détails relatifs aux remarques et exigences concernant la mise en réseau de vos instances vCenter Server on {{site.data.keyword.cloud}} with NSX-T. Prenez soin de respecter les exigences de sorte que vos instances puissent fonctionner correctement.

## Composants de mise en réseau des instances vCenter Server with NSX-T
{: #vc_nsx-t_networkingonvcenterserver-networking-components}
{: faq}

Pour passer en revue les composants de mise en réseau inclus dans votre instance vCenter Server with NSX-T, voir [Spécifications techniques relatives aux instances vCenter Server with NSX-T](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_overview#vc_nsx-t_overview-specs).

## Remarques relatives aux pare-feu
{: #vc_nsx-t_networkingonvcenterserver-firewall-considerations}
{: faq}

Si vous utilisez des pare-feu, vous devez configurer des règles pour toutes les communications établies à partir de l'instance de serveur virtuel {{site.data.keyword.IBM}} CloudDriver et des machines virtuelles SDDC Manager. Ces règles doivent autoriser tous les protocoles à communiquer sur les adresses IP `10.0.0.0/8` et `161.26.0.0/16`. Ces types de pare-feu sont notamment les pare-feu DFW (Distributed Firewall) NSX ou les pare-feu Vyatta.

## Utilisation de NSX avec vos machines virtuelles
{: #vc_nsx-t_networkingonvcenterserver-using-nsx-with-vm}
{: faq}

Lors du déploiement d'une instance vCenter Server with NSX-T, VMware NSX est commandé, installé, mis sous licence et configuré dans votre instance. De même, NSX Manager, des contrôleurs NSX et une zone de transport NSX sont configurés et chaque serveur ESXi est configuré avec les composants NSX.

Une passerelle NSX Edge Services Gateway est également déployée pour être utilisée par votre machine virtuelle de charge de travail. Pour plus d'informations, voir [Configuration du réseau en vue d'utiliser la passerelle NSX ESG gérée par le client avec vos machines virtuelles](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_esg_config#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

## Remarques relatives à la modification de mots de passe pour des composants NSX
{: #vc_nsx-t_networkingonvcenterserver-change-nsx-component-password-considerations}
{: faq}

Passez en revue les remarques suivantes avant de modifier les mots de passe de NSX Manager, des contrôleurs NSX et de la passerelle NSX Edge :
* Ne modifiez pas le mot de passe de NSX Manager figurant sur la page **Récapitulatif** de l'instance dans la console {{site.data.keyword.vmwaresolutions_short}}.
* Ne modifiez pas les mots de passe des contrôleurs NSX. Pour savoir comment modifier les mots de passe des contrôleurs NSX, voir [Modification du mot de passe d'un contrôleur](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html){:external}.
* Ne modifiez pas le mot de passe et les paramètres SSH de la passerelle VMware NSX ESG (Edge Services Gateway) gérée par le client. Ne modifiez pas le mot de passe de la passerelle VMware NSX ESG (Edge Services Gateway) de gestion et du routeur logique distribué associé.

## Liens connexes
{: #vc_nsx-t_networkingonvcenterserver-related}

* [Présentation de NSX](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:external}
* [Passerelle NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:external}
* [Gestion des règles de conversion d'adresses réseau](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:external}
