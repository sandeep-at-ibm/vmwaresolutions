---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-24"

---

# VMware Federal-Instanzen schützen

Führen Sie die nachfolgend beschriebene Prozedur aus, um Ihre bereitgestellte VMware Federal-Instanz zu schützen,
indem Sie die offene Managementverbindung für den kontinuierlichen Zugriff auf die Instanz entfernen.

## Vorbereitende Schritte

Lesen Sie die folgenden Informationen aufmerksam durch um die Konsequenzen zu verstehen, die sich aus dem Schützen Ihrer bereitgestellten VMware Federal-Instanz ergeben:

* Notieren Sie sich alle Berechtigungsnachweise, die Sie für Ihre Umgebung benötigen könnten, und bewahren Sie sie an einem sicheren Ort auf, bevor Sie diese Prozedur ausführen. Alle Berechtigungsnachweise für Ihre Umgebung werden aus der {{site.data.keyword.vmwaresolutions_full}} Datenbank gelöscht und können nicht mehr abgerufen werden, nachdem die Aktion zum Schützen aufgerufen wurde.
* Nachdem Sie die Aktion zum Schützen aufgerufen haben, werden mit Ausnahme des vollständigen Löschens der Instanz alle Managementfunktionen inaktiviert.
* Das VMware NSX Edge Services Gateway (ESG) für abgehenden HTTPS-Managementdatenverkehr und die virtuelle Maschine für IBM CloudDriver werden im Rahmen der Aktion für das Schützen der bereitgestellten VMware Federal-Instanz gelöscht.

## Vorgehensweise

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, die Sie schützen wollen.
3. Klicken Sie auf das Überlaufmenüsymbol rechts neben der **vCenter-Konsole**.
4. Klicken Sie auf **Instanz schützen**.
5. Klicken Sie auf **OK**, um zu bestätigen, dass Sie die Verbindung zu der Instanz von der Automation trennen möchten.
   
   **Hinweis**: Vergewissern Sie sich, dass Sie die wichtigen Informationen unter **Vorbereitende Schritte** gelesen haben müssen, bevor Sie diesen Schritt ausführen.

## Ergebnisse

Der Status der Instanz ändert sich in **Wird geändert**.

Sobald die Instanz erfolgreich geschützt wurde, ändert sich der Status der Instanz in **Geschützt**. Dann sind nur die Instanzeigenschaften und der Bereitstellungsverlauf verfügbar.

## Zugehörige Links

* [Überblick zu VMware Federal on IBM Cloud](vc_fed_overview.html)
* [VMware Federal-Instanzen bestellen](vc_fed_orderinginstance.html)
* [VMware Federal-Instanzen anzeigen](vc_fed_viewinginstance.html)
* [VMware Federal-Instanzen löschen](vc_fed_deletinginstance.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
