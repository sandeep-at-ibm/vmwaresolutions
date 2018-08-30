---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-13"

---

# Design des Infrastrukturmanagements

Das Infrastrukturmanagement bezieht sich auf die Komponenten, die die VMware-Infrastruktur verwalten. Dieses Design arbeitet mit einer einzelnen externen PSC-Instanz (PSC - Platform Services Controller) und einer einzelnen vCenter Server-Instanz:
* Der vCenter Server ist die zentrale Plattform für die Verwaltung von vSphere-Umgebungen und gehört zu den grundlegenden Komponenten dieser Lösung.
* Der PSC wird in dieser Lösung dazu verwendet, eine Reihe von Infrastrukturservices wie den VMware vCenter Single Sign On-Service, den Lizenzservice, den Suchservice und den VMware-Zertifizierungsstellenservice bereitzustellen.

Die PSC-Instanzen und die vCenter Server-Instanzen sind separate virtuelle Maschinen (VMs).

## PSC-Design

In diesem Design wird ein einzelner externer PSC als virtuelle Appliance in einem portierbaren Teilnetz im privaten VLAN bereitgestellt, das den Management-VMs zugeordnet ist. Das zugehörige Standardgateway wird auf den Back-End-Kundenrouter (BCR - Back-end Customer Router) eingestellt. Die virtuelle Appliance wird mit den Spezifikationen in der folgenden Tabelle konfiguriert.

**Hinweis:** Diese Werte werden bei der Bereitstellung festgelegt und können nicht geändert werden.

Tabelle 1. Spezifikationen für Platform Services Controller

| Attribut                    | Spezifikation                  |
|------------------------------|--------------------------------|
| Platform Services Controller | Virtual Appliance              |
| Anzahl vCPUs              | 2                              |
| Speicher                       | 4 GB                           |
| Festplattenspeicher                         | 114 GB in lokalem VMFS-Datenspeicher |
| Plattentyp                    | Thin Provisioning-Platte               |

Dem PSC, der sich in der primären Instanz befindet, wird die SSO-Standarddomäne `vsphere.local` zugeordnet.

## vCenter Server-Design

Der vCenter Server wird ebenfalls als virtuelle Appliance bereitgestellt. Darüber hinaus wird der vCenter Server in einem portierbaren Teilnetz im privaten VLAN installiert, das den Management-VMs zugeordnet ist. Das zugehörige Standardgateway wird auf die IP-Adresse eingestellt, die auf dem Back-End-Kundenrouter (BCR) für dieses bestimmte Teilnetz zugeordnet wurde. Die virtuelle Appliance wird mit den Spezifikationen in der folgenden Tabelle konfiguriert.

Tabelle 2. vCenter Server Appliance-Spezifikationen

| Attribut                    | Spezifikation                       |
|------------------------------|-------------------------------------|
| vCenter Server               | Virtual Appliance                   |
| Appliance-Installationsgröße  | Mittel (bis zu 400 Hosts, 4000 VMs) |
| Platform Services Controller | Extern                            |
| Anzahl vCPUs              | 8                                   |
| Speicher                       | 24 GB                               |
| Festplattenspeicher                         | 400 GB auf lokalem Datenspeicher           |
| Plattentyp                    | Thin Provisioning-Platte                    |

### vCenter Server-Datenbank

Die vCenter Server-Konfiguration arbeitet mit einer lokalen, eingebetteten PostgreSQL-Datenbank, die in die Appliance integriert ist. Die eingebettete Datenbank dient zur Beseitigung aller Abhängigkeiten von externen Datenbanken und Lizenzierungen.

### vCenter Server-Clusterspezifikation

In diesem Design können Sie die vSphere ESXi-Hosts, die durch die Lösung zur Verfügung gestellt werden, in einem Cluster konfigurieren. Bevor jedoch Cluster erstellt werden können, wird ein Rechenzentrumsobjekt (RZ-Objekt) erstellt, das die Position der vSphere ESXi-Hosts sowie den Pod innerhalb des Rechenzentrums bezeichnet. Nach der Erstellung des RZ-Objekts wird ein Cluster erstellt. Der Cluster wird mit aktivierter VMware vSphere High Availability (HA) und aktiviertem VMware vSphere Distributed Resource Scheduler (DRS) bereitgestellt.

### vSphere Distributed Resource Scheduler

Dieses Design verwendet vSphere Distributed Resource Scheduling (DRS) im ersten Cluster, um VMs anzuordnen, und verwendet DRS in weiteren Clustern, um VMs zur Erzielung ausgeglichener Cluster dynamisch zu migrieren. Die Automatisierungsstufe ist auf vollständig automatisiert eingestellt, sodass die erste Anordnung und Migrationsempfehlungen von vSphere automatisch ausgeführt werden. Ferner wird der Migrationsschwellenwert auf moderat eingestellt, sodass vCenter Empfehlungen der Priorität 1, 2 und 3 anwendet, um wenigstens eine annehmbare Verbesserung in der Lastverteilung des Clusters zu erreichen.

**Hinweis:** Das Energiemanagement unter Verwendung der Komponente **Distributed Power Management** wird in diesem Design nicht verwendet.

### vSphere-Hochverfügbarkeit

In diesem Design wird vSphere High Availability (HA) im ersten Cluster und in weiteren Clustern verwendet, um Verarbeitungsfehler zu erkennen und VMs wiederherzustellen, die in einem Cluster ausgeführt werden. Das vSphere HA-Feature in diesem Design wird mit den im Cluster aktivierten Optionen **Hostüberwachung** (Host Monitoring) und **Zugangssteuerung** (Admission Control) konfiguriert. Darüber hinaus reserviert der erste Cluster die Ressourcen eines Knotens als Ersatzkapazität für die Zugangssteuerungsrichtlinien.

**Hinweis:** Sie sind dafür verantwortlich, die Zugangssteuerungsrichtlinie anzupassen, wenn der Cluster später erweitert oder verkleinert wird.

Die Option der VM-Neustartpriorität (**VM restart priority**) wird standardmäßig auf Mittel ("medium") gesetzt und die Option der Antwort für Hostisolation (**Host isolation response**) wird inaktiviert. Darüber hinaus wird die VM-Überwachung (**VM monitoring**) inaktiviert und die Funktion zum Austausch von Datenspeicherüberwachungssignalen (**Datastore Heartbeating**) wird so konfiguriert, dass alle Clusterdatenspeicher einbezogen werden. Dieses Konzept verwendet die NAS-Datenspeicher, wenn sie vorhanden sind.

## Automatisierung

Das wesentliche Kennzeichen für diese Lösungen ist die Automatisierung. Die Automatisierung bietet die folgenden Vorteile:
* Vereinfachung der Bereitstellung.
* Drastische Verkürzung der Bereitstellungszeit.
* Sicherstellung, dass die VMware-Instanz in konsistenter Weise bereitgestellt wird.

{{site.data.keyword.IBM}} CloudBuilder-, IBM CloudDriver- und SDDC Manager-VMs arbeiten zusammen, um eine neue VMware-Instanz verfügbar zu machen und Lebenszyklusmanagementfunktionen auszuführen.

### IBM CloudBuilder und IBM CloudDriver

Die virtuellen Serverinstanzen (VSI) für IBM CloudBuilder und IBM CloudDriver sind von IBM entwickelte Komponenten, auf die Sie nicht zugreifen können.
* Die IBM CloudBuilder-Instanz ist eine temporäre {{site.data.keyword.cloud_notm}}-VSI, die die Bereitstellung, Konfiguration und Validierung der Lösungskomponenten innerhalb der bereitgestellten Bare Metal-ESXi-Hosts startet.
* Die IBM CloudDriver-VSI wird für die Instanzerstellung bereitgestellt und anschließend nach Bedarf in regelmäßigen Abständen mit dem neuesten {{site.data.keyword.cloud_notm}} for VMware-Code für Operationen wie das Bereitstellen weiterer Knoten, Cluster oder Services verwendet. IBM CloudDriver kommuniziert mit der Konsole von {{site.data.keyword.vmwaresolutions_short}} über ein VMware NSX Edge Services Gateway, das exklusiv für Instanzmanagementzwecke bereitgestellt wurde, und fungiert als Agent zur Verwaltung der Instanz. IBM CloudDriver ist für laufende Aktionen verantwortlich, wie das Hinzufügen neuer Bare-Metal-Hosts zum Cluster und das Bereitstellen von Add-on-Services in der Instanz. Bei Cloud Foundation-Instanzen kommuniziert IBM CloudDriver mit der VMware SDDC Manager-VM, um Funktionen wie das Hinzufügen von Hosts oder Aktualisierungen von Hosts auszuführen.

Es ist möglich, dass der Benutzer die in den folgenden Abschnitten beschriebenen VMs löscht oder beschädigt. Wenn eine VM entfernt, heruntergefahren oder nicht funktionsfähig wird, werden die folgenden Cloud Foundation- oder vCenter Server-Operationen in der Konsole von {{site.data.keyword.vmwaresolutions_short}} unterbrochen:
* Anzeigen des Instanz- oder Hoststatus
* Hinzufügen oder Entfernen von Clustern
* Hinzufügen oder Entfernen von ESXi-Hosts
* Hinzufügen oder Entfernen von Services
* Patches

### SDDC Manager

Bei Cloud Foundation-Instanzen ist die SDDC Manager-VM eine Komponente, die von VMware entwickelt und gewartet wird. Sie bleibt während ihres gesamten Lebenszyklus ein Teil der Instanz. Sie ist für die folgenden Lebenszyklusfunktionen von Instanzen verantwortlich:
* Management von VMware-Komponenten: vCenter Server, Platform Services Controller (PSC), vSAN und NSX, einschließlich IP-Adresszuordnung und Hostnamensauflösung.
* Erweiterung und Zurückziehung von ESXi-Hosts im Cluster, einschließlich betroffener Services wie NSX-VTEP, vSAN, Ressourcenpools.

Bei vCenter Server-Instanzen werden diese Aktivitäten durch IBM CloudDriver ausgeführt, da kein SDDC Manager vorhanden ist.

### Automatisierungsablauf

Die folgende Prozedur beschreibt die Reihenfolge der Ereignisse, wenn eine VMware-Instanz über die Konsole von {{site.data.keyword.vmwaresolutions_short}} bestellt wird:
1.  Bestellung von VLANs und Teilnetzen für den Netzbetrieb von {{site.data.keyword.cloud_notm}}.
2.  Bestellung von {{site.data.keyword.baremetal_short}} mit installiertem vSphere Hypervisor.
3.  Sofern zutreffend: Bestellung von Microsoft Windows Virtual Server Instance (VSI) für die Funktion als Active Directory-Domänencontroller.
4.  Validierung der Vernetzung und der bereitgestellten Hardware.
5.  Sofern zutreffend: Erstkonfiguration eines vSAN mit einzelnem Knoten.
6.  Sofern zutreffend: Bereitstellung und Konfiguration von zwei virtuellen Microsoft Windows-Maschinen für die Funktion als Active Directory-Domänencontroller.
7.  Bereitstellung und Konfiguration von vCenter, PSC und NSX.
8.  Clustering der übrigen ESXi-Knoten, Erweiterung von vSAN, sofern zutreffend, und Konfiguration von NSX-Komponenten (VTEP).
9.  Bereitstellung der VMware Cloud Foundation-SDDC Manager-VM, sofern zutreffend, und der IBM CloudDriver-VSI.
10.  Validierung der Installation und Konfiguration der Umgebung.
11. Entfernung der CloudBuilder-VSI.
12. Bereitstellung optionaler Services, wie Sicherungsserver und -speicher.

### Zugehörige Links

* [Design der physischen Infrastruktur](design_physicalinfrastructure.html)
* [Design der virtuellen Infrastruktur](design_virtualinfrastructure.html)
* [Design der allgemeinen Services](design_commonservice.html)
