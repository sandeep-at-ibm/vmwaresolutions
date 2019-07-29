---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: NetApp delete instance, delete NetApp ONTAP, remove NetApp

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# NetApp ONTAP Select-Instanzen löschen
{: #np_deletinginstance}

Wenn Sie eine NetApp ONTAP Select-Instanz löschen, werden die folgenden Komponenten nacheinander freigegeben:
1. Bereitgestellte Cluster-VMs (virtuelle Maschinen) für NetApp ONTAP Select und virtuelle Maschine für NetApp ONTAP Select Deploy
2. Support- und Servicegebühren
3. VMware-Produktlizenzen
4. ESXi-Server
5. Teilnetze
6. VLANs

Aufgrund von Ressourcenabhängigkeiten werden die Komponenten in Ihrer Instanz nicht sofort freigegeben, wenn Sie die Instanz löschen. Beispielsweise können die Teilnetze und VLANs erst gelöscht werden, nachdem die ESXi-Server vollständig von der {{site.data.keyword.cloud}}-Infrastruktur zurückgefordert wurden, was am Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus passiert. Am Ende des Abrechnungszyklus, der normalerweise 30 Tage beträgt, werden die Teilnetze und VLANs zurückgefordert und die Instanzlöschung ist abgeschlossen.

Die gelöschte Instanz wird Ihnen bis zum Ende des Abrechnungszyklus berechnet.
{:note}

## Vorgehensweise zum Löschen von Instanzen auf der Seite "Ressourcen"
{: #np_deletinginstance-procedure1}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Suchen Sie in der Tabelle **NetApp ONTAP Select-Instanzen** nach der Instanz, die gelöscht werden soll.
3. Klicken Sie in der Spalte **Aktionen** auf das Symbol "Löschen".
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde und sich ihr Status in **Gelöscht** geändert hat, klicken Sie erneut in der Spalte **Aktionen** auf das Symbol "Löschen".
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie in der Spalte **Aktionen** erneut auf das Symbol "Löschen".
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

## Vorgehensweise zum Löschen von Instanzen auf der Seite "Instanzdetails"
{: #np_deletinginstance-procedure2}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **NetApp ONTAP Select-Instanzen** auf die Instanz, die gelöscht werden soll.
3. Klicken Sie auf das Überlaufmenüsymbol neben der **NetApp-Konsole** und klicken Sie auf **Instanz löschen**.
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde, werden die Komponenten der Instanz freigegeben und der Status der Instanz ändert sich in **Gelöscht**.
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie erneut auf das Überlaufmenüsymbol neben der **vCenter-Konsole** und klicken Sie auf **Instanz löschen**.
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

## Zugehörige Links
{: #np_deletinginstance-related}

* [NetApp ONTAP Select-Instanzen bestellen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)
* [NetApp ONTAP Select-Instanzen anzeigen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_viewinginstances)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
