---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-23"

---

# Anforderungen für das IBM Cloud-Infrastrukturkonto

Um {{site.data.keyword.vmwaresolutions_full}} für die Bestellung von Instanzen verwenden zu können, müssen Sie ein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) besitzen. Die Kosten der Komponenten, die in Ihren Instanzen bestellt werden, werden diesem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt.

**Hinweis:** Das Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) wurde früher als IBM SoftLayer-Konto bezeichnet.

## Berechtigungen für das IBM Cloud-Infrastrukturkonto

Das von Ihnen verwendete {{site.data.keyword.cloud_notm}}-Infrastrukturkonto muss bestimmte Berechtigungen besitzen, damit in Ihrem Namen die Komponenten in Ihren Instanzen bestellt und Operationen ausgeführt werden können. Die Berechtigungsanforderungen gelten für alle Typen von Instanzen und Services, die Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole bestellen.

Berechtigte Benutzer können die Berechtigungen für ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto im {{site.data.keyword.slportal}} prüfen und aktualisieren. Weitere Informationen finden Sie unter _Kundenportalberechtigungen eines Benutzers bearbeiten_ im Abschnitt [Benutzerprofil verwalten](../../../customer-portal/cpmanuserprof.html){:new_window}.

Tabelle 1. Erforderliche Berechtigungen für das {{site.data.keyword.cloud_notm}}-Infrastrukturkonto

| Berechtigung         | Details                                 |
|:-------------------|:----------------------------------------|
| Server hinzufügen | Diese Berechtigung ist für die folgenden Operationen erforderlich: {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}-Instanzen bestellen, auf denen VMware ESXi ausgeführt wird, und stündlich virtuelle Server bereitstellen, die für Operationen zur Konfiguration, zur Verwaltung und zum Support für Instanzen verwendet werden. |
| Server stornieren | Diese Berechtigung ist erforderlich, um {{site.data.keyword.baremetal_short}}-Instanzen, auf denen VMware ESXi ausgeführt wird, freizugeben und zurückzufordern. Wenn Sie Ihre Instanz löschen, werden die bestellten Komponenten automatisch in der richtigen Abhängigkeitsfolge freigegeben. |
| Virtual Server-Details anzeigen | Diese Berechtigung ist erforderlich, um die Details für die Servereinrichtung abzurufen, die für die Validierung der Bestellung und die automatisierte Konfiguration benötigt werden. |
| Speicher hinzufügen | Diese Berechtigung ist erforderlich, um den Sicherungsspeicher und den gemeinsam genutzten Speicher für die Instanz zu bestellen. |
| Speicher verwalten | Diese Berechtigung ist erforderlich, um den Sicherungsspeicher und den gemeinsam genutzten Speicher für die Instanz zu verwalten. |
| Hardware Firewall | Diese Berechtigung ist erforderlich, um die Firewallprotokolldateien und -einstellungen des Service "Fortinet on {{site.data.keyword.cloud_notm}}" anzuzeigen und zu bearbeiten, wenn dieser Service in Ihrer Instanz installiert ist. |
| Rechenressourcen mit öffentlichem Netzport bestellen | Diese Berechtigung ist erforderlich, um Hardware und Virtual Server-Instanzen (VSIs) mit öffentlichen Netzports zu bestellen. |
| IP-Adressen hinzufügen | Diese Berechtigung ist erforderlich, um portierbare private Teilnetzbereiche in Ihrem Namen zu bestellen, die für das Management der in einem vSphere-Cluster ausgeführten virtuellen Maschinen benötigt werden. Sobald Sie weitere Services zu Ihrer Instanz hinzufügen, werden die portierbaren privaten IP-Adressen zu VMware ESXi-Servern zugeordnet, um Bandbreite zu isolieren und zuzuordnen. |
| Tickets hinzufügen | Diese Berechtigung ist erforderlich, um Service-Tickets in Ihrem Namen zu öffnen. Tickets können für die folgenden Operationen erstellt werden: Einleitung von Wiederherstellungsoperationen und automatische Einleitung von Problemlösungsprozessen bei der Feststellung von Problemen. |
| Tickets bearbeiten | Diese Berechtigung ist erforderlich, um die Service-Tickets zu bearbeiten, die in Ihrem Namen erstellt wurden. |
| Tickets anzeigen | Diese Berechtigung ist erforderlich, um die Service-Tickets zu überwachen, die sich bei Verzögerungen und Problemen hinsichtlich der {{site.data.keyword.cloud_notm}}-Infrastrukturbereitstellung auf die Komponenten in Ihrer Instanz beziehen. |
| Hardwaredetails anzeigen | Diese Berechtigung ist erforderlich, um die Hardwaredetails abzurufen, die für die Validierung der Bestellung und die automatisierte Konfiguration benötigt werden. |
| Lizenzen anzeigen | Diese Berechtigung ist erforderlich, um die Lizenzen abzurufen und zu validieren, die von Ihrer Instanz verwendet werden. |
| Kennwörter anzeigen | Diese Berechtigung ist erforderlich, um die bestellten VSIs zu verwalten. |
| Einheitenüberwachung verwalten | Diese Berechtigung ist nicht erforderlich, um eine Bestellung aufzugeben, sie wird jedoch benötigt, um den Überwachungsstatus der {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}-Instanzen abzurufen und zu validieren, auf denen die VMware ESXi-Server in Ihrer Instanz ausgeführt werden. |

## VLAN Spanning für klassische Konten (ohne VRF)

Wenn Sie ein klassisches {{site.data.keyword.cloud_notm}}-Infrastrukturkonto verwenden (also kein VRF-Konto), muss die VLAN Spanning-Funktion aktiviert sein. Wenn die VLAN Spanning-Funktion bei klassischen Konten nicht aktiviert ist, sind die verschiedenen Komponenten der VMware-Virtualisierungsumgebung möglicherweise nicht in der Lage, miteinander zu kommunizieren. Informationen zum Aktivieren der VLAN Spanning-Funktion in Ihrem {{site.data.keyword.cloud_notm}}-Infrastrukturkonto finden Sie unter [VLAN Spanning aktivieren oder inaktivieren](../../../infrastructure/vlans/vlan-spanning.html){:new_window}.

### Zugehörige Links

* [Voraussetzungen für Cloud Foundation-Instanzen](../sddc/sd_planning.html)
* [Voraussetzungen für vCenter Server-Instanzen](../vcenter/vc_planning.html)
* [Benutzerkonten und -einstellungen](useraccount.html)
