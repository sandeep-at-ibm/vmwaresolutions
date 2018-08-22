---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Kapazität für vCenter Server with Hybridity Bundle-Instanzen erweitern und verringern

Sie können die Kapazität Ihrer VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle-Instanz entsprechend Ihren Geschäftsanforderungen erweitern oder verringern, indem Sie ESXi-Server hinzufügen oder entfernen.

Da Ihr erster Cluster vSAN als Speicher verwendet, kann das Hinzufügen einzelner oder mehrerer ESXi-Server nach der Bereitstellung die Speicherkapazität des Clusters erhöhen.

## Vorbereitende Schritte

* Verwenden Sie nicht VMware vSphere Web Client, um ESXi-Server hinzuzufügen oder zu entfernen. Die Änderungen, die Sie in vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert.
* Für den vSAN-Speicher sind mindestens 4 ESXi-Server erforderlich.
* Bevor Sie ESXi-Server mit installiertem Service "F5 on {{site.data.keyword.cloud_notm}}" oder "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" entfernen, müssen Sie die VMs für F5 BIG-IP und FortiGate auf einen ESXi-Server verlagern, auf dem die VMs nicht aktuell gehostet werden.
* Stellen Sie vor dem Entfernen von ESXi-Servern mit installiertem Service "IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}" sicher, dass keine (fehlgeschlagenen oder laufenden) Sicherungs- oder Wiederherstellungsoperationen aktiv sind, da diese aktiven Operationen das Entfernen der ESXi-Server verhindern könnten.
* Wenn Sie ESXi-Server entfernen, werden die Server in den Wartungsmodus versetzt. Anschließend werden alle virtuellen Maschinen (VMs), die auf den Servern ausgeführt werden, migriert, bevor sie aus vCenter Server entfernt werden. Damit die Verlagerung von VMs maximal gesteuert werden kann, empfiehlt es sich, die zu entfernenden ESXi-Server in den Wartungsmodus zu versetzen und die auf ihnen ausgeführten VMs manuell mithilfe von VMware vSphere Web Client zu migrieren. Anschließend entfernen Sie die ESXi-Server in der {{site.data.keyword.vmwaresolutions_short}}-Konsole.

## Vorgehensweise

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die Sie die Kapazität erweitern oder verringern wollen.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, zu dem ESXi-Server hinzugefügt oder aus dem ESXi-Server entfernt werden sollen.
5. Gehen Sie zum Hinzufügen von ESXi-Servern folgendermaßen vor:
   1. Klicken Sie in der Tabelle **ESXi-Server** auf **Hinzufügen**.
   2. Wählen Sie im Fenster **Server hinzufügen** die Anzahl der Server aus, die Sie hinzufügen wollen, klicken Sie auf den Link "Preis", um die geschätzten Kosten zu prüfen, und klicken Sie dann auf **Hinzufügen**.
6. Um ESXi-Server zu entfernen, wählen Sie die entsprechenden Server in der Tabelle **ESXi-Server** aus und klicken Sie dann auf **Entfernen**.

## Ergebnisse

Nachdem Sie die Operation zum Hinzufügen oder Entfernen gestartet haben, stellen Sie möglicherweise eine leichte Verzögerung fest, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.

Sie werden per E-Mail benachrichtigt, dass Ihre Anforderung zum Hinzufügen oder Entfernen von ESXi-Servern verarbeitet wird. Der Status des Clusters, der den ESXi-Servern zugeordnet ist, ändert sich in **Wird geändert**. Beim Entfernen von Servern ist zu beachten, dass die ESXi-Server am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur (der in der Regel 30 Tage umfasst) vollständig von der {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgefordert werden.

**Achtung** Die entfernten ESXi-Server werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.

Wenn die neuen ESXi-Server nicht zur Liste im Cluster hinzugefügt werden, überprüfen Sie die E-Mail- oder Konsolenbenachrichtigungen, um weitere Details über den Fehler zu ermitteln.

### Zugehörige Links

* [vCenter Server-Teileliste](vc_bom.html)
* [Voraussetzungen und Planung für vCenter Server with Hybridity Bundle-Instanzen](vc_hybrid_planning.html)
* [Cluster für vCenter Server with Hybridity Bundle-Instanzen hinzufügen, anzeigen und löschen](vc_hybrid_addingviewingclusters.html)
* [Place a host in maintenance mode](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
