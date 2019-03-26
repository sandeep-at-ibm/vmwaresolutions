---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Kapazität für Cloud Foundation-Instanzen erweitern und verringern
{: #sd_addingremovingservers}

Sie können die Kapazität Ihrer VMware Cloud Foundation-Instanz entsprechend Ihren Geschäftsanforderungen erweitern oder verringern, indem Sie ESXi-Server hinzufügen oder entfernen.

Eine Cloud Foundation-Instanz kann bis zu fünf Cluster umfassen, von denen einer der Standardcluster ist. Jeder erste Cluster kann bis zu 51 ESXi-Server umfassen; weitere Cluster können bis zu 59 Server beinhalten.

## ESXi-Server zu Cloud Foundation-Instanzen hinzufügen
{: #sd_addingremovingservers-adding}

### Vor dem Hinzufügen von ESXi-Servern
{: #sd_addingremovingservers-adding-prereq}

* Fügen Sie keine ESXi-Server über VMware vSphere Web Client hinzu. Die Änderungen, die Sie in VMware vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_full}}-Konsole synchronisiert.
* Die von Ihnen bestellte Basisplattform umfasst standardmäßig 4 ESXi-Server. Sie können die Plattform auf maximal 32 ESXi-Server erweitern. Für die Anzahl der {{site.data.keyword.baremetal_short}}-Instanzen, die Sie jeweils hinzufügen können, gilt jedoch Folgendes:
   * Bei Konfigurationen des Typs **S (Klein)** und **L (Groß)** können Sie gleichzeitig 1 bis 10 ESXi-Server hinzufügen.
   * Bei Konfigurationen des Typs **Skylake** und **Broadwell** können Sie gleichzeitig 1 bis 20 ESXi-Server hinzufügen.

## Vorgehensweise beim Hinzufügen von ESXi-Servern
{: #sd_addingremovingservers-adding-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**. 
2. Klicken Sie in der Tabelle **Cloud Foundation-Instanzen** auf die Instanz, für die die Kapazität erweitert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, zu dem ESXi-Server hinzugefügt werden sollen.
5. Klicken Sie im Abschnitt **ESXi-Server** auf **Hinzufügen**.
6. Geben Sie im Fenster **Server hinzufügen** die Anzahl der Server ein, die Sie hinzufügen wollen. Prüfen Sie geschätzten Kosten und klicken Sie dann auf **Hinzufügen**.

### Ergebnisse nach dem Hinzufügen von ESXi-Servern
{: #sd_addingremovingservers-adding-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, wenn Ihre ESXi-Server hinzugefügt wurden.
3. Wenn die neuen ESXi-Server nicht zur Liste im Cluster hinzugefügt werden, überprüfen Sie die E-Mail- oder Konsolenbenachrichtigungen, um weitere Details über den Fehler zu ermitteln.

## ESXi-Server in Cloud Foundation-Instanzen entfernen
{: #sd_addingremovingservers-removing}

### Vor dem Entfernen von ESXi-Servern
{: #sd_addingremovingservers-removing-prereq}

* Entfernen Sie keine ESXi-Server über VMware vSphere Web Client. Die Änderungen, die Sie in VMware vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert.
* Die von Ihnen bestellte Basisplattform umfasst standardmäßig 4 ESXi-Server. Sie können die von Ihnen hinzugefügten ESXi-Server entfernen. Die ESXi-Standardserver können nicht entfernt werden.
* Bevor Sie ESXi-Server mit installiertem Service "F5 on {{site.data.keyword.cloud_notm}}" oder "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" entfernen, müssen Sie die VMs für F5 BIG-IP und FortiGate auf einen ESXi-Server verlagern, auf dem die VMs nicht gehostet werden.
* Stellen Sie vor dem Entfernen von ESXi-Servern mit installiertem Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" sicher, dass keine Sicherungs- oder Wiederherstellungsoperationen aktiv sind. Aktive Operationen (fehlgeschlagene oder laufende) könnten das Entfernen der ESXi-Server verhindern.

## Vorgehensweise beim Entfernen von ESXi-Servern
{: #sd_addingremovingservers-removing-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**. 
2. Klicken Sie in der Tabelle **Cloud Foundation-Instanzen** auf die Instanz, für die die Kapazität verringert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, in dem ESXi-Server entfernt werden sollen.
6. Wählen Sie die zu entfernenden Server im Bereich **ESXi-Server** aus und klicken Sie auf **Entfernen**.

### Ergebnisse nach dem Entfernen von ESXi-Servern
{: #sd_addingremovingservers-removing-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, wenn Ihre ESXi-Server entfernt wurden.
3. Die ESXi-Server werden am Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus (der in der Regel 30 Tage umfasst) vollständig von der {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgefordert.

   Die entfernten ESXi-Server werden Ihnen bis zum Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus berechnet.
   {:note}

## Zugehörige Links
{: #sd_addingremovingservers-related}

* [Cloud Foundation-Teileliste](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_bom)
* [Cluster für Cloud Foundation-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-sd_addingviewingclusters#sd_addingviewingclusters)
* [Versetzen eines Hosts in den Wartungsmodus](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Prozessorunterstützung für EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
