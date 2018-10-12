---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Komponenten sichern

Sie sind für die Konfiguration, Verwaltung und Überwachung sämtlicher Softwarekomponenten verantwortlich. Dies schließt die Sicherung Ihrer Managementinfrastruktur und Ihrer Workloads sowie die Gewährleistung der Verfügbarkeit dieser Komponenten ein.

Als Teil der Lösung können Sie optional {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus in {{site.data.keyword.cloud_notm}} oder Veeam auf {{site.data.keyword.cloud_notm}}-Add-on-Services bereitstellen. Veeam und IBM Spectrum Protect Plus können helfen, die Sicherungsanforderungen für Ihre Managementkomponenten zu erfüllen.

Diese Add-on-Services werden zusammen mit {{site.data.keyword.cloud_notm}} Endurance-Speicher bereitgestellt. Die Services unterstützen Sie bei der Sicherung Ihrer Workloads und der Managementkomponenten. Die [Übersicht über die IBM Spectrum Protect Plus-Architektur](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_spplus){:new_window} und die [Übersicht über die Veeam-Architektur](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_veeam){:new_window} bieten nützliche Anleitungen zur Planung und Dimensionierung Ihrer Bereitstellung. Sie können auch [verwaltete Services](https://console.bluemix.net/infrastructure/vmware-solutions/console/gettingstarted/veeam/vcs/managed) für Ihre Veeam-Bereitstellung anfordern.

Verschiedene Lösungskomponenten erfordern unterschiedliche Strategien für die Sicherung. Einige Komponenten werden geschützt, indem für die zugehörige Konfiguration und die Daten Sicherungen auf Imageebene verwendet werden; für die Konfiguration und die Daten anderer Komponenten werden dateibasierte Sicherungen verwendet.

## Dateiserver für dateibasierte Sicherung

Für einige Komponenten, wie VMware vCenter Server, Platform Services Controller (PSC) und VMware NSX muss die Konfiguration auf einem Dateiserver gesichert werden.

Stellen Sie zur Speicherung dieser Sicherungen einen Linux-Dateiserver in Ihrem Cluster mithilfe der folgenden Schritte bereit:

1. Bestellen Sie ein privates portierbares Teilnetz aus der {{site.data.keyword.cloud_notm}}-Infrastruktur und verwenden Sie für dieses Teilnetz dasselbe VLAN wie für Ihre Systemkomponenten. Dies ist das private VLAN, in dem sich die Management-IP-Adressen für Ihre Hosts befinden.
2. Laden Sie ein Betriebssystemimage in Ihren VMware-Managementdatenspeicher, wie zum Beispiel ein Image für [Ubuntu Server 18.04 LTS](http://mirrors.service.softlayer.com/ubuntu-releases/ubuntu-server/bionic/daily-live/current/){:new_window}, aus der privaten {{site.data.keyword.cloud_notm}}-Spiegelung (Mirror) hoch.
3. Stellen Sie diese virtuelle Maschine (VM) in Ihrem Cluster über die Management-Portgruppe unter Verwendung einer zuvor bestellten privaten portierbaren IP-Adresse bereit. Stellen Sie sicher, dass die VM so konfiguriert wird, dass sie auf Ihre Active Directory/DNS-Server verweist, und fügen Sie die VM optional dem DNS Ihrer Unterdomäne hinzu.
4. Erstellen Sie auf diesem Server eine Sicherungsbenutzer-ID (kein Rootbenutzer) und stellen Sie sicher, dass alle erforderlichen Services konfiguriert und für Dateiübertragungen gestartet werden. Beispiel: FTP oder SSH.
5. Stellen Sie sicher, dass diese virtuelle Maschine in Ihren Veeam- oder IBM Spectrum Protect Plus-Managementsicherungsjob eingefügt wird.

## Dateibasierte vCenter-Sicherung

VMware vCenter Server und PSC stellen eine [Benutzerschnittstelle für das Appliance-Management und eine API zum Exportieren der Datenbank und der Konfiguration auf einen Dateiserver ](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.install.doc/GUID-3EAED005-B0A3-40CF-B40D-85AD247D7EA4.html){:new_window} unter Verwendung verschiedener Protokolle zur Verfügung. VMware dokumentiert ein Beispiel dafür, wie diese zur [regelmäßigen Ausführung als Cron-Job](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vsphere.vcsapg-rest.doc%2FGUID-222400F3-678E-4028-874F-1F83036D2E85.html){:new_window} direkt auf der vCenter Server Appliance und dem PSC konfiguriert werden kann. Sie können dieses Beispiel für Ihren Verwendungszweck anpassen.

Bei diesem Verfahren müssen Sie sowohl die vCenter Server Appliance als auch PSC separat sichern. Machen Sie sich mit den von VMware dokumentierten Aspekten und Einschränkungen vertraut und planen Sie entsprechend. Sehen Sie außerdem eine regelmäßige Rotation und einen regelmäßigen Gültigkeitsablauf für die Dateisicherungen auf Ihrem Dateiserver vor. Beachten Sie, dass VMware voraussetzt, dass die Sicherungsposition ein leerer Ordner ist. Daher müssen Sie dafür sorgen, dass Ihre Sicherungsrotation oder -automatisierung die Position für jeden nachfolgenden Sicherungsjob leer zurücklässt.

## Dateibasierte NSX-Sicherung

Eine geeignete Sicherung aller NSX-Komponenten ist für die Wiederherstellung des Betriebsstatus des Systems im Falle eines Ausfalls von entscheidender Bedeutung. Für das Design müssen Sie die NSX-Sicherung über die NSX-Manager-Sicherungsfunktion konfigurieren. Zu diesem Zweck können Sie den [NSX-Manager zur regelmäßigen Ausführung von Sicherungen auf Ihren Dateiserver konfigurieren](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window}. Stellen Sie sicher, dass Ihr Dateiserver oder die zugehörigen Daten ordnungsgemäß gesichert werden, und stellen Sie die Rotation alter NSX-Sicherungen sicher.

## Imagebasierte Sicherung von virtuellen Maschinen für das Management

Wenn Sie Ihre Instanz bereitgestellt und entweder den IBM Spectrum Protect Plus- oder den Veeam-Sicherungsservice bereitgestellt haben, konfigurieren Sie einen Sicherungsjob für Ihre virtuellen Maschinen für das Management. Planen Sie eine Sicherung der folgenden VMs mit mindestens sieben Tagen täglicher Sicherungen:

* Sofern vorhanden: VMware SDDC Manager
* Sofern vorhanden: Active Directory-Server
* Dateisicherungsserver

Planen Sie die Zuordnung einer ausreichenden Anzahl von Veeam- oder IBM Spectrum Protect Plus-Lizenzen für die Sicherung dieser virtuellen Maschinen und planen Sie mindestens 2 TB an Sicherungsspeicher für die VMs ein.

## Add-on-Services

Wenn Sie Add-on-Lösungskomponenten in Ihrer Instanz bereitstellen, müssen Sie außerdem die Sicherung dieser Komponenten im Rahmen Ihrer Sicherungsstrategie für das Management planen:

* Zerto Virtual Replication: Das Zerto Virtual Manager-System (ZVM-System) wird als {{site.data.keyword.cloud_notm}}-VSI (virtuelle Serverinstanz) bereitgestellt und seine Sicherung wird von Veeam oder IBM Spectrum Protect Plus nicht unterstützt. Wenn Ihre Disaster-Recovery-Strategie erfordert, dass das ZVM-System ohne Durchführung eines Standortfailovers wiederhergestellt wird, sollten Sie Ihre bevorzugte Windows-Sicherungslösung verwenden und das ZVM-System wiederherstellen.
* F5 BIG-IP: F5 empfiehlt eine [dateibasierte Sicherung der F5-Konfiguration](https://support.f5.com/csp/article/K13132){:new_window}, die Sie auf Ihren Dateiserver leiten können.
* FortiGate Security Appliance oder VM: Fortinet empfiehlt eine [dateibasierte Sicherung der FortiGate-Konfiguration](http://help.fortinet.com/fos50hlp/54/Content/FortiOS/fortigate-best-practices-54/Firmware/Performing_Config_Backup.htm){:new_window}, die Sie auf Ihren Dateiserver leiten können.
* HyTrust Cloud Control und Data Control: HyTrust unterstützt sowohl image- als auch dateibasierte Sicherungen der HyTrust-Server-Appliances. Weitere Informationen finden Sie in den HyTrust-Administrationshandbüchern.
* VMware HCX: Die HCX-Appliance-Managementschnittstelle bietet die Möglichkeit, ähnlich wie bei der vCenter Server Appliance eine dateibasierte Sicherung der HCX-Managerkonfiguration zu erstellen und herunterzuladen.

## Weitere Aspekte

Wenn Sie Ihren DNS-Server für Active Directory (AD) als {{site.data.keyword.cloud_notm}}-VSI (virtuelle Serverinstanz) bereitstellen, können Sie diesen nicht mit Veeam oder IBM Spectrum Protect Plus sichern. Verwenden Sie in diesem Fall Ihre bevorzugte Windows-Sicherungslösung für Sicherungs- und Wiederherstellungsoperationen oder planen Sie eine Bereitstellung Ihrer Instanz mit AD/DNS-VMs in Ihrem VMware-Cluster, sodass eine Sicherung mit Veeam oder IBM Spectrum Protect Plus möglich ist.

Ab VMware vCenter 6.5u2 unterstützt VMware die Sicherung der vCenter-Postgres-Datenbank durch die Verwendung imagebasierter Sicherungen mit integrierten Aussetzungs- und Fortsetzungsscripts für die Datenbank während des Sicherungsfensters, um die Datenbankintegrität sicherzustellen. Wenn Sie ein Upgrade Ihrer VMware-Instanz auf vCenter 6.5u2 durchführen, können Sie anstelle von dateibasierten Sicherungen Veeam oder IBM Spectrum Protect Plus verwenden, um Ihren vCenter Server und den PSC zu sichern. In diesem Fall müssen Sie die Stilllegungsfunktion (Quiesce) von Veeam oder IBM Spectrum Protect Plus verwenden, um die Datenbankintegrität sicherzustellen.

## Von der Sicherung wiederherstellen

Beim Wiederherstellen Ihrer Managementsicherungen sind einige besondere Aspekte zu beachten:

* Für vCenter und PSC stellt VMware ein Installationsprogramm zur Verfügung, das eine neue virtuelle Appliance bereitstellen und die Konfiguration von einer Sicherung wiederherstellen kann.
* Wenn Sie eine Appliance aus einer Sicherung wiederherstellen, erkennt das Installationsprogramm den Typ der Appliance (vCenter Server oder PSC) anhand der von Ihnen angegebenen Sicherungsinformationen.
* Da Sie die Bereitstellung direkt auf einem Ihrer Hosts durchführen, können Sie die Bereitstellung möglicherweise nicht auf einem verteilten Switch oder einer verteilten Portgruppe durchführen. Sie müssen möglicherweise einen temporären Standardswitch und eine Portgruppe für die Bereitstellung der wiederhergestellten Appliances erstellen und eine Ihrer VM-NICs zeitweilig auf diesen Switch migrieren, um Netzkonnektivität für Ihre VMs bereitzustellen. Nach der Bereitstellung können Sie die VMs auf die verteilte Portgruppe migrieren und die VM-NIC auf den verteilten virtuellen Switch zurückverlegen.
* Für NSX müssen Sie Ihren NSX-Manager und Ihre Controller möglicherweise erneut bereitstellen, bevor Sie die Konfiguration aus einer Sicherung wiederherstellen.
* Stellen Sie sicher, dass Sie sich mit den VMware-Aspekten und -Einschränkungen für die vCenter-Sicherung und -Wiederherstellung vertraut machen.

## Zusammenfassung

Durch geeignete Planung können Sie sicherstellen, dass Ihre VMware-Instanz in der Lage ist, den Verlust von Managementkomponenten durch eine erfolgreiche Wiederherstellung aufzufangen. Stellen Sie sicher, dass Sie den Erfolg Ihrer Sicherungsjobs und die Verfügbarkeit Ihrer Sicherungsdaten regelmäßig überwachen, und stellen Sie sicher, dass Sie Ihren Sicherungs- und Wiederherstellungsplan regelmäßig testen, und zwar sowohl für die Managementinfrastruktur als auch für Ihre Workloads.

### Zugehörige Links

* [Lösungsübersicht](solution_overview.html)
* [Übersicht über das Design](design_overview.html)
* [Skalierungskapazität](solution_scaling.html)
