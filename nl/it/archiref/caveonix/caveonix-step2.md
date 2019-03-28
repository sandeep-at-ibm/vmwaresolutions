---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Passo 2 - distribuzione della VM (Virtual Machine)
{: #caveonix-step2}

L'automazione {{site.data.keyword.vmwaresolutions_full}} richiede una subnet IP privata portatile aggiuntiva e la VM (Virtual Machine) “tutto-in-uno” è configurata con un indirizzo IP da questa subnet in modo che i componenti Caveonix RiskForesight possano:

- Stabilire una connessione a vCenter e a NSX Manager tramite BCR.
- Stabilire una connessione ai raccoglitori remoti, sulle VXLAN oppure ospitati non in loco.
- Consentire al client di gestire lo spazio di indirizzo IP quando viene eseguito il ridimensionamento incrementale.


## Link correlati
{: #caveonix-step2-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
