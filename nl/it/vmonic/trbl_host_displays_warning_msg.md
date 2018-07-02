---

copyright:

  years:  2016, 2018

lastupdated: "2017-06-29"

---

# Problema di configurazione nel server ESXi

## Problema
Viene visualizzato un problema di configurazione nella scheda **Problemi** della scheda **Monitoraggio** del server VMware ESXi nel client vSphere.

Nella scheda **Problemi** viene visualizzato il seguente messaggio per il server ESXi:

`This host currently has no management network redundancy`

Il messaggio viene visualizzato anche se ci sono due uplink disponibili per lo switch privato distribuito, che fornisce una ridondanza.

## Risoluzione
Questo è un problema noto di VMware. Per risolvere il problema, segui le istruzioni in [ESX/ESXi host displays warning message when test condition is false (2008602)](https://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2008602){:new_window}.
