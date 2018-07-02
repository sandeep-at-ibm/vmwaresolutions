---

copyright:

  years:  2016, 2018

lastupdated: "2018-01-03"

---

# Le système vCenter Server secondaire ne figure pas dans l'inventaire du client Web vSphere

## Problème

Dans une configuration multisite, alors que vous avez ajouté une instance secondaire, son système vCenter Server n'est pas visible lorsque vous vous connectez au client Web VMware vSphere d'une instance précédemment commandée.

## Résolution

Il s'agit d'un problème connu de VMware 6.5.

Pour résoudre le problème, vous devez redémarrer le client Web vSphere, comme suit :

1. Avec le compte **root**, connectez-vous via **ssh** à la machine virtuelle vCenter de l'instance précédemment commandée.
2. Entrez ``shell`` pour accéder à l'interpréteur de commandes bash.
3. Entrez `service-control --stop vsphere-client` pour arrêter le client.
4. Entrez `service-control --start vsphere-client` pour redémarrer le client.
5. Une fois le client Web vSphere de l'instance précédemment commandée redémarré, vérifiez que le système vCenter Server de l'instance secondaire ajoutée est visible dans le client Web vSphere.
