---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-30"

---

# Note sulla release per la V1.5

Questa release include nuove funzioni, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e ulteriori suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Requisiti dell'account SoftLayer VRF rispetto all'account classico

Per gli account SoftLayer® classici, lo spanning della VLAN è un'impostazione che può essere abilitata a livello di account. {{site.data.keyword.vmwaresolutions_short}} richiede che lo spanning della VLAN sia abilitato.

Per gli account SoftLayer VRF (Virtual Routing and Forwarding), l'equivalente di spanning della VLAN è un'impostazione permanente che non può essere modificata. Non è richiesta alcuna configurazione utente per gli account VRF.

Prima di effettuare un ordine di istanza, assicurati che il tuo account SoftLayer sia un account VRF o un account classico (non VRF) con spanning della VLAN abilitato. Altrimenti, l'ordine potrebbe non riuscire.

Per confermare che il tuo account SoftLayer sia un account VRF, consulta il supporto IBM Bluemix. Per gli account classici, devi abilitare lo spanning della VLAN seguendo le istruzioni in [Abilita o disabilita lo spanning della VLAN](../../../infrastructure/vlans/vlan-spanning.html){:new_window}.

## Aggiornamenti del modello di addebito del servizio

Per le istanze Cloud Foundation, viene introdotta una nuova licenza _SDDC Manager_, che è una tariffa mensile applicata a ciascun nodo. Per ulteriori informazioni, vedi [Specifiche tecniche per le istanze Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).

## Miglioramenti dell'usabilità

Sono stati apportati miglioramenti in tutta l'interfaccia utente:

* La disponibilità dei vari data center e se hanno un inventario sufficiente per soddisfare l'ordine è chiaramente indicato sull'interfaccia utente in modo da poter prendere una decisione consapevole sul data center da selezionare durante l'ordine dell'istanza. Per ulteriori informazioni, vedi [Requisiti e pianificazione per le istanze Cloud Foundation](../sddc/sd_planning.html) e [Requisiti e pianificazione per le istanze vCenter Server](../vcenter/vc_planning.html).
* Per le istanze Cloud Foundation, informazioni come il nome dell'istanza, il nome del dominio e del dominio secondario e l'ubicazione del data center vengono automaticamente visualizzate in formato grafico mentre immetti le informazioni richieste nei campi di input. Per ulteriori informazioni, vedi [Ordine di istanze Cloud Foundation](../sddc/sd_orderinginstance.html).
