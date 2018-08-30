---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# Mise à niveau de vos instances à partir d'éditions antérieures à la version 1.4

## Problème

La topologie de réseau des instances en version 1.4 et éditions ultérieures diffère de celle des instances des éditions antérieures à la version 1.4. Compte tenu de cette différence, les instances déployées dans des éditions antérieures à la version 1.4 ne peuvent pas être utilisées en l'état dans l'édition actuelle.

## Résolution

En version 1.4 et éditions ultérieures, plusieurs améliorations de la topologie de réseau sont disponibles pour vos instances :
* (S'applique à toutes les instances) : Configuration de réseau optimisée. Etant donné que le compte {{site.data.keyword.cloud}} que vous utilisez doit être un compte d'acheminement et de routage virtuels (VRF, Virtual Routing and Forwarding) ou pour lequel le spanning VLAN est activé s'il s'agit d'un compte classique (non VRF), une seconde adresse IP portable n'est pas nécessaire. Seule l'adresse IP portable de l'infrastructure {{site.data.keyword.cloud_notm}} principal est requise pour le déploiement.
* (S'applique uniquement aux instances Cloud Foundation) : possibilité de déploiement multisite avec connexion unique Microsoft Windows AD (Active Directory) et serveur de noms de domaine (DNS, Domain Name System).

Si vous n'avez pas migré ou supprimé vos instances des éditions antérieures à la version 1.4, elles seront visibles sur la console {{site.data.keyword.vmwaresolutions_short}} mais en mode affichage uniquement. Dans l'interface utilisateur, la mention **Obsolète** apparaît pour ces instances avec une icône de symbole d'avertissement.

**Remarque** : es informations affichées dans les propriétés d'instance correspondent aux données de la date d'édition de la version 1.4 et ne peuvent plus être actualisée.

Les actions suivantes sont disponibles sur les instances antérieures à la version 1.4 :
*  Affichage des informations sur la page des détails de l'instance.
*  Affichage des informations de sauvegarde de l'instance.
*  Ouverture du client Web vSphere et utilisation de l'instance dans vCenter.
*  Demande de restauration de l'instance via l'ouverture d'un ticket de demande de service {{site.data.keyword.cloud_notm}}.
*  Suppression de l'instance.

Toutes les autres actions des instances antérieures à la version 1.4 ne sont plus disponibles.

Si vos instances sont en version antérieure à 1.4 et que vous prévoyez de continuer à les utiliser, vous pouvez les mettre à niveau en créant de nouvelles instances puis en déplaçant vos configurations existantes vers ces nouvelles instances.

Pour déplacer vos instances de version antérieur à 1.4 vers de nouvelles instances, procédez comme suit depuis le client Web vSphere :
1. Depuis votre instance de version antérieur à 1.4, exportez toutes les machines virtuelles.
2. Créez une instance dans l'édition actuelle.
3. Importez toutes les machines virtuelles exportées à l'**Etape 1**.
4. Utilisez votre nouvelle instance.

Pour plus d'informations sur l'exportation et l'importation de machines virtuelles, reportez-vous à votre documentation VMware vSphere.

Si vous avez besoin d'aide concernant {{site.data.keyword.vmwaresolutions_short}}, [contactez le support IBM](trbl_support.html) via l'un des canaux de support.
