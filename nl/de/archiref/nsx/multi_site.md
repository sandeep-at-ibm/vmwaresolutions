---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# Architektur mit mehreren Standorten

Ein wichtiges Differenzierungsmerkmal zwischen {{site.data.keyword.cloud}} und anderen Cloud-Angeboten ist die Fähigkeit, dedizierte Rechenleistung weltweit bereitzustellen und automatisch eine bedarfsgesteuerte Infrastruktur mit dem Netz in Ihrem privaten {{site.data.keyword.cloud_notm}}-Konto zu verbinden. Die softwaredefinierten Netzfunktionen von VMware vCenter Server und VMware Cloud Foundation zusammen mit {{site.data.keyword.cloud_notm}} stellen eine differenzierte globale Infrastruktur bereit, die innerhalb weniger Tage erstellt werden kann. In den folgenden Abschnitten wird ein Beispiel für eine Architektur mit mehreren Standorten beschrieben, das zeigt, was mit der Out-of-the-box-Funktionalität von vCenter Server oder Cloud Foundation erreicht werden kann.

## Cross-vCenter NSX-Umgebung

Die Cross-vCenter NSX-Funktionalität ermöglicht die Verknüpfung von bis zu neun NSX-Managern - in einer Beziehung von einem primären und acht sekundären NSX-Managern. vCenter Server in einer ELM-Beziehung (Enhanced Linked Mode) sind zwar nicht für den Betrieb von Cross-vCenter NSX erforderlich, sie bieten jedoch die folgenden Vorteile:

* Vereinfachte Erstellung einer Primär/Sekundär-Beziehung mithilfe von SSO-Berechtigungsnachweisen (SSO = Single Sign-on)
* Konfiguration der vCenter Server- und Cloud Foundation-Automation für die DNS-Namensauflösung für alle verbundenen Standorte
* Zentrales Management auf einen Blick über alle Standorte hinweg für NSX- und normale vCenter-Funktionen

## Beispiel für mehrere Standorte

Im folgenden Beispiel wird eine NSX Universal Transport Zone zu den Basismanagement- und Workloadtopologien hinzugefügt, die in den vorherigen Abschnitten beschrieben wurden, zusätzlich zu den folgenden Merkmalen:

* Die Universal Transport Zone erstreckt sich über zwei {{site.data.keyword.CloudDataCents_notm}} oder PODs innerhalb eines {{site.data.keyword.CloudDataCent_notm}}.
* Nachdem die Transportzone hinzugefügt wurde, werden mehrere VXLANs zusammen mit einem Universal Distributed Router hinzugefügt, der sich über die neuen VXLANs erstreckt.
* Sie müssen Uplinks zu den Workload-ESGs an beiden Standorten konfigurieren. Bei dieser Konfiguration können virtuelle Maschinen (VMs) am lokalen Standort zum lokalen ESG traversieren.
* Für den eingehenden Datenverkehr ist eine globale Lastausgleichsfunktion erforderlich. Informieren Sie sich über die {{site.data.keyword.cloud_notm}}-Angebote für einen globalen Lastausgleich, um diese Anforderung zu erfüllen.
* Für dieses Beispiel ist VMware NSX Enterprise Edition erforderlich.

Abbildung 1. Topologie mit mehreren Standorten

![Topologie mit mehreren Standorten](multisite_topology.svg "Topologie mit mehreren Standorten")

### Zugehörige Links

* [Netzservices unter {{site.data.keyword.cloud_notm}}](networking_services.html)
