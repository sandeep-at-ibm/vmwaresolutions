---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# Registrazione dell'HCX Manager con vCenter
{: #hcx-archi-reg-vcenter}

Registra il plugin Hybrid Cloud Services nel client web VMware vSphere e avvia il servizio di gestione Hybrid Cloud Services.

## Prima di iniziare
{: #hcx-archi-reg-vcenter-prereq}

L'applicazione virtuale Hybrid Cloud Services deve essere accesa prima di poter essere registrata.

## Procedura per registrare HCX Manager con vCenter
{: #hcx-archi-reg-vcenter-proc-register}

1. Accedi all'applicazione virtuale del servizio Hybrid Cloud Services.
2. Fai clic sul tile **Manage Settings**.
  1. Nel pannello di sinistra, in **Configure Systems**, seleziona vCenter.
  2. Fai clic su **Add vCenter** in alto a destra.
  3. Immetti l'indirizzo IP di vCenter Server nel formato `https:vCenter-host-name` o `https:vCenter-IP-address`. Ad esempio, `https:My-vCenter` o `https:10.108.26.211`.
  4. Immetti il nome utente e la password vCenter Server. L'account che viene utilizzato deve avere il ruolo di amministratore di vCenter.
  5. Fai clic su **OK**. Non riavviare quando viene visualizzato il messaggio _You need to restart the app_.
3. Configura il servizio di ricerca.
  1. Fai clic sulla scheda **Manage**.
  2. Fai clic sul pulsante **Edit** all'estrema destra della casella di testo **Lookup Service URL**.
  3. Immetti l'endpoint del servizio di ricerca nel seguente formato:
    * Per vCenter Server 5.5u3 `https://ssoip:/7444/lookupservice/sdk`
    * Per vCenter Server 6.0u2 `https://ssoip/lookupservice/sdk`
  4. Fai clic su **OK**. Non riavviare quando viene visualizzato un messaggio che richiede di riavviare il motore web.
4. Fai clic sulla scheda **Summary** e trova la sezione **Hybridity Management Components**. Arresta e avvia il motore dell'applicazione e il motore web.
5. Per finalizzare la registrazione, disconnettiti dal client web vSphere. Riaccedi per verificare che si è verificato l'aggiornamento della schermata.

## Risultati
{: #hcx-archi-reg-vcenter-results}

Nota l'icona **Hybrid Cloud** esistente e la voce di menu **Hybrid Cloud Services** sulla sinistra. La registrazione a Hybrid Cloud Services aggiorna queste etichette. Nell'inventario, l'etichetta dell'icona diventa **Hybrid Cloud Services**.

## Link correlati
{: #hcx-archi-reg-vcenter-related}

* [Installazione e configurazione dei servizi ibridi](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-hybrid)
