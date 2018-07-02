---

copyright:

  years:  2016, 2018

lastupdated: "2017-12-29"

---

# Unterstützte Fehlerbehebung

## Problem

In einigen Situationen kann es zu einem komplexeren Problem kommen und die Protokolldateien reichen nicht aus, um die Ursachenanalyse vollständig durchzuführen und eine Lösung zur Verfügung zu stellen.

## Lösung

Um solche Probleme beheben und lösen zu können, benötigt das {{site.data.keyword.vmwaresolutions_full}}-Support-Team Zugriff auf die virtuelle Maschine (VM) für das Management der {{site.data.keyword.cloud_notm}}. Diese "IBM CloudDriver" genannte Management-VM ist die Hauptschnittstelle, die zum Verwalten der bereitgestellten VMware Cloud Foundation-Instanzen und VMware vCenter Server-Instanzen verwendet wird.

Der Zugriff auf IBM CloudDriver ist aus Sicherheitsgründen eingeschränkt. Das {{site.data.keyword.vmwaresolutions_short}}-Support-Team fordert eine Kundengenehmigung an und kann nach deren Erhalt mit einem Virtual Server der {{site.data.keyword.cloud_notm}}-Infrastruktur auf die CloudDriver-Komponenten zugreifen. Der Server bildet über das öffentliche Netz für den Front-End-Kundenrouter (Frontend Customer Router, FCR) der {{site.data.keyword.cloud_notm}}-Infrastruktur eine Brücke in die Umgebung.

Anschließend verwendet das {{site.data.keyword.vmwaresolutions_short}}-Support-Team den {{site.data.keyword.slapi_short}}-Schlüssel der {{site.data.keyword.cloud_notm}}-Infrastruktur, der für die Bestellung und Konfiguration der Instanz zur Verfügung gestellt wurde (bzw. erforderlichenfalls den vom Kunden bereitgestellten aktualisierten Schlüssel), um einen Virtual Server der {{site.data.keyword.cloud_notm}}-Infrastruktur mit stündlicher Abrechnung bereitzustellen.

Die Verwendung der Tools von IBM CloudBuilder für Fehlerbehebungszwecke wird dem Kundenkonto in Rechnung gestellt. Nachdem die Fehlerbehebung und Korrektur abgeschlossen ist, wird die IMB CloudBuilder-Komponente freigegeben.

Der Virtual Server der {{site.data.keyword.cloud_notm}}-Infrastruktur, der für die Fehlerbehebung verwendet wird, wird mit den folgenden Spezifikationen bereitgestellt:

* Es wird 1 Virtual Server-Instanz (VSI) mit 1 CPU und 1 GB RAM für einen öffentlichen Knoten mit CentOS 7 verwendet.
* Die VSI wird in demselben Rechenzentrum in demselben primären öffentlichen und privaten VLAN wie die Instanz bereitgestellt.
* Für die VSI wird ein Installationsabschlussscript verwendet, um Firewallregeln festzulegen, von denen nur eingehende SSH-Verbindungen von einer bestimmten Gruppe von IP-Adressen zugelassen werden, die dem {{site.data.keyword.vmwaresolutions_short}}-Support-Team gehören und von ihm verwendet werden.
* Das Startsystem für den Support, das diese IP-Adressen verwendet, wird auf einer virtuellen Maschine (VM) der {{site.data.keyword.cloud_notm}}-Infrastruktur ausgeführt, auf die nur über ein privates Netz der {{site.data.keyword.cloud_notm}}-Infrastruktur zugegriffen werden kann und die mit einem HA-Paar von Vyatta-Systemen der {{site.data.keyword.cloud_notm}}-Infrastruktur geschützt ist.
* Das Startsystem für den Support wird mit IBM Security-Tools wie QRadar®, Nessus und IBM BigFix® auf Sicherheitsbedrohungen hin überwacht.
