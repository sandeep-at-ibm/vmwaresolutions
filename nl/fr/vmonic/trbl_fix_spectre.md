---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Résolution des vulnérabilités Spectre et Meltdown

Pour résoudre les vulnérabilités Spectre et Meltdown, vous devez appliquer un certain nombre de correctifs dans un ordre précis.

## Mise à jour du microprogramme

Pour les informations les plus récentes concernant la mise à jour du microprogramme, voir [Sécurisation contre les plus récentes vulnérabilité en matière de sécurité](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/).

## Mise à jour d'instances déployées en version 2.0 ou ultérieure

Les instances en version 2.0 ou ultérieure sont été déployées avec VMware vSphere 6.5 et VMware vCenter Server 6.5. Ces deux composants logiciels nécessitent l'application de correctifs.

### Instances vCenter Server déployées en version 2.0 ou ultérieure

Pour VMware vSphere 6.5 :
* Pour toutes vos nouvelles instances V2.3, vSphere sera déployé avec les modules de correction suivants appliqués : ESXi650-201712101-SG, ESXi650-201803401-BG et ESXi650-201803402-BG.  
* Pour toutes vos instances existantes déployées avant l'édition V2.3, tous les nouveaux clusters et tous les nouveaux serveurs ESXi seront mis à jour avec les modules de correction suivants : ESXi650-201712101-SG, ESXi650-201803401-BG et ESXi650-201803402-BG.
* Pour tous vos serveurs ESXi existants, et pour tous les clusters ou tous les serveurs ESXi que vous continuez de déployer avant de procéder à la mise à niveau vers V2.3, vous devez appliquer les modules de correction ESXi650-201712101-SG, ESXi650-201803401-BG et ESXi650-201803402-BG depuis le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch).

Pour VMware vCenter Server 6.5 :
* Pour toutes vos nouvelles instances V2.3, vCenter Server sera déployé avec le module de correction vCenter 6.5 U1g appliqué.
* Pour toutes les instances existantes déployées avant l'édition V2.3, vous devez appliquer le module de correction vCenter 6.5 U1g depuis le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch).

### Instances Cloud Foundation déployées en version 2.0 ou ultérieure

Pour appliquer les modules de correction requis pour VMware vSphere 6.5 et VMware vCenter Server 6.5, vous devez effectuer une mise à niveau de vos instances Cloud Foundation vers l'édition V2.3 en cours.

Pour toutes vos instances et tous vos serveurs ESXi existants, vous serez invité à appliquer les modules de correction (ESXi650-201712101-SG, ESXi650-201803401-BG et ESXi650-201803402-BG pour vSphere et vCenter 6.5 U1g pour vCenter Server) sur la page **Mise à jour et module de correction** depuis la console {{site.data.keyword.vmwaresolutions_full}}. Pour plus d'informations, voir [Application de mises à jour à des instances Cloud Foundation](../sddc/sd_applyingupdates.html).

### Clusters VMware vSphere déployés en version 2.0 ou ultérieure

Pour VMware vSphere 6.5, vous devez appliquer les modules de correction ESXi650-201712101-SG, ESXi650-201803401-BG et ESXi650-201803402-BG depuis le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch) à tous vos clusters vSphere et à tous vos serveurs ESXi, nouvellement déployés ou existants.

Pour VMware vCenter Server 6.5, vous devez appliquer le module de correction vCenter 6.5 U1g depuis le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch) à tous vos serveurs vCenter, nouvellement déployés ou existants.

## Instances déployées en version 1.9 ou antérieure

Les instances Cloud Foundation et vCenter Server, de même que les clusters VMware vSphere de version 1.9 ou antérieure, ont été déployés avec VMware vSphere 6.0 et VMware vCenter Server 6.0.

### Instances vCenter Server déployées en version 1.9 ou antérieure

Pour VMware vSphere 6.0 et VMware vCenter Server 6.0, vous devez appliquer les modules de correction (ESXi600-201711101-SG, ESXi600-201803401-BG et ESXi600-201803402-BG pour vSphere et vCenter 6.0 U3e pour vCenter Server) depuis le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch) à toutes vos instances et à tous vos serveurs ESXi, nouvellement déployés ou existants

### Instances Cloud Foundation déployées en version 1.9 ou antérieure

Des mises à jour pour ces instances seront disponibles lorsque les mises à jour requises du fournisseur dont dépendent ces instances seront publiées.

### Clusters VMware vSphere déployés en version 1.9 ou antérieure

Pour VMware vSphere 6.0 et VMware vCenter Server 6.0, vous devez appliquer les modules de correction (ESXi600-201711101-SG, ESXi600-201803401-BG et ESXi600-201803402-BG pour vSphere et vCenter 6.0 U3e pour vCenter Server) depuis le [site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch) à tous vos clusters vSphere et à tous vos serveurs ESXi, nouvellement déployés ou existants.

### Liens connexes

* [Application de mises à jour à des instances Cloud Foundation](../sddc/sd_applyingupdates.html)
* [Sécurisation contre les plus récentes vulnérabilité en matière de sécurité](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [Site des modules de correction pour les produits VMware](https://my.vmware.com/group/vmware/patch)
