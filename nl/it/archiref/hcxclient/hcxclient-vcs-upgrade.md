---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Upgrade dei componenti HCX
{: #hcxclient-vcs-upgrade}

L'upgrade di HCX è un semplice processo che utilizza l'interfaccia utente (IU) web client nell'aggiornamento di HCX Manager lato client e l'IU web cloud nell'aggiornamento di HCX Manager sul lato cloud.

Devi eseguire l'upgrade su entrambi i lati poiché qualsiasi aggiornamento di componenti della flotta fa in modo che entrambi ridistribuiscano i componenti della flotta con il livello di codice installato su HCX Manager. 

Se il supporto di VMware chiede l'ID sistema, fornisci sia il lato client che quello cloud. Usa SSH in HCX Manager (client o cloud) ed esegui `cat /common/location` per individuare l'ID sistema.

## Link correlati
{: #hcxclient-vcs-upgrade-related}

* [Glossario di componenti e termini HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparazione dell'ambiente di installazione](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Distribuzione client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Rete di servizi in loco HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrazioni VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitoraggio di parametri e componenti](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Risoluzione dei problemi di HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
