---

copyright:

  years:  2016, 2017

lastupdated: "2017-08-28"

---

# Releaseinformationen für V1.8
{: #relnotes_v18}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Service "Fortinet on IBM Cloud"
{: #relnotes_v18-fortinet}

Der Service "Fortinet on {{site.data.keyword.cloud_notm}}" ist jetzt für Cloud Foundation- und für vCenter Server-Instanzen verfügbar. Dieser Service stellt ein Paar von Einheiten der FortiGate Security Appliance (FSA) 300-Serie in einem Hochverfügbarkeitsmodus bereit, um Firewall-, Routing-, NAT- und VPN-Services für den Schutz aller Server und virtuellen Maschinen im öffentlichen VLAN Ihrer Instanzen zur Verfügung zu stellen. Sie können Instanzen bestellen, die den Service "Fortinet" enthalten, oder diesen Service zu einem späteren Zeitpunkt über die Seite mit den Instanzdetails zu Ihren vorhandenen Instanzen hinzufügen.

Nachdem der Fortinet-Service erfolgreich installiert wurde, können Sie Firewallregeln für FSA über die FortiGate-Konsole verwalten und konfigurieren. Sie müssen sicherstellen, dass die FSA-Firewallregeln definiert sind, um abgehende HTTPS-Übertragungen zu ermöglichen, die von Managementkomponenten wie der virtuellen Maschine von IBM CloudDriver oder von Zerto Virtual Manager eingeleitet werden, um mit der externen Managementdatenbank in IBM Bluemix® über das Internet zu kommunizieren. Die abgehende HTTPS-Kommunikation stammt aus der öffentlichen IP-Adresse der Management-Services für VMware NSX Edge Services Gateway (ESG) in Ihrer Instanz.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Fortinet on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Fortinet on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfsa)

## Service "Veeam on IBM Cloud"
{: #relnotes_v18-veeam}

Mit diesem Release wird der Service "Veeam on {{site.data.keyword.cloud_notm}}" eingeführt, der sowohl Managementkomponenten als auch Workloads sichern kann. Der neue Service ersetzt die vorherige virtuelle Serverinstanz von Veeam, die in Releases vor V1.8 zur ausschließlichen Sicherung von Managementkomponenten integriert war.

Aufgrund dieser Änderung sind die Sicherungspunkte für die Instanzen nicht mehr in der {{site.data.keyword.vmwaresolutions_short}}-Konsole verfügbar und Sie müssen ein Support-Ticket erstellen, um bei einer Wiederherstellung Unterstützung zu erhalten, obwohl die virtuelle Serverinstanz für Veeam in den Instanzen aus Releases vor V1.8 weiterhin funktioniert.

Darüber hinaus läuft die Lizenz der virtuellen Serverinstanz für Veeam in Instanzen aus Releases vor V1.8 am 14. Oktober 2017 ab. Daher müssen Sie die vorherige virtuelle Serverinstanz für Veeam so bald wie möglich durch den neuen Veeam-Service ersetzen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Veeam on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Veeam on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)

## Updates für VMware Cloud Foundation-Instanzen
{: #relnotes_v18-vcf}

### Eigene VMware-Lizenzen (BYOL) bei der Bestellung von Cloud Foundation-Instanzen verwenden
{: #relnotes_v18-byol}

Ab Release V1.8 haben Sie bei der Bestellung einer Cloud Foundation-Instanz zwei Möglichkeiten für die Lizenzierung der VMware-Komponenten der Instanz (inklusive vSphere, vCenter Server, NSX und vSAN). Sie können auswählen, dass in Ihrem Namen neue Lizenzen erworben werden sollen.

Sie können aber auch die Verwendung Ihrer eigenen VMware-Lizenz für eine Komponente auswählen. In diesem Fall müssen Sie die Lizenzschlüssel bereitstellen. Die Unterstützung für die VMware-Komponenten, für die Sie Lizenzen selbst bereitstellen, erhalten Sie dann durch VMware und nicht durch den IBM Support.

## Updates für VMware vCenter Server-Instanzen
{: #relnotes_v18-vcs}

### CPU und Speicher von Instanzen anpassen
{: #relnotes_v18-custom-cpu}

Neben den vordefinierten und getesteten Optionen "S (Klein)", "M (Mittel)" und "L (Groß)" gibt es eine anpassbare Serveroption. Sie können eine Auswahl in einer Liste mit VMware-HCL-kompatiblen Servern treffen, die auf Dual-CPUs und der Gesamtzahl der Kerne sowie der RAM-Menge basiert. Lokaler Speicher kann nicht angepasst werden.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Cluster für vCenter Server-Instanzen hinzufügen und anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

### Unterstützung für das Hinzufügen von mehr als sieben gemeinsam genutzten NFS-Dateiressourcen
{: #relnotes_v18-nfs}

 Für alle ESXi-Server in einem Cluster können Sie bis zu maximal 32 gemeinsam genutzte Dateiressourcen zuordnen.

 Weitere Informationen finden Sie in den folgenden Abschnitten:
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Cluster für vCenter Server-Instanzen hinzufügen und anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

### Updates für Rechenzentren
{: #relnotes_v18-dc}

Die folgenden neuen Rechenzentren sind für die Bereitstellung verfügbar: **DAL-09, DAL-12, DAL-13 - Dallas**; **LON-04, LON-06 - London**; **SJC-04 - San Jose**; **WDC-06, WDC-07 - Washington, DC**.

Weitere Informationen finden Sie unter [Voraussetzungen und Planung für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).

## Erweiterungen beim Bedienungskomfort
{: #relnotes_v18-ui}

In der gesamten Benutzerschnittstelle wurden Verbesserungen vorgenommen:
* Auf der Seite **Einführung** im linken Navigationsfenster können Sie sich über Services informieren und eine Instanz bestellen.
* Mit dem Überlaufmenü auf der Seite mit den Instanzdetails können Sie eine Instanz löschen, die den Status **Bereit** aufweist.
* Die Option zum Durchführen eines Upgrades für Ihre NSX-Lizenzedition befindet sich jetzt auf der Registerkarte **Update und Patch**. Bei der Aktualisierung der Lizenz werden alle vorhandenen NSX-Lizenzen in Ihrem IBM SoftLayer-Konto durch die neue Lizenz ersetzt.
* Die Registerkarte **Sicherung und Wiederherstellung** auf der Seite mit den Instanzdetails ist nicht mehr verfügbar.
* Am Beginn einer Bestellung können Sie mehrere Services für die Bereitstellung auswählen. Neben dem Service "Zerto on {{site.data.keyword.cloud_notm}}" sind Optionen für die Auswahl der Services "Veeam on {{site.data.keyword.cloud_notm}}" und "Fortinet on {{site.data.keyword.cloud_notm}}" verfügbar.
* Die Registerkarte **Verfügbare Services** auf der Registerkarte **Services** der Seite mit den Instanzdetails heißt jetzt **Services hinzufügen**.
