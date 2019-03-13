---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Résolution des vulnérabilités Spectre et Meltdown
{: #trbl_fix_spectre}

Pour résoudre les vulnérabilités Spectre et Meltdown, vous devez appliquer un certain nombre de modules de correction dans un ordre précis.

## Mise à jour du microprogramme
{: #trbl_fix_spectre-firmware-update}

Pour les informations les plus récentes concernant la mise à jour du microprogramme, voir [Sécurisation contre les plus récentes vulnérabilité en matière de sécurité](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/).

## Mise à jour d'instances déployées en version 2.0 ou ultérieure
{: #trbl_fix_spectre-instance2.0-update}

Les instances en version 2.0 ou ultérieure sont été déployées avec VMware vSphere 6.5 et VMware vCenter Server 6.5. Ces deux composants logiciels nécessitent l'application de modules de correction.

### Instances vCenter Server déployées dans la version 2.0 ou ultérieure
{: #trbl_fix_spectre-vcs2.0}

#### Pour VMware vSphere 6.5
{: #trbl_fix_spectre-vcs2.0-vsphere}

* Pour toutes vos nouvelles instances V2.6, vSphere sera déployé avec les modules de correction suivants appliqués : ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG et ESXi650-201808403-BG.
* Pour toutes vos instances existantes déployées avant la version 2.5, tous les nouveaux clusters et tous les nouveaux serveurs ESXi seront mis à jour avec les modules de correction suivants : ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG et ESXi650-201808403-BG.
* Pour tous vos serveurs ESXi existants, tout comme pour tous les éventuels clusters ou serveurs ESXi que vous pourriez continuer de déployer avant une mise à niveau vers la version 2.5, vous devez appliquer les modules de correction ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG et ESXi650-201808403-BG disponibles sur le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch).

#### Pour VMware vCenter Server 6.5
{: #trbl_fix_spectre-vcs2.0-vcenter}

* Pour toutes vos nouvelles instances V2.6, vCenter Server sera déployé avec les modules de correction cumulés vCenter 6.5 U2c appliqués.
* Pour toutes les instances existantes déployées avant la version 2.6, vous devez appliquer le module de correction vCenter 6.5 U2c depuis le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch).

### Instances Cloud Foundation déployées dans la version 2.0 ou ultérieure
{: #trbl_fix_spectre-cf2.0}

Pour appliquer les modules de correction requis pour VMware vSphere 6.5 et VMware vCenter Server 6.5, vous devez effectuer une mise à niveau de vos instances Cloud Foundation vers le dernier bundle de modules de correction VMware. Pour toutes vos instances et tous vos serveurs ESXi existants, vous serez invité à appliquer les modules de correction sur la page **Mise à jour et module de correction** depuis la console {{site.data.keyword.vmwaresolutions_full}}. Pour plus d'informations, voir [Application de mises à jour à des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_applyingupdates).

### Clusters VMware vSphere déployés avec la version 2.0 ou ultérieure
{: #trbl_fix_spectre-vss2.0}

Pour tous les nouveaux clusters VMware vSphere 6.5 et tous les nouveaux serveurs ESXi, vous devez appliquer les modules de correction ESXi650-201808401-BG, ESXi650-201808402-BG et ESXi650-201808403-BG, disponibles sur le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch).

Pour tous les clusters VMware vSphere 6.5 existants, vous devez appliquer les modules de correction ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG et ESXi650-201808403-BG, disponibles sur le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch).

Pour VMware vCenter Server 6.5, vous devez appliquer le module de correction vCenter 6.5 U2c, disponible sur le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch), à tous les serveurs vCenter, nouvellement déployés ou existants.

## Instances déployées en version 1.9 ou antérieure
{: #trbl_fix_spectre-instance1.9-update}

Instances Cloud Foundation, instances vCenter Server et clusters VMware vSphere de la version 1.9 ou antérieure, déployés avec VMware vSphere 6.0 et VMware vCenter Server 6.0.

### Instances vCenter Server déployées dans la version 1.9 ou antérieure
{: #trbl_fix_spectre-vcs1.9}

Pour VMware vSphere 6.0 et pour VMware vCenter Server 6.0, vous devez appliquer les modules de correction ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG, ESXi600-201808401-BG, ESXi600-201808402-BG et ESXi600-201808403-BG pour vSphere et vCenter 6.0 U3h pour vCenter Server, disponibles sur le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch), à toutes les instances et à tous les serveurs ESXi, nouvellement déployés ou existants.

### Instances Cloud Foundation déployées dans la version 1.9 ou antérieure
{: #trbl_fix_spectre-cf1.9}

Des mises à jour pour ces instances seront disponibles lorsque les mises à jour requises du fournisseur dont dépendent ces instances seront publiées.

### Clusters VMware vSphere déployés avec la version 1.9 ou ultérieure
{: #trbl_fix_spectre-vss1.9}

Pour VMware vSphere 6.0 et pour VMware vCenter Server 6.0, vous devez appliquer les modules de correction ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG, ESXi600-201808401-BG, ESXi600-201808402-BG et ESXi600-201808403-BG pour vSphere et vCenter 6.0 U3h pour vCenter Server, disponibles sur le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch), à tous les clusters vSphere et à tous les serveurs ESXi, nouvellement déployés ou existants.

## Liens connexes
{: #trbl_fix_spectre-related}

* [Application de mises à jour à des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_applyingupdates)
* [Sécurisation contre les plus récentes vulnérabilité en matière de sécurité](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [Site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch)
