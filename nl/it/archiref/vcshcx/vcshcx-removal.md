---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Rimozione di HCX
{: #vcshcx-removal}

La rimozione di HCX presume che le reti estese non siano più in uso. Utilizza la seguente procedura per rimuovere HCX.

1. Annulla l'estensione di tutte le reti estese.
2. Nell'IU (interfaccia utente) client, elimina gli eventuali dispositivi L2C. Attendi che i dispositivi L2C scompaiano dall'IU web.
3. Elimina CGW. Questo rimuove anche l'ottimizzatore WAN. Attendi la rimozione dei dispositivi CGW e ottimizzatore WAN.
4. Arresta ed elimina le VM del dispositivo di HCX Manager dal lato client e da quello cloud.
5. Rimuovi l'ESG HCX dal lato cloud NSX.
6. Utilizza il browser vCenter Mob per rimuovere lo snap-in HCX.

## Link correlati
{: #vcshcx-removal-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro) 
