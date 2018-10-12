---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Beim Hinzufügen eines HA-Clusters festgestelltes Konfigurationsproblem für die vSphere-Konsole

## Problem
Beim Hinzufügen einer Clusterkonfiguration für die Hochverfügbarkeit (High Availability, HA) mit einer einzigen gemeinsam genutzten Dateiressource tritt das folgende Konfigurationsproblem auf den ESXi-Hosts auf:

`Die Anzahl der Überwachungssignaldatenspeicher für Host ist 1, also kleiner als der erforderliche Wert: 2`

## Lösung
Dieses Problem tritt auf, wenn es im gemeinsam genutzten Speicher keine Redundanz gibt, die den Austausch von Überwachungssignalen für Datenspeicher ermöglicht.

Weitere Informationen und Schritte zur Korrektur des Problems finden Sie auf der Seite [HA error: "The number of heartbeat data for host is 1, which is less than required: 2" (2004739)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739).
