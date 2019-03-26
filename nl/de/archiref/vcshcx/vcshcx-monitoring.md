---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Überwachung von Parametern und Komponenten
{: #vcshcx-monitoring}

## WAN-Optimierungsprogramm für die Überwachung verwenden
{: #vcshcx-monitoring-using-wan}

Für die Silver Peak WAN-Optimierungsappliance, die als Teil von HCX bereitgestellt wird, wird die Verwaltungsschnittstelle nicht konfiguriert. Die Webbenutzerschnittstelle (UI) ist ein wertvolles Tool, um eine Baseline für den Datenverkehrdurchsatz und für die Bandbreitennutzung zur Regulierung der Netzmigration zu erstellen.

Nur der HCX-CGW-Gateway-WAN-Tunnel-Datenfluss fließt durch die WAN-Optimierungs-Appliance. Daher kann er erweiterten L2-Datenverkehr nicht überwachen.
{:note}

### Schnittstelle konfigurieren
{: #vcshcx-monitoring-config-ui}

Wenn Sie nicht gerade eine IP-Adresse für die Webbenutzerschnittstelle konfigurieren, nehmen Sie keine Konfigurationsänderungen an der WAN-Optimierungs-Appliance vor, es sei denn, Sie werden von {{site.data.keyword.IBM}} oder von Mitarbeitern des VMware-Supports dazu angewiesen.   

So konfigurieren Sie die Webbenutzerschnittstelle für die WAN-Optimierung:
1.	Suchen Sie die virtuelle Maschine (VM) für die WAN-Optimierungs-Appliance im vCenter-Client.
2.	Öffnen Sie eine Konsole für die VM, die den vCenter-Client verwendet.
3.	Klicken Sie in der Konsole auf **F4**, um die Managementschnittstelle zu konfigurieren.
4.	Wählen Sie die Konfiguration einer statischen IP.
5.	Verwenden Sie eine IP-Adresse für den der Management-{{site.data.keyword.cloud}} zugeordneten Bereich portierbare IP-Adressen und das Standardgateway.
6.	Klicken Sie zum Speichern im nächsten Bildschirm auf **Anwenden**.
7.  Klicken Sie in der vCenter-Konsole auf die Einstellungen für die VM für WAN-Optimierung.
8.	Wählen Sie **Verbinden beim Einschalten** und **Verbunden für Netzadapter 1** aus.
9.	Klicken Sie zum Speichern auf **OK**.
10.	Suchen Sie CGW-<xxx>-WANOPT in vCenter.
11.	Bearbeiten Sie die Einstellungen für die VM.
12.	Klicken Sie auf das Kontrollkästchen, um Netzwerkadapter 1 anzuschließen.
13.	Klicken Sie auf **OK**.
14.	Rufen Sie folgende Adresse auf: `https://<configured_WAN_OPT_IP>`.
15.	Melden Sie sich mit dem `admin`-Standardbenutzer und dem `admin`-Kennwort an.

Sie können jetzt die Webbenutzerschnittstelle des WAN-Optimierungsprogramms verwenden, um Durchsatzraten und Komprimierungsverhältnisse zu überwachen sowie um Einschränkungen der Bandbreite festzulegen. 

### Bandbreitenregulierung bei der Migration
{: #vcshcx-monitoring-mig-bandwidth}

Bevor Sie VMs migrieren, führen Sie eine Bewertung der verwendeten Netzverbindung durch. Arbeiten Sie zusammen mit Netzentwicklern an dem Netz, das die Quelleninstanz von vSphere enthält, oder prüfen Sie wöchentlich und monatlich den Datenverkehr. Begrenzen Sie die verfügbare Bandbreite für Migrationen, wenn dieser Datenverkehr einen für Ihr Geschäft kritischen Link überquert, insbesondere wenn dieser Link weniger als 1 Gb/s beträgt. Verwenden Sie die Seite mit der am stärksten eingeschränkten Bandbreite. Typischerweise ist dies die Clientseite.

Dies ist dann angebracht, wenn Sie die Paketkomponenten in der HCX-Client-Benutzerschnittstelle bereitstellen, aber die Nachbereitstellung erfordert, dass Sie zur Benutzerschnittstelle für die WAN-Optimierung wechseln.

Änderungen gehen verloren, wenn Sie den HCX-CGW über die HCX-Webbenutzerschnittstelle erneut bereitstellen.
Dadurch werden Bandbreitengrenzwerte nur für den Migrationsdatenverkehr festgelegt. Erweiterter L2-Datenverkehr wird von dieser Einstellung nicht beeinflusst.
{:note}

1. Melden Sie sich bei der Webbenutzerschnittstelle für das WAN-Optimierungsprogramm an. 
2. Wählen Sie auf der Registerkarte **Konfiguration** die Option **Shaper** aus dem Dropdown-Menü aus.
3. Legen Sie im Feld **Max. Bandbreite** die maximale Bandbreite in Kb/s fest, die für die WAN-Optimierungs-Appliance verfügbar ist. Überschreiten Sie nicht die maximale Bandbreite der WAN-Verbindung. Um den Wert in Mb/s festzulegen, multiplizieren Sie die Zahl mit 1.000. Um den Wert in Gb/s festzulegen, multiplizieren Sie die Zahl mit 1.000.000. Der Standardwert ist 10 Gb/s (10.000.000 Kb/s). 
4. Klicken Sie auf **Anwenden**.

Zur Bandbreitenregulierung für erweitertes L2 kann QoS für UDP 500 und 4500 für den Tunnelverkehr zwischen den L2C-Appliances eingesetzt werden.

## HCX-Komponenten überwachen
{: #vcshcx-monitoring-hcx-comp}

Sie können HCX-Komponenten wie HCX-Manager, Cloud-Gateway, WAN-Optimierung und die Layer-2-Konzentrator-Operationen auf folgende Arten überwachen:

- Konfigurieren Sie den HCX-Manager für das Senden von Protokollen an einen Syslog-Server. Verwenden Sie das Verwaltungsdienstprogramm der HCX-Manager-Appliance, um `https://<hcxhostname or
IP>:9443` auszuführen.
- Richten Sie ein Pingsignal an eine VM ein, die vor dem Netz-Swing für jedes erweiterte L2-Netz migriert wurde.
- Überwachen Sie den Zustand der VM für die HCX-Komponente mit VMware vRealize Operations Manager oder anderen VMware VM-Überwachungstools.

## Bandbreitennutzung
{: #vcshcx-monitoring-band-use}

Mit den folgenden Methoden können Sie die Bandbreitennutzung und die Latenzzeit überwachen.

- vMotion Traffic wird am besten über die Webbenutzerschnittstelle für das WAN-Optimierungsprogramm realisiert. Das WAN-Optimierungsprogramm reduziert den Datenverkehr, der über das WAN geht, drastisch und reduziert den Paketverlust durch das Senden von redundanten Paketen. Es wurde beobachtet, dass das typische Verhältnis von LAN- zu WAN-Bandbreite ungefähr 3:1 beträgt (350 Mb/s LAN = 90-120 Mb/s WAN). 

- Die replikationsbasierte (Massen-)Migration von VMs in HCX führt zur Verschiebung von VMs mit Thick Provisioning. Während dies nicht wünschenswert ist, zeigt die Benutzerschnittstelle des WAN-Optimierungsprogramms ein hohes Verhältnis zwischen LAN- und WAN-Nutzung an, wenn Sie die Daten nicht verwendeter Platten verschieben. Umgekehrt ist zu beobachten, dass bei der Migration von nicht komprimierbaren Daten wie DB-Daten und digitalen Medien die WAN-Nutzung am höchsten ist und der LAN-Nutzung näher kommt. 

Beobachtungen:
- Die vMotion-Migration einer VM innerhalb von HCX erzeugt nicht mehr Durchsatz als der vMotion-Netzbetrieb für einen einzelnen ESXi-Host. 
- Da bei der Massenmigration mehrere Migrationen gleichzeitig ausgeführt werden können, erreicht sie eine höhere Bandbreitennutzung als die vMotion-Migration. Das auf Kundenseite beobachtete Verhältnis mit vMotion-Links von 1 Gb/s zu den ESX-Hosts betrug acht Replikationen = Bandbreitennutzung von 1 vMotion.
- Das Verschieben von leerem Bereich auf die Platte führt zur Anzeige einer hohen LAN-Nutzung mit einem hohen Verhältnis und daher niedrigen WAN-Nutzung. Beachten Sie, dass 1 Gb/s der Grenzwert zu sein scheint. In diesem speziellen Fall ist das vMotion-Netz nur zu 1 Gb/s in der Lage, stellt also den Engpass dar.
- vMotion-Migration einer Oracle-Datenbank von mehreren TB. Bei einer WAN-Verbindung von 1 Gb/s ist die Begrenzung das vMotion-Netz mit 1 Gb/s.

## Erweiterter Layer-2-Datenverkehr
{: #vcshcx-monitoring-stretched-layer-2-traffic}

Der Layer-2-Konzentrator der HCX-Paketkomponente hat eine Bandbreitenbegrenzung von ungefähr 4 Gb/s für den gesamten L2-Netzverkehr, der ihn durchquert. Einzelne erweiterte Netze haben je nach Datenverkehrstyp eine Bandbreitenbegrenzung von maximal ca. 1 Gb/s. Es ist möglich, mehrere erweiterte L2-Netze über ein einziges L2C-Paar zu betreiben (theoretisch zulässig sind maximal 4096 Netze pro L2C-Paar). Während der L2C so konstruiert ist, dass kleine Datenflüsse erkannt und vor großen Datenflüssen im selben L2C-Paar geschützt werden, kann es von Vorteil sein, festzustellen, ob diese Situation auftritt, und weitere L2Cs zur Erhöhung der verfügbaren Gesamtbandbreite aufzubringen.

Die Bereitstellung mehrerer L2Cs kann auch dann vorteilhaft sein, wenn zwischen dem Kundenstandort und {{site.data.keyword.cloud}} mehrere Pfade vorhanden sind, z. B. eine direkte Verbindung und das Internet. Ein einzelnes Netz kann nicht redundant gemacht werden oder mit einer höheren Bandbreite über mehrere L2C-Paare hinweg ausgestattet werden.

Sie können den Datenverkehr über alle Schnittstellen überwachen, die die Registerkarte "Überwachung" der L2C-VM verwenden. Wenn sich die Gesamtdatenrate 8 Gb/s (4 Gb/s ein/aus) nähert, können Sie ein weiteres L2-Paar hinzufügen und die erweiterten Netze neu verteilen, um einen neuen Ausgleich zu erhalten.

## Zugehörige Links
{: #vcshcx-monitoring-related}

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
