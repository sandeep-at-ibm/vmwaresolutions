---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Virtuelle Maschine migrieren

HCX ermöglicht die bidirektionale Migration: vom lokalen Rechenzentrum in die Cloud oder umgekehrt. HCX verwendet während des Migrationsprozesses die Replikationstechnologie. Die Replikationstechnologie ist in die virtuelle Hybrid-Cloud-Gateway-Appliance integriert. Es muss keine zusätzliche Replikationssoftware installiert werden.

## Migration mit geringer Ausfallzeit

Für eine Migration mit geringer Ausfallzeit wird die hostbasierte Replikation verwendet, mit der eine virtuelle Live-Maschine von einer vCenter-Instanz in ein virtuelles Rechenzentrum oder in die entgegengesetzte Richtung verschoben wird. Zur Reduktion der Ausfallzeit bleibt die Quellen-VM während der Replikation online und wird nach Abschluss der Replikation auf dem Ziel ESX-Host gebootet.

1. Eine Migrationsanforderung löst die folgenden Aktionen aus:
  * Die Replikation beginnt mit einer vollständigen Synchronisierungsübertragung in ein virtuelles VCF/VCS HCX-Rechenzentrum. Die Zeit, die für die Replikation benötigt wird, ist abhängig von der Größe der VM und der verfügbaren Bandbreite. 
  * Der Bandbreitennutzung bei der Replikation ist davon abhängig, inwiefern die Workload Blöcke auf der Platte ändert.
2. Wenn die vollständige Synchronisation abgeschlossen ist, findet eine Deltasynchronisation statt.
3. Nachdem die Deltasynchronisation abgeschlossen ist, löst HCX eine Umschaltung aus. Die Umschaltung kann sofort gestartet oder auf einen bestimmten Zeitpunkt festgelegt werden.
4. Nach der Umschaltung wird die Quellen-VM ausgeschaltet und das migrierte Replikat eingeschaltet. Wenn die VM aus irgendeinem Grund nicht eingeschaltet werden kann, wird die neue VM ausgeschaltet (bzw. bleibt ausgeschaltet) und die ursprüngliche eingeschaltet.
5. HCX benennt die ausgeschaltete ursprüngliche VM um, um einen Namenskonflikt mit der migrierten VM zu vermeiden, und hängt an den ursprünglichen VM-Namen eine binäre Zeitmarke an.
6. Wenn nicht angegeben wurde, dass **MAC-Adresse beibehalten** aktiviert werden soll, ruft die migrierte VM eine neue MAC-Adresse ab.
7. Die Migration ist abgeschlossen. Hybrid-Cloud-Services kopiert die ursprüngliche VM in den Ordner **Migrierte VMs** in der Vorlagenansicht von vSphere.

## vMotion ohne Ausfallzeit

Mit vMotion wird eine virtuelle Live-Maschine von einer vSphere vCenter-Instanz in eine VCF/VCS-Cloud übertragen. Für diese vMotion ist ein erweitertes Netz erforderlich. Bei der vMotion-Übertragung werden der aktive Arbeitsspeicher, der Ausführungsstatus, die IP-Adresse und die MAC-Adresse der virtuellen Maschine erfasst.

Die Hardwareversion der virtuellen Maschine muss mindestens Version 9 sein. Andernfalls kann die cloudumfassende vMotion fehlschlagen.
{:note}

## Cold Migration

Cold Migration verwendet die gleiche Datenebene wie cloudumfassende vMotion, um eine ausgeschaltete virtuelle Maschine über ein erweitertes Netz zu übertragen. Ihre IP-Adresse und MAC-Adresse bleiben erhalten. Die Anforderungen und Einschränkungen der virtuellen Maschine sind die gleichen wie bei vMotion.

### VMs mit dem Assistenten für Bidirektionalität migrieren

Bei Verwendung von vSphere Web Client kann der Assistent für bidirektionale Migration über die Registerkarte "Erste Schritte mit Hybrid-Cloud-Services" aufgerufen werden. In diesem Assistenten können sämtliche Migrationsdetails eingegeben werden, einschließlich der Angabe mehrerer virtueller Maschinen.

In vSphere Web Client kann der Assistent für bidirektionale Migration über die Registerkarte "Erste Schritte mit Hybrid-Cloud-Services" aufgerufen werden. In diesem Assistenten können sämtliche Migrationsdetails eingegeben werden, einschließlich der Angabe mehrerer virtueller Maschinen.
* Von vSphere auf VCF/VCS Hybrid-Cloud-Services
* Von VCF/VCS HCX Cloud auf vSphere

### Überprüfung der VMs vor der Migration

Um eine virtuelle Maschine zu migrieren, ist eine sichere Verbindung erforderlich, die vom Hybrid-Cloud-Gateway verwaltet wird. Zusätzlich muss die VM die folgenden Anforderungen erfüllen:
* Die virtuelle Maschine muss eingeschaltet sein.
* Die zugrunde liegende Architektur muss x86 sein, unabhängig vom Betriebssystem.
* Um die vMotion-Migration verwenden zu können, muss die Hardwareversion 9 oder höher sein.
* Die Hardwareversion muss unter 10 sein.
* VMs mit Raw Disk Mapping im Kompatibilitätsmodus können migriert werden.

VMs mit den folgenden Attributen werden für die Migration nicht unterstützt:
* VMs mit mehr als 2 TB.
* VMS mit gemeinsam genutzten VMDK-Dateien.
* VMs mit virtuellen Medien oder angehängten ISOs.
* VMs mit einer Hardwareversion unter 9.

### Migration überwachen

Der Fortschritt einer replikationsbasierten Migration kann über die Benutzerschnittstelle oder über die Befehlszeile überwacht werden. Zeigen Sie die Taskkonsole an, wie im Abschnitt zur Überwachung der Bereitstellung einer Service-Appliance beschrieben, und suchen Sie nach der Task **Migrate VM**. Wenn der Status **Abgeschlossen** lautet, wird die VM migriert und eingeschaltet. 

Bei dieser Prozedur wird eine nicht zugehörige VM in derselben vCenter-Instanz verwendet, um den Fortschritt einer migrierten VM zu verfolgen.

1. Identifizieren Sie die zu migrierende VM und wählen Sie eine VM-Überwachungsfunktion aus, die die Migration der VM mit Ping überprüfen kann.
2. Starten Sie von der Benutzerschnittstelle aus die Migration der VM und überwachen Sie sie über die Taskkonsole.
3. Melden Sie sich mit SSH an dem ESXi-Host an, der die VM-Überwachungsfunktion ausführt.
4. Führen Sie den folgenden Befehl aus, um die VM-ID (vmid) abzurufen:

  ```
  # vim-cmd vmsvc/getallvms | grep -i vmname 5
  ```

5. Führen Sie die folgenden Befehle aus, um den Replikationsstatus zu überwachen, wobei 'vmid' der Wert ist, der im vorherigen Schritt abgerufen wurde:

  ```
  # vim-cmd hbrsvc/vmreplica.getState vmid
  # vim-cmd hbrsvc/vmreplica.queryReplicationState vmid 6
  ```

6. ICMP-Ping - Überwachen Sie das kontinuierliche Pingsignal, das zuvor gestartet wurde.

Während der Umschaltung kann es zu einer Unterbrechung des kontinuierlichen Pingsignals kommen. Nach Abschluss der Task **VM migrieren** wird das Test-Pingsignal jedoch schnell wieder aufgenommen, was auch in der Taskkonsole angezeigt wird.

### Migrierte VMs anzeigen

Wenn Hybrid-Cloud-Services auf einer erfolgreich migrierten virtuellen Maschine eingeschaltet wird, wird die ursprüngliche VM ausgeschaltet und in einem Ordner in vCenter gespeichert. Die gespeicherten virtuellen Maschinen bleiben so lange erhalten, bis sie manuell gelöscht werden.

Nach der Migration zeigen Sie vCenter an und beachten Sie die Ordner mit der Bezeichnung **Aus Cloud migrierte VMs** und **In Cloud migrierte VMs**.
* Als Repliken besitzen die ausgeschalteten VMs ihren ursprünglichen Namen mit angehängter binärer Zeitmarke.
* Migrierte VMs können wie alle anderen VMs behandelt werden. Sie können beispielsweise an eine andere Position verschoben und eingeschaltet werden. 
* Unerwünschte VMs in diesen Ordnern können gelöscht werden.
* Dieser Löschvorgang ist endgültig, sofern keine Sicherungslösung vorhanden ist.

### Zugehörige Links

* [HCX ändern oder deinstallieren](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-mod-uninstall.html)
