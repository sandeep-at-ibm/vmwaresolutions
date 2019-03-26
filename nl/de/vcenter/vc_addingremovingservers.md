---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Kapazität für vCenter Server-Instanzen erweitern und verringern
{: #vc_addingremovingservers}

Sie können die Kapazität Ihrer VMware vCenter Server-Instanz entsprechend Ihren Geschäftsanforderungen erweitern oder verringern, indem Sie ESXi-Server oder NFS-Speicher (Network File System) hinzufügen oder entfernen.

Ab dem Release V2.9 können Sie einem Cluster neue ESXi-Server hinzufügen, während sich die Server im Wartungsmodus befinden. Darüber hinaus können Sie ESXi-Server über mehrere Cluster hinweg gleichzeitig hinzufügen oder entfernen. Die folgenden gleichzeitigen Operationen sind verfügbar: 

* Hosts zu einem Cluster hinzufügen und Hosts zu weiteren Clustern hinzufügen. 
* Hosts aus einem Cluster entfernen und Hosts aus weiteren Clustern entfernen. 
* Hosts zu einem Cluster hinzufügen und Hosts aus weiteren Clustern entfernen. 
* Hosts aus einem Cluster entfernen und Hosts zu weiteren Clustern hinzufügen. 

Sie können NFS-Speicherfreigaben zu einem vorhandenen NFS- oder vSAN vCenter Server-Cluster hinzufügen oder aus einem vorhandenen NFS-oder vSAN vCenter Server-Cluster entfernen.
{:note}

Wenn Ihr erster Cluster vSAN als Speicher verwendet, kann das Hinzufügen von einem oder mehreren ESXi-Servern nach der Bereitstellung die Speicherkapazität des Clusters erhöhen.

## ESXi-Server zu vCenter Server-Instanzen hinzufügen
{: #vc_addingremovingservers-adding}

### Vor dem Hinzufügen von ESXi-Servern
{: #vc_addingremovingservers-adding-prereq}

* Fügen Sie keine ESXi-Server über VMware vSphere Web Client hinzu. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_full}}-Konsole synchronisiert.
* Eine vCenter Server-Instanz mit NFS-Speicher benötigt mindestens 2 ESXi-Server. Bei in V2.1 oder höheren Versionen bereitgestellten Instanzen können Sie den Standardcluster auf bis zu 51 ESXi-Server erweitern. Jeder Cluster, bei dem es sich nicht um den Standardcluster handelt, kann auf bis zu 59 ESXi-Server erweitert werden.
* Eine vCenter Server-Instanz mit vSAN-Speicher benötigt mindestens 4 ESXi-Server.
* Bei vCenter Server-Instanzen, die in V2.0 oder einer früheren Version bereitgestellt wurden, können Sie jeden Cluster auf bis zu 32 ESXi-Server erweitern.
* Sie können gleichzeitig 1 bis 20 ESXi-Server hinzufügen. Weitere Informationen zum Minimum von ESXi-Servern finden Sie unter [Ist eine vCenter Server-Instanz mit zwei Knoten hoch verfügbar?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)

### Vorgehensweise beim Hinzufügen von ESXi-Servern
{: #vc_addingremovingservers-adding-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**. 
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität erweitert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, zu dem ESXi-Server hinzugefügt werden sollen.
5. Klicken Sie im Abschnitt **ESXi-Server** auf **Hinzufügen**.
6. Geben Sie im Fenster **Server hinzufügen** die Anzahl der Server an, die hinzugefügt werden sollen. 
7. Wählen Sie optional das Kontrollkästchen zum Hinzufügen von Servern während des Wartungsmodus aus. 
8. Überprüfen Sie die geschätzten Kosten und klicken Sie auf **Hinzufügen**. 

### Ergebnisse nach dem Hinzufügen von ESXi-Servern
{: #vc_addingremovingservers-adding-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Hinzufügen von ESXi-Servern verarbeitet wird. In der Konsole wird der Status des Clusters, der den ESXi-Servern zugeordnet ist, in **Wird geändert** geändert.
3. Wenn die neuen ESXi-Server nicht zur Liste im Cluster hinzugefügt werden, überprüfen Sie die E-Mail- oder Konsolenbenachrichtigungen, um weitere Details über den Fehler zu ermitteln.
4. In den folgenden Situationen müssen Sie die Konsole von Zerto Virtual Manager (ZVM) und die bereits ausgefüllte IP-Adresse von Zerto Virtual Replication Appliance (VRA) verwenden, um die virtuelle VRA-Maschine (VM) manuell bereitzustellen: 
   * Wenn Sie ESXi-Server zu einem Standardcluster hinzufügen, während sich die Server im Wartungsmodus befinden und Zerto for {{site.data.keyword.cloud_notm}} installiert ist. 
   * Wenn Sie Zerto for {{site.data.keyword.cloud_notm}} zu einer vCenter Server-Instanz hinzufügen, die über einen ESXi-Server im Wartungsmodus verfügt. 

Wenn Sie ESXi-Server während des Wartungsmodus hinzufügen, werden virtuelle Maschinen erst dann auf die neuen Server migriert, wenn Sie den Wartungsmodus beenden.    
{:important}

## ESXi-Server in vCenter Server-Instanzen entfernen
{: #vc_addingremovingservers-removing}

### Vor dem Entfernen von ESXi-Servern
{: #vc_addingremovingservers-removing-prereq}

* Entfernen Sie keine ESXi-Server über VMware vSphere Web Client. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert.
* Eine vCenter Server-Instanz mit NFS-Speicher benötigt mindestens 2 ESXi-Server und eine vCenter Server-Instanz mit vSAN-Speicher muss über mindestens 4 ESXi-Server verfügen.
* Bevor Sie ESXi-Server mit installiertem Service "F5 on {{site.data.keyword.cloud_notm}}" oder "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" entfernen, müssen Sie die VMs für F5 BIG-IP und FortiGate auf einen ESXi-Server verlagern, auf dem die VMs nicht gehostet werden.
* Stellen Sie vor dem Entfernen von ESXi-Servern mit installiertem Service "IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}" sicher, dass keine (fehlgeschlagenen oder laufenden) Sicherungs- oder Wiederherstellungsoperationen aktiv sind, da diese aktiven Operationen das Entfernen der ESXi-Server verhindern könnten.
* Wenn Sie ESXi-Server entfernen, werden die Server in den Wartungsmodus versetzt. Anschließend werden alle virtuellen Maschinen (VMs), die auf den Servern ausgeführt werden, migriert, bevor sie aus vCenter Server entfernt werden. Damit die Verlagerung von VMs maximal gesteuert werden kann, empfiehlt es sich, die zu entfernenden ESXi-Server in den Wartungsmodus zu versetzen und die auf ihnen ausgeführten VMs manuell mithilfe von VMware vSphere Web Client zu migrieren. Anschließend entfernen Sie die ESXi-Server mithilfe der {{site.data.keyword.vmwaresolutions_short}}-Konsole.

### Vorgehensweise beim Entfernen von ESXi-Servern
{: #vc_addingremovingservers-removing-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**. 
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität verringert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, in dem ESXi-Server entfernt werden sollen.
5. Wählen Sie die zu entfernenden Server im Bereich **ESXi-Server** aus und klicken Sie auf **Entfernen**.

### Ergebnisse nach dem Entfernen von ESXi-Servern
{: #vc_addingremovingservers-removing-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Entfernen von ESXi-Servern verarbeitet wird. In der Konsole wird der Status des Clusters, der den ESXi-Servern zugeordnet ist, in **Wird geändert** geändert.
3. Die ESXi-Server werden am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur (der in der Regel 30 Tage umfasst) vollständig von der {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgefordert.

   Die entfernten ESXi-Server werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.
   {:note}

## NFS-Speicher zu vCenter-Server-Instanzen hinzufügen
{: #section-adding-nfs-storage-to-vcenter-server-instances}

### Vor dem Hinzufügen von NFS-Speicher
{: #vc_addingremovingservers-adding-nfs-storage-prereq}

Fügen Sie NFS-Speicher nicht über VMware vSphere Web Client hinzu. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert. IBM verwaltet keine NFS-Dateifreigaben, die Sie manuell zu einer Instanz hinzugefügt haben.

### Vorgehensweise zum Hinzufügen von NFS-Speicher
{: #vc_addingremovingservers-adding-nfs-storage-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**. 
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität erweitert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, zu dem NFS-Speicher hinzugefügt werden soll.
5. Klicken Sie im Abschnitt **Speicher** auf **Hinzufügen**.
6. Führen Sie im Fenster **Speicher** die Speicherkonfiguration durch.
   * Wenn Sie für alle Dateifreigaben dieselben Einstellungen hinzufügen und konfigurieren wollen, geben Sie **Anzahl der gemeinsam genutzten Ressourcen**, **Leistung** und **Größe (GB)** an.
   * Wenn Sie Dateifreigaben einzeln hinzufügen und konfigurieren wollen, wählen Sie **Gemeinsam genutzte Ressourcen einzeln konfigurieren** an, klicken auf das Plussymbol (**+**) neben der Bezeichnung **Gemeinsam genutzten Speicher hinzufügen** und wählen für jede einzelne Dateifreigabe die **Leistung** und **Größe (GB)** aus. Sie müssen mindestens eine gemeinsam genutzte Dateiressource auswählen.
7. Klicken Sie auf **NFS-Speicher hinzufügen**.

### Ergebnisse nach dem Hinzufügen von NFS-Speicher
{: #vc_addingremovingservers-adding-nfs-storage-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Hinzufügen von NFS-Speicher verarbeitet wird. In der Konsole wird der Status des Clusters, der dem NFS-Speicher zugeordnet ist, in **Wird geändert** geändert.
3. Wenn der neue NFS-Speicher nicht zur Liste im Cluster hinzugefügt wird, überprüfen Sie die E-Mail- oder Konsolenbenachrichtigungen, um weitere Details über den Fehler zu ermitteln.

## NFS-Speicher aus vCenter Server-Instanzen entfernen
{: #vc_addingremovingservers-removing-nfs-storage}

### Vor dem Entfernen von NFS-Speicher
{: #vc_addingremovingservers-removing-nfs-storage-prereq}

* Entfernen Sie den NFS-Speicher nicht über VMware vSphere Web Client. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert.
* Stellen Sie vor dem Entfernen des NFS-Speichers sicher, dass alle im Speicher befindlichen VMs entfernt wurden.
* Stellen Sie sicher, dass die gemeinsam genutzten Ressourcen, die entfernt werden sollen, der korrekten vCenter Server-Instanz zugeordnet sind.
* Der Cluster muss den Status **Bereit** haben.

### Vorgehensweise zum Entfernen von NFS-Speicher
{: #vc_addingremovingservers-removing-nfs-storage-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**. 
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität verringert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, von dem der NFS-Speicher entfernt werden soll.
5. Wählen Sie im Abschnitt **Speicher** die zu entfernende Speicherfreigabe aus und klicken Sie auf **Löschen**.
6. Klicken Sie im Fenster **Speicher entfernen** auf **Entfernen**.

### Ergebnisse nach dem Entfernen von NFS-Speicher
{: #vc_addingremovingservers-removing-nfs-storage-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Entfernen von NFS-Speicher verarbeitet wird. In der Konsole wird der Status des Clusters, der dem NFS-Speicher zugeordnet ist, in **Wird geändert** geändert.
3. Der NFS-Speicher wird von der {{site.data.keyword.cloud_notm}}-Infrastruktur am Ende des {{site.data.keyword.cloud_notm}}-Infrastruktur-Abrechnungszyklus, der in der Regel 30 Tage umfasst, vollständig zurückgefordert.

   Der NFS-Speicher wird Ihnen bis zum Ende des {{site.data.keyword.cloud_notm}}-Infrastrukturabrechnungszyklus in Rechnung gestellt.
   {:note}

## Zugehörige Links
{: #vc_addingremovingservers-related}

* [vCenter Server-Teileliste](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Voraussetzungen und Planung für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)
* [Versetzen eines Hosts in den Wartungsmodus](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Prozessorunterstützung für EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
