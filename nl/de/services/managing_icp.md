---

copyright:

  years:  2016, 2019

lastupdated: "2018-09-27"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# IBM Cloud Private Hosted anfordern - nicht mehr verwendet

Die Informationen in diesem Thema werden nicht weiter unterstützt. Die neuesten Informationen zu IBM Cloud Private Hosted finden Sie in [Übersicht über IBM Cloud Private Hosted](icp_overview.html).
{:deprecated}

{{site.data.keyword.cloud}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} führt eine automatische Bereitstellung von {{site.data.keyword.cloud_notm}} Private Hosted auf Ihren VMware vCenter Server-Instanzen durch.

{{site.data.keyword.cloud_notm}} Private Hosted stellt die Leistungsfähigkeit von Mikroservices und Containern in Ihrer VMware-Umgebung unter {{site.data.keyword.cloud_notm}} zur Verfügung. Mit diesem Service können Sie den Einsatz des bereits vertrauten VMware- und {{site.data.keyword.cloud_notm}} Private-Betriebsmodells und der zugehörigen Tools von Ihrem lokalen Standort (On-Premises) auf {{site.data.keyword.cloud_notm}}-Umgebungen erweitern.

## Technische Spezifikationen für IBM Cloud Private Hosted

Im Folgenden sind die Mindestvoraussetzungen zur Anforderung des Service "{{site.data.keyword.cloud_notm}} Private Hosted" aufgeführt:

* VMware vCenter Server on {{site.data.keyword.cloud_notm}}
  **Hinweis:** VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle wird nicht unterstützt.
* VMware NSX Advanced oder Enterprise Edition
* Drei {{site.data.keyword.baremetal_long}}-Instanzen
* Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz
* 384 GB Arbeitsspeicher (RAM) pro Server
* Eine gemeinsam genutzte Dateiressource des gemeinsam genutzten NFS-Speichers mit 8.000 GB bei 4 IOPS/GB
* 33 IBM Cloud Private Virtual Processor Core-Lizenzen
* Zur Datensicherung wird die Verwendung des Service "Veeam on IBM Cloud" empfohlen

## Vorgehensweise zur Anforderung von IBM Cloud Private Hosted

1. Bestellen Sie eine neue vCenter Server-Instanz und führen Sie dazu die Schritte aus, die im Abschnitt zum [Bestellen von vCenter Server-Instanzen](../vcenter/vc_orderinginstance.html) beschrieben werden. Sie können IBM Cloud Private Hosted auch für eine bereits vorhandene Instanz anfordern.
  **Wichtig:** Vergewissern Sie sich, dass Ihre Umgebung die Mindestvoraussetzungen erfüllt, die hier aufgeführt wurden.
2. Vergewissern Sie sich, dass Sie über alle erforderlichen IBM Cloud Private-Berechtigungen verfügen.
3. Nach Erhalt der Bestätigung, in der Sie darüber informiert werden, dass Ihre vCenter Server-Instanz einsatzbereit ist, führen Sie die folgenden Schritte aus, um IBM Cloud Private Hosted anzufordern.
4. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Einführung**.
5. Blättern Sie auf der Seite nach unten und klicken Sie unter **Zusätzliche Services bestellen** auf die Karte für **IBM Cloud Private Hosted**.
6. Geben Sie auf der Seite **IBM Cloud Private Hosted on vCenter Server on IBM Cloud** im Feld zur **Kontaktaufnahme mit dem IBM Cloud Private Hosted-DevOps-Team** eine Beschreibung Ihrer Voraussetzungen ein und klicken Sie dann auf **Beratungsgespräch anfordern**.

Der zuständige {{site.data.keyword.cloud_notm}} Private Hosted-DevOps-Mitarbeiter setzt sich dann über Ihre {{site.data.keyword.cloud_notm}}-Kontaktinformationen mit Ihnen in Verbindung, um Sie bei den ersten Schritten zu unterstützen.
