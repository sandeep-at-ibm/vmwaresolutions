---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmware-solutions


---

# Graphique de comparaison des offres
{: #inst_comp_chart}

Passez en revue le graphique suivant pour comprendre les différentes fonctions prises en charge pour les instances VMware vCenter Server, les instances VMware vCenter Server with Hybridity Bundle et les clusters VMware vSphere.

Tableau 1. Fonctions prises en charge pour les instances vCenter Server et vCenter Server with Hybridity Bundle et les clusters vSphere

| Fonction | vCenter Server | vCenter Server with Hybridity | VMware vSphere |
|:--- |:--- |:--- |:--- |
| Optimisée par l'automatisation avancée {{site.data.keyword.IBM}} <sup>1</sup> | Oui | Oui | Non. Auto générée et configurée |
| Options de stockage | Stockage vSAN ou NFS (niveau fichier partagé) | vSAN ou NFS <sup>2</sup> | vSAN ou NFS |
| Nombre de serveurs ESXi dans le cluster initial | 4 pour vSAN et 2 au minimum (3 recommandé) pour NFS | 4 | 1 pour mise à l'échelle d'un cluster existant, 4 pour un nouveau cluster vSAN et 3 au minimum pour un nouveau cluster avec NFS |
| Nombre maximal de serveurs ESXi <sup>3</sup> | 59 par cluster | 59 par cluster | 60 par cluster |
| Déploiement multisite automatisé par le cloud |Pris en charge pour les nouvelles instances déployées dans la version 2.0 ou ultérieure | Pris en charge | Pris en charge. Configuration automatisée non incluse |
| Ajout de serveurs ESXi | Pris en charge | Pris en charge | Pris en charge. Configuration automatisée non incluse |
| Suppression de serveurs ESXi | Pris en charge | Pris en charge | Pris en charge. Configuration automatisée non incluse |
| Prise en charge de multiples clusters | Le nombre maximal dépend des instructions de dimensionnement de VMware | Le nombre maximal dépend des instructions de dimensionnement de VMware | Pris en charge. Configuration automatisée non incluse |
| Mise à jour et application de correctif de la pile VMware gérées par le client | Mises à jour gérées par le client :<br/>outils VMware natifs (VMware Update Manager) | Mises à jour gérées par le client :<br/>outils VMware natifs (VMware Update Manager) | Mises à jour gérées par le client :<br/>outils VMware natifs (VMware Update Manager) |
| Sauvegarde et restauration | Utilisation manuelle d'IBM Spectrum Protect Plus ou de Veeam | Utilisation manuelle d'IBM Spectrum Protect Plus ou de Veeam | Solution de sauvegarde et de restauration non incluse |
| Mise en réseau définie par logiciel (SDN) | NSX Base, Advanced ou Enterprise | NSX Advanced ou Enterprise | NSX Standard, Base ou Enterprise. Configuration automatisée non incluse |
| BYOL pour vSphere et vSAN | Intégralement pris en charge par cluster | Non pris en charge | Pris en charge |
| BYOL pour vCenter et NSX | Intégralement pris en charge par instance | Non pris en charge | Pris en charge |
| Options de mise à niveau de licence NSX | Mise à niveau disponible depuis NSX Base vers Advanced ou Enterprise et depuis NSX Advanced vers Enterprise La mise à niveau vers l'instance vCenter Server with Hybridity Bundle est disponible. | Mise à niveau disponible depuis NSX Advanced vers Enterprise  | Aucun |
| Editions de licence vSAN | vSAN Advanced ou Enterprise | vSAN Advanced ou Enterprise | vSAN Advanced ou Enterprise  |
| Services complémentaires | Pris en charge, sans inclure le service HCX on {{site.data.keyword.cloud_notm}}. La mise à niveau vers l'instance vCenter Server with Hybridity Bundle est disponible. | Pris en charge, avec le service HCX on {{site.data.keyword.cloud_notm}} inclus. | Non pris en charge par l'automatisation de cette solution, mais vous pouvez fournir et installer vos propres logiciels. |

## Remarques
{: #inst_comp_chart-notes}

<sup>1</sup> Conformément à une conception validée et avec une vérification durant le déploiement.

<sup>2</sup> vSAN uniquement pour les nouvelles instances et les nouveaux clusters vCenter Server with Hybridity. Après le déploiement, vous pouvez ajouter du stockage NFS.

<sup>3</sup> Vous pouvez augmenter le nombre de serveurs ESXi dans un cluster vSAN et le porter à un maximum de 64. Pour plus d'informations, voir _Combien de serveurs ESXi puis-je ajouter à un cluster ?_ dans la [Foire aux questions sur les serveurs ESXi](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi).

## Liens connexes
{: #inst_comp_chart-related}

* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Présentation de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Présentation de vCenter Server Hybridity](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [Présentation de VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)
* [Nomenclature de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Nomenclature de VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
