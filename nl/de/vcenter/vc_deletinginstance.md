---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# vCenter Server-Instanzen löschen

Zum Freigeben der Komponenten, die Sie in einer VMware vCenter Server-Instanz bestellt haben, löschen Sie die Instanz.

Wenn Sie eine vCenter Server-Instanz löschen, werden die folgenden Komponenten nacheinander freigegeben:
1. Alle bereitgestellten Services
2. Support- und Servicegebühren
3. VMware-Produktlizenzen
4. ESXi-Server
5. Teilnetze
6. VLANs

Aufgrund von Ressourcenabhängigkeiten werden die Komponenten in Ihrer Instanz nicht sofort freigegeben, wenn Sie die Instanz löschen. Beispielsweise können die Teilnetze und VLANs erst gelöscht werden, nachdem die ESXi-Server vollständig von der {{site.data.keyword.cloud}}-Infrastruktur zurückgefordert wurden, was am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur erfolgt. Am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur, der normalerweise 30 Tage beträgt, werden die Teilnetze und VLANs gelöscht und die Instanzlöschung ist abgeschlossen.

**Achtung:** Die gelöschte Instanz wird Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.

## Instanzen auf der Seite "Bereitgestellte Instanzen" löschen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Suchen Sie in der Tabelle **vCenter Server-Instanzen** nach der Instanz, die Sie löschen wollen.
3. Klicken Sie in der Spalte **Aktionen** auf das Symbol "Löschen".
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde, werden die Komponenten der Instanz freigegeben und der Status der Instanz ändert sich in **Gelöscht**.
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie in der Spalte **Aktionen** erneut auf das Symbol "Löschen".
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

## Instanzen auf der Seite mit den Instanzdetails löschen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, die Sie löschen wollen.
3. Klicken Sie auf das Überlaufmenüsymbol rechts neben der **vCenter-Konsole** und anschließend auf **Instanz löschen**.
   Der Status der Instanz ändert sich in **Wird gelöscht**. Nachdem die Instanz erfolgreich gelöscht wurde, werden die Komponenten der Instanz freigegeben und der Status der Instanz ändert sich in **Gelöscht**.
4. Wenn Sie den Instanzdatensatz aus der {{site.data.keyword.vmwaresolutions_short}}-Konsole entfernen möchten, führen Sie die folgenden Schritte aus:
   1. Klicken Sie erneut auf das Überlaufmenüsymbol rechts neben der **vCenter-Konsole** und anschließend auf **Instanz löschen**.
   2. Klicken Sie im Fenster **Instanz löschen** auf **OK**.

### Zugehörige Links

* [vCenter Server-Instanzen in einer Konfiguration mit mehreren Standorten löschen](vc_deletinginstance_multi.html)
* [vCenter Server-Instanzen bestellen](vc_orderinginstance.html)
* [vCenter Server-Instanzen anzeigen](vc_viewinginstances.html)
* [Kapazität für vCenter Server-Instanzen erweitern und verringern](vc_addingremovingservers.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
