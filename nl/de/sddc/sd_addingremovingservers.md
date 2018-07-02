---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# Kapazität für Cloud Foundation-Instanzen erweitern und verringern

Sie können die Kapazität Ihrer VMware Cloud Foundation-Instanz entsprechend Ihren Geschäftsanforderungen erweitern oder verringern, indem Sie ESXi-Server hinzufügen oder entfernen.

Eine Cloud Foundation-Instanz kann bis zu 5 Cluster besitzen, von denen einer der Standardcluster ist. Jeder erste Cluster kann bis zu 51 ESXi-Server umfassen; zusätzliche Cluster können bis zu 59 Server beinhalten.

## Vorbereitende Schritte

* Verwenden Sie nicht VMware vSphere Web Client, um ESXi-Server hinzuzufügen oder zu entfernen. Die Änderungen, die Sie in VMware vSphere Web Client vornehmen, werden nicht mit der {{site.data.keyword.vmwaresolutions_short}}-Konsole synchronisiert.
* Die von Ihnen bestellte Basisplattform umfasst standardmäßig 4 ESXi-Server. Sie können die Plattform auf maximal 32 ESXi-Server erweitern. Für die Anzahl der {{site.data.keyword.baremetal_short}}-Instanzen, die Sie jeweils hinzufügen können, gilt jedoch Folgendes:
   * Bei Konfigurationen des Typs **S (Klein)** und **L (Groß)** können Sie gleichzeitig 1 bis 10 ESXi-Server hinzufügen.
   * Bei Konfigurationen des Typs **Angepasst** können Sie gleichzeitig 1 bis 20 ESXi-Server hinzufügen.
* Sie können die von Ihnen hinzugefügten ESXi-Server entfernen. Die ESXi-Standardserver können nicht entfernt werden.
* Bevor Sie ESXi-Server mit installiertem Service "F5 on {{site.data.keyword.cloud_notm}}" oder "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" entfernen, müssen Sie die VMs für F5 BIG-IP und FortiGate auf einen ESXi-Server verlagern, auf dem die VMs nicht aktuell gehostet werden.
* Stellen Sie vor dem Entfernen von ESXi-Servern mit installiertem Service "IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}" sicher, dass keine (fehlgeschlagenen oder laufenden) Sicherungs- oder Wiederherstellungsoperationen aktiv sind, da diese aktiven Operationen das Entfernen der ESXi-Server verhindern könnten.

## Vorgehensweise

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **Cloud Foundation-Instanzen** auf die Instanz, für die Sie die Kapazität erweitern oder verringern wollen.
3. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
4. Klicken Sie in der Tabelle **CLUSTER** auf den Cluster, zu dem ESXi-Server hinzugefügt bzw. aus dem ESXi-Server entfernt werden sollen.
5. Gehen Sie zum Hinzufügen von ESXi-Servern folgendermaßen vor:
   1. Klicken Sie im Abschnitt **ESXi-Server** auf **Hinzufügen**.
   2. Geben Sie im Fenster **Server hinzufügen** die Anzahl der Server ein, die Sie hinzufügen wollen. Prüfen Sie geschätzten Kosten und klicken Sie dann auf **Hinzufügen**.
6. Um ESXi-Server zu entfernen, wählen Sie die entsprechenden Server im Abschnitt **ESXi-Server** aus und klicken Sie dann auf **Entfernen**.

## Ergebnisse

Nachdem Sie die Operation zum Hinzufügen oder Entfernen gestartet haben, stellen Sie möglicherweise eine leichte Verzögerung fest, während sich der Instanzstatus von **Bereit** in **Wird geändert** ändert. Warten Sie, bis die Operation vollständig abgeschlossen ist, bevor Sie weitere Änderungen an der Instanz vornehmen.

Sie werden per E-Mail benachrichtigt, wenn ESXi-Server hinzugefügt oder entfernt wurden. Beim Entfernen von Servern ist zu beachten, dass die ESXi-Server am Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus (der in der Regel 30 Tage umfasst) vollständig von der {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgefordert werden.

**Achtung** Die entfernten ESXi-Server werden Ihnen bis zum Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus berechnet.

Wenn die neuen ESXi-Server nicht zur Liste im Cluster hinzugefügt werden, überprüfen Sie die E-Mail- oder Konsolenbenachrichtigungen, um weitere Details über den Fehler zu ermitteln.

## Zugehörige Links

* [Cloud Foundation-Teileliste](sd_bom.html)
* [Voraussetzungen und Planung für Cloud Foundation-Instanzen](sd_planning.html)
* [Cluster für Cloud Foundation-Instanzen hinzufügen, anzeigen und löschen](sd_addingviewingclusters.html)
* [Versetzen eines Hosts in den Wartungsmodus](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
