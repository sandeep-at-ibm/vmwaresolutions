---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-31"

---

# Considerazioni sulla modifica delle risorse Cloud Foundation

La modifica di utenti, risorse o sottoreti riservati a {{site.data.keyword.vmwaresolutions_full}} può influire sulle operazioni di gestione per le istanze VMware Cloud Foundation.

**Importante:** non modificare le autorizzazioni globali del gruppo **ic4v-vCenter** nella pagina **Utenti e gruppi** del client web VMware vSphere. Tali modifiche includono la modifica del nome utente, l'eliminazione dell'utente o la modifica della sua password.

## Account utente specifici del servizio

Ogni servizio crea un account utente interno in vCenter Server. Questo account è necessario affinché le operazioni di gestione associate a un servizio possano connettersi a vCenter Server per eseguire le operazioni sul servizio.

**Importante**: per evitare interruzioni e problemi di connessione, se modifichi le impostazioni di ID utente, password o scadenza password per questo account utente, assicurati di aggiornare le informazioni anche nel servizio associato.

L'ID utente per questo account è nel formato `<service_name>-<service_uuid>@VSPHERE.LOCAL`. Ad esempio, l'ID utente utilizzato dal servizio Veeam on {{site.data.keyword.cloud_notm}} per connettersi a vCenter Server per eseguire backup pianificati è `Veeam-<Veeam_uuid>@VSPHERE.LOCAL`.

## Risorse VMware per le istanze Cloud Foundation

La seguente tabella elenca le operazioni che potrebbero essere interessate se modifichi le risorse VMware all'esterno della console {{site.data.keyword.vmwaresolutions_short}}. Se disponibile, verrà fornita anche una soluzione per il recupero.

Tabella 1. Operazioni interessate per l'amministratore SSO (cliente)

| Tentativo di modifica  | Operazioni interessate  | Severità  | Metodo di recupero  |
|:------------- |:------------- |:--------------|:--------------|
| Modifica del nome del data center virtuale VMware. | L'aggiunta di un data center VMware potrebbe non riuscire perché il nuovo server ESXi non può raggiungere il data center modificato. | Importante | Modifica di nuovo il nome del data center virtuale VMware con il nome originale. |
| Modifica dei nomi dei gruppi di porte.    | L'aggiunta di un server ESXi potrebbe non riuscire. | Importante | Modifica di nuovo il nome del gruppo di porte con il nome originale. |
| Modifica del nome del cluster. | L'aggiunta di un server ESXi potrebbe non riuscire. | Importante | Modifica di nuovo il nome del cluster con il nome originale.
| Modifica del nome del DVS (Distributed Virtual Switch) pubblico o privato. | L'aggiunta di un server ESXi potrebbe non riuscire. | Importante | Modifica di nuovo il nome del DVS con il nome originale.
| Modifica del nome dell'archivio dati VSAN. | L'aggiunta di un server ESXi potrebbe non riuscire.<br><br>L'aggiornamento dell'istanza potrebbe non riuscire. | Importante | Modifica di nuovo il nome dell'archivio dati VSAN con il nome originale, **vsanDatastore**.
| Modifica del nome di istanza o del nome di dominio. | L'istanza è inutilizzabile. | Critico | N/A

## Sottoreti di gestione per le istanze Cloud Foundation

Le seguenti informazioni trattano le sottoreti ordinate da {{site.data.keyword.vmwaresolutions_short}} e forniscono opzioni per ordinare sottoreti aggiuntive per uso personale.

**ATTENZIONE**: non utilizzare questi componenti per altri scopi o la stabilità del tuo ambiente sarà gravemente compromessa.

Con ogni ordine di Bare Metal Server {{site.data.keyword.cloud_notm}}, vengono ordinati i seguenti intervalli di indirizzi IP per impostazione predefinita:

*  Un intervallo pubblico primario di 32 indirizzi IP
*  Un intervallo privato primario di 64 indirizzi IP

Inoltre, a {{site.data.keyword.vmwaresolutions_short}} sono anche riservate le seguenti sottoreti di gestione:

*  Due sottoreti private portatili di 64 indirizzi IP sulla prima VLAN: una per la gestione e l'altra per VTEPS.
*  Due sottoreti private portatili di 64 indirizzi IP sulla seconda VLAN: una per vMotion e una per vSAN.
*  Una sottorete portatile pubblica di 16 indirizzi IP sulla VLAN pubblica.

Se hai bisogno di utilizzare più sottoreti, puoi ottenere gli indirizzi IP da utilizzare in uno dei seguenti modi:

* **Opzione 1 (consigliata)**: utilizza le sovrapposizioni della rete virtuale VMware NSX. Viene fornito un template VXLAN di esempio al momento dell'ordine. Questo template VXLAN può essere utilizzato come punto di partenza per la creazione di SDN.
* **Opzione 2**: ordina le tue proprie sottoreti pubbliche o private portatili per ottenere gli indirizzi IP. Per distinguere le sottoreti che ordini da quelle di gestione, puoi aggiungere delle note a tutte le sottoreti che stai ordinando.
