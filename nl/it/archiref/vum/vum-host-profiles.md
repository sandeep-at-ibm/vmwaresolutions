---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-15"

subcollection: vmware-solutions


---

#	Profili host
{: #vum-host-profiles}

vCenter ha una funzione denominata Profili host. Questa funzione crea un profilo che cattura una configurazione dell'host di riferimento preconfigurata e convalidata e aiuta un amministratore di sistema a gestire le configurazioni host in un cluster. I profili host forniscono un meccanismo automatizzato e gestito centralmente per la configurazione dell'host e la conformità della configurazione. I profili host consentono di considerare la configurazione come un oggetto gestito, che dispone di un catalogo di parametri da configurare, come rete, archiviazione, sicurezza e altri parametri a livello di host. Questi profili host possono essere applicati a singoli host, a un cluster o a tutti gli host e i cluster associati a un profilo host.

Poiché più host vSphere ESXi di VMware vCenter Server on {{site.data.keyword.cloud}} vengono distribuiti dall'automazione IBM Cloud for VMware Solutions che ha distribuito il cluster iniziale, ci sono meno scostamenti della configurazione rispetto ai metodi manuali di aggiunta degli host. Tuttavia, le azioni dell'amministratore di sistema, oltre all'automazione, possono rendere diversa la configurazione degli host. Ad esempio, viene aggiunto più spazio di archiviazione NFS o vengono aggiunte altre VLAN. L'utilizzo dei profili host per convalidare la configurazione di un nuovo host controllando la conformità di questo host con un host esistente, è un caso di utilizzo valido di questo strumento all'interno di {{site.data.keyword.cloud_notm}}.

Per aggiungere altri host al tuo cluster vCenter Server, vedi [Espansione e contrazione della capacità per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers).

Nota:
*	Per le istanze distribuite o di cui è stato eseguito l'upgrade alla V2.1 o superiore, i cluster e i server ESXi appena distribuiti vengono corretti con i recenti aggiornamenti ESXi da VMware, ma non necessariamente con gli aggiornamenti più recenti.
*	Sei responsabile di tutti gli altri aggiornamenti ai componenti VMware, inclusa la garanzia che i cluster e i server ESXi appena distribuiti abbiano tutti gli aggiornamenti più recenti necessari.

Consigliamo che dopo l'aggiunta di un nuovo host nel cluster, esso venga messo in modalità di manutenzione in modo che possa essere riesaminato per verificare lo scostamento di conformità e corretto prima di ospitare qualsiasi carico di lavoro.

Per verificare la conformità è necessaria la seguente sequenza di operazioni:
1.	Creare un profilo host da un host esistente.
2.	Collegare il nuovo host al profilo host.
3.	Verificare la conformità del nuovo host con il profilo host.
4.	Riesaminare gli errori di conformità ed effettuare la correzione.

##	Creazione di un profilo host da un host esistente
{: #vum-host-profiles-create-host-profile}

1.	Dalla Home del client web vSphere, fai clic su **Policies and Profiles**.
2.	Fai clic su **Host Profiles** e vai alla vista dei profili host.
3.	Fai clic sull'**icona Extract Profile from a Host**.
4.	Seleziona un host esistente che funge da host di riferimento e fai clic su **Next**.
5.	Immetti il nome e una descrizione per il nuovo profilo e fai clic su **Next**.
6.	Rivedi le informazioni di riepilogo per il nuovo profilo e fai clic su **Finish**.
7.	Il nuovo profilo viene visualizzato nell'elenco dei profili.

##	Collegamento del nuovo host al profilo host
{: #vum-host-profiles-attach-to-profile}

1.	Dal **Profile List** nella vista principale Host Profiles, seleziona il profilo host precedentemente creato per applicarlo al nuovo host.
2.	Fai clic sull'**icona Attach/Detach a host profile to hosts and clusters**.
3.	Seleziona il nuovo host dall'elenco espanso e fai clic su **Attach**.
4.	Il nuovo host viene aggiunto all'elenco Attached Entities.
5.	Fai clic su **Next** e quindi su **Finish**.

##	Verifica della conformità del nuovo host con il profilo host
{: #vum-host-profiles-check-compliance}

1.	Passa al profilo host che è stato precedentemente completato.
2.	Fai clic sull'**icona Check Host Profile Compliance**.
3.	Nella scheda **Objects**, lo stato di conformità viene aggiornato come _Compliant, Unknown o _Non-compliant_. Uno stato non conforme indica che è stata rilevata un'incongruenza specifica tra il profilo e il nuovo host.

##	Riesame degli errori di conformità e correzione
{: #vum-host-profiles-review-compliance}

1. Per visualizzare ulteriori dettagli sugli errori di conformità, seleziona **Host Profile** dalla scheda **Objects** utilizzata nella verifica di conformità.
2. Per visualizzare dettagli specifici su quali parametri differiscono tra l'host che non ha rispettato la conformità e il profilo host, fai clic sulla scheda **Monitor** e seleziona la vista **Compliance**.
3. Espandi la gerarchia degli oggetti e seleziona l'host in errore.
4. I parametri che differiscono vengono visualizzati nella finestra Compliance, sotto la gerarchia.
5. Esamina i parametri e comprendi il motivo per cui il nuovo host può variare dall'host di riferimento. Per i parametri in cui la conformità non è accettabile, correggi prima di spostare il nuovo host dalla modalità di manutenzione. Ad esempio, laddove lo scostamento della configurazione sia provocato dall'azione dell'amministratore di sistema.

## Link correlati
{: #vum-host-profiles-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (dimostrazioni)
