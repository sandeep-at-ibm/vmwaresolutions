---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-18"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Kapazität für vCenter Server with Hybridity Bundle-Instanzen erweitern und verringern
{: #vc_hybrid_addingremovingservers}

Sie können die Kapazität Ihrer VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle-Instanz entsprechend Ihren Geschäftsanforderungen erweitern oder verringern, indem Sie ESXi-Server hinzufügen oder entfernen.

Ab dem Release V2.9 können Sie einem Cluster neue ESXi-Server hinzufügen, während sich der Cluster im Wartungsmodus befindet. Darüber hinaus können Sie ESXi-Server über mehrere Cluster hinweg gleichzeitig hinzufügen oder entfernen. Die folgenden gleichzeitigen Operationen sind verfügbar:

* Hosts zu einem Cluster hinzufügen und Hosts zu weiteren Clustern hinzufügen.
* Hosts aus einem Cluster entfernen und Hosts aus weiteren Clustern entfernen.
* Hosts zu einem Cluster hinzufügen und Hosts aus weiteren Clustern entfernen.
* Hosts aus einem Cluster entfernen und Hosts zu weiteren Clustern hinzufügen.

Da Ihr erster Cluster vSAN als Speicher verwendet, kann das Hinzufügen einzelner oder mehrerer ESXi-Server nach der Bereitstellung die Speicherkapazität des Clusters erhöhen.

## ESXi-Server zu vCenter Server with Hybridity Bundle-Instanzen hinzufügen

### Vor dem Hinzufügen von ESXi-Servern
{: #vc_hybrid_addingremovingservers-adding-prereq}

* Fügen Sie keine ESXi-Server über VMware vSphere Web Client hinzu. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert.
* Für den vSAN-Speicher sind mindestens 4 ESXi-Server erforderlich.

## Vorgehensweise beim Hinzufügen von ESXi-Servern
{: #vc_hybrid_addingremovingservers-adding-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität erweitert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, zu dem ESXi-Server hinzugefügt werden sollen.
5. Klicken Sie in der Tabelle **ESXi-Server** auf **Hinzufügen**.
6. Geben Sie im Fenster **Server hinzufügen** die Anzahl der Server an, die hinzugefügt werden sollen.
7. Wählen Sie optional das Kontrollkästchen zum Hinzufügen von Servern während des Wartungsmodus aus.
8. Überprüfen Sie die geschätzten Kosten und klicken Sie auf **Hinzufügen**.

### Ergebnisse nach dem Hinzufügen von ESXi-Servern
{: #vc_hybrid_addingremovingservers-adding-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Hinzufügen von ESXi-Servern verarbeitet wird. In der Konsole wird der Status des Clusters, der den ESXi-Servern zugeordnet ist, in **Wird geändert** geändert.
3. Wenn die neuen ESXi-Server nicht zur Liste im Cluster hinzugefügt werden, überprüfen Sie die E-Mail- oder Konsolenbenachrichtigungen, um weitere Details über den Fehler zu ermitteln.

Wenn Sie ESXi-Server während des Wartungsmodus hinzufügen, werden virtuelle Maschinen (VMs) erst dann auf die neuen Server migriert, wenn Sie den Wartungsmodus für den Cluster beenden.   
{:important}

## ESXi-Server in vCenter Server with Hybridity Bundle-Instanzen entfernen
{: #vc_hybrid_addingremovingservers-removing}

### Vor dem Entfernen von ESXi-Servern
{: #vc_hybrid_addingremovingservers-removing-prereq}

* Entfernen Sie keine ESXi-Server über VMware vSphere Web Client. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert.
* Für den vSAN-Speicher sind mindestens 4 ESXi-Server erforderlich.
* Bevor Sie ESXi-Server mit installiertem Service "F5 on {{site.data.keyword.cloud_notm}}" oder "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" entfernen, müssen Sie die VMs für F5 BIG-IP und FortiGate auf einen ESXi-Server verlagern, auf dem die VMs nicht gehostet werden.
* Stellen Sie vor dem Entfernen von ESXi-Servern mit installiertem Service "IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}" sicher, dass keine (fehlgeschlagenen oder laufenden) Sicherungs- oder Wiederherstellungsoperationen aktiv sind, da diese aktiven Operationen das Entfernen der ESXi-Server verhindern könnten.
* Wenn Sie ESXi-Server entfernen, werden die Server in den Wartungsmodus versetzt. Anschließend werden alle virtuellen Maschinen (VMs), die auf den Servern ausgeführt werden, migriert, bevor sie aus vCenter Server entfernt werden. Damit die Verlagerung von VMs maximal gesteuert werden kann, empfiehlt es sich, die zu entfernenden ESXi-Server in den Wartungsmodus zu versetzen und die auf ihnen ausgeführten VMs manuell mithilfe von VMware vSphere Web Client zu migrieren. Anschließend entfernen Sie die ESXi-Server in der {{site.data.keyword.vmwaresolutions_short}}-Konsole.

## Vorgehensweise beim Entfernen von ESXi-Servern
{: #vc_hybrid_addingremovingservers-removing-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität verringert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, in dem ESXi-Server entfernt werden sollen.
5. Wählen Sie die zu entfernenden Server in der Tabelle **ESXi-Server** aus und klicken Sie auf **Entfernen**.

### Ergebnisse nach dem Entfernen von ESXi-Servern
{: #vc_hybrid_addingremovingservers-removing-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Entfernen von ESXi-Servern verarbeitet wird. In der Konsole wird der Status des Clusters, der den ESXi-Servern zugeordnet ist, in **Wird geändert** geändert.
3. Die ESXi-Server werden am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur (der in der Regel 30 Tage umfasst) vollständig von der {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgefordert.

   Die entfernten ESXi-Server werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.
   {:note}

## Zugehörige Links
{: #vc_hybrid_addingremovingservers-related}

* [vCenter Server-Teileliste](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Voraussetzungen und Planung für vCenter Server with Hybridity Bundle-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Cluster für vCenter Server with Hybridity Bundle-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [Versetzen eines Hosts in den Wartungsmodus](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Prozessorunterstützung für EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
