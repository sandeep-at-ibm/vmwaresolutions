---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-30"

---

# Note sulla release per la V1.5
{: #relnotes_v15}

Questa release include nuove funzioni, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Requisiti dell'account SoftLayer VRF rispetto all'account classico
{: #relnotes_v15-vrf}

Per gli account SoftLayer® classici, lo spanning della VLAN è un'impostazione che può essere abilitata a livello di account. {{site.data.keyword.vmwaresolutions_short}} richiede che lo spanning della VLAN sia abilitato.

Per gli account SoftLayer VRF (Virtual Routing and Forwarding), l'equivalente di spanning della VLAN è un'impostazione permanente che non può essere modificata. Non è richiesta alcuna configurazione utente per gli account VRF.

Prima di effettuare un ordine di istanza, assicurati che il tuo account SoftLayer sia un account VRF o un account classico (non VRF) con spanning della VLAN abilitato. Altrimenti, l'ordine potrebbe non riuscire.

Per confermare che il tuo account SoftLayer sia un account VRF, consulta il supporto IBM Bluemix. Per gli account classici, devi abilitare lo spanning della VLAN seguendo le istruzioni in [Abilita o disabilita il VLAN Spanning](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}.

## Aggiornamenti del modello di addebito del servizio
{: #relnotes_v15-svc-charge}

Per le istanze Cloud Foundation, viene introdotta una nuova licenza _SDDC Manager_, che è una tariffa mensile applicata a ciascun nodo.

## Miglioramenti dell'usabilità
{: #relnotes_v15-ui}

Sono stati apportati miglioramenti in tutta l'interfaccia utente:

* La disponibilità dei vari {{site.data.keyword.CloudDataCents_notm}} e se hanno un inventario sufficiente per soddisfare l'ordine è chiaramente indicato sull'interfaccia utente. Utilizza questi dettagli per prendere una decisione consapevole sul {{site.data.keyword.CloudDataCent_notm}} da selezionare quando ordini un'istanza. Per ulteriori informazioni, vedi [Requisiti e pianificazione per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).
* Per le istanze Cloud Foundation, informazioni come il nome dell'istanza, il nome del dominio e del dominio secondario e l'ubicazione del data center vengono visualizzate automaticamente in formato grafico quando immetti le informazioni richieste nei campi di input.
