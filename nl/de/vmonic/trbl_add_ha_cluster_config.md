---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: troubleshooting, vSphere configuration issue, HA cluster issue

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# Beim Hinzufügen eines HA-Clusters festgestelltes Konfigurationsproblem für die vSphere-Konsole
{: #trbl_add_ha_cluster_config}

## Problem
{: #trbl_add_ha_cluster_config-problem}

Beim Hinzufügen einer Clusterkonfiguration für die Hochverfügbarkeit (High Availability, HA) mit einer einzigen gemeinsam genutzten Dateiressource tritt das folgende Konfigurationsproblem auf den ESXi-Hosts auf:

> Die Anzahl der Überwachungssignaldatenspeicher für Host ist 1, also kleiner als der erforderliche Wert: 2

## Lösung
{: #trbl_add_ha_cluster_config-resolution}

Dieses Problem tritt auf, wenn es im gemeinsam genutzten Speicher keine Redundanz gibt, die den Austausch von Überwachungssignalen für Datenspeicher ermöglicht.

Weitere Informationen und Schritte zur Korrektur des Problems finden Sie auf der Seite [HA-Fehler: Die Anzahl der Überwachungssignaldatenspeicher für Host ist 1, also kleiner als der erforderliche Wert: 2 (2004739)](https://kb.vmware.com/s/article/2004739).{:external}
