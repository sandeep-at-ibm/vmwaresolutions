---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Staging und Korrektur

Patches und Erweiterungen können optional vor der Korrektur zwischengespeichert ("staged") werden, um sicherzustellen, dass sie von VUM auf den vSphere ESXi-Host heruntergeladen werden, ohne dass die Patches oder Erweiterungen sofort angewendet werden. Bei der Korrektur ("remediation") wendet VUM die Patches, Erweiterungen und Upgrades auf die Bestandsobjekte an. Das Staging von Patches und Erweiterungen beschleunigt den Korrekturprozess, da die Patches und Erweiterungen bereits lokal auf den Hosts verfügbar sind.

Wenn während des Korrekturprozesses ein Host nicht in den Wartungsmodus wechselt, meldet VUM einen Fehler und der Korrekturprozess wird gestoppt und schlägt fehl. Die vSphere ESXi-Hosts, die bereits korrigiert wurden, bleiben auf der aktualisierten Ebene erhalten.

Damit der Korrekturprozess reibungslos abläuft, sollten Sie einige der Cluster-Features wie DPM, HA Admission Control und Fault Tolerance (FT) inaktivieren und alle Wechselmedien von den virtuellen Maschinen (VMs) trennen, damit DRS bei der Migration von VMs auf andere Hosts nicht auf Probleme stößt.
Außerdem können Sie bei der Ausführung des Assistenten für die Korrektur Berichte generieren, um sicherzustellen, dass auf der Host-/VM-Ebene keine inkonsistenten Einstellungen vorliegen, die dazu führen, dass die Korrektur fehlschlägt.

1. Bei Verwendung des vSphere Web Client wählen Sie **Home** > **Hosts und Cluster** aus.
2. Klicken Sie auf ein Rechenzentrum, einen Cluster oder einen Host und klicken Sie auf **Patches zwischenspeichern**.
3. Wählen Sie auf der Seite "Baselineauswahl" des Staging-Assistenten die Patch- und Erweiterungsbaselines für das Staging aus.
4. Wählen Sie die Hosts aus, auf denen Patches und Erweiterungen angewendet werden sollen, und klicken Sie auf **Weiter**. Wenn Sie angegeben haben, dass die Patches und Erweiterungen auf einem einzelnen Host zwischengespeichert werden sollen, wird dieser standardmäßig ausgewählt.
5. Wahlweise können Sie die Patches und Erweiterungen abwählen, die von der Staging-Operation ausgeschlossen werden sollen. Um in der Liste der Patches und Erweiterungen zu suchen, geben Sie den Text in das Textfeld im Filterfeld ein. Klicken Sie auf **Weiter**.
6. Überprüfen Sie die Seite **Bereit zum Abschließen** und klicken Sie auf **Fertigstellen**.

Die Anzahl der zwischengespeicherten Patches und Erweiterungen für den entsprechenden Host wird in der Spalte "Patches und Erweiterungen" im unteren Bereich der Registerkarte "Update Manager" angezeigt. Nach dem ordnungsgemäßen Abschluss einer Korrektur werden alle zwischengespeicherten Patches und Erweiterungen auf dem Host gelöscht, und zwar unabhängig davon, ob sie während der Korrektur installiert wurden oder nicht.
Die Korrektur ist der Prozess, in dem VUM Patches, Erweiterungen und Upgrades auf vSphere ESXi-Hosts, virtuelle Maschinen (VMs) oder virtuelle Appliances nach Abschluss einer Prüfung (Scan) anwendet und die Konformität der ausgewählten Objekte ermöglicht. Sie können Hosts, virtuelle Maschinen (VMs) oder virtuelle Appliances einzeln oder auf Ordner-, Cluster- oder Rechenzentrumsebene korrigieren. VUM unterstützt für die folgenden Bestandsobjekte entweder eine manuelle oder eine geplante Korrektur:
* ESXi-Hosts für die Korrektur von Patches, Erweiterungen und Upgrades
* Eingeschaltete, ausgesetzte oder ausgeschaltete virtuelle Maschinen (VMs) und Vorlagen für VMware Tools und Hardware-Upgrade für virtuelle Maschinen
* Eingeschaltete virtuelle Appliances, die mit VMware Studio 2.0 und höher erstellt wurden, für das Upgrade der virtuellen Appliance

Wenn es das Update erfordert, werden die Hosts vor der Korrektur in den Wartungsmodus versetzt. Die VCSA migriert die virtuellen Maschinen (VMs) auf andere Hosts innerhalb der VMware vCenter Server on {{site.data.keyword.cloud}}-Instanz, bevor der Host in den Wartungsmodus versetzt wird.

## Hinweis für Hosts in einem vSAN-Cluster
Beachten Sie das folgende Verhalten bei Hosts, die Teil eines vSAN-Clusters sind:
* Der Hostkorrekturprozess nimmt möglicherweise sehr viel Zeit in Anspruch.
* Designbedingt kann sich immer nur ein Host eines VSAN-Clusters im Wartungsmodus befinden.
* VUM korrigiert Hosts, die Teil eines VSAN-Clusters sind, immer sequenziell, auch wenn Sie angegeben haben, dass die Hosts parallel korrigiert werden sollen.
* Für jede virtuelle Maschine (VM) auf dem Host, die eine VM-Speicherrichtlinie mit einer Einstellung für **Anzahl der zu tolerierenden Fehler** = 0 verwendet, können beim Host ungewöhnliche Verzögerungen beim Wechseln in den Wartungsmodus auftreten. Die Verzögerung tritt auf, da vSAN die VM-Daten von einer Platte auf eine andere Platte im vSAN-Datenspeicher migrieren muss und dies viele Stunden dauern kann. Sie können dies umgehen, indem Sie für die VM-Speicherrichtlinie die **Anzahl der zu tolerierenden Fehler=1** festlegen. Dies bewirkt, dass zwei Kopien der VM-Dateien im vSAN-Datenspeicher erstellt werden.
* Für jede virtuelle Maschine (VM) auf dem Host, die eine VM-Speicherrichtlinie mit einer Einstellung für **Number of failures to tolerate** = 1 verwendet, wird die virtuelle Maschine nicht redundant, wenn der Host in den Wartungsmodus wechselt. Wenn dies nicht akzeptabel ist, finden Sie weitere Informationen im Abschnitt [Redundanz virtueller vSAN-Maschinen](/docs/services/vmwaresolutions/archiref/vum/vum-vsan-redundancy.html).

Führen Sie die folgenden Schritte aus, um Hosts und Cluster zu korrigieren:
1. Bei Verwendung des vSphere Web Client wählen Sie **Home** > **Hosts und Cluster** aus.
2. Wählen Sie im Navigator des Bestandsobjekts ein Rechenzentrum, einen Cluster oder einen Host aus, klicken Sie auf die Registerkarte **Update Manager** und klicken Sie auf **Korrigieren**. Wenn Sie ein Containerobjekt ausgewählt haben, werden alle Hosts unter dem ausgewählten Objekt korrigiert. Der Assistent zum Durchführen der Korrektur (Remediation) wird geöffnet.
3. Wählen Sie **Patch-Baselines** oder **Erweiterungsbaselines** aus, abhängig davon, welchen Typ von Update Sie auf dem Host ausführen möchten. Wählen Sie auf der Seite "Baseline auswählen" des Korrekturassistenten die **Baselinegruppe** und **Baselines** aus, die angewendet werden sollen.
4. Wählen Sie die Zielhosts aus, die Sie korrigieren möchten, und klicken Sie auf **Weiter**. Wenn Sie ausgewählt haben, dass ein einzelner Host und kein Containerobjekt korrigiert werden soll, wird der Host standardmäßig ausgewählt.
5. Optional können Sie auf der Seite **Patches und Erweiterungen** bestimmte Patches oder Erweiterungen abwählen, um sie vom Korrekturprozess auszuschließen. Klicken Sie anschließend auf **Weiter**.
6. Optional können Sie auf der Seite **Erweiterte Optionen** angeben, dass die Korrektur zu einem späteren Zeitpunkt ausgeführt werden soll, und Sie können einen eindeutigen Namen und eine optionale Beschreibung für die Task angeben. Die Zeit, die Sie für die geplante Task festlegen, ist die Uhrzeit in der VCSA. Optional können Sie auswählen, dass Warnungen zu nicht unterstützten Geräten auf dem Host oder zu nicht mehr unterstütztem VMFS-Datenspeicher ignoriert werden sollen, damit die Korrektur fortgesetzt wird. Klicken Sie auf **Weiter**.
7. Auf der Hostseite **Korrekturoptionen** können Sie im Dropdown-Menü **VM-Betriebszustand** die Änderung im Betriebszustand der virtuellen Maschinen (VMs) und virtuellen Appliances auswählen, die auf den zu korrigierenden Hosts ausgeführt werden. Ein Host kann erst dann in den Wartungsmodus wechseln, wenn VMs auf dem Host ausgeschaltet, ausgesetzt oder mit vMotion auf andere Hosts in einem DRS-Cluster migriert werden. Bei einigen Updates ist es erforderlich, dass ein Host vor der Korrektur in den Wartungsmodus wechselt. VMs und Appliances können nicht ausgeführt werden, wenn sich ein Host im Wartungsmodus befindet. Wenn Sie die Ausfallzeit für die Hostkorrektur auf Kosten der Verfügbarkeit virtueller Maschinen (VMs) reduzieren möchten, können Sie VMs und virtuelle Appliances vor der Korrektur herunterfahren oder aussetzen. Wenn Sie in einem DRS-Cluster die virtuellen Maschinen (VMs) nicht ausschalten, dauert die Korrektur länger, aber die virtuellen Maschinen bleiben während des gesamten Korrekturprozesses verfügbar, da sie mit vMotion auf andere Hosts migriert werden. Die Auswahlmöglichkeiten lauten wie folgt:

- **Virtuelle Maschinen ausschalten** - Schalten Sie vor der Korrektur alle virtuellen Maschinen (VMs) und virtuellen Appliances aus.
- **Virtuelle Maschinen aussetzen** - Setzen Sie alle aktiven virtuellen Maschinen (VMs) und virtuellen Appliances vor der Korrektur aus.
- **VM-Betriebszustand nicht ändern** - Belassen Sie virtuelle Maschinen (VMs) und virtuelle Appliances in ihrem aktuellen Betriebszustand.

8. (Optional) Wählen Sie **Alle mit den virtuellen Maschinen auf dem Host verbundenen Wechselmedien trennen** aus. VUM korrigiert keine Hosts, auf denen sich virtuelle Maschinen (VMs) befinden, die mit CD-, DVD- oder Diskettenlaufwerken verbunden sind. In einer Clusterumgebung verhindern verbundene Geräte möglicherweise die Ausführung von vMotion, wenn der Zielhost nicht über ein identisches Gerät oder ein angehängtes ISO-Image verfügt, was wiederum den Quellhost daran hindert, in den Wartungsmodus zu wechseln. Nach der Korrektur verbindet VUM die Wechselmedien neu, sofern diese noch verfügbar sind.
9. (Optional) Wählen Sie **Versuchen Sie im Falle eines Fehlschlags, erneut in den Wartungsmodus zu wechseln** aus, und geben Sie die Anzahl der Wiederholungen und die Wartezeit zwischen den Wiederholungen an. VUM wartet den Zeitraum der Verzögerung bis zur Wiederholung ab und versucht erneut, den Host in den Wartungsmodus zu versetzen. Dieser Vorgang wird so oft wiederholt, wie dies im Feld "Anzahl an Wiederholungen" angegeben ist.

In einer vCenter Server-Instanz ist es nicht erforderlich, das Kontrollkästchen unter den ESXi-Patcheinstellungen auszuwählen, damit Update Manager eingeschaltete, mit PXE gebootete ESXi-Hosts korrigiert.
10. Klicken Sie auf **Weiter**.
11. Wenn Sie Hosts in einem Cluster korrigieren, müssen Sie die Korrekturoptionen für den Cluster bearbeiten. Die Seite **Clusterkorrekturoptionen** ist nur verfügbar, wenn Sie Cluster korrigieren. Die folgenden Optionen können ausgewählt werden:
* **Distributed Power Management (DPM) inaktivieren**, wenn die Funktion für einen der ausgewählten Cluster aktiviert ist - VUM korrigiert Cluster mit aktivem DPM nicht. DPM überwacht die Ressourcennutzung der aktiven VMs im Cluster. Wenn genug zusätzliche Kapazität vorhanden ist, empfiehlt DPM, virtuelle Maschinen (VMs) auf andere Hosts im Cluster zu verschieben und den ursprünglichen Host in den Standby-Modus zu versetzen, um Strom zu sparen. Beim Versetzen von Hosts in den Standby-Modus kann die Korrektur unterbrochen werden.
* **High Availability Admission Control inaktivieren**, wenn die Funktion für einen der ausgewählten Cluster aktiviert ist - VUM korrigiert Cluster mit aktiver High Availability Admission Control nicht. Die Admission Control ist eine Richtlinie, die von VMware HA verwendet wird, um die Failover-Kapazität in einem Cluster sicherzustellen. Wenn die High Availability Admission Control während des Korrekturprozesses aktiviert ist, können die virtuellen Maschinen (VMs) in einem Cluster möglicherweise nicht mit vMotion migriert werden.
* **Fault Tolerance (FT) inaktivieren**, wenn die Funktion aktiviert ist. Dies wirkt sich auf alle fehlertoleranten VMs in den ausgewählten Clustern aus. Wenn FT für eine der VMs auf einem Host aktiviert ist, wird dieser Host von VUM nicht korrigiert. Damit FT aktiviert ist, müssen die Hosts, auf denen die primären und sekundären VMs ausgeführt werden, dieselbe Version aufweisen und sie müssen dieselben Patches installiert haben. Wenn Sie unterschiedliche Patches auf diese Hosts anwenden, kann FT nicht erneut aktiviert werden.
* **Parallele Korrektur für die Hosts in den ausgewählten Clustern aktivieren** - Sie können Hosts in Clustern parallel korrigieren. Wenn diese Einstellung nicht ausgewählt wird, korrigiert VUM die Hosts in einem Cluster nacheinander. Sie können eine der folgenden Optionen für die parallele Korrektur auswählen:
  - Sie können VUM kontinuierlich die maximale Anzahl von Hosts berechnen lassen, für die eine gleichzeitige Korrektur möglich ist, ohne dass die DRS-Einstellungen unterbrochen werden.
  - Sie können einen Grenzwert für die Anzahl gleichzeitig korrigierter Hosts in jedem Cluster angeben, für den Sie die Korrektur vornehmen. Beachten Sie, dass VUM nur die Hosts, auf denen virtuelle Maschinen (VMs) ausgeschaltet oder ausgesetzt sind, gleichzeitig korrigieren kann. Sie können virtuelle Maschinen im Menü "VM-Betriebszustand" im Teilfenster "Wartungsmodusoptionen" auf der Seite "Hostkorrekturoptionen" ausschalten oder aussetzen. Designbedingt kann sich immer nur ein Host eines vSAN-Clusters im Wartungsmodus befinden. VUM korrigiert Hosts, die Teil eines vSAN-Clusters sind, immer sequenziell, auch wenn Sie ausgewählt haben, dass die Hosts parallel korrigiert werden sollen.
* **Migration ausgeschalteter und ausgesetzter virtueller Maschinen machines auf andere Hosts im Cluster**, wenn ein Host in den Wartungsmodus versetzt werden muss. Update Manager migriert die ausgesetzten und ausgeschalteten virtuellen Maschinen (VMs) von Hosts, die in den Wartungsmodus versetzt werden müssen, auf andere Hosts im Cluster. Sie können virtuelle Maschinen (VMs) vor der Korrektur im Teilfenster **Wartungsmoduseinstellungen** ausschalten oder aussetzen.
12. Auf der Seite "Bereit zum Abschließen" können Sie optional auf **Korrektur vorab prüfen** klicken, um einen Bericht für die Clusterkorrekturoptionen zu generieren. Klicken Sie anschließend auf **OK**. Ein Dialogfenster "Clusterkorrekturoptionen" wird geöffnet. Sie können diesen Bericht exportieren oder die Einträge für Ihre eigenen Zwecke kopieren und auf **Weiter** klicken.
13. Überprüfen Sie die Seite **Bereit zum Abschließen** und klicken Sie auf **Fertigstellen**.

### Zugehörige Links

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demonstrationen)
