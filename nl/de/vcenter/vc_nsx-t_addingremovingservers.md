---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: vCenter Server NSX-T add hosts, add servers to vCenter Server NSX-T, remove hosts from vCenter Server NSX-T

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Kapazität für vCenter Server with NSX-T-Instanzen erweitern und verringern
{: #vc_nsx-t_addingremovingservers}

Sie können die Kapazität Ihrer VMware vCenter Server with NSX-T-Instanz entsprechend Ihren Geschäftsanforderungen erweitern oder verringern, indem Sie ESXi-Server oder NFS-Speicher (Network File System) hinzufügen oder entfernen.

* Ab dem Release V3.1 können Sie einem vorhandenen Cluster neue ESXi-Server hinzufügen, indem Sie entweder eine vorhandene Konfiguration oder eine alternative Konfiguration als die vorhandenen Hosts im Cluster auswählen. Vorhandene Konfigurationen stehen zur sofortigen Auswahl bereit, wenn Sie einen neuen Server bestellen. Zur Vermeidung von Leistungs- und Stabilitätsproblemen wird empfohlen, für die Cluster dieselben oder ähnliche Konfiguration für CPU, RAM und Speicher zu verwenden. Diese Funktion ist für Hardwareaktualisierungen innerhalb desselben Clusters nützlich. Ein Cluster kann nur einen Speichertyp aufweisen.
* Ab dem Release V3.0 können Sie gleichzeitig NFS-Speicher und ESXi-Server zu Clustern hinzufügen, die sich im Status **Bereit** befinden, bzw. daraus entfernen. Sie können z. B. einen ESXi-Server in einem Cluster hinzufügen oder entfernen und einen NFS-Speicher in einem weiteren Cluster hinzufügen oder entfernen.
* Ab dem Release V2.9 können Sie einem Cluster neue ESXi-Server hinzufügen, während sich die Server im Wartungsmodus befinden. Darüber hinaus können Sie ESXi-Server über mehrere Cluster hinweg gleichzeitig hinzufügen oder entfernen.

**Hinweise**:
* Wenn Ihr erster Cluster vSAN als Speicher verwendet, kann das Hinzufügen von einem oder mehreren ESXi-Servern nach der Bereitstellung die Speicherkapazität des Clusters erhöhen.
* Sie können NFS-Speicherfreigaben in einem vorhandenen NFS- oder vSAN-Cluster für vCenter Server with NSX-T hinzufügen oder aus diesem entfernen.

## ESXi-Server zu vCenter Server with NSX-T-Instanzen hinzufügen
{: #vc_nsx-t_addingremovingservers-adding}

### Vor dem Hinzufügen von ESXi-Servern
{: #vc_nsx-t_addingremovingservers-adding-prereq}

* Fügen Sie ESXi-Server nach Möglichkeit über die {{site.data.keyword.vmwaresolutions_full}}-Konsole hinzu, da Änderungen, die Sie am VMware vSphere Web Client vornehmen, nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert werden. Fügen Sie daher ESXi-Server nur für On-Premise-ESXi-Server oder ESXi-Server hinzu, die Sie nicht in der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten können/möchten.
* Eine vCenter Server with NSX-T-Instanz mit NFS-Speicher benötigt mindestens 3 ESXi-Server. Sie können den Standardcluster auf bis zu 51 ESXi-Server erweitern. Jeder Cluster, bei dem es sich nicht um den Standardcluster handelt, kann auf bis zu 59 ESXi-Server erweitert werden.
* Eine vCenter Server with NSX-T-Instanz mit vSAN-Speicher benötigt mindestens 4 ESXi-Server.

### Vorgehensweise beim Hinzufügen von ESXi-Servern
{: #vc_nsx-t_addingremovingservers-adding-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität erweitert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, zu dem ESXi-Server hinzugefügt werden sollen.
5. Klicken Sie im Abschnitt **ESXi-Server** auf **Hinzufügen**.
6. Geben Sie im Fenster **Server hinzufügen** die Anzahl der Server an, die hinzugefügt werden sollen.
7. Wählen Sie optional das Kontrollkästchen zum Hinzufügen von Servern während des Wartungsmodus aus. Das Kontrollkästchen ist standardmäßig ausgewählt.

   Wenn Sie den neuen ESXi-Server bereitstellen, werden die virtuellen Maschinen (VMs) sofort auf die neuen Server migriert, falls Sie das Kontrollkästchen **Wartungsmodus** nicht auswählen. Sie empfangen die Bestätigungsnachricht erst, wenn die Migration beginnt.
   {:important}

8. Führen Sie die Bare-Metal-Konfiguration durch.
   * Wählen Sie eine Konfiguration aus den vorhandenen Hosts im Cluster aus.
   * Wählen Sie eine neue {{site.data.keyword.baremetal_short_sing}}-Konfiguration aus und geben Sie anschließend das CPU-Modell und die RAM-Größe an.
9. Führen Sie die Speicherkonfiguration durch. Geben Sie die Plattentypen für die Kapazitäts- und Cacheplatten, die Anzahl der Platten und die vSAN-Lizenzedition an. Falls Sie mehr Speicher benötigen, müssen Sie das Feld für **Hohe Leistung mit Intel Optane** auswählen.
10. Überprüfen Sie die geschätzten Kosten und klicken Sie auf **Hinzufügen**.

  Sie können die bereitgestellten Ressourcen auch durch Klicken auf **Zur Schätzung hinzufügen** zum {{site.data.keyword.cloud_notm}}-Schätztool hinzufügen. Dies ist nützlich, wenn Sie die Kosten für die ausgewählten {{site.data.keyword.vmwaresolutions_short}}-Ressourcen zusammen mit anderen {{site.data.keyword.cloud_notm}}-Ressourcen schätzen möchten, die Sie für den Kauf in Betracht ziehen könnten.

### Ergebnisse nach dem Hinzufügen von ESXi-Servern
{: #vc_nsx-t_addingremovingservers-adding-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Hinzufügen von ESXi-Servern verarbeitet wird. In der Konsole wird der Status des Clusters, der den ESXi-Servern zugeordnet ist, in **Wird geändert** geändert.
3. Wenn die neuen ESXi-Server nicht zur Liste im Cluster hinzugefügt werden, überprüfen Sie die E-Mail- oder Konsolenbenachrichtigungen, um weitere Details über den Fehler zu ermitteln.

Wenn Sie ESXi-Server während des Wartungsmodus hinzufügen, werden virtuelle Maschinen (VMs) erst dann auf die neuen Server migriert, wenn Sie den Wartungsmodus für den Cluster beenden.   
{:important}

## ESXi-Server in vCenter Server with NSX-T-Instanzen entfernen
{: #vc_nsx-t_addingremovingservers-removing}

### Vor dem Entfernen von ESXi-Servern
{: #vc_nsx-t_addingremovingservers-removing-prereq}

* Entfernen Sie ESXi-Server nach Möglichkeit über die {{site.data.keyword.vmwaresolutions_full}}-Konsole, da die Änderungen, die Sie im vSphere Web Client vornehmen, nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert werden. Entfernen Sie daher ESXi-Server nur von On-Premise-ESXi-Servern oder ESXi-Servern, die Sie nicht in der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten können/möchten.
* Eine vCenter Server with NSX-T-Instanz mit NFS-Speicher benötigt mindestens 3 ESXi-Server und eine vCenter Server with NSX-T-Instanz mit vSAN-Speicher benötigt mindestens 4 ESXi-Server.
* Wenn Sie ESXi-Server entfernen, werden die Server in den Wartungsmodus versetzt. Anschließend werden alle auf den Servern ausgeführten VMs migriert, bevor sie aus vCenter Server entfernt werden. Damit die Verlagerung von VMs maximal gesteuert werden kann, empfiehlt es sich, die zu entfernenden ESXi-Server in den Wartungsmodus zu versetzen und die auf ihnen ausgeführten VMs manuell mithilfe von VMware vSphere Web Client zu migrieren. Anschließend entfernen Sie die ESXi-Server mithilfe der {{site.data.keyword.vmwaresolutions_short}}-Konsole.

### Vorgehensweise beim Entfernen von ESXi-Servern
{: #vc_nsx-t_addingremovingservers-removing-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität verringert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, in dem ESXi-Server entfernt werden sollen.
5. Wählen Sie die zu entfernenden Server im Bereich **ESXi-Server** aus und klicken Sie auf **Entfernen**.

### Ergebnisse nach dem Entfernen von ESXi-Servern
{: #vc_nsx-t_addingremovingservers-removing-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Entfernen von ESXi-Servern verarbeitet wird. In der Konsole wird der Status des Clusters, der den ESXi-Servern zugeordnet ist, in **Wird geändert** geändert.
3. Die ESXi-Server werden am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur (der in der Regel 30 Tage umfasst) vollständig von der {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgefordert.

   Die entfernten ESXi-Server werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.
   {:note}

## NFS-Speicher zu vCenter Server with NSX-T-Instanzen hinzufügen
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-to-vcs-nsx-t}

### Vor dem Hinzufügen von NFS-Speicher
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-prereq}

Fügen Sie NFS-Speicher nicht über VMware vSphere Web Client hinzu. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert. IBM verwaltet keine NFS-Dateifreigaben, die Sie manuell zu einer Instanz hinzugefügt haben.

### Vorgehensweise zum Hinzufügen von NFS-Speicher
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität erweitert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, zu dem NFS-Speicher hinzugefügt werden soll.
5. Klicken Sie im Abschnitt **Speicher** auf **Hinzufügen**.
6. Führen Sie im Fenster **Speicher** die Speicherkonfiguration durch.
   * Wenn Sie für alle Dateifreigaben dieselben Einstellungen hinzufügen und konfigurieren wollen, geben Sie **Anzahl der gemeinsam genutzten Ressourcen**, **Leistung** und **Größe (GB)** an.
   * Wenn Sie Dateifreigaben einzeln hinzufügen und konfigurieren wollen, wählen Sie **Gemeinsam genutzte Ressourcen einzeln konfigurieren** an, klicken auf das Plussymbol (**+**) neben der Bezeichnung **Gemeinsam genutzten Speicher hinzufügen** und wählen für jede einzelne Dateifreigabe die **Leistung** und **Größe (GB)** aus. Sie müssen mindestens eine gemeinsam genutzte Dateiressource auswählen.
7. Überprüfen Sie die geschätzten Kosten und klicken Sie auf **NFS-Speicher hinzufügen**.

  Sie können die bereitgestellten Ressourcen auch durch Klicken auf **Zur Schätzung hinzufügen** zum {{site.data.keyword.cloud_notm}}-Schätztool hinzufügen. Dies ist nützlich, wenn Sie die Kosten für die ausgewählten {{site.data.keyword.vmwaresolutions_short}}-Ressourcen zusammen mit anderen {{site.data.keyword.cloud_notm}}-Ressourcen schätzen möchten, die Sie für den Kauf in Betracht ziehen könnten.

### Ergebnisse nach dem Hinzufügen von NFS-Speicher
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Hinzufügen von NFS-Speicher verarbeitet wird. In der Konsole wird der Status des Clusters, der dem NFS-Speicher zugeordnet ist, in **Wird geändert** geändert.
3. Wenn der neue NFS-Speicher nicht zur Liste im Cluster hinzugefügt wird, überprüfen Sie die E-Mail- oder Konsolenbenachrichtigungen, um weitere Details über den Fehler zu ermitteln.

## NFS-Speicher aus vCenter Server with NSX-T-Instanzen entfernen
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage}

### Vor dem Entfernen von NFS-Speicher
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-prereq}

* Entfernen Sie den NFS-Speicher nicht über VMware vSphere Web Client. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert.
* Stellen Sie vor dem Entfernen des NFS-Speichers sicher, dass alle im Speicher befindlichen VMs entfernt wurden.
* Stellen Sie sicher, dass die gemeinsam genutzten Ressourcen, die entfernt werden sollen, der korrekten vCenter Server-Instanz zugeordnet sind.
* Der Cluster muss den Status **Bereit** haben.

### Vorgehensweise zum Entfernen von NFS-Speicher
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die die Kapazität verringert werden soll.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, von dem der NFS-Speicher entfernt werden soll.
5. Wählen Sie im Abschnitt **Speicher** die zu entfernende Speicherfreigabe aus und klicken Sie auf **Löschen**.
6. Klicken Sie im Fenster **Speicher entfernen** auf **Entfernen**.

### Ergebnisse nach dem Entfernen von NFS-Speicher
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-results}

1. Es kann eine leichte Verzögerung in der Konsole auftreten, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.
2. Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Entfernen von NFS-Speicher verarbeitet wird. In der Konsole wird der Status des Clusters, der dem NFS-Speicher zugeordnet ist, in **Wird geändert** geändert.
3. Der NFS-Speicher wird von der {{site.data.keyword.cloud_notm}}-Infrastruktur am Ende des {{site.data.keyword.cloud_notm}}-Infrastruktur-Abrechnungszyklus, der in der Regel 30 Tage umfasst, vollständig zurückgefordert.

   Der NFS-Speicher wird Ihnen bis zum Ende des {{site.data.keyword.cloud_notm}}-Infrastrukturabrechnungszyklus in Rechnung gestellt.
   {:note}

## Zugehörige Links
{: #vc_nsx-t_addingremovingservers-related}

* [vCenter Server-Teileliste](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Voraussetzungen und Planung für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [vCenter Server with NSX-T-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [Cluster für vCenter Server with NSX-T-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_addingviewingcluster#vc_nsx-t_addingviewingcluster)
* [Versetzen eines Hosts in den Wartungsmodus](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:external}
* [Prozessorunterstützung für EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/s/article/1003212){:external}
