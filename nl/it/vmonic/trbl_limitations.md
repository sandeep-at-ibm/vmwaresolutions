---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Ulteriori limitazioni e considerazioni

Esamina le seguenti considerazioni e limitazioni quando utilizzi {{site.data.keyword.vmwaresolutions_full}}.

## Istallazione automatica degli aggiornamenti di Windows

Microsoft Active Directory (AD) / Domain Name Server (DNS) viene configurato automaticamente per scaricare solo gli aggiornamenti. Non esegue automaticamente l'installazione di questi aggiornamenti né il riavvio. Devi installare gli aggiornamenti manualmente ed eseguire il riavvio in un momento pianificato che eviti interruzioni della configurazione del server AD in corso e di altri lavori di backup. Per applicare gli aggiornamenti di Windows, installa gli aggiornamenti manualmente.

## Considerazioni sulla scelta del nome del dominio root per le istanze Cloud Foundation

Quando scegli un nome di dominio durante la distribuzione di un'istanza Cloud Foundation primaria o secondaria, devi verificare che il nome host `sddcmanager.<subdomain>` non venga risolto in un dominio esterno utilizzando il comandi `ping` o `nslookup`.

La struttura del dominio secondario dell'istanza Cloud Foundation è `<VCF instance name>.<domain name>`. Ad esempio, se il tuo `<domain name>` è `test.local` e il nome dell'istanza Cloud Foundation è `mytest`, il nome host `sddcmanager.mytest.test.local` non deve essere risolto in un indirizzo IP prima di distribuire l'istanza Cloud Foundation. Altrimenti, la distribuzione dell'istanza potrebbe non riuscire.
