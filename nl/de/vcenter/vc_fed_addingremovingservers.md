---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-28"

---

# Kapazität für VMware Federal-Instanzen erweitern und verringern

Sie können die Kapazität Ihrer VMware Federal-Instanz entsprechend Ihren Geschäftsanforderungen erweitern oder verringern, indem Sie ESXi-Server hinzufügen oder entfernen.

Wenn Ihr primärer Cluster vSAN als Speicher verwendet, kann das Hinzufügen von einem oder mehreren ESXi-Servern nach der Bereitstellung die Speicherkapazität des Clusters erhöhen.

**Hinweis:** Diese Funktion ist nur für VMware Federal-Instanzen verfügbar, die nicht geschützt sind.

## ESXi-Server zu VMware Federal-Instanzen hinzufügen

### Vor dem Hinzufügen von ESXi-Servern

* Fügen Sie keine ESXi-Server über VMware vSphere Web Client hinzu. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_full}}-Konsole synchronisiert.
* Eine VMware Federal-Instanz mit NFS-Speicher benötigt mindestens 2 ESXi-Server. Sie können den Standardcluster auf bis zu 51 ESXi-Server erweitern. Jeder Cluster, bei dem es sich nicht um den Standardcluster handelt, kann auf bis zu 59 ESXi-Server erweitert werden.
* Eine VMware Federal-Instanz mit vSAN-Speicher benötigt mindestens 4 ESXi-Server.

## Vorgehensweise beim Hinzufügen von ESXi-Servern

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität erweitert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, zu dem ESXi-Server hinzugefügt werden sollen.
5. Klicken Sie in der Tabelle **ESXi-Server** auf **Hinzufügen**.
6. Wählen Sie im Fenster **Server hinzufügen** die Anzahl der Server aus, die Sie hinzufügen wollen, klicken Sie auf den Link "Preis", um die geschätzten Kosten zu prüfen, und klicken Sie dann auf **Hinzufügen**.

### Ergebnisse nach dem Hinzufügen von ESXi-Servern

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Hinzufügen von ESXi-Servern verarbeitet wird. In der Konsole wird der Status des Clusters, der den ESXi-Servern zugeordnet ist, in **Wird geändert** geändert.
3. Wenn die neuen ESXi-Server nicht zur Liste im Cluster hinzugefügt werden, überprüfen Sie die E-Mail- oder Konsolenbenachrichtigungen, um weitere Details über den Fehler zu ermitteln.

## ESXi-Server in VMware Federal-Instanzen entfernen

### Vor dem Entfernen von ESXi-Servern

* Entfernen Sie keine ESXi-Server über VMware vSphere Web Client. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert.
* Eine VMware Server-Instanz mit NFS-Speicher benötigt mindestens 2 ESXi-Server und eine VMware Federal-Instanz mit vSAN-Speicher muss über mindestens 4 ESXi-Server verfügen.
* Wenn Sie ESXi-Server entfernen, werden die Server in den Wartungsmodus versetzt. Anschließend werden alle virtuellen Maschinen (VMs), die auf den Servern ausgeführt werden, migriert, bevor sie aus vCenter Server entfernt werden. Damit die Verlagerung von VMs maximal gesteuert werden kann, empfiehlt es sich, die zu entfernenden ESXi-Server in den Wartungsmodus zu versetzen und die auf ihnen ausgeführten VMs manuell mithilfe von VMware vSphere Web Client zu migrieren. Anschließend entfernen Sie die ESXi-Server in der {{site.data.keyword.vmwaresolutions_short}}-Konsole.

## Vorgehensweise beim Entfernen von ESXi-Servern

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität verringert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, in dem ESXi-Server entfernt werden sollen.
5. Wählen Sie die zu entfernenden Server in der Tabelle **ESXi-Server** aus und klicken Sie auf **Entfernen**.

### Ergebnisse nach dem Entfernen von ESXi-Servern

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Entfernen von ESXi-Servern verarbeitet wird. In der Konsole wird der Status des Clusters, der den ESXi-Servern zugeordnet ist, in **Wird geändert** geändert.
3. Die ESXi-Server werden am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur (der in der Regel 30 Tage umfasst) vollständig von der {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgefordert.

   **Achtung:** Die entfernten ESXi-Server werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.

### Zugehörige Links

* [Voraussetzungen und Planung für VMware Federal-Instanzen](vc_fed_planning.html)
* [Cluster für VMware Federal-Instanzen hinzufügen, anzeigen und löschen](fed_addviewdeleteclusters.html)
* [Versetzen eines Hosts in den Wartungsmodus](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Prozessorunterstützung für EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
