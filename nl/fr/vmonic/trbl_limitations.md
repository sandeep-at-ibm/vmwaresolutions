---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Limitations et remarques supplémentaires

Passez en revue les remarques et limitations suivantes liées à l'utilisation de {{site.data.keyword.vmwaresolutions_full}}.

## Installation automatique des mises à jour de Windows

Microsoft Active Directory (AD) / Domain Name Server (DNS) est automatiquement configuré pour ne télécharger que les mises à jour. Il n'installe pas ces mises à jour et ne redémarre pas automatiquement les éléments concernés. Vous devez installer les mises à jour manuellement et redémarrer à une heure planifiée ne provoquant pas d'interruptions de la configuration du serveur AD ou d'autres travaux de sauvegarde. Pour appliquer les mises à jour Windows, installez-les manuellement.

## Remarques relatives au choix d'un domaine racine pour des instances Cloud Foundation

Lorsque vous choisissez un nom de domaine lors du déploiement d'une instance Cloud Foundation principal ou secondaire, vous devez vérifier que le nom d'hôte `sddcmanager.<subdomain>` n'est pas résolu en domaine externe en exécutant la commande `ping` ou `nslookup`.

La structure du sous-domaine de l'instance Cloud Foundation est `<VCF instance name>.<domain name>`. Par exemple, si `<domain name>` est `test.local` et que le nom de l'instance Cloud Foundation est `mytest`, le nom d'hôte `sddcmanager.mytest.test.local` ne doit pas être résolu en adresse IP avant le déploiement de l'instance Cloud Foundation. Sinon, le déploiement de l'instance risque d'échouer.
