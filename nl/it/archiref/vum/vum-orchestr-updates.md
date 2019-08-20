---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

#	Aggiornamenti orchestrati
{: #vum-orchestr-updates}

Puoi utilizzare gli aggiornamenti orchestrati per aggiornare l'hardware virtuale e i VMware Tools delle VM (Virtual Machine) nell'inventario dopo aver eseguito l'aggiornamento degli host vSphere ESXi. Dopo l'aggiornamento degli host, viene eseguita prima la baseline di aggiornamento di VMware Tools, seguita dalla baseline di aggiornamento hardware delle VM (Virtual Machine). Puoi utilizzare gli aggiornamenti orchestrati a livello di cluster, cartella o data center.

VUM ti consente di eseguire aggiornamenti orchestrati di host e quindi di VM (Virtual Machine) utilizzando i gruppi di baseline. Viene utilizzato un gruppo di baseline che contiene una singola baseline di aggiornamento dell'host e più baseline di patch o estensione. VUM aggiorna prima gli host e quindi applica le baseline di patch o estensione. Puoi eseguire un aggiornamento orchestrato di VM (Virtual Machine) utilizzando un gruppo di baseline della VM (Virtual Machine) che contiene le seguenti baseline:
* VM Hardware Upgrade to Match Host
* VMware Tools Upgrade to Match Host

Gli aggiornamenti orchestrati VUM ti consentono di aggiornare gli oggetti di inventario in VCSA in un processo a due fasi. Innanzitutto, vengono aggiornati gli host vSphere ESXi, seguiti dagli aggiornamenti della VM (Virtual Machine). Questo processo a due fasi può essere configurato a livello di cluster o puoi configurarlo a livello del singolo host vSphere ESXi o della singola VM (Virtual Machine) per un controllo più granulare.

Nell'aggiornamento orchestrato, il cluster viene prima corretto in base al gruppo di baseline dell'host, che applica patch, estensioni e aggiornamenti e, dopo l'aggiornamento, le VM (Virtual Machine) nel cluster vengono corrette in base al gruppo di baseline di aggiornamento della VM (Virtual Machine) che contiene le baseline VM Hardware Upgrade to Match Host e VMware Tools Upgrade to Match Host.

Se il gruppo di baseline contiene anche una baseline di aggiornamento, VUM aggiorna prima gli host vSphere ESXi e quindi applica le baseline di patch o estensione poiché le patch sono applicabili alla specifica versione dell'host. Per le VM (Virtual Machine), vengono aggiornati prima gli strumenti VMware, seguiti dall'aggiornamento dell'hardware virtuale.

Pertanto, durante l'aggiornamento degli strumenti VMware, le VM (Virtual Machine) vengono accese se si trovano in uno stato spento o sospeso, quindi VUM la accende, esegue l'aggiornamento e ripristina lo stato di alimentazione originale della VM (Virtual Machine). Quindi, durante l'aggiornamento dell'hardware virtuale, le VM devono essere in uno stato spento se ci sono VM (Virtual Machine) accese, VUM le spegne, aggiorna l'hardware virtuale e le riaccende.

Per impostazione predefinita, la correzione degli host vSphere ESXi avviene in modo sequenziale e viene corretto un host alla volta. Quando il processo viene completato per un host, VUM inizierà a correggere l'host successivo. Questa impostazione predefinita può essere modificata per consentire la correzione in parallelo in modo che sia possibile correggere più di un host alla volta, tuttavia ciò è possibile solo se hai una capacità di failover adeguata nel tuo cluster.

Se gli host vSphere ESXI fanno parte di un cluster vSAN, il processo di correzione è sempre sequenziale anche se hai selezionato la correzione in parallelo nella procedura guidata di correzione, in quanto solo un host da un cluster vSAN può essere in modalità di manutenzione in un determinato momento. VUM è intelligente ed esegue un calcolo su quanti host possono essere corretti in parallelo senza bloccare le impostazioni DRS.

In alternativa, puoi definire il limite per il numero di host che possono essere corretti in parallelo durante la procedura guidata di correzione.

Il seguente flusso di lavoro descrive il processo per eseguire un aggiornamento orchestrato:

## Passo 1
{: #vum-orchestr-updates-step1}

1. Utilizza il client web vSphere per accedere al VCSA.
2. Seleziona **Home** > **Update Manager**, dalla scheda **Objects**, seleziona un'**istanza Update Manager**.
3. Fai clic sulla scheda **Manage**, quindi sulla scheda **Host Baselines** e fai clic su **New Baseline Group**.
4. Immetti un nome univoco per il gruppo di baseline e fai clic su **Next**.
5. Seleziona una baseline di aggiornamento dell'host per includerla nel gruppo di baseline.
6. Facoltativamente, crea una nuova baseline di aggiornamento dell'host facendo clic su **Create a new Host Upgrade Baseline** nella parte inferiore della pagina Upgrades e completa la procedura guidata per la nuova baseline. Fai clic su **Next**.
7. Seleziona le baseline di patch che vuoi includere nel gruppo di baseline.
8. Facoltativamente, crea una nuova baseline di patch facendo clic su **Create a new Host Patch Baseline** nella parte inferiore della pagina Patches e completa la procedura guidata per la nuova baseline. Fai clic su **Next**.
9. Seleziona le baseline di estensione da includere nel gruppo di baseline.
10. Facoltativamente, crea una nuova baseline di estensione facendo clic su **Create a new Extension Baseline** nella parte inferiore della pagina Patches e completa la procedura guidata per la nuova baseline.
11. Esamina la pagina **Ready to Complete**, fai clic su **Finish** e il gruppo di baseline dell'host viene visualizzato nel riquadro Baseline Groups.

## Passo 2
{: #vum-orchestr-updates-step2}

1. Crea un gruppo di baseline della VM (Virtual Machine), che contiene le baseline VMware Tools Upgrade to Match Host e VM Hardware Upgrade to Match Host, nella vista di amministrazione VUM.
2. Collega il gruppo di baseline a un oggetto contenitore vCenter contenente le VM (Virtual Machine) che vuoi aggiornare.
3. Esegui la scansione dell'oggetto contenitore per visualizzare lo stato di conformità delle VM (Virtual Machine) nel contenitore. Puoi avviare la scansione manualmente o pianificare un'attività di scansione.
4. Esamina i risultati della scansione visualizzati nella vista di conformità (Compliance) del client VUM.
5. Correggi le VM (Virtual Machine) non conformi nell'oggetto contenitore per renderle conformi al gruppo di baseline collegato. Puoi avviare la correzione manualmente o pianificare un'attività di correzione.
* Durante un aggiornamento dei VMware Tools, le VM (Virtual Machine) devono essere accese. Se una VM (Virtual Machine) è in uno stato spento o sospeso prima di essere corretta, VUM accende la macchina. Al termine dell'aggiornamento, VUM riavvia la macchina e ripristina lo stato di alimentazione originale della VM (Virtual Machine).
* Durante un aggiornamento hardware della VM (Virtual Machine), le VM (Virtual Machine) devono essere spente. Al termine della correzione, VUM ripristina lo stato di alimentazione originale delle VM (Virtual Machine). Se una VM (Virtual Machine) è accesa, VUM spegne la macchina, aggiorna l'hardware virtuale e quindi accende la VM (Virtual Machine).

Puoi ora utilizzare questi gruppi di baseline nei processi di scansione, revisione, preparazione e correzione.

## Link correlati
{: #vum-orchestr-updates-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [{{site.data.keyword.vmwaresolutions_full}} Demos](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (dimostrazioni)
