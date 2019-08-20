---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

#	Koordinierte Upgrades
{: #vum-orchestr-updates}

Sie können koordinierte Upgrades verwenden, um die virtuelle Hardware und die VMware Tools virtueller Maschinen im Bestand aufzurüsten, nachdem die vSphere ESXi-Hosts aktualisiert wurden. Nachdem die Hosts aktualisiert wurden, wird zuerst die Upgrade-Baseline für VMware Tools und danach die Hardware-Upgrade-Baseline der virtuellen Maschine ausgeführt. Koordinierte Upgrades können auf Cluster-, Ordner- oder Rechenzentrumsebene verwendet werden.

Mit VUM können Sie koordinierte Upgrades für Hosts und dann virtuelle Maschinen mithilfe von Baselinegruppen durchführen. Es wird eine Baselinegruppe verwendet, die eine einzelne Host-Upgrade-Baseline und mehrere Patch- oder Erweiterungsbaselines enthält. VUM führt zunächst das Upgrade für die Hosts durch und wendet dann die Patch- oder Erweiterungsbaselines an. Zur Durchführung eines koordinierten Upgrades für virtuelle Maschinen verwenden Sie eine Baselinegruppe für virtuelle Maschinen, die die folgenden Baselines enthält:
* VM-Hardware-Upgrade übereinstimmend mit Host
* VMware Tools-Upgrade übereinstimmend mit Host

Mit durch VUM koordinierten Upgrades können Sie die Bestandsobjekte in VCSA in einem zweistufigen Prozess aufrüsten. Zuerst wird für die vSphere ESXi-Hosts ein Upgrade durchgeführt, gefolgt von den Upgrades für die virtuellen Maschinen. Dieser zweistufige Prozess kann auf Clusterebene konfiguriert werden oder Sie können die Konfiguration für den individuellen vSphere ESXi-Host oder die virtuelle Maschine vornehmen, was eine differenziertere Steuerung ermöglicht.

Im koordinierten Upgrade wird der Cluster zuerst anhand der Host-Baseline-Gruppe korrigiert, die Patches, Erweiterungen und Upgrades anwendet. Nach diesem Upgrade werden die virtuellen Maschinen im Cluster mit der Upgrade-Baseline-Gruppe für virtuelle Maschinen korrigiert, die die Baselines "VM-Hardware-Upgrade übereinstimmend mit Host" und "VMware Tools-Upgrade übereinstimmend Host" enthält.

Wenn die Baselinegruppe auch eine Upgrade-Baseline enthält, führt VUM zunächst ein Upgrade der vSphere ESXi-Hosts durch und wendet dann die Patch- oder Erweiterungsbaselines an, da sich die Patches immer auf eine bestimmte Hostversion beziehen. Für die virtuellen Maschinen werden zuerst die VMware Tools aktualisiert, danach erfolgt die Aktualisierung der virtuellen Hardware.

Daher werden die virtuellen Maschinen während des Upgrades der VMware Tools eingeschaltet, wenn sich virtuelle Maschinen in einem ausgeschalteten oder ausgesetzten Zustand befinden; VUM übernimmt das Einschalten, führt das Upgrade durch und stellt so den ursprünglichen Betriebszustand der virtuellen Maschine wieder her. Daher müssen sich die VMs während des Upgrades für virtuelle Hardware im ausgeschalteten Zustand befinden. Wenn virtuelle Maschinen eingeschaltet sind, schaltet VUM diese aus, führt das Upgrade der virtuellen Hardware durch und schaltet die VMS wieder ein.

Standardmäßig erfolgt die Korrektur der vSphere ESXi-Hosts sequenziell, d. h. die Hosts werden nacheinander korrigiert. Wenn der Prozess für einen Host abgeschlossen ist, beginnt VUM mit der Korrektur des nächsten Hosts. Dieser Standardprozess kann geändert werden, wenn die parallele Korrekturfunktion aktiviert werden soll, sodass mehr als ein Host gleichzeitig korrigiert werden kann. Dies ist jedoch nur möglich, wenn Sie über genug Failover-Kapazität in Ihrem Cluster verfügen.

Wenn die vSphere ESXi-Hosts Teil eines vSAN-Clusters sind, ist der Korrekturprozess immer sequenziell, auch wenn Sie im Korrekturassistenten das parallele Korrekturverfahren ausgewählt haben, da sich immer nur ein Host im vSAN-Cluster im Wartungsmodus befinden kann. VUM verfügt über intelligente Berechnungsverfahren, die ermitteln, wie viele Hosts parallel korrigiert werden können, ohne die DRS-Einstellungen zu beeinträchtigen.

Alternativ können Sie das Limit für die Anzahl der Hosts definieren, die während der Ausführung des Korrekturassistenten parallel korrigiert werden können.

Der folgende Workflow beschreibt den Prozess zur Durchführung eines koordinierten Upgrades:

## Schritt 1
{: #vum-orchestr-updates-step1}

1. Melden Sie sich mit dem vSphere Web Client bei der VCSA an.
2. Wählen Sie **Home** > **Update Manager** in der Registerkarte **Objekte** aus und wählen Sie dann eine **Update Manager-Instanz** aus.
3. Klicken Sie auf die Registerkarte **Verwalten**, dann auf die Registerkarte **Host-Baselines** und klicken Sie anschließend auf **Neue Baselinegruppe**.
4. Geben Sie einen eindeutigen Namen für die Baselinegruppe ein und klicken Sie auf **Weiter**.
5. Wählen Sie eine Host-Upgrade-Baseline aus, um sie in die Baselinegruppe aufzunehmen.
6. Sie können optional eine neue Host-Upgrade-Baseline erstellen, indem Sie auf **Neue Host-Upgrade-Baseline erstellen** unten auf der Seite "Upgrades" klicken und im Assistenten "Neue Baseline" die entsprechenden Angaben machen. Klicken Sie auf **Weiter**.
7. Wählen Sie die Patch-Baselines aus, die in die Baselinegruppe aufgenommen werden sollen.
8. Sie können optional eine neue Patch-Baseline erstellen, indem Sie auf **Neue Host-Patch-Baseline erstellen** unten auf der Seite "Patches" klicken und im Assistenten "Neue Baseline" die entsprechenden Angaben machen. Klicken Sie auf **Weiter**.
9. Wählen Sie die Erweiterungsbaselines aus, die in die Baselinegruppe aufgenommen werden sollen.
10. Sie können optional eine neue Erweiterungsbaseline erstellen, indem Sie auf **Neue Erweiterungsbaseline erstellen** unten auf der Seite "Patches" klicken und im Assistenten "Neue Baseline" die entsprechenden Angaben machen.
11. Überprüfen Sie die Seite **Bereit zum Abschließen**, klicken Sie auf **Fertigstellen** und die Host-Baseline-Gruppe wird im Teilfenster "Baselinegruppen" angezeigt.

## Schritt 2
{: #vum-orchestr-updates-step2}

1. Erstellen Sie eine Baselinegruppe für virtuelle Maschinen, die die Baseline "VMware Tools-Upgrade übereinstimmend mit Host" und die Baseline "VM-Hardware-Upgrade übereinstimmend mit Host" (Ansicht "VUM-Verwaltung") enthält.
2. Hängen Sie die Baselinegruppe an ein vCenter-Containerobjekt an, das die virtuellen Maschinen enthält, für die Sie ein Upgrade durchführen möchten.
3. Prüfen Sie das Containerobjekt, um den Konformitätsstatus der virtuellen Maschinen in dem Container anzuzeigen. Sie können die Prüfung manuell starten oder eine Prüftask planen.
4. Sehen Sie sich die Suchergebnisse an, die in der Konformitätsansicht des VUM-Clients angezeigt werden.
5. Korrigieren Sie die nicht konformen virtuellen Maschinen im Containerobjekt, um sie mit der angehängten Baselinegruppe konform zu machen. Sie können die Korrektur manuell starten oder eine Korrekturtask planen.
* Während eines Upgrades von VMware Tools müssen die virtuellen Maschinen eingeschaltet sein. Wenn sich eine virtuelle Maschine vor der Korrektur in einem ausgeschalteten oder ausgesetzten Status befindet, schaltet VUM die Maschine ein. Nachdem das Upgrade abgeschlossen ist, startet VUM die Maschine neu und stellt so den ursprünglichen Betriebszustand wieder her.
* Während eines VM-Upgrades für virtuelle Maschinen müssen die virtuellen Maschinen ausgeschaltet sein. Nachdem das Upgrade abgeschlossen ist, startet VUM die virtuelle Maschine neu und stellt so den ursprünglichen Betriebszustand wieder her. Wenn eine virtuelle Maschine eingeschaltet ist, wird die Maschine von VUM ausgeschaltet, führt das Upgrade der virtuellen Hardware durch und schaltet die virtuelle Maschine dann wieder ein.

Sie können diese Baselinegruppen nun in Prozessen zum Prüfen und Auswerten, für das Staging und zur Korrektur verwenden.

## Zugehörige Links
{: #vum-orchestr-updates-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [{{site.data.keyword.vmwaresolutions_full}} Demos](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (Vorführungen)
