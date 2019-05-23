---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmware-solutions


---

# Zerto VRA ist auf dem ESXi-Host in der vCenter-Konsole sichtbar, nachdem Zerto on IBM Cloud deinstalliert wurde.
{: #trbl_zerto_vra}

## Problem
{: #trbl_zerto_vra-problem}

Zerto Virtual Replication Appliances (VRAs) werden nach der Verwendung von {{site.data.keyword.slportal}} nicht entfernt, um den Zerto on {{site.data.keyword.cloud}}-Service zu deinstallieren.

## Lösung
{: #trbl_zerto_vra-resolution}

Entfernen Sie die VRAs manuell aus der vCenter-Konsole.

1. Melden Sie sich an der vCenter-Konsole an.
2. Klicken Sie auf **Hosts and Clusters** und suchen Sie die virtuellen Maschinen mit den Namen, die mit **Z-VRA** beginnen. Beispiel: **Z-VRA-host0-vcs40dal.vcs.icvs.org**.
3. Klicken Sie mit der rechten Maustaste auf die virtuelle Maschine **Z-VRA-** und klicken Sie auf **Aus Platte löschen**.
