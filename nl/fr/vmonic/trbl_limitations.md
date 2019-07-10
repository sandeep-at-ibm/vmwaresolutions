---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, Windows automatic installation, Windows updates

subcollection: vmware-solutions


---

{:faq: data-hd-content-type='faq'}

# Limitations et remarques supplémentaires
{: #trbl_limitations}

Passez en revue les remarques et limitations suivantes liées à l'utilisation de {{site.data.keyword.vmwaresolutions_full}}.

## Installation automatique des mises à jour de Windows
{: #trbl_limitations-windows-update}
{: faq}

Microsoft Active Directory (AD) / Domain Name Server (DNS) est automatiquement configuré pour ne télécharger que les mises à jour. Il n'installe pas ces mises à jour et ne redémarre pas automatiquement les éléments concernés. Vous devez installer les mises à jour manuellement et redémarrer à une heure planifiée ne provoquant pas d'interruptions de la configuration du serveur AD ou d'autres travaux de sauvegarde. Pour appliquer les mises à jour Windows, installez-les manuellement.
