---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Redundanz virtueller vSAN-Maschinen

Wenn Sie einen vSphere ESXi-Host in einem vSAN-Cluster in den Wartungsmodus versetzen, müssen Sie einen Datenevakuierungsmodus auswählen. Die Auswahl des Modus kann Auswirkungen auf die virtuellen Maschinen (VMs) und auf Appliances haben, die den vSAN-Datenspeicher verwenden:
* Eine **vollständige Datenmigration** evakuiert alle Daten von einem Host und verschiebt sie auf die anderen vSphere ESXi-Hosts im vSAN-Cluster. Dieser Evakuierungsmodus erzeugt ein sehr hohes Datenvolumen und ist sehr zeit- und ressourcenintensiv. Alle Komponenten im lokalen Speicher des ausgewählten Hosts werden an eine andere Stelle im Cluster migriert. Wenn der Host in den Wartungsmodus wechselt, haben alle VMs und Appliances Zugriff auf ihre Speicherkomponenten und sind immer noch mit den zugeordneten Speicherrichtlinien kompatibel. Die vollständige Evakuierung der Daten kann lange dauern und auch das Wartungsfenster für ein Upgrade erheblich verlängern.
* Der Modus für den **sichergestellten Zugriff** bei der Datenevakuierung ist die Standardoption. Wenn der vSphere ESXi-Host in den Wartungsmodus versetzt wird, stellt vSAN sicher, dass alle zugänglichen VMs oder Appliances auf dem Host zugänglich bleiben. Da nur eine teilweise Datenevakuierung erfolgt, ist die virtuelle Maschine (VM) oder die virtuelle Appliance während der Evakuierung möglicherweise nicht mehr vollständig mit einer VM-Speicherrichtlinie kompatibel und hat nicht mehr auf alle zugeordneten Replikate Zugriff. Wenn ein Fehler auftritt, während sich der Host im Wartungsmodus befindet, und die primäre Ebene der tolerierbaren Fehler auf 1 gesetzt ist, kommt es zu Datenverlusten und die virtuelle Maschine (VM) oder die Appliance ist möglicherweise nicht verfügbar.
* Im Modus **Keine Datenmigration** evakuiert vSAN beim Wechseln in den Wartungsmodus keine Daten vom Host. Dadurch kann zwar schneller in den Wartungsmodus gewechselt werden und das Wartungsfenster wird verkürzt, möglicherweise sind aber manche virtuelle Maschinen (VMs) oder Appliances nicht mehr zugänglich.

In diesem Abschnitt wird eine neue Speicherrichtlinie für virtuelle Maschinen (VMs) erstellt, sodass der Modus für den **sichergestellten Zugriff** bei der Datenevakuierung ausgewählt werden kann, um die Wartungsfenster zu reduzieren; gleichzeitig wird aber das Risiko gemindert, dass ein Ausfall eines Hosts - während sich ein anderer Host im Wartungsmodus befindet - dazu führt, dass eine virtuelle Maschine oder eine Appliance nicht mehr zugänglich ist. Für jede virtuelle Maschine (VM) oder Appliance, bei der stets Redundanz sichergestellt sein muss, wenn ein vSAN-Host in den Wartungsmodus versetzt wird, ist der folgende Prozess vor dem Ausführen von Korrekturmaßnahmen durchzuführen. Es ist ein Cluster mit mindestens sechs Hosts erforderlich.

1. Erstellen Sie ein neues vSAN-Profil mit den Einstellungen von RAID 5/6 und FTT=2 (RAID 6) und wenden Sie diese Richtlinie anschließend auf die erforderlichen virtuellen Maschinen (VMs) oder Appliances an.

2. Warten Sie, bis das vSAN die Synchronisation abgeschlossen hat, bevor Sie mit den Korrekturaktionen beginnen. Der Fertigstellungsstatus kann überprüft werden, indem Sie zur Seite für die **Überwachung der virtuellen vSAN-Objekte** für den Cluster navigieren und den **Fertigstellungsstatus** überprüfen.

### Zugehörige Links

* [VMware HCX on {{site.data.keyword.cloud}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
