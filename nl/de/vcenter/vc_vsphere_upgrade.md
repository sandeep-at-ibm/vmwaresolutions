---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-30"

keywords: vSphere upgrade, NSX upgrade, PSC upgrade

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrade von vCenter Server vSphere-Software von VMware vSphere 6.5 auf Version 6.7 durchführen
{: #vc_vsphere_upgrade}

Das Angebot vCenter Server on {{site.data.keyword.cloud}} ist eine vollständig automatisierte Bereitstellungslösung für den VMware vSphere-SDDC-Stack einschließlich vSphere-, NSX- und (optional) vSAN-Produkten. vCenter Server automatisiert zwar die anspruchsvollsten Teile der Bereitstellung, Erweiterung und Verringerung einer VMware SDDC-basierten Infrastruktur, ist jedoch kein verwalteter Service. Da vCenter Server eine Richtlinie zur Unterstützung der Automatisierung von VMware-SDDC-Softwareversionen im Bereich von N-1 hat, müssen Sie vorhandene Instanzen von vCenter Server aktualisieren, wenn Sie weiterhin von der {{site.data.keyword.vmwaresolutions_short}}-Automatisierung profitieren wollen.

vCenter Server-Versionen außerhalb der für die Automatisierungsunterstützung erforderlichen Versionen werden zwar weiterhin im Rahmen der VMware-Support-Richtlinie unterstützt, können jedoch die {{site.data.keyword.vmwaresolutions_short}}-Automatisierung nicht mehr nutzen. Sie müssen für die VMware-Software in regelmäßigen Abständen im Lebenszyklus einer vCenter Server-Instanz Patches und Upgrades anwenden. Dies schließt ein Upgrade der VMware-SDDC-Software auf eine Version ein, die nach Bedarf von der {{site.data.keyword.vmwaresolutions_short}}-Automatisierung unterstützt wird.

Die folgende Prozedur enthält die Schritte, die erforderlich sind, um eine vCenter Server-basierte Instanz von VMware vSphere Version 6.5 auf eine vCenter Server-basierte Instanz von VMware vSphere 6.7 zu konvertieren. Mit diesen Schritten wird das erste Upgrade auf die aktuelle Version (Version 6.7) von vSphere, NSX und vSAN durchgeführt. Nach diesem Upgrade müssen Sie unter Umständen die normale vSphere-Funktionalität verwenden, um die Hardwarestufen und Tools der virtuellen Maschine (VM) zu aktualisieren.

vCenter Server ist so konzipiert, dass ein "rollierendes" Upgrade möglich ist. Dies bedeutet, dass VM-Workloads, die derzeit funktionieren, ohne Ausfall weiter funktionieren, wenn Sie die folgende Prozedur ausführen. Unternehmen müssen ihre Change-Management-Richtlinien einbinden, um ein strukturiertes und kommuniziertes Upgrade durchzuführen und einen Plan für unvorhergesehene Ereignisse bereitzuhalten. Während des Upgradeprozesses für bestimmte Verwaltungsfunktionen, wie z. B. vCenter und NSX-Manager, kann es jedoch zu temporären Ausfällen von Verwaltungsfunktionen sowie zu Konfigurationsänderungen und zum An- und Ausschalten von VMs kommen.
{:note}

## Vorbereitende Schritte
{: #vc_vsphere_upgrade-prereq}

Die geschätzte Zeit für die Durchführung des Upgrades ist unbekannt. Es ist möglich, dass mehrere Wartungsfenster erforderlich sind, um eine Umgebung vollständig zu aktualisieren. Die Ausführung von hoch- und heruntergestuften Versionen der SDDC-Software wird von VMware während des Upgradeprozesses von VMware unterstützt. Einige Funktionen, wie vMotion, können jedoch während dieses Prozesses nur begrenzt verfügbar sein.

Überprüfen Sie vor dem Durchführen des Upgrades die folgenden Voraussetzungen:  
* Es liegt in Ihrer Verantwortung, alle Erweiterungen oder Snap-ins in der vCenter Server-Umgebung zu aktualisieren. Lesen Sie die folgende Dokumentation, bevor Sie das Upgrade planen:
  * [Releaseinformationen zu VMware vCenter Server 6.7 Update 1b](https://docs.vmware.com/en/VMware-vSphere/6.7/rn/vsphere-vcenter-server-67u1b-release-notes.html){:external}
  * [Informationen zum Upgrade von VMware ESXi](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.upgrade.doc/GUID-65B5B313-3DBB-4490-82D2-A225446F4C99.html){:external}
* Richten Sie vSphere Update Manager (VUM) in Ihrer vCenter Server-Instanz ein, um die neuesten Updates von VMware vSphere herunterzuladen. Weitere Informationen finden Sie in der [Einführung in VMware Update Manager](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vum-intro#vum-intro).
* Öffnen Sie beim {{site.data.keyword.vmwaresolutions_short}}-Team ein Support-Ticket mit der Benachrichtigung darüber, dass ein Upgrade durchgeführt wird. Das Ticket bleibt so lange geöffnet, bis die Instanz mit der aktualisierten Version in der {{site.data.keyword.vmwaresolutions_short}}-Konsole registriert ist.
* Bestätigen Sie, ob die vCenter Server-Instanz, für die Sie ein Upgrade durchführen, mit einer anderen vCenter Server-Instanz als primärer oder sekundärer Server in der {{site.data.keyword.vmwaresolutions_short}}-Konsole verbunden ist. Für alle verknüpften Instanzen muss zunächst ein Upgrade der entsprechenden PSCs (Platform Services Controller) als Teil des Upgrades für einen bestimmten Standort durchgeführt werden.
* Stellen Sie sicher, dass Folgendes für vSAN-basierte Instanzen gilt:
  * Stellen Sie sicher, dass das Tool für die vSAN-Statusprüfung aktiviert ist und keine kritischen Fehler meldet. Wenn kritische Fehler vorhanden sind, wenden Sie sich mit der entsprechenden Support-Ticket-ID für das Upgrade an das IBM Support-Team.
  * Stellen Sie sicher, dass auf jedem Knoten Speicherplatz für die erneute Schaffung von Redundanz von vSAN-Objekten vorhanden ist, falls ein ESXi-Host während des Upgrades nicht wieder hochgefahren werden kann. Möglicherweise müssen Sie vor dem Upgrade entweder die Plattenbelegung reduzieren oder einen zusätzlichen ESXi-Host hinzufügen.  
  * Überprüfen Sie, ob der gesamte vSAN-Datenträger mit mehr als 70 Prozent belegt ist. Möglicherweise müssen Sie vor dem Upgrade entweder die Plattenbelegung reduzieren oder einen zusätzlichen ESXi-Host hinzufügen.
* Wenn Ihre vCenter Server-Instanz ursprünglich als {{site.data.keyword.vmwaresolutions_short}} Version 2.5 oder höher gestartet wurde, müssen Sie sich für das Kennwort des **root**-Benutzers für PSC und vCenter an IBM Support wenden, da nur ein Servicekonto mit **customerroot**-Zugriff auf dem Portal sichtbar ist. Wenn die **root**-Benutzer-ID für PSC und vCenter mit dem entsprechenden Kennwort angezeigt wird, ist dieser Schritt nicht erforderlich.
* Stellen Sie sicher, dass Sie über eine Benutzer-ID für 'https://my.vmware.com' verfügen, um die erforderlichen Binärdateien für das Upgrade herunterladen zu können. Wenn dies nicht der Fall ist, wenden Sie sich mit der entsprechenden Support-Ticket-ID für das Upgrade an das IBM Support-Team.
* Stellen Sie sicher, dass VUM zum Herunterladen von Patches für den Zugriff auf 'https://www.vmware.com' konfiguriert ist. Wenn dies aufgrund von Sicherheitsrichtlinien nicht möglich ist, müssen Sie die neuesten Patch-Sets manuell herunterladen und in VUM hochladen. Weitere Informationen finden Sie in der [Einführung in VMware Update Manager](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro).

### Jump-Box-Server vorbereiten
{: #vc_vsphere_upgrade-prereq-jumpbox}

Da die {{site.data.keyword.cloud_notm}}-VPN für den Clientzugriff auf 512 Kb/s beschränkt ist, wird empfohlen, entweder eine {{site.data.keyword.cloud_notm}}-VSI für Windows 2012-2016 Server bereitzustellen oder in einer separaten vSphere vCenter Server-Umgebung im selben {{site.data.keyword.CloudDataCent_notm}} eine ähnliche Windows-VM einzurichten. Diese wird als Jump-Box-Server in der vCenter Server-Instanz für Upgrades verwendet und ermöglicht schnelle Downloads der Binärdateien von 'https://my.vmware.com'. Es ist zwar möglich, diese VM in der vCenter Server-Instanz zu implementieren, für die gerade ein Upgrade durchgeführt wird, es ist jedoch nicht die empfohlene Vorgehensweise.

Führen Sie die folgenden Schritte aus, um einen VSI-Jump-Box-Server zu bestellen.

Überspringen Sie den ersten Schritt, wenn Sie bereits über einen VSI-Jump-Box-Server in Ihrer Umgebung verfügen.
{:note}

1. Bestellen Sie über das Kundenportal der [{{site.data.keyword.cloud_notm}}-Infrastruktur](https://control.softlayer.com/){:external} eine VSI auf stündlicher oder monatlicher Basis. Bestellen Sie die folgenden Attribute:
  * Windows 2012 oder 2016 Server Standard
  * 2 CPUs
  * 16 GB Speicher
  * 100 GB Platte
  * 1 Gb/s öffentliche und private Uplinks
2. Wenn die VSI bereitgestellt wird, konfigurieren Sie die {{site.data.keyword.cloud_notm}}-Zugriffssteuerungslisten (Access Control Lists, ACLs) in der Steuerkonsole so, dass der gesamte eingehende und abgehende Datenverkehr über die privaten Verbindungen und abgehender Verkehr nur über öffentliche Verbindungen möglich ist. Sie müssen die {{site.data.keyword.cloud_notm}}-VPN für den Clientzugriff für RDP-Sitzungen (Remote Desktop Protocol) in der Windows-VSI verwenden.
3. Greifen Sie über RDP auf die Windows-VSI zu. Ändern Sie die DNS-Einstellungen (DNS - Domain Name System) für den privaten Netzadapter so, dass sie nur auf den Windows AD-Server in der vCenter Server-Instanz verweisen, für die ein Upgrade durchgeführt werden soll.
4. Laden Sie den Google Chrome-Browser herunter und installieren Sie diesen. Sie können auch Mozilla Firefox verwenden; hier kann es jedoch bei der Verwendung der VUM-Anzeigen in der vCenter-Benutzerschnittstellen zu Problemen beim Cache kommen.
5. Laden Sie Ihre bevorzugte SSH-Terminalsoftware herunter. Beispiel: Putty.
6. Greifen Sie über Google Chrome auf die vCenter Server-Instanz zu, für die das Upgrade durchgeführt werden soll. Verwenden Sie **administrator@vsphere.local** und stellen Sie sicher, dass Sie die Benutzerschnittstelle anzeigen können.  
7. Überprüfen Sie die vSphere-Umgebung auf Fehler und Probleme, die im vorherigen Abschnitt erläutert wurden.
8. Greifen Sie mit der SSH-Terminalsoftware mithilfe der über das Portal oder den Support für **root** bereitgestellten Kennwörter auf PSC und vCenter zu.
9. Optional können Sie die für **root** in der SL-Steuerkonsole angegebene Benutzer-ID und das Kennwort für den Zugriff auf die einzelnen ESXi-Hosts verwenden, um das Kennwort für **root** zu überprüfen.

#### Binärdateien herunterladen
{: #vc_vsphere_upgrade-prereq-jumpbox-binary}

Verwenden Sie den Jump-Box-Server Ihrer Windows-VSI und melden Sie sich unter 'https://my.vmware.com' an Ihrem Konto an, um die folgenden Binärdateien herunterzuladen:

* Image für VMware vSphere 6.7u1 Hypervisor (ESXi-ISO-Datei) (enthält VMware-Tools)
* Appliance-ISO-Datei für vCenter 6.7u1b. Nicht das Update-Bundle.
* Upgrade-Bundle für NSX for vSphere 6.4.4

Laden Sie bei Intel Optane-Laufwerken die folgende Datei herunter, die als Teil des Patchprozesses nach dem Upgrade verwendet wird, bei dem VMware Update Manager verwendet wird.

Suchen Sie unter unter 'https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX67-INTEL-INTEL-NVME-VMD-1401016&productId=742' nach der Datei ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` für den Intel NVMe-Treiber für Intel® Optane™ SSD DC P4800X Series SSDPED1K750GA (750 GB, HHHL).

#### Komponenten sichern

Führen Sie vor dem Upgrade für alle Komponenten eine Sicherung durch.

* Informationen zum Sichern von vCenter Server- und PSC-Instanzen finden Sie in der [Übersicht über Sicherung- und Wiederherstellungsoptionen in vCenter Server 6.x (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:external}.
* Weitere Hinweise und Informationen zum Sichern von Server- und PSC-Instanzen finden Sie im Abschnitt [Dateibasierte vCenter-Sicherung](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup#solution_backingup-vcenter).
* Informationen zum Sichern von NSX finden Sie im Abschnitt [NSX-Manager-Daten sichern](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:external}.

Es empfiehlt sich die Verwendung eines dateibasierten Backups. Das imagebasierte Backup (mit vSphere Data Protection) wird in VMware vSphere 6.7 nicht unterstützt.
{:note}

## Vorgehensweise beim Upgrade der vSphere-Software von IBM vCenter Server von Version 6.5 auf Version 6.7
{: #vc_vsphere_upgrade-procedure}

Wenn während des Upgradeprozesses ein Problem auftritt, verwenden Sie das Ticket zum {{site.data.keyword.vmwaresolutions_short}}-Upgrade, das Sie zu Beginn des Prozesses zur Kontaktaufnahme mit IBM Support geöffnet haben. IBM Support öffnet bei Bedarf Tickets in Zusammenarbeit mit VMware-Support.

**Wichtig**:

* Sie müssen diesen Pfad verwenden, um sicherzustellen, dass {{site.data.keyword.vmwaresolutions_short}} Unterstützung für VMware mit allen erforderlichen Informationen zum Design, zur Einrichtung und zu {{site.data.keyword.cloud_notm}}-Informationen für vCenter Server bereitstellt. Indem Sie diesen Prozess verfolgen, um sicherzustellen, dass die richtigen Informationen mit VMware-Suppport geteilt werden, verkürzen Sie die Zeit, die Sie den Support nutzen müssen. Sobald IBM Support die nötigen Informationen an VMware-Support weitergibt, können Sie direkt bei Bedarf mit dem Support von VMware interagieren.
* Stellen Sie sicher, dass Sie alle neuen Kennwörter und Berechtigungsnachweise notieren, die Sie im Rahmen dieses Upgradeprozesses erstellen. Für den IBM Support sind diese Berechtigungsnachweise am Ende des Upgradeprozesses erforderlich, um die interne Datenbank zu aktualisieren.

### Upgrade für VMware NSX durchführen
{: #vc_vsphere_upgrade-procedure-nsx}

Das Durchführen eines Upgrades für VMware NSX kann einige Zeit in Anspruch nehmen, da im Rahmen des Upgradeprozesses vSphere Installation Bundles (VIBs) auf den ESXi-Hosts aktualisiert werden und anschließend ein Warmstart für jeden einzelnen Host durchgeführt werden muss. Planen Sie Ihr Wartungsfenster entsprechend.

#### Vor dem Upgrade von VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-before}

* Wenn Zerto for {{site.data.keyword.cloud_notm}} in Ihrer Umgebung installiert ist, verwenden Sie die Zerto-Benutzerschnittstelle, um die zVRA-VMs auf jedem Host herunterzufahren. Wählen Sie in der Zerto-Benutzerschnittstelle im Abschnitt mit den Richtlinien für die Zerto-Siteeinstellungen die Option aus, die es **Zerto ermöglicht, Hosts während der Korrektur immer in den Wartungsmodus zu versetzen**. Andernfalls startet Zerto zVRA und verhindert, dass das Upgrade fortgesetzt wird, indem der ESXi-Host, für den das Upgrade durchgeführt wird, nicht in den Wartungsmodus wechseln darf.
* Für VMs, für die keine VMware-Tools installiert sind, sollten Sie das System entweder manuell herunterfahren und ein Ausschalten erzwingen, bevor Sie das NSX ESXi-Hostmodul installieren. Diese VMs verhindern, dass der ESXi-Zielhost in den Wartungsmodus wechselt.

#### Vorgehensweise beim Upgrade von VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-procedure}

Weitere Informationen zur folgenden Prozedur finden Sie im [Leitfaden für NSX-Upgrades](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:external}.

1. Lesen Sie die Releaseinformationen zu NSX 6.4.4, um die Kompatibilität mit Ihrer spezifischen Umgebungskonfiguration zu gewährleisten. Weitere Informationen finden Sie in den [Releaseinformationen zu VMware NSX Data Center for vSphere 6.4.4](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:external}.
2. Führen Sie zuerst ein Upgrade des NSX-Managers durch. Wenn Sie mehrere NSX-Umgebungen im vCenter-übergreifenden Verbindungsmodus verwenden, führen Sie ein Upgrade für alle NSX-Manager-Instanzen durch, bevor Sie Komponenten in der NSX-Benutzerschnittstelle (**Upgrade-Coordinator**) aktualisieren.
3. Verwenden Sie den **Upgrade-Coordinator** in der NSX-Benutzerschnittstelle innerhalb der vCenter-Benutzerschnittstelle, um ein Upgrade für die NSX-Komponenten durchzuführen.
4. Überwachen Sie in der NSX-Benutzerschnittstelle für das Upgrade in der vCenter-Benutzerschnittstelle die Behebung möglicher Probleme, um sicherzustellen, dass das Upgrade solange fortgesetzt wird, bis alle Komponenten aktualisiert wurden.

### Upgrade für Platform Services Controller durchführen
{: #vc_vsphere_upgrade-procedure-psc}

Wenn Sie über mit vCenter Server verknüpfte Instanzen verfügen, müssen Sie ein Upgrade für alle PSC-Instanzen an den primären und sekundären vCenter Server-Standorten durchführen. Da verknüpfte vCenter Server-Instanzen eine Hub- und Peripherietopologie für die PSC-Replikation erstellen, wobei die primäre vCenter Server-Instanz der Hub ist, wird empfohlen, dass Sie zunächst ein Upgrade für den primären PSC der vCenter Server-Instanz und anschließend für alle PSCs an den sekundären Standorten durchführen.

#### Vor dem Upgrade von Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc-before}

* Halten Sie für die folgende Prozedur Ihre Rootkennwörter für vCenter und PSC bereit. Verwenden Sie die {{site.data.keyword.vmwaresolutions_short}}-Konsole, um festzustellen, ob für die Version der vCenter Server-Instanz ein Upgrade von Version 2.4 oder früher auf Version 2.7 oder höher durchgeführt wurde.
* In der {{site.data.keyword.vmwaresolutions_short}}-Konsole wird ein einzelnes Kennwort für das PSC- und das vCenter-Stammverzeichnis angezeigt. Dies ist jedoch nur das Kennwort für vCenter. Sie müssen sich [an den IBM Support wenden](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support), um das Kennwort für Rootbenutzer in PSC zu erhalten.
* Um Konflikte zu vermeiden, verwenden Sie die IP-Adresse im oberen Teil des Teilnetzes, das derzeit von vCenter und PSC verwendet wird. Sie müssen eine temporäre IP-Adresse für die neue Appliancebereitstellung verwenden.

#### Vorgehensweise beim Upgrade von Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc-procedure}

1. Melden Sie sich bei PSC (`https://<psc-fqdn>:5480`) und den vCenter-Benutzerschnittstellen für das Appliance-Management an, um zu überprüfen, ob das Rootkennwort abgelaufen ist. Wenn das Ablaufdatum für das Kennwort **1970** lautet, ist es abgelaufen, und Sie müssen SSH und die Bash-Shell in der PSC-Benutzerschnittstelle für das Appliance-Management aktivieren.
    1. Greifen Sie über SSH mit der Root-ID und dem entsprechenden Kennwort auf PSC zu. Auch wenn das Kennwort abgelaufen ist, können Sie sich anmelden.
    2. Verwenden Sie den Shell-Befehl **passwd**, um ein neues Rootkennwort für PSC und vCenter festzulegen.
    3. Speichern Sie die Kennwörter, die in der {{site.data.keyword.vmwaresolutions_short}}-Konsole angezeigt werden oder die Sie von IBM Support erhalten haben. Diese Kennwörter werden später wiederverwendet, wenn Sie ein Upgrade für die Appliances durchführen.
2. Verwenden Sie die integrierte Windows-ISO-Mount-Funktion, um die vCenter 6.7u1b ISO-Datei an Ihren Jump-Box-Server anzuhängen.
3. Befolgen Sie die VMware-Anweisungen, um zuerst ein Upgrade für alle PSC-Instanzen durchzuführen. Weitere Informationen hierzu finden Sie unter [Durchführen eines Upgrades einer vCenter Server Appliance 6.0 oder 6.5 mit einer externen vCenter Single Sign-On- oder Platform Services Controller-Instanz unter Verwendung der GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html){:external}.

Die dort angegebene Voraussetzung **Das GUI-Upgrade muss auf einem Windows-, Linux- oder Mac-Computer ausgeführt werden, der sich im selben Netz wie die Appliance, für die Sie das Upgrade durchführen möchten, befindet** gilt für alle Teilnetze in {{site.data.keyword.cloud_notm}} in Ihrem Konto.
{:note}

Es wird empfohlen, vCenter als Quelle und Ziel für das Upgrade zu verwenden.

### Upgrade für vCenter durchführen
{: #vc_vsphere_upgrade-procedure-vcenter}

Obwohl bei verknüpften vCenter Server-Instanzen empfohlen wird, für alle vCenter-Instanzen ein Upgrade an den primären und sekundären vCenter Server-Standorten durchzuführen, ist dieser Schritt nicht obligatorisch.

#### Vor dem Upgrade von vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-before}

* Halten Sie für die folgende Prozedur Ihre Rootkennwörter für vCenter und PSC bereit. Verwenden Sie die {{site.data.keyword.vmwaresolutions_short}}-Konsole, um festzustellen, ob für die Version der vCenter Server-Instanz ein Upgrade von Version 2.4 oder früher auf Version 2.7 oder höher durchgeführt wurde.
* Um Konflikte zu vermeiden, verwenden Sie die IP-Adresse im oberen Teil des Teilnetzes, das derzeit von vCenter und PSC verwendet wird. Sie müssen eine temporäre IP-Adresse für die neue Appliancebereitstellung verwenden.

#### Vorgehensweise beim Upgrade von vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-procedure}

1. Melden Sie sich bei PSC (`https://<psc-fqdn>:5480`) und den vCenter-Benutzerschnittstellen für das Appliance-Management an, um zu überprüfen, ob das Rootkennwort abgelaufen ist. Wenn das Ablaufdatum für das Kennwort **1970** lautet, ist es abgelaufen, und Sie müssen SSH und die Bash-Shell in der PSC-Benutzerschnittstelle für das Appliance-Management aktivieren.
    1. Greifen Sie über SSH mit der Root-ID und dem entsprechenden Kennwort auf PSC zu. Auch wenn das Kennwort abgelaufen ist, können Sie sich anmelden.
    2. Verwenden Sie den Shell-Befehl **passwd**, um ein neues Rootkennwort für PSC und vCenter festzulegen.
    3. Speichern Sie die Kennwörter, die in der {{site.data.keyword.vmwaresolutions_short}}-Konsole angezeigt werden oder die Sie von IBM Support erhalten haben. Diese Kennwörter werden später wiederverwendet, wenn Sie ein Upgrade für die Appliances durchführen.
2. Verwenden Sie die integrierte Windows-ISO-Mount-Funktion, um die vCenter 6.7u1b ISO-Datei an Ihren Jump-Box-Server anzuhängen.
3. Befolgen Sie die VMware-Anweisungen, um ein Upgrade für vCenter durchzuführen. Weitere Informationen hierzu finden Sie unter [Durchführen eines Upgrades einer vCenter Server Appliance 6.0 oder 6.5 mit einer externen vCenter Single Sign-On- oder Platform Services Controller-Instanz unter Verwendung der GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html){:external}. Die VMware-Anweisungen ähneln dem Upgradeprozess von PSC. Sie verweisen
jedoch nicht auf den PSC, sondern auf den/die vCenter-FQDN/IP für den Upgradeprozess.

**Hinweise**:
* Die dort angegebene Voraussetzung **Das GUI-Upgrade muss auf einem Windows-, Linux- oder Mac-Computer ausgeführt werden, der sich im selben Netz wie die Appliance, für die Sie das Upgrade durchführen möchten, befindet** gilt für alle Teilnetze in {{site.data.keyword.cloud_notm}} in Ihrem Konto.
* Es wird empfohlen, vCenter als Quelle und Ziel für das Upgrade zu verwenden.

#### PSC-Funktion in vCenter konsolidieren

1. Melden Sie sich nach dem erfolgreichen Upgrade für PSC und vCenter bei der FLEX basierten vCenter-Benutzerschnittstelle an und überprüfen Sie im Abschnitt **Systemkonfiguration** den Zustand aller vCenter und PSC zugeordneten Services.  
2. Sichern Sie die PSC-Instanz.  Es empfiehlt sich die Verwendung eines dateibasierten Backups. Weitere Informationen finden Sie unter [File based backup in vSphere 6.7](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-8A16C037-F1E0-40C9-B106-05C30625B9CB.html){:external}.
3. Navigieren Sie zum Verzeichnis ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\converge``.
4. Kopieren Sie die Datei ``converge.json`` in ein lokales Laufwerk auf Ihrer virtuellen Jump-Maschine.
  * Wenn es sich um die erste PSC-Instanz handelt, die Sie konsolidieren, müssen Sie den Abschnitt **replication** aus der ``json``-Datei entfernen.
  * Wenn es sich um eine nachfolgende verknüpfte PSC-Instanz handelt, müssen Sie die Attribute ausfüllen, die im Abschnitt **replication** der ``json``-Datei angefordert werden.
5. Navigieren Sie zum Verzeichnis ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\decommission``.
6. Kopieren Sie die Datei ``decommission_psc.json`` in ein lokales Laufwerk auf Ihrer virtuellen Jump-Maschine.
7. Bearbeiten Sie die Dateien ``converge.json`` und ``dekommiss_psc.json``. Anweisungen für die zu bearbeitenden Felder befinden sich in den ``json``-Dateien. Es wird empfohlen, dass der ESXi-Host, der die PSC-Instanz enthält, anstelle von vCenter im Abschnitt **managing_esxi_or_vc** verwendet wird.
8. Navigieren Sie in einem Befehlsfenster zum Verzeichnis ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32``.
9. Führen Sie die Datei ``vcsa-util.exe`` mit dem Switch **converge** und dem Pfad zur zuvor bearbeiteten Datei ``converge.json`` aus. Beispiel: ``vcsa-util converge --no-ssl-certificate-verification c:\temp\converge.json -v``.
   1. Um fortfahren zu können, geben Sie **Y** ein, um zu bestätigen, dass die PSC-Instanz gesichert wurde.
   2. Geben Sie nach Abschluss des Prozesses **Y** ein, um den Warmstart von vCenter zu bestätigen.

   Wenn der Converge-Prozess mit der Nachricht ``ERROR converge Failed to get vecs users and permissions`` fehlschlägt, finden Sie Informationen zur Lösung des Problems unter [Converge to embedded failed!](https://virtualtassie.com/2018/vcenter-6-7-update-1-converge-to-embedded-failed/#comment-3713){:external}.
   {:note}

10. Nachdem vCenter neu gestartet wurde, überprüfen Sie den normalen Betrieb, indem Sie sich an der vCenter-Benutzerschnittstelle anmelden.
11. Navigieren Sie in einem Befehlsfenster zum Verzeichnis ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32``.
12. Führen Sie die Datei ``vcsa-util.exe`` mit dem Switch **decommission** und dem Pfad zur zuvor bearbeiteten Datei ``converge.json`` aus. Beispiel: ``vcsa-util decommission --no-ssl-certificate-verification c:\temp\decommission_psc.json -v``.
13.	Wenn der Befehl erfolgreich ausgeführt wurde, melden Sie sich an der FLEX-basierten vCenter-Benutzerschnittstelle an und überprüfen Sie, ob die vCenter-Appliance die einzige Appliance in nicht verknüpften Umgebungen ist und dass alle Services in einwandfreien Zustand sind.
14. Löschen Sie die alten PSC- und vCenter-Instanzen und die nicht verwendeten konsolidierten PSC-VMs.
15. Benennen Sie die vCenter Server-Instanz in der vCenter-Benutzerschnittstelle in **<instanzname>_vc_separate** um. Wenn der Name der vCenter Server-Instanz beispielsweise **production** ist, dann lautet der Name der vCenter-Benutzerschnittstelle **production_vc_separate**. Dies ist erforderlich, damit die Automatisierung ihre Funktion für diese vCenter Server-Instanz wiederaufnehmen kann.  

### Upgrade für ESXi-Hosts durchführen
{: #vc_vsphere_upgrade-procedure-esxi}

Die Funktion 'VMware Update Manager' in vCenter wird dazu verwendet, die ESXi-Hosts mit Updates und Patches auf die Version 6.7u1 zu aktualisieren. Ähnlich wie im Abschnitt zum NSX-Upgrade in diesem Dokument beschrieben müssen VMs, die nicht mit vMotion auf einen anderen Host migriert werden können, beendet werden; ansonsten kann es sein, dass der Upgradeprozess blockiert wird.
{:note}

#### ESXi-ISO-Datei in VUM hochladen
{: #vc_vsphere_upgrade-procedure-esxi-iso}

1. Stellen Sie sicher, dass VUM konfiguriert ist, um Patches von 'https://www.vmware.com' herunterzuladen. Weitere Informationen finden Sie in der [Einführung in VMware Update Manager](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro#vmware-update-manager-introduction).
2. Verwenden Sie FLEX oder HTML zum Öffnen der vCenter-Benutzerschnittstelle und navigieren Sie zur **VUM-Administratoransicht**.
3. Wählen Sie in der **VUM-Administratoransicht** die Registerkarte **ESXi-Images** und anschließend die Option **ESXi-Images importieren** aus.
4. Suchen Sie nach dem Image **ESXi 6.7u1iso**, das von VMware heruntergeladen wurde, und importieren Sie es in das VUM-Repository.

#### Vorgehensweise beim Upgrade der ESXi-Hosts
{: #vc_vsphere_upgrade-procedure-esxi-upgrade}

1. Navigieren Sie in der vCenter-Benutzerschnittstelle zu dem Cluster, der die ESXi-Hosts enthält, für die ein Upgrade durchgeführt werden soll.
2. Klicken Sie im Navigationsfenster auf die Registerkarte **Aktualisierungen**. Rufen Sie die Hostaktualisierungen auf und klicken Sie auf **Anhängen**.
3. Wählen Sie die Referenzversion (ISO-Image für ESXi-Upgrade) aus, die Sie in VUM hochgeladen haben, und klicken Sie auf **Korrigieren**.
4. Akzeptieren Sie die Endbenutzerlizenzvereinbarung und klicken Sie auf **OK**.
5. Überprüfen Sie die Hosts, die korrigiert werden sollen, und bestätigen Sie die Ergebnisse der Vorkorrektur.

   Sie müssen alle CDs oder DVDs abhängen, die an die VMs angeschlossen sind; ansonsten darf der Host, der diese VM enthält, nicht in den Wartungsmodus wechseln.
   {:note}

6. Nachdem die Vorkorrektur erfolgreich durchgeführt wurde, klicken Sie auf **Korrigieren**. Überwachen Sie den Upgradeprozess mit der Task zur Korrektur der Entität.
7. Überprüfen Sie nach dem Upgrade den Abschnitt mit der Zusammenfassung des Hosts, um sicherzustellen, dass ``VMware ESXi, 6.7.0`` angezeigt wird.

Wenn der Upgradeprozess sofort fehlschlägt und eine Fehlernachricht darüber angezeigt wird, dass der **Host nicht in den Wartungsmodus wechseln kann**, beenden Sie die Zerto-ZVAs und versuchen Sie es erneut. Die ZVRA-VMs werden automatisch gestartet, sobald ein Server korrigiert wurde. Informationen zum Fortsetzen der Zerto-Replikation während des Upgradeprozesses finden Sie im Abschnitt mit der [Vorgehensweise zum Versetzen eines Hosts mit einer zugeordneten VRA in den Wartungsmodus](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/){:external}.
{:note}

#### Intel NVME-Treiber-Patch zum VUM-Repository hinzufügen
{: #vc_vsphere_upgrade-procedure-esxi-nvme}

Wie im Abschnitt zum Herunterladen von Binärdateien beschrieben, müssen Sie den Inhalt der Datei ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` in das Repository importieren. Dieser wird dann im Folgeabschnitt als nicht kritische ESXi-Host-Erweiterung angewendet.

1. Extrahieren Sie die Datei ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` in ein lokales Laufwerk auf Ihrer virtuellen Jump-Maschine.
2. Verwenden Sie FLEX oder HTML zum Öffnen der vCenter-Benutzerschnittstelle und navigieren Sie zur **VUM-Administratoransicht**.
3. Wählen Sie in der **VUM-Administratoransicht** die Registerkarte **Patch-Repository** und anschließend die Option **Patches importieren** aus.
4. Suchen Sie nach dem extrahierten Inhalt des Verzeichnisses ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` und wählen Sie die Datei ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-offline_bundle-8733247.zip`` aus. Die Datei wird sofort in das VUM-Repository importiert.

Suchen Sie das Image im Patch-Repository als **wichtige** Hosterweiterung.

#### Patches für die ESXi-Hosts ausführen
{: #vc_vsphere_upgrade-procedure-esxi-patch}

Nach dem Upgrade wird empfohlen, alle kritischen und nicht kritischen ESXi-Host-Patches anzuwenden.

1. Wählen Sie in der vCenter-Benutzerschnittstelle den Cluster aus, der die Hosts enthält, die aktualisiert und korrigiert werden sollen.
2. Klicken Sie im Navigationsfenster auf die Registerkarte **Aktualisierungen** und wählen Sie die Registerkarte **Hostaktualisierungen** aus. Wählen Sie **Kritische Host-Patches (vordefiniert)** aus. Wiederholen Sie die Prozedur, um ein Upgrade für die ESXi-Hosts durchzuführen.
3. Klicken Sie im Navigationsfenster auf die Registerkarte **Aktualisierungen** und wählen Sie die Registerkarte **Hostaktualisierungen** aus. Wählen Sie **Nicht kritische Host-Patches (vordefiniert)** aus. Wiederholen Sie die Prozedur, um ein Upgrade für die ESXi-Hosts durchzuführen.

Sie müssen die Zerto zVRA-VMs möglicherweise als Teil dieses Prozesses erneut beenden.
{:note}

### Upgrade für zusätzliche Elemente durchführen
{: #vc_vsphere_upgrade-procedure-addtl}

#### Upgrade der vSAN Disk Format-Version durchführen
{: #vc_vsphere_upgrade-procedure-addtl-vsan}

Führen Sie ein Upgrade für die vSAN Disk Format-Version auf Version 7 durch.

1. Navigieren Sie in der vCenter-Benutzerschnittstelle zum dem Cluster, der die vSAN-Instanz enthält, für die ein Upgrade durchgeführt werden soll.
2. Wählen Sie im Clusterobjekt **Konfiguration > vSAN > Allgemein** aus.
3. Klicken Sie auf **Upgrade vorab prüfen**, um die Kompatibilität des Upgrades zu überprüfen und mögliche Probleme zu ermitteln. Warten Sie, bis die Überprüfung **Bereit zum Upgrade..** zurückgibt.
4. Klicken Sie auf **Upgrade**. Da das Upgrade eine Plattengruppe zu einem bestimmten Zeitpunkt verarbeitet, kann es je nach Größe des Clusters einige Zeit dauern, bis der Prozess beendet wird. Wählen Sie optional während des Prozesses die Option **Reduzierte Redundanz** aus. Dies kann zwar die Zeit, die für das Upgrade benötigt wird, erheblich reduzieren, es kann jedoch zu Datenverlusten kommen, wenn während des Upgradeprozesses ein Plattenfehler auftritt.

#### Upgrade für Virtual Distributed Switch durchführen
{: #vc_vsphere_upgrade-procedure-addtl-vds}

Durch das Durchführen eines Upgrades für Virtual Distributed Switch (VDS) auf Version 6.6.0 wird auch die E/A-Netzsteuerung aktualisiert und eine erweiterte Unterstützung für Link Aggregation Control Protocol (LACP) hinzugefügt.

1.	Wenn Sie HCX bereitgestellt haben, müssen Sie die Bereitstellung für den Cloud-Gateway-Teil von HCX zurücknehmen, bevor Sie ein Upgrade des VDS durchführen, auf dem sich die HCX-Instanz befindet. Stellen Sie sicher, dass HCX auf die aktuelle Version aktualisiert wird, bevor Sie das Cloud-Gateway erneut bereitstellen.
2.	Navigieren Sie in der vCenter-Benutzerschnittstelle zur Registerkarte **Netz**.
3.	Klicken Sie auf die Distributed Switch-Instanz, um ein Upgrade durchzuführen (entweder **SDDC-Dswitch-Private** oder **SDDC-Dswitch-Public**) und wählen Sie **Upgrade für Distributed Switch-Instanz durchführen** aus.

#### Upgrade für die Erweiterungen und Plug-ins der vCenter-Benutzerschnittstelle durchführen
{: #vc_vsphere_upgrade-procedure-addtl-extension}

Es liegt in Ihrer Verantwortung, alle Erweiterungen oder Snap-ins in der vCenter Server-Umgebung zu aktualisieren. Klicken Sie in der vCenter-Benutzerschnittstelle auf **Home > Verwaltung > Lösungen**, um den Status anzuzeigen und die vCenter-Erweiterungen und -Plug-ins zu aktivieren oder zu inaktivieren.

#### Upgrade für VMware-Tools durchführen
{: #vc_vsphere_upgrade-procedure-addtl-tools}

Verwenden Sie die vCenter-Benutzerschnittstelle zum Durchführen von Upgrades für VMware-Gastmaschinentools. Einige VMware-Tools sind möglicherweise für einige ältere VMs erforderlich, die in die vCenter Server-Umgebung migriert wurden.  

#### Upgrade der Hardwarestufe von virtuellen Maschinen durchführen
{: #vc_vsphere_upgrade-procedure-addtl-vmhw}

Ähnlich wie bei VMware-Gastmaschinentools kann ein Upgrade der vCenter Server-Umgebung dazu führen, dass sich ältere VMs in einem nicht unterstützten Status auf ihrer aktuellen Hardwarestufe befinden. Verwenden Sie die vCenter-Benutzerschnittstelle, um diese VMs nach Bedarf zu suchen und zu aktualisieren.  

#### Enhanced vMotion Compatibility-Modus auf Intel Skylake festlegen
{: #vc_vsphere_upgrade-procedure-addtl-evc}

Sie können Hosts mit der Intel Skylake-Generierung für einen Cluster nach dem Upgrade auf den Skylake Enhanced vMotion Compatibility (EVC)-Modus festlegen. Führen Sie die folgenden Schritte aus, um den EVC-Modus zu aktualisieren:

1. Klicken Sie im Cluster, der die Hosts enthält, auf **Konfigurieren**.
2. Klicken Sie in **VMware EVC** auf **Bearbeiten** und ändern Sie den EVC-Modus in **Intel "Skylake" Generation**.

Weitere Informationen hierzu finden Sie im Abschnitt [Enhanced vMotion Compatibility (EVC) processor support (1003212)](https://kb.vmware.com/s/article/1003212){:external}.

#### NSX-Manager und HCX-Manager neu konfigurieren, damit diese auf den PSC zeigen

1. Navigieren Sie in einem Web-Browser zur Benutzerschnittstelle der NSX-Manager-Appliance unter ``https://<nsx-manager-ip>`` oder `` https://<nsx-manager-hostname>``. Melden Sie sich mit den Berechtigungsnachweisen an.
2. Klicken Sie auf der Homepage auf **vCenter-Registrierung verwalten**.
3. Bearbeiten Sie die **URL des Suchservice** so, dass sie auf die vCenter-IP zeigt. Verwenden Sie den integrierten eigenständigen PSC (**PSC doesn’t exist anymore**).

## Ergebnisse nach dem Upgrade von vCenter Server vSphere-Software
{: #vc_vsphere_upgrade-results}

Wenn Sie die vSAN-Statusprüfung nach Abschluss des Upgrades ausführen, können Warnungen zu Firmware-Updates für die von {{site.data.keyword.cloud_notm}} gelieferten RAID- und Netzcontroller angezeigt werden. Nachdem Sie die Hosts ermittelt haben, für die Firmware-Updates erforderlich sind, öffnen Sie ein Ticket bei IBM Support, um die Firmware auf die empfohlenen Versionen zu aktualisieren.

1. Wählen Sie in der vCenter-Benutzerschnittstelle den Cluster aus, der die vSAN-Instanz enthält, deren Status überprüft werden soll.
2. Wählen Sie die Registerkarte **Überwachen** und anschließend die Registerkarte **vSAN** aus.
3. Wählen Sie **Status** aus und beachten Sie alle angezeigten Warnungen.
4. Wenn eine Warnung zur **Hardwarekompatibilität** angezeigt wird, erweitern Sie die Warnung, und klicken Sie auf die Nachricht **Controller-Firmware ist VMware-zertifiziert**, wenn sie sich in einem Warnstatus befindet.
5. Notieren Sie sich die Hosts, für die Empfehlungen zum Firmware-Update aufgeführt sind.
6. Öffnen Sie ein Ticket bei IBM Support, um die Zeiten zu planen, zu denen Sie die einzelnen Hosts für die jeweiligen Firmware-Updates außer Betrieb setzen können.

Wenn das Upgrade abgeschlossen ist, aktualisieren Sie das Support-Ticket bei IBM Support. Geben Sie die neuen Kennwörter an, die Sie im Rahmen dieses Upgradeprozesses erstellt haben. Geben Sie beispielsweise Kennwörter an, um die Appliance-Management-Services (-PSC und vCenter) im Support-Ticket bereitzustellen. IBM Support aktualisiert dann die {{site.data.keyword.vmwaresolutions_short}}-Konsole und die interne Datenbank, um die {{site.data.keyword.vmwaresolutions_short}}-Automatisierung auf einem Stand von Version 6.7 fortzusetzen. Dazu gehören das Hinzufügen und Entfernen von Services, Hosts, Clustern und der sekundären vCenter Server-Instanz.

## Zugehörige Links
{: #vc_vsphere_upgrade-related}

* [Releaseinformationen zu VMware NSX Data Center for vSphere 6.4.4](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:external}
* [Leitfaden zu NSX-Upgrades](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:external}
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
