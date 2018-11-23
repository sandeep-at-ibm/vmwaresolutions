---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# NetApp ONTAP Select-Instanzen löschen

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

## Vorgehensweise zum Löschen von Instanzen auf der Seite "Bereitgestellte Instanzen"

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Suchen Sie in der Tabelle **NetApp ONTAP Select-Instanzen** nach der Instanz, die gelöscht werden soll.
3. Klicken Sie in der Spalte **Aktionen** auf das Symbol "Löschen".
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde und sich ihr Status in **Gelöscht** geändert hat, klicken Sie erneut in der Spalte **Aktionen** auf das Symbol "Löschen".
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie in der Spalte **Aktionen** erneut auf das Symbol "Löschen".
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

## Vorgehensweise zum Löschen von Instanzen auf der Seite "Instanzdetails"

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **NetApp ONTAP Select-Instanzen** auf die Instanz, die gelöscht werden soll.
3. Klicken Sie auf das Überlaufmenüsymbol neben der **NetApp-Konsole** und klicken Sie auf **Instanz löschen**.
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde, werden die Komponenten der Instanz freigegeben und der Status der Instanz ändert sich in **Gelöscht**.
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie erneut auf das Überlaufmenüsymbol neben der **vCenter-Konsole** und klicken Sie auf **Instanz löschen**.
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

### Zugehörige Links

* [NetApp ONTAP Select-Instanzen bestellen](np_orderinginstances.html)
* [NetApp ONTAP Select-Instanzen anzeigen](np_viewinginstances.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
