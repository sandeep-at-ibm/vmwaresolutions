---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-31"

---

# Conformità
{: #opsprocs-compliance}

La conformità è una serie di requisiti necessari per soddisfare i controlli minimi stabiliti da un'agenzia di regolamentazione o dalle procedure ottimali del settore. I framework di conformità della regolarità sono solitamente framework generali che forniscono indicazioni su un'ampia gamma di tecnologie, mentre le procedure ottimali del settore da parte dei fornitori sono spesso specifiche per la tecnologia per affrontare i rischi tecnologici.

Per la tua istanza vCenter Server, è consigliato che la sicurezza sia gestita mediante un team dedicato alla post distribuzione. Questa separazione delle mansioni dovrebbe aumentare e monitorare il livello di sicurezza della tua istanza. HyTrust CloudControl può aiutare i tuoi team con la separazione basata sui ruoli.

HyTrust DataControl e KeyControl possono aiutarti a fornire protezione per i carichi di lavoro, ad esempio tramite la crittografia dei dati inattivi e la recinzione virtuale (geofencing). Potresti essere interessato alla distribuzione del servizio Caveonix RiskForesight per aiutarti non solo in merito ai tuoi requisiti di conformità ma anche nella gestione dei rischi informatici e dell'analisi.

Le guide di protezione avanzata di VMware forniscono indicazioni prescrittive su come distribuire e utilizzare i prodotti VMware in modo sicuro. Le guide per vSphere sono fornite in un formato di foglio di calcolo facile da utilizzare, con metadati avanzati per consentire la classificazione delle linee guida e la valutazione del rischio. Includono anche degli esempi di script per abilitare l'automazione della sicurezza. Sono forniti documenti di confronto che elencano le modifiche delle indicazioni nelle versioni successive della guida.

Mentre molti dei controlli documentati nelle guide di protezione avanzata di VMware sono stati incorporati nell'architettura di riferimento {{site.data.keyword.vmwaresolutions_full}} e, quindi, distribuiti automaticamente, assicurati di adattare il livello di sicurezza della piattaforma alle tue esigenze e alla politica aziendale. Le guide di protezione avanzata di VMware forniscono i controlli specifici della tecnologia necessari per eseguire questa revisione. Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} automatizza questa attività di conformità e fornisce ulteriori indicazioni delle agenzie di regolamentazione.

vRealize Operations Manager ti consente di monitorare gli oggetti VMware per determinare possibili violazioni rispetto alle regole di conformità nella guida alla configurazione di sicurezza vSphere. Gli avvisi di conformità vengono attivati sull'istanza vCenter Server, sugli host, sulle macchine virtuali, sui gruppi di porte distribuiti o sugli switch distribuiti, consentendo l'analisi della violazione della conformità. Inoltre, per i clienti interessati alla conformità ad HIPAA (Health Insurance Portability and Accountability Act) e PCI DSS (Payment Card Industry Data Security Standard), sono disponibili i Compliance Pack di vRealize Operations Manager che possono essere scaricati dal sito web VMWare Solutions Exchange, concessi in licenza e installati. Questi Compliance Pack forniscono avvisi, politiche e report per convalidare le risorse vSphere rispetto alla guide di protezione HIPAA e PCI.


## Link correlati
{: #opsprocs-compliance-links}

* [Guida di protezione avanzata di VMware](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Guida alla sicurezza di vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-security-guide.pdf){:new_window}
* [Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
