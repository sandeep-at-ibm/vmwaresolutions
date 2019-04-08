---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# Problèmes de configuration de la console vSphere rencontré lors de l'ajout d'un cluster haute disponibilité
{: #trbl_add_ha_cluster_config}

## Problème
{: #trbl_add_ha_cluster_config-problem}

Lorsque vous ajoutez une configuration de cluster à haute disponibilité doté d'un seul partage de fichiers, le problème de configuration suivant se produit sur les hôtes ESXi :

> The number of heartbeat datastores for host is 1, which is less than required: 2

## Résolution
{: #trbl_add_ha_cluster_config-resolution}

Ce problème se produit en l'absence de redondance au niveau du stockage partagé de manière à activer le signal de présence des magasins de données.

Pour obtenir plus d'informations et pour connaître la procédure permettant de corriger ce problème, voir [HA error: "The number of heartbeat data stores for host is 1, which is less than required: 2" (2004739)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739).
