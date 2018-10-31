---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# VMware Federal-Instanzen schützen

Führen Sie die nachfolgend beschriebene Prozedur aus, um Ihre bereitgestellte VMware Federal-Instanz zu schützen, indem Sie die offene Managementverbindung für den kontinuierlichen Zugriff auf die Instanz entfernen.

## Vorbereitende Schritte

Lesen Sie die folgenden Informationen aufmerksam durch um die Konsequenzen zu verstehen, die sich aus dem Schützen Ihrer bereitgestellten VMware Federal-Instanz ergeben:

* Notieren Sie sich alle Berechtigungsnachweise, die Sie für Ihre Umgebung benötigen könnten, und bewahren Sie sie an einem sicheren Ort auf, bevor Sie diese Prozedur ausführen. Alle Berechtigungsnachweise für Ihre Umgebung werden aus der {{site.data.keyword.vmwaresolutions_full}}-Datenbank gelöscht und können nicht mehr abgerufen werden, nachdem die Aktion zum Schützen gestartet wurde.
* Bis auf die Möglichkeit zum vollständigen Löschen der Instanz werden nach dem Starten der Aktion zum Schützen alle Managementfunktionen inaktiviert.

## Vorgehensweise beim Schützen einer VMware Federal-Instanz

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, die Sie schützen wollen.
3. Klicken Sie auf das Überlaufmenüsymbol neben **vCenter-Konsole**.
4. Klicken Sie auf **Instanz schützen**.
5. Klicken Sie auf **OK**, um zu bestätigen, dass Sie die Verbindung zu der Instanz von der Automation trennen möchten.

  **Anmerkung:** Stellen Sie vor dem Ausführen dieses Schritts sicher, dass Sie die Informationen unter **Vorbereitende Schritte** gelesen haben.

6. Entfernen Sie die öffentlichen Management-Services für VMware NSX Edge Services Gateway (ESG) in Ihrer Umgebung und bei Bedarf auch das vom Kunden verwaltete VMware NSX Edge Services Gateway (ESG), das bei der Automatisierung bereitgestellt wird.
7. Setzen Sie Kennwörter und Schlüssel für alle von der IBM Automatisierung verwendeten Konten zurück. Weitere Informationen hierzu finden Sie auf der Seite zum [Schützen der Umgebung durch Entfernen des IBM Automatisierungs- und Supportzugriffs](https://developer.ibm.com/answers/questions/452354/how-can-i-secure-my-environment-to-remove-access-b/).

## Ergebnisse

Der Status der Instanz ändert sich in **Wird geändert**.

Sobald die Instanz erfolgreich geschützt wurde, ändert sich der Status der Instanz in **Geschützt**. Dann sind nur die Instanzeigenschaften und der Bereitstellungsverlauf verfügbar.

### Zugehörige Links

* [Übersicht über VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [VMware Federal-Instanzen bestellen](vc_fed_orderinginstance.html)
* [VMware Federal-Instanzen anzeigen](vc_fed_viewinginstance.html)
* [VMware Federal-Instanzen löschen](vc_fed_deletinginstance.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
