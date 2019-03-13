---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:faq: data-hd-content-type='faq'}

# Altre limitazioni e considerazioni
{: #trbl_limitations}

Esamina le seguenti considerazioni e limitazioni quando utilizzi {{site.data.keyword.vmwaresolutions_full}}.

## Istallazione automatica degli aggiornamenti di Windows
{: #trbl_limitations-windows-update}
{: faq}

Microsoft Active Directory (AD) / Domain Name Server (DNS) viene configurato automaticamente per scaricare solo gli aggiornamenti. Non esegue automaticamente l'installazione di questi aggiornamenti né il riavvio. Devi installare gli aggiornamenti manualmente ed eseguire il riavvio in un momento pianificato che eviti interruzioni della configurazione del server AD in corso e di altri lavori di backup. Per applicare gli aggiornamenti di Windows, installa gli aggiornamenti manualmente.

## Considerazioni sulla scelta del nome del dominio root per le istanze Cloud Foundation
{: #trbl_limitations-considerations}

Quando scegli un nome di dominio durante la distribuzione di un'istanza Cloud Foundation primaria o secondaria, devi verificare che il nome host `sddcmanager.<subdomain>` non venga risolto in un dominio esterno utilizzando i comandi `ping` o `nslookup`.

La struttura del dominio secondario dell'istanza Cloud Foundation è `<VCF instance name>.<domain name>`. Ad esempio, se il tuo `<domain name>` è `test.local` e il nome dell'istanza Cloud Foundation è `mytest`, quindi il nome host `sddcmanager.mytest.test.local` non viene risolto in un indirizzo IP prima di distribuire l'istanza Cloud Foundation. Altrimenti, la distribuzione dell'istanza potrebbe non riuscire.
