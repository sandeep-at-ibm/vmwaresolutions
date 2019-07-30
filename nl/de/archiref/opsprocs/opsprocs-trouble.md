---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

---

# Fehlerbehebung
{: #opsprocs-trouble}

Um die Probleme mit Ihrer vCenter Server-Instanz zu beheben, müssen die Systemadministratoren die Symptome des Problems identifizieren, feststellen, welche Lösungskomponenten betroffen sind, einen Fix oder eine Ausweichlösung ermitteln und vorschlagen und den Fix dann testen.

* Symptome identifizieren - Für die schlechte Leistung oder die Nichtausführbarkeit Ihrer Instanz kann es mehrere Ursachen geben. Der erste Schritt einer effizienten Fehlerbehebung besteht darin, genau zu erkennen, was schief läuft. Diese Symptome werden unter Umständen in vSphere-Ereignissen und -Alarmen oder vom Operations Management unter	{{site.data.keyword.cloud}} gemeldet. Alternativ werden sie von einem Ihrer Benutzer über Ihren Service-Desk berichtet.
* Betroffene Komponenten isolieren - Nachdem Sie die Symptome des Problems identifiziert haben, müssen Sie ermitteln, welche Software- oder Hardwarekomponenten betroffen sind und unter Umständen das Problem verursachen und welche Komponenten nicht betroffen sind. Tools wie vCenter Operations Management unter {{site.data.keyword.cloud_notm}} unterstützen Sie bei diesem Schritt.
* Fix oder Ausweichlösung vorschlagen - Sobald Sie die Symptome kennen und die Komponenten isoliert haben, können Sie nach möglichen Fixes und Ausweichlösungen suchen. Ihre Systemadministratoren verwenden dafür auch das {{site.data.keyword.cloud_notm}}-Portal, einschließlich der Fehlerbehebungsszenarios in diesem Dokument sowie IBM ServiceNow und VMware Knowledge Base. Darüber hinaus gibt es viele Wikis und Blogs, die Ihnen helfen können. Für noch schnellere Problemlösungen umfasst Operations Management unter {{site.data.keyword.cloud_notm}} eine Reihe von Lösungen für bereits bekannte Probleme.
* Mögliche Lösungen testen - Wenn Sie die Symptome des Problems kennen, die betroffenen Komponenten kennen und einen Fix bzw. eine Ausweichlösung vorgeschlagen haben, testen Ihre Systemadministratoren die Lösungen systematisch, bis das Problem behoben wurde.

vSphere enthält ein benutzerkonfigurierbares Ereignis- und Alarm-Subsystem, das Ereignisse in der gesamten vSphere-Umgebung verfolgt und die Daten in Protokolldateien und in der vCenter-Datenbank speichert. Dieses Subsystem ermöglicht es Systemadministratoren auch, die Bedingungen anzugeben, unter denen Alarme ausgelöst werden. Alarme ändern ihren Status von Warnungen zu schwerwiegenderen Alerts, wenn sich die Systembedingungen ändern, und können automatische Alarmaktionen auslösen, z. B. eine E-Mail an das Systemadministratorteam. Diese Funktionalität ist nützlich, wenn Sie informiert werden oder Sofortmaßnahmen ergreifen möchten, wenn bestimmte Ereignisse oder Bedingungen für ein bestimmtes Bestandsobjekt oder für eine Gruppe von Objekten auftreten.

Zusätzliche Tools wie die in Operations Management in der {{site.data.keyword.cloud_notm}}-Architektur enthaltenen Tools stellen weiterführende Unterstützung zum Identifizieren von Symptomen, Isolieren der betroffenen Komponenten und Vorschlagen eines Fix oder einer Ausweichlösung bereit.

## Richtlinien
{: #opsprocs-trouble-guidelines}

Die folgenden Richtlinien haben sich bei der Fehlerbehebung Ihrer {{site.data.keyword.vmwaresolutions_short}}-Probleme bewährt:
* Gehen Sie die Fehlerbehebung und Problemlösung systematisch an.
* Stehen die Symptome im Zusammenhang mit Verfügbarkeit, Nutzung oder Konfiguration:
 *  Verfügbarkeit - Diese Symptome beziehen sich auf die Verfügbarkeit von Hardware- und Softwarekomponenten und sind durch das Ausbleiben einer Antwort gekennzeichnet. Diese Probleme werden häufig durch ein Hochverfügbarkeitsdesign aufgefangen und wirken sich nicht direkt auf Ihre Workloads und Benutzer aus.
 * Nutzung - Diese Symptome beziehen sich auf Kapazität und Leistung und sind durch langsame Ausführung oder das Nichtladen von Komponenten gekennzeichnet. Eine proaktive Verwaltung von Kapazitäten reduziert diese Probleme erheblich.
 * Konfiguration - Diese Probleme treten in der Regel bei der Bereitstellung neuer Services oder infolge einer Änderung auf. Falsche Einstellungen können sich in Form von Verfügbarkeits- oder Nutzungssymptomen bemerkbar machen. Beispielsweise wird eine falsche IP-Adresse als Verfügbarkeitsproblem angezeigt, während zu geringe RAM-Einstellungen einer virtuellen Maschine (VM) Symptome für ein Nutzungsproblem hervorrufen können.
* Versuchen Sie, das Problem auf eine Komponente in der Umgebung zu isolieren.
* Notieren Sie sich Ihre Schritte.
* Dokumentieren Sie Ihre Softwareversionen.
* Dokumentieren Sie Ihre Teilnetze und die Nutzung von IP-Adressen, einschließlich VIP- und NAT-Adressen.
* Erstellen Sie Diagramme Ihres Netzes. Sie benötigen eine Reihe von Diagrammen, die die physischen (zugrunde liegenden) und die logischen (darüber liegenden) Schichten darstellen.
* Sehen Sie sich die letzten Änderungen an der Umgebung an.
* Finden Sie heraus, welche Auswirkungen der Fix hat, sperren Sie sich nicht selbst aus den Managementschnittstellen aus.
* Stellen Sie sicher, dass Sie über Sicherungen aller Schlüsselkomponenten verfügen, falls diese erneut geladen oder zurückgesetzt werden müssen.
* Nehmen Sie jeweils nur eine Änderung vor.
* Dokumentieren Sie jede Änderung und ihre Ergebnisse.
* Wenn Sie eine Support-Anforderung öffnen, muss Ihre Dokumentation vollständig sein und relevante Informationen enthalten. Überprüfen Sie die angezeigten Symptome und ermitteln Sie die Komponenten, von denen Sie vermuten, dass sie fehlerhaft sind. Verwenden Sie die korrekte Terminologie. Versuchen Sie, Ungenauigkeiten oder Mehrdeutigkeiten in Ihren Aussagen zu minimieren.
* vSphere ESXi- und vCenter Server-Konfigurationsdateien steuern das Verhalten des Systems. Finden Sie heraus wo sich diese Dateien befinden. Die meisten Konfigurationsdateieinstellungen werden während der Installation festgelegt, können jedoch nach der Installation geändert werden.
* Protokolldateien erfassen Nachrichten, die vom Kernel und von verschiedenen Subsystemen und Services generiert werden. vSphere ESXi- und vCenter-Services verwalten separate Protokolldateien. Finden Sie heraus, wo sich diese befinden und wie darauf zugegriffen werden kann.
* Setzen Sie sich damit auseinander, wie gängige Systemverwaltungstools Sie bei der Diagnose unterstützen können.

Weitere Informationen finden Sie unter [Fehlerbehebungsrichtlinien KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}.

## Fehlerbehebung mit Protokolldateien
{: #opsprocs-trouble-logs}

Protokolldateien sind eine hervorragende Quelle für Informationen zur Fehlerbehebung. Allerdings sind in der Praxis die Anzahl der Protokolldateien und die schiere Menge an Einträgen in den einzelnen Protokolldateien ein Hindernis bei der Diagnose. Unter [Fehlerbehebung mit Protokolldateien KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window} wird genau angegeben, wo sich diese Protokolldateien in der VMware-Umgebung befinden. Aufgrund der Anzahl der Protokolldateien und der schieren Menge an Einträgen in den einzelnen Protokollen sollten Sie in Betracht ziehen, die Tools in Operations Management unter {{site.data.keyword.cloud_notm}} zur Unterstützung bei der Erfassung und Analyse von Ereignisprotokollen zu nutzen.

## Gängige Fehlerbehebungsszenarios
{: #opsprocs-trouble-common}

Um Hilfestellung bei der Isolierung der betroffenen Komponenten zu geben, wurde diese Dokumentation gängiger Fehlerbehebungsszenarios wie folgt unterteilt:

* Virtuelle Maschinen - diese Fehlerbehebungskapitel enthalten Anweisungen für potenzielle Probleme auf VMs.
* Hosts - diese Fehlerbehebungskapitel enthalten Anweisungen für vSphere ESXi-Hostprobleme.
* Cluster - diese Fehlerbehebungskapitel enthalten Anweisungen zur Verfügbarkeit und zum Ressourcenmanagement.
* Speicher - diese Fehlerbehebungskapitel enthalten Anweisungen zum Beheben von vSAN- und NFS-Speicherproblemen.
* Netz - diese Fehlerbehebungskapitel enthalten Anweisungen zum Beheben von Netzproblemen.
* vCenter - diese Fehlerbehebungskapitel enthalten Anweisungen zum Beheben von vCenter-Problemen.
* Lizenzen - diese Fehlerbehebungskapitel enthalten Anweisungen zum Beheben von Lizenzproblemen. Typischerweise beziehen sie sich auf Clients, die ihre eigenen Lizenzen zu {{site.data.keyword.cloud_notm}} hinzugefügt haben.

### Virtuelle Maschinen
{: #opsprocs-trouble-common-vm}

Tabelle 1. Fehlerbehebung für virtuelle Maschinen

| Titel | Beschreibung |
|---|---|
| Generische VM-Fehlerbehebung | Weitere Informationen finden Sie unter [Fehlerbehebung bei virtuellen Maschinen](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window}. |
| VM-Leistungsprobleme | Informationen zum Beheben der Symptome von VM-Leistungsproblemen, z. B. ein langsames Starten des Gastbetriebssystem, eine schlechte Leistung von Anwendungen, ein langsames Starten von Anwendungen oder das Ausbleiben einer Antwort von Anwendungen, finden Sie unter [Fehlerbehebung bei Leistungsproblemen virtueller Maschinen auf ESX/ESXi (2001003)](https://kb.vmware.com/s/article/2001003){:new_window}. |
| Wiederherstellen einer verwaisten VM | Informationen zum Wiederherstellen verwaister VMs, bei denen es sich um VMs handelt, die in der vCenter-Datenbank vorhanden sind, aber vom vSphere ESXi-Host nicht erkannt werden, finden Sie unter [Knowledge Base-Artikel - KB0012862 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=57c90b74dbdd7300c4fa302f9d96199e){:new_window}. |
| VM lässt sich nicht einschalten | Weitere Informationen finden Sie unter [Fehlerbehebung einer virtuellen Maschine, die sich nicht einschalten lässt (2001005)](https://kb.vmware.com/s/article/2001005){:new_window}. |
| VM lässt sich nach dem Klonen oder Bereitstellen aus einer Vorlage nicht einschalten | In diesem [VMware-Artikel](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2742CE14-20FD-416F-B89C-A156053A973F.html){:new_window} werden Probleme besprochen, die sich auf eine VM auswirken, nachdem sie geklont oder aus einer Vorlage bereitgestellt wurde. |
| VMware-Tools sind veraltet oder nicht installiert - VMware-Tools sollten auf den VMs installiert und auf dem neuesten Stand sein | Unter [IBM Cloud KB0012161](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=797afaf0dbb477486001327e9d9619e6){:new_window} finden Sie Anweisungen zu diesen Tasks. |
| Alte VM-Netzeinheiten | Wenn VM-Netzeinheiten nicht auf dem neuesten Stand sind, kann dies die Netzleistung und die Anwendungsleistung beeinträchtigen. Weitere Informationen zum Bereitstellen einer neuen virtuellen Netzeinheit und eines neuen Treibers finden Sie unter [Auswählen eines Netzadapters für Ihre virtuelle Maschine (1001805)](https://kb.vmware.com/s/article/1001805){:new_window}. |
| VM-Speicherbegrenzung | Speicherbegrenzungen werden häufig verwendet. Wenn allerdings ein Gastbetriebssystem nicht auf den erforderlichen Speicher zugreifen kann, können die Anwendungen im Gastbetriebssystem eine schlechte Leistung aufweisen. Weitere Informationen zum Beheben des Problems finden Sie unter [Konfigurieren von Einstellungen für die Ressourcenzuteilung](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-14102AB7-2CF9-42E3-9642-3EB6629EF530.html){:new_window}. |
| VM-Snapshots | Snapshots sind zwar nützlich, aber die Menge und das Alter der Snapshots einer VM wirken sich direkt auf die Leistung der VM aus. Informationen zum Beheben des Problems finden Sie unter [Konsolidieren von Snapshots](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2F4A6D8B-33FF-4C6B-9B02-C984D151F0D5.html){:new_window}. |
| VM-Protokollierung | Wenn die Protokollierung nicht ordnungsgemäß konfiguriert wurde, kann die Kapazität des Datenspeichers negativ beeinflusst werden. Informationen zum Beheben des Problems finden Sie unter [Konfigurieren der Protokollierungsebenen für das Gastbetriebssystem](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-F465D340-6556-49E8-B137-C0B4A060E83B.html){:new_window}. |
| Fehlerbehebung bei Netzkonnektivitätsproblemen | Symptome können sein, dass die VM keine Verbindung zum Netz herstellen kann oder dass keine Netzkonnektivität mit einer einzelnen VM besteht. Weitere Informationen zum Beheben des Problems finden Sie unter [Fehlerbehebung bei Netzverbindungsproblemen der virtuellen Maschine (1003893)](https://kb.vmware.com/s/article/1003893?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}.  |
| Bestimmen, ob mehrere virtuelle CPUs Leistungsprobleme verursachen  | Informationen zur Fehlerbehebung von VMs, die Leistungsprobleme feststellen, wenn sie mit mehreren CPUs konfiguriert werden, finden Sie unter [Bestimmen, ob mehrere virtuelle CPUs Leistungsprobleme verursachen (1005362)](https://kb.vmware.com/s/article/1005362?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}. Diese Probleme können geringe Übertragungsgeschwindigkeiten beim Kopieren von Daten auf eine oder von einer VM, Zeitüberschreitungen für Sicherungsjobs oder eine schlechte VM-Leistung sein.  |
| Eine VM wurde ausgeschaltet oder erneut gestartet  | Informationen zum Beheben des Problems finden Sie unter [Bestimmen, warum eine virtuelle Maschine ausgeschaltet oder erneut gestartet wurde (1019064)](https://kb.vmware.com/s/article/1019064?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}. |
| Mindestens eine virtuelle Maschine weist eine schlechte Antwortzeit auf |  Informationen zum Isolieren eines Leistungsproblems auf einem vSphere ESXi-Host finden Sie unter [Fehlerbehebung bei Leistungsproblemen virtueller Maschinen auf ESX/ESXi (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}. Leistungsprobleme können durch CPU-Einschränkungen, Speicherüberbelegung, Speicherlatenz oder Netzlatenz verursacht werden. |

### vSphere ESXi-Hosts
{: #opsprocs-trouble-common-host}

Tabelle 2. Typische Fehlerbehebung für vSphere ESXi-Hosts

| Titel | Beschreibung |
|---|---|
| ESXi-Befehle | Eine Übersicht der Befehlszeilenschnittstellen in vSphere, der ESXi-Shellbefehle und der vCLI-Befehle (vCLI - VMware® vSphere CommandLine Interface) finden Sie unter [Einführung in vSphere-Befehlszeilenschnittstellen](https://vdc-download.vmware.com/vmwb-repository/dcr-public/bc4fa31a-40ac-4aa9-a6a1-7171d1fff7f4/740990ee-4d65-4627-a9d4-0f046cb78aec/vsphere-esxi-vcenter-server-67-command-line-interface-getting-started-guide.pdf){:new_window}. |
| vSphere HA-Hostzustände | Wenn vCenter einen vSphere HA-Hostzustand meldet, der auf eine Fehlerbedingung auf dem Host hinweist, muss dieses Problem behoben werden, da es verhindern kann, dass vSphere HA die VMs nach einem Fehler erneut startet. Weitere Informationen finden Sie unter [Fehlerbehebung von vSphere HA-Hostzuständen](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window}. |
| vSphere ESXi-Host reagiert nicht | Informationen zur Fehlerbehebung eines vSphere ESXi-Host mit dem Zustand 'Antwortet nicht' oder 'Verbindung unterbrochen' bzw. wenn die VMs auf dem Host in vCenter ausgeblendet sind, finden Sie unter [ESX/ESXi-Hosts reagieren nicht oder sind ausgeblendet (1019082)](https://kb.vmware.com/s/article/1019082){:new_window}. |
| Beim Einschalten einer VM wird der Fehler `Datei nicht gefunden` angezeigt | Informationen zum erneuten Erstellen einer verlorenen VM-Festplattendeskriptordatei (VMDK) finden Sie unter [Neuerstellen einer fehlenden VM-Festplattendeskriptordatei (1002511)](https://kb.vmware.com/s/article/1002511){:new_window}. |
| VM-Leistungsprobleme | Informationen zum Isolieren eines Leistungsproblems auf einem vSphere ESXi-Host finden Sie unter [Fehlerbehebung bei Leistungsproblemen virtueller Maschinen auf ESX/ESXi (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}. Leistungsprobleme können durch CPU-Einschränkungen, Speicherüberbelegung, Speicherlatenz oder Netzlatenz verursacht werden. |
| Bare-Metal-Server ist inaktiv | Wenn der Bare-Metal-Server, auf dem vSphere ESXi ausgeführt wird, nicht reagiert oder inaktiv ist, melden Sie sich an der {{site.data.keyword.cloud_notm}}-Managementbenutzerschnittstelle oder -Konsole an und überprüfen Sie den Status. Falls erforderlich, öffnen Sie einen Fall, um Unterstützung für Ihren Bare-Metal-Server zu erhalten. Weitere Informationen finden Sie unter [Mit Supportfällen arbeiten](/docs/get-support?topic=get-support-open-case#open-case){:new_window}. |
| vSphere ESXi-Host ist getrennt oder reagiert nicht  | Weitere Informationen finden Sie unter [Diagnostizieren eines in VMware vCenter Server getrennten oder nicht reagierenden ESXi/ESX-Hosts (1003409)](https://kb.vmware.com/s/article/1003409?lang=en_US){:new_window}. |
| Purple Screen of Death  | Der Purple Screen of Death (PSOD) ist eine Kernelpanik und der vSphere ESXi-Kernel (vmkernel) löst diese Sicherheitsmaßname aus, wenn ein Ereignis/Fehler auftritt, das bzw. der nicht behebbar ist und eine weitere Ausführung ein hohes Risiko für die Services und VMs darstellen würde. Wenn die Panik auftritt und der vSphere ESXi-Host abstürzt, beendet er alle aktiven Services und alle gehosteten VMs. Die VMs werden nicht ordnungsgemäß heruntergefahren, sondern abrupt ausgeschaltet. Wenn der Host Teil eines Clusters ist und Sie HA konfiguriert haben, werden diese VMs auf den anderen Hosts im Cluster erneut gestartet. Weitere Informationen finden Sie unter [Knowledge Base-Artikel - KB0012864 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=dd5d2330db11f300c4fa302f9d96198d){:new_window}. |

### Speicher
{: #opsprocs-trouble-common-storage}

Tabelle 3. Typische Fehlerbehebung für Speicher

| Titel | Beschreibung |
|---|---|
| Speicherfehlerbehebung | Weitere Informationen zu langsamer Verarbeitung, unvorhersehbaren Fehlern, beschädigten Platten oder VMs finden Sie unter [Fehlerbehebung von Speicherproblemen bei Verwendung von VMware-Produkten (2013160)](https://kb.vmware.com/s/article/2013160?lang=en_US){:new_window}. |
| vSAN-Fehlerbehebung | Weitere Informationen finden Sie unter [Fehlerbehandlung in vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-35A4B700-6640-4519-A885-440A1AE8D3BD.html){:new_window}.  |
| vSAN-Plattenfehler | Weitere Informationen dazu, wie Sie eine fehlgeschlagene Platte ermitteln und ihre Ersetzung anfordern können, finden Sie unter [Festplatte/Magnetplatte in einer VMware vSAN-Plattengruppe schlägt fehl (2077185)](https://kb.vmware.com/s/article/2077185){:new_window}. |
| Beheben von Problemen mit dem vSAN-Status | Auf der Seite 'Überwachung' von VMware vSphere Web Client werden möglicherweise Alerts und Warnungen für Probleme im Zusammenhang mit dem vSAN-Status angezeigt. Informationen zum Beheben dieser Probleme finden Sie unter [Statusalerts und -warnungen für virtuelles SAN (vSAN)](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_vsan_alerts#trbl_vsan_alerts){:new_window}.|
| vSAN-Neuverteilung | Wenn Platten im Rahmen der Statusprüfung Fehler melden, die darauf hinweisen, dass der Cluster unausgewogen ist und dass es Platten mit einer hohen Speicherbelegung und andere mit einer niedrigen Speicherbelegung gibt, sollten Sie eine proaktive Neuverteilung ausführen. Dadurch wird manuell eine Neuverteilung der Objekte in einem vSAN-Cluster gestartet. Weitere Informationen zur proaktiven Neuverteilung in vSAN und wann diese anwendbar ist, finden Sie unter [Proaktive Neuverteilung in vSAN (2149809)](https://kb.vmware.com/s/article/2149809){:new_window}. |
| Starten eines vSAN-Statustests | Wenn Sie vermuten, dass mit vSAN ein Problem besteht, können Sie einen Statustest starten, um zu überprüfen, ob die Clusterkomponenten wie erwartet funktionieren. Wenn Sie einen Test der VM-Erstellung ausführen, wird auf jedem Host im Cluster eine VM erstellt und wieder gelöscht. Werden diese Tasks erfolgreich ausgeführt, funktionieren die Clusterkomponenten wie erwartet, und der Cluster kann verwendet werden. Der Test der Netzleistung wird verwendet, um Konnektivitätsprobleme zu erkennen und zu diagnostizieren und um sicherzustellen, dass die Netzbandbreite zwischen den Hosts angemessen ist. Weitere Informationen finden Sie unter [Proaktive Tests](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-B88B5900-33A4-4821-9659-59861EF70FB8.html){:new_window}. |
| Überwachen der vSAN-Leistung | Weitere Informationen finden Sie unter [Überwachen der vSAN-Leistung](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-3D2D1382-9DDC-44D4-AF3B-ACA4F1DDBDCC.html){:new_window}. Leistungsdiagramme stehen für Cluster, Hosts, physische Platten, VMs und virtuelle Platten zur Verfügung. |
| vSAN-Fehlerbehebung | Weitere Informationen finden Sie unter [Behandeln von Fehlern und Fehlerbehebung in vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-0F3C4D3F-9B86-4879-9C60-D6A977523112.html){:new_window}. |


### Netz
{: #opsprocs-trouble-common-network}

Tabelle 4. Typische Fehlerbehebung für Netze

| Titel | Beschreibung |
|---|---|
|  '/var/log' in NSX Edge läuft bei aktivem Edge voll | Weitere Informationen zu einer Ausweichlösung, wenn Sie darauf hingewiesen werden, dass die Belegung der Edge-Platte zunimmt, und feststellen dass die Partition '/var/log' vollläuft, finden Sie unter ['/var/log' in NSX Edge läuft bei aktivem Edge voll (50108355)](https://kb.vmware.com/s/article/50108355){:new_window}.  |
| Testen der HCX-Bandbreite  | Informationen zur Verwendung von `perftest` zum Suchen der verfügbaren Bandbreite in den HCX-Tunneln, falls Sie vermuten, dass ein Netzbandbreitenproblem mit HCX besteht, finden Sie unter [Schritte zum Ausführen von Perftest in HCX (56211)](https://kb.vmware.com/s/article/56211?lang=en_US){:new_window}. Für jeden Perftest (`perftest`) werden bidirektionale Tests durchgeführt. Ein Gateway des Gateway-Paars befindet sich im Quellenrechenzentrum (es wird das als OnPrem bezeichnet) und das andere in {{site.data.keyword.cloud_notm}}. Unter Verwendung von `perftest` wird getestet, ob der vom Absender erzielte Durchsatz so hoch wie die für die Verbindung mögliche Kapazität ist. Deshalb wird für jeden Test eine höhere Absenderrate als Empfängerrate angezeigt. Sie können den Wert der Empfängerrate als Ergebnis des unidirektionalen Durchsatzes betrachten. |
| Fehlerbehebung für HCX | Weitere Informationen finden Sie unter [Fehlerbehebung für HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting). |
| HCX-Synchronisation mit 0 % Fortschritt und 0 Bytes und dem Status 'Fehler' | Weitere Informationen finden Sie unter [HCX-Replikation wird synchronisiert mit 0 % Fortschritt und 0 Bytes und dem Status 'Fehler' (56710)](https://kb.vmware.com/s/article/56710?lang=en_US#q=HCX){:new_window}. |
| Schlechte VM-Netzleistung | Überprüfen Sie die Einstellungen für virtuelle NICs der VM. VMware empfiehlt virtuelle NICs vom Typ VMXNET 3 für VMs, da dies die aktuelle Generation paravirtualisierter NICs ist, die für eine höhere Leistung konzipiert wurden. Prüfen Sie die Kompatibilität von VMXNET 3 anhand der VMware-Kompatibilitätsliste. Wird VMXNET 3 unterstützt, ändern Sie den virtuellen NIC, um zusätzliche Netzleistung zu erhalten. Weitere Informationen finden Sie unter [Fehlerbehebung beim Netz](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}. |

### vCenter
{: #opsprocs-trouble-common-vcenter}

Tabelle 5. Typische Fehlerbehebung für vCenter

| Titel | Beschreibung |
|---|---|
| VM-Konsolenzugriff | Weitere Informationen finden Sie unter [Knowledge Base-Artikel - KB0012863 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=5446a73cdb1db300c4fa302f9d961934){:new_window}. |
| Neues vCenter Server-Zertifikat scheint nicht geladen zu werden | Nachdem Sie die vCenter Server-Standardzertifikate ersetzt haben, werden die neuen Zertifikate scheinbar nicht geladen. Weitere Informationen finden Sie unter [Neues vCenter Server-Zertifikat scheint nicht geladen zu werden](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-415CF843-42E8-4AD7-98EC-7265227337B6.html){:new_window}. |
| vCenter Server kann keine Verbindung zu verwalteten Hosts herstellen | Nachdem Sie die vCenter Server-Standardzertifikate ersetzt haben und das System erneut starten, kann vCenter Server keine Verbindung zu verwalteten Hosts herstellen. Weitere Informationen finden Sie unter [vCenter Server kann keine Verbindung zu verwalteten Hosts herstellen](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-8D3DCEC4-50B6-4523-BF24-0DE6C65600E9.html){:new_window}. |
| Konfigurieren von vSphere HA nicht möglich, wenn benutzerdefinierte SSL-Zertifikate verwendet werden | Nach der Installation von benutzerdefinierten SSL-Zertifikaten schlägt die Aktivierung von vSphere High Availability (HA) fehl. Weitere Informationen finden Sie unter [Konfigurieren von vSphere HA nicht möglich, wenn benutzerdefinierte SSL-Zertifikate verwendet werden](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3FC16DC8-7157-4340-AB8A-B8DC87D7DC0F.html){:new_window}. |

### Lizenzen
{: #opsprocs-trouble-common-licenses}

Tabelle 6. Typische Fehlerbehebung für Lizenzen

| Titel | Beschreibung |
|---|---|
|  Inkompatible oder falsche Konfiguration von Lizenzen | Weitere Informationen finden Sie unter [Fehlerbehebung bei der Hostlizenzierung](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window}. |
|  VM lässt sich nicht einschalten | Möglicherweise gibt es ein Lizenzproblem, wenn Sie eine VM auf einem vSphere ESXi-Host nicht einschalten können und die Nachricht ``Die 60-tägige Testphase des Hosts ist abgelaufen oder die Lizenz für den Host ist abgelaufen`` empfangen. Weitere Informationen finden Sie unter [Einschalten einer virtuellen Maschine fehlgeschlagen](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-D4770546-9F9A-4F1E-AC1C-CF313E6130F4.html){:new_window}. |
| Eine Funktion ist nicht verfügbar oder eine Konfiguration kann nicht geändert werden  | Weitere Informationen finden Sie unter [Eine Funktion kann nicht konfiguriert oder verwendet werden](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-26C0E2F0-A581-4A5A-B1F7-2BA4F151E27A.html){:new_window}.  |


## Zugehörige Links
{: #opsprocs-trouble-links}

* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-trbl_support#trbl_support)
* [Übersicht über die Fehlerbehebung für vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-C70D5A5E-7D84-446C-B8CE-0766AA7351A4.html){:new_window}
* [Fehlerbehebung für vSphere mit Protokollen](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-552CC9E8-441C-434A-88FC-3F50881245D7.html){:new_window}
* [Operations Management unter {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
* [Erfassen von Supportprotokollen](https://kb.vmware.com/s/article/1010705){:new_window}
* [Überwachen von Ereignissen, Alarmen und automatisierten Aktionen](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}
* [vSphere-Systemprotokolldateien](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-DABCB024-E083-4A4D-8AE0-D1AF4CB3800C.html){:new_window}
* [Hinweise zum Ändern von vCenter Server-Artefakten](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
