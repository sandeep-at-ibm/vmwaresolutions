---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-03"

---

# Prüfung und Auswertung

Wenn Sie Hosts, virtuelle Maschinen und virtuelle Appliances prüfen (scannen), werten Sie sie anhand von Baselines und Baselinegruppen aus, um ihre Konformitätsstufe zu ermitteln. Die Bestandsobjekte werden geprüft und die Ergebnisse ausgewertet, um zu ermitteln, wie sie den Baselines und Baselinegruppen entsprechen. Die Prüfergebnisse können anhand von Textsuche, Gruppenauswahl, Baselineauswahl und Konformitätsstatusauswahl gefiltert werden. Sie können die folgenden Prüfungen initiieren:
*	**Manuelles Initiieren einer Prüfung von vSphere ESXi-Hosts** - Sie können vSphere ESXi-Hosts im vSphere-Bestand anhand angehängter Baselines und Baselinegruppen prüfen.
*	**Manuelles Initiieren einer Prüfung von virtuellen Maschinen und virtueller Appliances** - Sie können virtuelle Maschinen und virtuelle Appliances anhand angehängter Baselines und Baselinegruppen prüfen.
*	**Manuelles Initiieren einer Prüfung eines Containerobjekts** - Sie können eine simultane Prüfung von Hosts, virtuellen Maschinen und virtuellen Appliances starten, indem Sie ein Containerobjekt prüfen, das ein Rechenzentrum oder ein Rechenzentrumsordner ist.
*	**Planen einer Prüfung** - Sie können den vSphere Web Client so konfigurieren, dass virtuelle Maschinen, virtuelle Appliances und ESXi-Hosts zu bestimmten Zeiten oder in den gewünschten Abständen durchsucht werden.

##	Prüfung von vSphere ESXi-Hosts manuell initiieren

1.	Klicken Sie auf die Schaltfläche **Auf Updates prüfen**, wählen Sie **Patches und Erweiterungen und Upgrades** aus und klicken Sie anschließend auf **OK**.
2.	Wenn die Prüfung abgeschlossen ist, wählen Sie **Kritische Host-Patches** aus und werten Sie die untere Anzeige nach den einzelnen Hosts aus.
3.	Wenn Sie auf die Zahl unter 'Anzahl Patches' klicken, zeigt ein Fenster die Patchdetails an.
4.	Nehmen Sie die Prüfung vor und wiederholen Sie den Vorgang für **Nicht kritische Patches**.

Beachten Sie, dass sich die VUM-Protokolldateien unter _/var/log/vmware/vmware-updatemgr/vum-server/vmware-vum-server-log4cpp.log_ befinden können.

##	Prüfung von virtuellen Maschinen und virtuellen Appliances manuell initiieren

Sie können virtuelle Maschinen und virtuelle Appliances anhand angehängter Baselines und Baselinegruppen prüfen. Die virtuellen Maschinen und Appliances, die Sie auswählen, werden - je nach den von Ihnen ausgewählten Optionen - anhand der angehängten Baselines geprüft. Alle untergeordneten Objekte werden ebenfalls geprüft, d. h. je größer die virtuelle Infrastruktur ist und je weiter oben in der Objekthierarchie sie die Prüfung initiieren, umso länger dauert die Prüfung und umso genauer wird die Konformitätsansicht.

1.	Bei Verwendung des vSphere Web Client wählen Sie **Home** > **VMs und Vorlagen** aus.
2.	Klicken Sie mit der rechten Maustaste auf eine _virtuelle Maschine_, eine _virtuelle Appliance_ oder einen _Ordner mit virtuellen Maschinen und Appliances_ und klicken Sie auf **Auf Updates prüfen**.
3.	Wählen Sie die Update-Typen aus, auf die geprüft werden soll. Die Optionen sind _Upgrades virtueller Appliances, VM-Hardware-Upgrades_ und _VMware Tools-Upgrades_.
4.	Klicken Sie auf **Prüfen**.

##	Prüfung eines Containerobjekts manuell initiieren

Sie können eine simultane Prüfung von Hosts, virtuellen Maschinen und virtuellen Appliances starten, indem Sie ein Containerobjekt prüfen, das ein Rechenzentrum oder ein Rechenzentrumsordner ist.
1.	Bei Verwendung des vSphere Web Client wählen Sie **Home** > **VMs und Vorlagen** aus.
2.	Klicken Sie mit der rechten Maustaste auf _Rechenzentrum_ oder _Rechenzentrumsordner_ und klicken Sie auf **Auf Updates prüfen**.
3.	Wählen Sie die Update-Typen aus, auf die geprüft werden soll. Die Optionen sind _Upgrades virtueller Appliances, VM-Hardware-Upgrades_ und _VMware Tools-Upgrades_.
4.	Klicken Sie auf **Prüfen**.

##	Prüfung planen

Sie können den vSphere Web Client so konfigurieren, dass virtuelle Maschinen, virtuelle Appliances und vSphere ESXi-Hosts zu bestimmten Zeiten oder in den gewünschten Abständen geprüft werden.

1.	Bei Verwendung des vSphere Web Client wählen Sie ein Objekt aus dem Bestand aus. Alle Objekte, die dem ausgewählten Objekt untergeordnet sind, werden ebenfalls geprüft.
2.	Wählen Sie die Registerkarte **Überwachen** und klicken Sie auf **Task und Ereignisse**.
3.	Wählen Sie **Geplante Tasks** aus und klicken Sie auf **Neue Task planen**.
4.	Wählen Sie in der dann angezeigten Dropdown-Liste die Option **Auf Updates prüfen** aus. Der Assistent für das Prüfen auf Updates wird geöffnet.
5.	Wählen Sie auf der Seite 'Einstellungen bearbeiten' die Typen von Updates aus, auf die das Bestandsobjekt geprüft werden soll. Sie müssen mindestens einen Prüftyp auswählen. Geben Sie auf der Seite 'Zeitplanungsoptionen' die Prüftask an und planen Sie sie.
6.	Geben Sie einen eindeutigen Namen und optional eine Beschreibung für die Prüftask ein. Klicken Sie auf **Ändern**, um die Häufigkeit und die Startzeit für die Prüftask festzulegen. Klicken Sie auf **OK**.
7.	Die Prüftask wird in der Ansicht 'Geplante Tasks' des vSphere Web Client aufgelistet.

### Zugehörige Links

* [VMware HCX on IBM Cloud Solution](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
