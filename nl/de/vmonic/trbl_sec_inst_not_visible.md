---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, secondary vCenter, vSphere inventory issue

subcollection: vmware-solutions


---

# Sekundäres vCenter Server-System ist im Bestand von vSphere Web Client nicht angegeben
{: #trbl_sec_inst_not_visible}

## Problem
{: #trbl_sec_inst_not_visible-problem}

Nachdem Sie in einer Konfiguration mit mehreren Standorten eine neue sekundäre Instanz hinzugefügt haben, ist deren vCenter Server-System nicht mehr sichtbar, wenn Sie bei VMware vSphere Web Client in einer zuvor bestellten Instanz angemeldet sind.

## Lösung
{: #trbl_sec_inst_not_visible-resolution}

Dies ist ein bekanntes Problem von VMware 6.5.

Zur Lösung des Problems müssen Sie vSphere Web Client erneut starten:

1. Stellen Sie unter Verwendung des **Rootkontos** eine Verbindung über **ssh** zur virtuellen vCenter-Maschine der zuvor bestellten Instanz her.
2. Geben Sie ``shell`` ein, um die Bash-Shell zu aktivieren.
3. Geben Sie `service-control --stop vsphere-client` ein, um den Client zu stoppen.
4. Geben Sie `service-control --start vsphere-client` ein, um den Client erneut zu starten.
5. Vergewissern Sie sich nach dem Neustart von vSphere Web Client der zuvor bestellten Instanz, dass das vCenter Server-System für die neu hinzugefügte sekundäre Instanz in vSphere Web Client sichtbar ist.
