---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX ändern oder deinstallieren
{: #hcxclient-removal-uninstall}

Für vorhandene Installationen kann ein Upgrade durchgeführt werden. Alternativ können einige oder alle Bereitstellungen von Hybrid-Cloud-Services entfernt werden.

##  Rückgängigmachen der Erweiterung eines Layer-2-Netzes
{: #hcxclient-removal-uninstall-unstretch-layer2}

Bevor Sie die zugeordnete virtuelle Service-Appliance für den Layer-2-Konzentrator entfernen oder Hybrid-Cloud-Services deinstallieren, muss die Erweiterung eines Layer-2-Netzes rückgängig gemacht werden.

1. Überprüfen Sie die erweiterten Netze.
2. Auf der Plug-in-Seite von Hybrid-Cloud-Services zeigen Sie die Registerkarte "Hybrid-Services" an und überprüfen Sie den Abschnitt "Network Extension Service". Wenn aktive oder geplante Jobs in Bearbeitung sind, warten Sie, bis sie abgeschlossen sind, oder stoppen Sie sie, bevor Sie fortfahren.
3. Um das Netz zu entfernen, klicken Sie auf das Symbol "Löschen" (rotes X) auf der rechten Seite.
4. Klicken Sie zur Bestätigung auf **OK**.

## Virtuelle HCX-Appliances deinstallieren
{: #hcxclient-removal-uninstall-uninst-hva}

Eine Service-Appliance kann in Vorbereitung auf die Deinstallation von Hybrid-Cloud-Services oder aufgrund einer Änderung in der Installationsarchitektur deinstalliert werden. Verwenden Sie Hybrid-Cloud-Services, um Appliances zu verwalten, wie in der folgenden Prozedur beschrieben.

### Voraussetzungen für die Deinstallation von virtuellen HCX-Appliances
{: #hcxclient-removal-uninstall-prereq-uninst-hva}

* Brechen Sie die Ausführungszeit für alle Migrationen ab, die während der Deinstallationstask auftreten können, oder setzen Sie sie zurück.
* Überprüfen Sie die vSphere Web Client-Taskkonsole auf aktive Migrationen und warten Sie, bis sie abgeschlossen sind.
* Stellen Sie sicher, dass keine aktiven Hybrid-Cloud-Services-Tasks jeglicher Art vorhanden sind.

Löschen Sie keinesfalls virtuelle Appliances aus dem vSphere-Bestand. Verwenden Sie für die Interaktion mit virtuellen Service-Appliances stets das Managementportal.
{:note}

### Vorgehensweise zum Deinstallieren von virtuellen HCX-Appliances
{: #hcxclient-removal-uninstall-proc-uninst-hva}

1. Wählen Sie in der vSphere Web Client-Schnittstelle das Hybrid-Cloud-Services-Plug-in aus dem linken Teilfenster aus.
2. Klicken Sie im mittleren Teilfenster auf die Registerkarte **Hybrid-Services**.
3. Suchen Sie die Hybrid-Cloud-Gateway-Appliance und klicken Sie auf den Eintrag, um die Details anzuzeigen.
4. Klicken Sie unten rechts auf das Symbol "Löschen", um die Appliance zu entfernen.
5. Wenn ein erweitertes Netz keine IP-Adresse mit dem Hybrid-Cloud-Gateway gemeinsam nutzt, müssen Sie es separat entfernen. Erweitern Sie die Details zu "Network Extensions Service" und klicken Sie auf das Symbol "Löschen", um den Layer-2-Konzentrator zu entfernen.

Das Hybrid-Cloud-Gateway und alle virtuellen Hybrid-Services-Appliances, die das Hybrid-Cloud-Gateway nutzen, werden sowohl aus vCenter als auch aus der VCS-Cloud für Hybrid-Cloud-Services entfernt.

## HCX-Manager deinstallieren
{: #hcxclient-removal-uninstall-unist-hcxm}

Die HCX-Manager-Appliance sollte deinstalliert werden, bevor Sie die HCX-Lösung aus dem lokalen Rechenzentrum entfernen. Führen Sie die folgenden Schritte aus, um die virtuelle Hybrid-Cloud-Services-Maschine zu deinstallieren.

1. Machen Sie die Erweiterung aller Layer-2-Netze rückgängig.
2. Entfernen Sie die virtuellen Appliances für Hybrid-Services.
3. Schalten Sie in der lokalen vCenter-Instanz die virtuelle Hybrid-Cloud-Services-Maschine aus.
4. Löschen Sie die virtuelle Hybrid-Cloud-Services-Maschine.

Alle virtuellen Service-Appliances werden entfernt. Die folgenden Elemente bleiben möglicherweise zurück:
* Protokolle
* Migrierte VMs

### Nächste Schritte
{: #hcxclient-removal-uninstall-what-next}

Die migrierten VMs und Protokolle können manuell gesichert oder gelöscht werden.

## Anmelden am HCX-Managementportal
{: #hcxclient-removal-uninstall-log-hcxmp}

Die Hybrid-Cloud-Services-Bereitstellung kann mithilfe einer browserbasierten Benutzerschnittstelle über das Managementportal verwaltet werden.

1. Geben Sie in einem Web-Browser die IP-Adresse ein, die Hybrid-Cloud-Services zugeordnet ist, und geben Sie die Portnummer 9443 an. Beispiel: `https://HCXip:9443`.
2. Die Hybrid-Cloud-Services-Benutzerschnittstelle wird unter Verwendung von SSL in einem Web-Browser-Fenster geöffnet. Akzeptieren Sie gegebenenfalls das Sicherheitszertifikat. Die Anmeldeanzeige für VMware Hybridity und Vernetzung wird angezeigt.
3. Geben Sie den Benutzernamen und das Kennwort ein. Der Benutzername lautet standardmäßig "Admin". Das Kennwort ist der Wert, der bei der Installation der virtuellen Hybrid-Cloud-Services-Appliance angegeben wurde.

## Zugehörige Links
{: #hcxclient-removal-related}

* [Glossar der HCX-Komponenten und -Begriffe](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Installationsumgebung vorbereiten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Bereitstellung des HCX-Clients](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Lokales HCX-Servicenetz](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud-Migrationen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Überwachung von Parametern und Komponenten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Fehlerbehebung für HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
