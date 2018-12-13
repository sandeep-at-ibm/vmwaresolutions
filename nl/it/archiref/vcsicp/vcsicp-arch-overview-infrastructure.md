---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-15"

---


# Rete e infrastruttura di IBM Cloud

## VRF (Virtual Routing and Forwarding)

Puoi configurare gli account {{site.data.keyword.cloud}} come account VRF per fornire funzionalità simili allo spanning della VLAN, consentendo l'instradamento automatico tra i blocchi di IP della sottorete. Tutti gli account con connessioni Direct-Link devono essere convertiti o creati come account VRF.

## Direct Link

{{site.data.keyword.cloud_notm}} Direct Link Connect offre l'accesso privato alla tua infrastruttura {{site.data.keyword.cloud_notm}} e a qualsiasi altro cloud collegato al Network Service Provider tramite il tuo data center IBM Cloud locale. Questa opzione è perfetta per la creazione della connettività multicloud in un unico ambiente. Una topologia di larghezza di banda condivisa viene utilizzata per connettere i clienti alla rete ICP ({{site.data.keyword.cloud_notm}} Private). Come con tutti i prodotti Direct Link, puoi aggiungere l'instradamento globale, che abilita il traffico di rete privato a tutte le ubicazioni di {{site.data.keyword.cloud_notm}}.

## VPN (Virtual Private Network)

### VPN strongSwan

Il servizio VPN strongSwan IPSec fornisce un canale di comunicazione end-to-end sicuro su internet che si basa sulla suite di protocolli standard del settore Internet Protocol Security (IPSec).

### Hybridity (HCX)

vCenter Server on {{site.data.keyword.cloud_notm}} Hybridity Bundle estende senza soluzione di continuità le reti dei data center in loco in {{site.data.keyword.cloud_notm}}, il che consente la migrazione delle macchine virtuali (VM) da e verso {{site.data.keyword.cloud_notm}} senza alcuna conversione o modifica.

## Struttura fisica

L'infrastruttura fisica richiesta per distribuire un'istanza di produzione ICP su un cluster VMware vCenter Server on {{site.data.keyword.cloud_notm}} richiede la seguente specifica minima.

Tabella 1. Specifica di vCenter Server per ICP

| Distribuzione NFS | Distribuzione vSAN |
:--|:----:|:----:
Numero di server | 3 | 4
CPU | 28 core 2,2 GHz | 28 core 2,2 GHz
Memoria | 384 GB | 384 GB
Archiviazione | Gestione 2000 GB 2IOPS/GB, Carico di lavoro 2000 GB 4IOPS/GB, ICP 4000 GB 4IOPS/GB | Min 960-GB SSD x 2

Oltre ai requisiti hardware di ICP, devi creare volumi persistenti nell'ambiente ICP per archiviare i dati database e log di CAM (Cloud Automation Manager). Mentre CAM supporta tutti i tipi di volumi persistenti supportati da ICP, le due configurazioni di archiviazione consigliate per CAM sono NFS e GlusterFS.

## Struttura virtuale

Figura 1. Struttura fisica della distribuzione vCenter Server e ICP
![Struttura fisica della distribuzione VCS e ICP](vcsicp-phy-ics-icp-deployment.svg)

All'interno dell'istanza vCenter Server, l'istanza ICP viene distribuita con un DLR (Distributed Logical Router) e ESG (Edge Services Gateway) NSX dedicato. L'installazione ICP viene caricata nella sottorete VXLAN definita nei componenti precedenti.

L'ESG è configurato con una regola NAT di origine (SNAT) per consentire il traffico in uscita, consentendo la connettività internet per scaricare i prerequisiti ICP e la connettività a GitHub e Docker o può essere utilizzato un proxy web per fornire la connettività internet. L'ESG è anche configurato per fornire accesso ai servizi DNS e NTP.

L'ESG è anche configurato con una regola NAT di destinazione (DNAT) agli indirizzi IP virtuali Master/Proxy ICP dalla rete {{site.data.keyword.cloud_notm}} 10.x all'ambiente VXLAN.

### Link correlati

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
