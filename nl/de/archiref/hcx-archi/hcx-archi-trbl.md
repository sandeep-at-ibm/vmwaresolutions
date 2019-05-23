---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---
# Fehlerbehebung für HCX on IBM Cloud
{: #hcx-archi-trbl}

## Cloud-Registrierung schlägt fehl
{: #hcx-archi-trbl-cloud-reg}

* Hybrid-Cloud-Services wiederholt den Versuch nicht, wenn die Berechtigungsnachweise falsch sind. Die Berechtigungsnachweise müssen authentifiziert werden, bevor Hybrid-Cloud-Services versucht, sich anzumelden und die Cloud-Registrierung zu starten.
* Die Cloud-Registrierung kann fehlschlagen, wenn die Berechtigungsnachweise falsch eingegeben wurden oder wenn die Berechtigungsnachweise für VCS Hybrid-Cloud-Services Cloud geändert werden, nachdem sich Hybrid-Cloud-Services bei VCS Hybrid-Cloud-Services Cloud registriert hat, und so eine fehlende Übereinstimmung entsteht.
* Um die Berechtigungsnachweise im Webclient zu aktualisieren, rufen Sie die Registerkarte "Erste Schritte mit Hybrid-Cloud-Services" auf und wählen Sie unter **Basistasks** die Option **Neue Cloud registrieren** aus.

## MAC-Adresse duplizieren
{: #hcx-archi-trbl-dupl-mac-addr}

Nach der Migration kann es zu Kommunikationsproblemen zwischen Ihren virtuellen Maschinen kommen. Wenn die MAC-Adresse während einer Migration beibehalten wird, kann versehentlich eine doppelte MAC-Adresse erstellt werden.

Zur Behebung dieses Problems kann die MAC-Adresse für die migrierte virtuelle Maschine geändert werden.

1. Schalten Sie im vSphere-Client die virtuelle Maschine aus.
2. Klicken Sie im Bestand mit der rechten Maustaste auf die virtuelle Maschine und wählen Sie im Menü die Option **Einstellungen bearbeiten** aus.
3. Erweitern Sie in der Registerkarte **Virtuelle Hardware** den Netzadapter.
4. Wählen Sie neben dem Textfeld "MAC-Adresse" die Option **Manuell** aus dem Menü aus.
5. Geben Sie eine eindeutige MAC-Adresse an und klicken Sie auf **OK**.
6. Überprüfen Sie, ob mit der eindeutigen MAC-Adresse das Kommunikationsproblem gelöst ist.

## Hoher Hostressourcenverbrauch
{: #hcx-archi-trbl-high-host-resource}

In seltenen Fällen, wenn sich alle virtuellen Service-Appliances auf demselben Host befinden, können die virtuellen Servicemaschinen von Hybrid-Cloud-Services die CPU- und Plattenressourcen eines Hosts vollständig beleben.

Einigen Benutzern begegnete dieses Problem, nachdem alle virtuellen Geräte auf einem physischen Host installiert worden waren. Bei dieser Konfiguration verschlechtert sich die Leistung, wenn die folgenden Dinge gleichzeitig passieren:
* Das Netz erhält eine hohe Latenzzeit oder einen Paketverlust oder beides. Die Migration oder der Datentransport verlangsamt sich, wenn Sie das öffentliche Internet oder ein ausgelastetes Netz verwenden.
* Das WAN-Optimierungsprogramm verbraucht Bandbreite, um große Workloads zu verschlüsseln und zu komprimieren (bzw. zu entschlüsseln und zu dekomprimieren).
* Es gibt einen hohen Anwendungsdatenverkehr zwischen lokalen und migrierten VMs.

Führen Sie die folgenden Schritte aus, um das Problem zu beheben:

1. Bevor Sie die Konfiguration des Rechenzentrums ändern, überprüfen Sie die Anforderungen an die Unterstützung eines stabilen Zustands.
2. Wenden Sie sich an den Support für stabilen Zustand, wenn Ressourcen bis an ihre Grenzen ausgelastet sind. Hier kann man Sie beraten, wie die Umgebung bei minimaler Ausfallzeit zu rekonfigurieren ist.

## Zugehörige Links
{: #hcx-archi-trbl-related}

* [HCX Manager bei vCenter registrieren](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-reg-vcenter)
* [HCX ändern oder deinstallieren](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
