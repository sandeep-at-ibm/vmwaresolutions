---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Cloud Foundation-Instanzen löschen

Zum Freigeben der Komponenten, die Sie in einer VMware Cloud Foundation-Instanz bestellt haben, müssen Sie die Instanz löschen.

Wenn Sie eine Cloud Foundation-Instanz löschen, werden die folgenden Komponenten nacheinander freigegeben:
1. Alle bereitgestellten Services
2. Support- und Servicegebühren
3. VMware-Produktlizenzen
4. ESXi-Server
5. Teilnetze
6. VLANs

Aufgrund von Ressourcenabhängigkeiten werden die Komponenten in Ihrer Instanz nicht sofort freigegeben, wenn Sie die Instanz löschen. Beispielsweise können die Teilnetze und VLANs erst gelöscht werden, nachdem die ESXi-Server vollständig von der {{site.data.keyword.cloud}}-Infrastruktur zurückgefordert wurden, was am Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus passiert. Am Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus, der normalerweise 30 Tage beträgt, werden die Teilnetze und VLANs gelöscht und die Instanzlöschung ist abgeschlossen.

**Achtung:** Die gelöschte Instanz wird bis zum Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus berechnet.

## Vorgehensweise zum Löschen von Instanzen auf der Seite "Bereitgestellte Instanzen"

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Suchen Sie in der Tabelle **Cloud Foundation-Instanzen** nach der Instanz, die Sie löschen wollen.
3. Klicken Sie in der Spalte **Aktionen** auf das Symbol "Löschen".
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde, werden die Komponenten der Instanz freigegeben und der Status der Instanz ändert sich in **Gelöscht**.
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie in der Spalte **Aktionen** erneut auf das Symbol "Löschen".
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

## Vorgehensweise zum Löschen von Instanzen auf der Seite "Instanzdetails"

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **Cloud Foundation-Instanzen** auf die Instanz, die Sie löschen wollen.
3. Klicken Sie auf das Überlaufmenüsymbol neben der **vCenter-Konsole** und klicken Sie auf **Instanz löschen**.
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde, werden die Komponenten der Instanz freigegeben und der Status der Instanz ändert sich in **Gelöscht**.
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie erneut auf das Überlaufmenüsymbol neben der **vCenter-Konsole** und klicken Sie auf **Instanz löschen**.
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

### Zugehörige Links

* [Cloud Foundation-Instanzen in Konfiguration mit mehreren Standorten löschen](sd_deletinginstance_multi.html)
* [Cloud Foundation-Instanzen bestellen](sd_orderinginstance.html)
* [Cloud Foundation-Instanzen anzeigen](sd_viewinginstances.html)
* [Kapazität für Cloud Foundation-Instanzen erweitern und verringern](sd_addingremovingservers.html)
* [Konfigurationen mit mehreren Standorten löschen](sd_deletinginstance_multi.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
