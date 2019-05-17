---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# Upgrade dei componenti HCX
{: #vcshcx-upgrade}

L'upgrade di HCX è un semplice processo che utilizza l'interfaccia utente (IU) web client nell'aggiornamento di HCX Manager lato client e l'IU web cloud nell'aggiornamento di HCX Manager sul lato cloud. Devi eseguire l'upgrade su entrambi i lati poiché qualsiasi aggiornamento di componenti della flotta fa in modo che entrambi ridistribuiscano i componenti della flotta con il livello di codice che il gestore ha installato. Se il supporto di VMware chiede l'ID sistema, fornisci sia il lato client che quello cloud. Usa SSH in HCX Manager (client o cloud) ed esegui `cat
/common/location` per individuare l'ID sistema.

## Link correlati
{: #vcshcx-upgrade-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro) 
