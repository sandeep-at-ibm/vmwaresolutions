---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-03"

---

# Benutzerkonten und -einstellungen verwalten

{{site.data.keyword.vmwaresolutions_full}} kommuniziert mit der {{site.data.keyword.cloud_notm}}-Infrastruktur über {{site.data.keyword.slapi_short}}-Aufrufe. Zum sicheren Zugriff auf die {{site.data.keyword.slapi_short}} müssen Sie die Berechtigungsnachweise Ihres {{site.data.keyword.cloud_notm}}-Kontos zu Ihrem {{site.data.keyword.vmwaresolutions_short}}-Benutzerkonto zuordnen.

**Hinweis**: Das {{site.data.keyword.cloud_notm}}-Konto hieß früher "IBM SoftLayer-Konto".

In der {{site.data.keyword.vmwaresolutions_short}}-Konsole können Sie außerdem angeben, ob Sie E-Mail-Benachrichtigungen für verschiedene Ereignisse erhalten wollen.

## Vorbereitende Schritte

* Sie können nur ein einziges {{site.data.keyword.cloud_notm}}-Konto zu Ihrem {{site.data.keyword.vmwaresolutions_short}}-Benutzerkonto zuordnen.
* Das {{site.data.keyword.cloud_notm}}-Konto, das Sie verwenden, muss bestimmte Voraussetzungen erfüllen. Weitere Informationen finden Sie unter [Voraussetzungen für {{site.data.keyword.cloud_notm}}-Konto](slaccountrequirement.html).
* Falls sich der API-Schlüssel Ihres {{site.data.keyword.cloud_notm}}-Kontos ändert, müssen Sie den Schlüssel in Ihrem {{site.data.keyword.vmwaresolutions_short}}-Benutzerkonto aktualisieren.

   **Wichtig**: Sie müssen dafür sorgen, dass der auf der Seite **Einstellungen** gespeicherte API-Schlüssel richtig und aktuell ist.
   Andernfalls können Operationen fehlschlagen, die eine Validierung des API-Schlüssels erforderlich machen.

Um das {{site.data.keyword.vmwaresolutions_short}}-Konto zum {{site.data.keyword.cloud_notm}}-Konto zuzuordnen, geben Sie die Berechtigungsnachweise für das {{site.data.keyword.cloud_notm}}-Konto auf der Seite **Einstellungen** der {{site.data.keyword.vmwaresolutions_short}}-Konsole ein.

Nachdem Sie das {{site.data.keyword.cloud_notm}}-Konto zugeordnet haben, ruft die Konsole automatisch die Berechtigungsnachweise für das {{site.data.keyword.cloud_notm}}-Konto für die Kommunikation mit Ihrer VMware-Umgebung in {{site.data.keyword.cloud_notm}} ab.

## Vorgehensweise

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Einstellungen**.
2. Wenn Sie per E-Mail über neu auftretende Ereignisse benachrichtigt werden wollen, wählen Sie das Kontrollkästchen **E-Mail-Benachrichtigungen aktivieren** aus.
3. Wenn Sie in der Konsole über neu auftretende Ereignisse benachrichtigt werden wollen, wählen Sie das Kontrollkästchen **Konsolenbenachrichtigungen aktivieren** aus.
4. Geben Sie im Bereich **Berechtigungsnachweise für IBM Cloud-Infrastruktur** den Benutzernamen Ihres {{site.data.keyword.cloud_notm}}-Kontos ein und befolgen Sie anschließend die Anweisungen in der Konsole, um den {{site.data.keyword.slapi_short}}-Schlüssel einzugeben.
5. Klicken Sie auf **Berechtigungsnachweise speichern**.

## Ergebnisse

Die gespeicherten Berechtigungsnachweise für das {{site.data.keyword.cloud_notm}}-Konto werden künftig bei Operationen verwendet, die eine Interaktion mit der {{site.data.keyword.cloud_notm}}-Infrastruktur erforderlich machen. Falls für bestimmte Instanzereignisse E-Mail- oder Konsolenbenachrichtigungen aktiviert sind, werden Sie per E-Mail oder in der Konsole benachrichtigt, wenn diese Ereignisse stattfinden.

## Zugehörige Links

* [Häufig gestellte Fragen](faq.html)
* [Cloud Foundation-Instanzen bestellen](../sddc/sd_orderinginstance.html)
* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html)
* [Benachrichtigungen](notifications.html)
* [SoftLayer-API](../../../customer-portal/cpapi.html){:new_window}
