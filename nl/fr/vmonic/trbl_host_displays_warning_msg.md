---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Problème de configuration de l'affichage des serveurs ESXi
{: #trbl_host_displays_warning_msg}

## Problème
{: #trbl_host_displays_warning_msg-problem}

Un problème de configuration est signalé dans l'onglet **Problèmes** de l'onglet **Surveiller** du serveur VMware ESXi du client vSphere.

Le message suivant s'affiche dans l'onglet **Problèmes** pour le serveur ESXi :

`This host currently has no management network redundancy`

Ce message s'affiche alors que deux liaisons montantes sont disponibles pour le commutateur distribué privé, ce qui assure la redondance.

## Résolution
{: #trbl_host_displays_warning_msg-resolution}

Il s'agit d'un problème VMware connu. Pour résoudre le problème, suivez les instructions fournies dans la rubrique [ESX/ESXi host displays warning message when test condition is false (2008602)](https://kb.vmware.com/s/article/2008602){:new_window}.
