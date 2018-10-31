---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# VMware Federal-Instanzen löschen

Zum Freigeben der Komponenten, die Sie in einer VMware Federal-Instanz bestellt haben, löschen Sie die Instanz.

Wenn Sie eine VMware Federal-Instanz löschen, werden die folgenden Komponenten nacheinander freigegeben:

1. Gebühren für Support und Service
2. VMware-Produktlizenzen
3. ESXi-Server
4. Teilnetze

Aufgrund von Ressourcenabhängigkeiten werden die Komponenten in Ihrer Instanz nicht sofort freigegeben, wenn Sie die Instanz löschen. Beispielsweise können die Teilnetze erst gelöscht werden, nachdem die ESXi-Server vollständig von der {{site.data.keyword.cloud}}-Infrastruktur zurückgefordert wurden, was am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur erfolgt. Am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur, der normalerweise 30 Tage beträgt, werden die Teilnetze gelöscht und die Instanzlöschung ist abgeschlossen.

**Achtung:** Die gelöschte Instanz wird Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.

## Vorgehensweise zum Löschen von Instanzen auf der Seite "Bereitgestellte Instanzen"

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Suchen Sie in der Tabelle **vCenter Server-Instanzen** nach der Instanz, die Sie löschen wollen.
3. Klicken Sie in der Spalte **Aktionen** auf das Symbol "Löschen".
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde, werden die Komponenten der Instanz freigegeben und der Status der Instanz ändert sich in **Gelöscht**.
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie in der Spalte **Aktionen** erneut auf das Symbol "Löschen".
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

## Vorgehensweise zum Löschen von Instanzen auf der Seite "Instanzdetails"

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, die Sie löschen wollen.
3. Klicken Sie auf das Überlaufmenüsymbol neben der **vCenter-Konsole** und klicken Sie auf **Instanz löschen**.
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde, werden die Komponenten der Instanz freigegeben und der Status der Instanz ändert sich in **Gelöscht**.
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie erneut auf das Überlaufmenüsymbol neben der **vCenter-Konsole** und klicken Sie auf **Instanz löschen**.
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

### Zugehörige Links

* [Übersicht über VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [VMware Federal-Instanzen bestellen](vc_fed_orderinginstance.html)
* [VMware Federal-Instanzen schützen](vc_fed_securinginstance.html)
* [VMware Federal-Instanzen anzeigen](vc_fed_viewinginstance.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
