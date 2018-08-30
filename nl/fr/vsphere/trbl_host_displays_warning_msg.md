---

copyright:

  years:  2016, 2018

lastupdated: "2017-06-29"

---

# Problème de configuration de l'affichage des serveurs ESXi

## Problème
Un problème de configuration est signalé dans l'onglet **Problèmes** de l'onglet **Surveiller** du serveur VMware ESXi du client vSphere.

Le message suivant s'affiche dans l'onglet **Problèmes** pour le serveur ESXi :

`This host currently has no management network redundancy`

Ce message s'affiche alors que deux liaisons montantes sont disponibles pour le commutateur distribué privé, ce qui assure la redondance.

## Résolution
Il s'agit d'un problème VMware connu. Pour résoudre le problème, suivez les instructions fournies dans la rubrique [ESX/ESXi host displays warning message when test condition is false (2008602)](https://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2008602){:new_window}.
