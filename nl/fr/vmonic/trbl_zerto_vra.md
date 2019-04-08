---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmwaresolutions


---

# Dispositifs VRA Zerto visibles sur l'hôte ESXi dans la console vCenter une fois Zerto on IBM Cloud désinstallé
{: #trbl_zerto_vra}

## Problème
{: #trbl_zerto_vra-problem}

Les dispositifs VRA (Virtual Replication Appliance) Zerto ne sont pas supprimés une fois que vous avez désinstallé le service Zerto on {{site.data.keyword.cloud}} à l'aide de {{site.data.keyword.slportal}}.

## Résolution
{: #trbl_zerto_vra-resolution}

Supprimez manuellement les dispositifs VRA de la console vCenter.

1. Connectez-vous à la console vCenter.
2. Cliquez sur **Hosts and Clusters** et recherchez les machines virtuelles dont le nom commence par **Z-VRA-**. Par exemple, **Z-VRA-host0-vcs40dal.vcs.icvs.org**.
3. Cliquez sur la machine virtuelle **Z-VRA-** avec le bouton droit de la souris, puis cliquez sur **Delete from Disk**.
