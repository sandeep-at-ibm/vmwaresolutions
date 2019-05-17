---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmware-solutions


---

# Zerto VRA visibile sull'host ESXi nella console vCenter dopo che è stato disinstallato Zerto on IBM Cloud
{: #trbl_zerto_vra}

## Problema
{: #trbl_zerto_vra-problem}

I dispositivi Zerto Virtual Replication Appliance (VRA) non vengono rimossi dopo l'utilizzo di {{site.data.keyword.slportal}} per disinstallare correttamente il servizio Zerto on {{site.data.keyword.cloud}}.

## Risoluzione
{: #trbl_zerto_vra-resolution}

Rimuovi manualmente i VRA dalla console vCenter.

1. Accedi alla console vCenter.
2. Fai clic su **Hosts and Clusters** e individua le macchine virtuali con i nomi che iniziano con **Z-VRA-**. Ad esempio, **Z-VRA-host0-vcs40dal.vcs.icvs.org**.
3. Fai clic con il tasto destro sulla macchina virtuale **Z-VRA-** e poi fai clic su **Delete from Disk**.
