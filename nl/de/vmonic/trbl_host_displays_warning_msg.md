---

copyright:

  years:  2016, 2018

lastupdated: "2017-06-29"

---

# ESXi-Server zeigt Konfigurationsproblem an

## Problem
Auf der Registerkarte **Probleme** der Seite **Überwachung** für den VMware ESXi-Server im vSphere-Client wird ein Konfigurationsproblem angezeigt.

Die folgende Nachricht wird auf der Registerkarte **Probleme** für den ESXi-Server angezeigt:

`This host currently has no management network redundancy (Dieser Host besitzt gegenwärtig keine Managementnetzredundanz.)`

Die Nachricht wird angezeigt, obwohl es zwei verfügbare Uplinks für den privaten verteilten Switch gibt, die eine Redundanz zur Verfügung stellen.

## Lösung
Dies ist ein bekanntes VMware-Problem. Zur Lösung des Problems befolgen Sie die Anweisungen auf der Seite [ESX/ESXi host displays warning message when test condition is false (2008602)](https://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2008602){:new_window}.
