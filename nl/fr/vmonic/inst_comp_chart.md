---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-31"

---

# Graphique de comparison des offres

Passez en revue le graphique suivant pour comprendre les différentes fonctions prises en charge pour les instances VMware Cloud Foundation, les instances VMware vCenter Server, les instances VMware vCenter Server with Hybridity Bundle et les clusters VMware vSphere.

Tableau 1. Fonctions prises en charge pour les instances Cloud Foundation, vCenter Server et vCenter Server with Hybridity Bundle et les clusters vSphere

| Fonction                          | Cloud Foundation    | vCenter Server | vCenter Server with Hybridity | VMware vSphere |
|:----------------------------------|:--------------------|:---------------|:-------------------------|:-------------- |
| Optimisée par l'automatisation avancée {{site.data.keyword.IBM}} <sup>1</sup> | Oui | Oui | Oui | Non. Auto générée et configurée |
| Options de stockage        | vSAN                | Stockage vSAN ou de niveau fichier partagé (NFS) | vSAN | Stockage vSAN ou de niveau fichier partagé (NFS) |
| Nombre de serveurs ESXi dans le cluster initial | 4 | 4 pour vSAN et 2 au minimum (3 vivement recommandé) pour NFS | 4 | 1 pour mise à l'échelle d'un cluster existant, 4 pour un nouveau cluster vSAN et 3 au minimum pour un nouveau cluster avec NFS |
| Nombre maximal de serveurs ESXi <sup>2</sup> | 32 par cluster      | 59 par cluster     | 59 par cluster | 60 par cluster     |
| Déploiement multisite automatisé par le cloud | Pris en charge pour les nouvelles instances déployées en version 2.0 ou ultérieure | Pris en charge pour les nouvelles instances déployées en version 2.0 ou ultérieure | Pris en charge | Pris en charge. Configuration automatisée non incluse |
| Ajout de serveurs ESXi              | Pris en charge           | Pris en charge | Pris en charge | Pris en charge. Configuration automatisée non incluse |
| Suppression de serveurs ESXi           | Pris en charge           | Pris en charge | Pris en charge | Pris en charge. Configuration automatisée non incluse |
| Prise en charge de multiples clusters         | 5 clusters | 10 clusters | 10 clusters | Pris en charge. Configuration automatisée non incluse |
| Mise à jour et application de correctif de la pile VMware gérées par le client | Mises à jour VMware | Non inclus | Non inclus | Non inclus |
| Sauvegarde et restauration            | Utilisation manuelle d'IBM Spectrum Protect Plus ou de Veeam | Utilisation manuelle d'IBM Spectrum Protect Plus ou de Veeam | Utilisation manuelle d'IBM Spectrum Protect Plus ou de Veeam | Solution de sauvegarde et de restauration non incluse |
| Mise en réseau définie par logiciel (SDN)   | NSX Enterprise   | NSX Base, Advanced ou Enterprise | NSX Advanced ou Enterprise | NSX Standard, Base ou Enterprise. Configuration automatisée non incluse |
| BYOL pour vSphere et vSAN | Intégralement pris en charge par cluster   | Intégralement pris en charge par cluster     | Non pris en charge | Pris en charge |
| BYOL pour vCenter et NSX | Intégralement pris en charge par instance   | Intégralement pris en charge par instance     | Non pris en charge | Pris en charge |
| Options de mise à niveau de licence NSX           | Aucun   | Mise à niveau disponible depuis NSX Base vers Advanced ou Enterprise et depuis NSX Advanced vers Enterprise La mise à niveau vers l'instance vCenter Server with Hybridity Bundle est disponible. | Mise à niveau disponible depuis NSX Advanced vers Enterprise  | Aucun |
| Editions de licence vSAN         | vSAN Advanced ou Enterprise  | vSAN Advanced ou Enterprise  | vSAN Advanced ou Enterprise | vSAN Advanced ou Enterprise  |
| Services complémentaires               | Pris en charge, sans inclure le service HCX on {{site.data.keyword.cloud_notm}}.  | Pris en charge, sans inclure le service HCX on {{site.data.keyword.cloud_notm}}. La mise à niveau vers l'instance vCenter Server with Hybridity Bundle est disponible. | Pris en charge, avec le service HCX on {{site.data.keyword.cloud_notm}} inclus. | Non pris en charge par l'automatisation de cette solution, mais vous pouvez fournir et installer vos propres logiciels. |

**Remarques** :

<sup>1</sup> Conformément à une conception validée et avec une vérification durant le déploiement.

<sup>2</sup> Vous pouvez augmenter le nombre de serveurs ESXi dans un cluster vSAN et le porter à un maximum de 64. Pour plus d'informations, voir _Combien de serveurs ESXi puis-je ajouter à un cluster ?_ dans la [Foire aux questions sur les serveurs ESXi](faq_esxi.html).

### Liens connexes

* [Foire aux questions](faq.html)
* [Présentation de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Présentation de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Présentation de vCenter Server Hybridity](../vcenter/vc_hybrid_overview.html)
* [Présentation de Vmware vSphere](../vsphere/vs_vsphereclusteroverview.html)
* [Nomenclature de Cloud Foundation](../sddc/sd_bom.html)
* [Nomenclature de vCenter Server](../vcenter/vc_bom.html)
* [Nomenclature de Vmware vSphere](../vsphere/vs_bom.html)
