---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# Benutzerkonten und -einstellungen verwalten

{{site.data.keyword.vmwaresolutions_full}} kommuniziert mit der {{site.data.keyword.cloud_notm}}-Infrastruktur über {{site.data.keyword.slapi_short}}-Aufrufe. Für den sicheren Zugriff auf die {{site.data.keyword.slapi_short}} müssen Sie die Berechtigungsnachweise Ihres Kontos für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) mit Ihrem {{site.data.keyword.cloud_notm}}-Konto verknüpfen.

**Hinweis:** Das Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) wurde früher als IBM SoftLayer-Konto bezeichnet.

Sie können außerdem angeben, ob Sie E-Mail- und Konsolenbenachrichtigungen für verschiedene Ereignisse empfangen wollen.

## Vorbereitende Schritte

* Sie können nur ein Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) mit einem {{site.data.keyword.cloud_notm}}-Benutzerkonto verknüpfen.
* Das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer), das Sie verwenden, muss bestimmte Anforderungen erfüllen. Weitere Informationen finden Sie unter [Anforderungen an das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur](slaccountrequirement.html).
* Wenn der API-Schlüssel für Ihr Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) geändert wird, müssen Sie den Schlüssel auf der Seite **Einstellungen** in der Konsole von {{site.data.keyword.vmwaresolutions_short}} aktualisieren.

   **Wichtig:** Sie müssen dafür sorgen, dass der auf der Seite **Einstellungen** gespeicherte API-Schlüssel richtig und aktuell ist.
   Andernfalls können Operationen fehlschlagen, die eine Validierung des API-Schlüssels erforderlich machen.

## Vorgehensweise

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Einstellungen**.
2. Geben Sie im Bereich **Benachrichtigungen** Ihre Benachrichtigungseinstellungen an:
   * Wenn Sie bei Auftreten von Ereignissen per E-Mail benachrichtigt werden wollen, klicken Sie auf **E-Mail-Benachrichtigungen aktivieren**.
   * Wenn Sie in der Konsole bei Auftreten von Ereignissen benachrichtigt werden wollen, klicken Sie auf **Konsolenbenachrichtigungen aktivieren**.
3. Geben Sie im Bereich **Berechtigungsnachweise für IBM Cloud-Infrastruktur** den Benutzernamen und den API-Schlüssel Ihres Kontos der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) mit einer der folgenden Methoden ein:
   * Wenn Ihr Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) und Ihr {{site.data.keyword.cloud_notm}}-Konto verknüpft sind, klicken Sie auf **Abrufen**, um die Berechtigungsnachweise automatisch eintragen zu lassen.
   * Wenn Ihr Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) und Ihr {{site.data.keyword.cloud_notm}}-Konto nicht verknüpft sind, melden Sie sich im [Kundenportal für die {{site.data.keyword.cloud_notm}}-Infrastruktur](https://control.softlayer.com/) an und führen die Anweisungen in der Konsole aus, um die Berechtigungsnachweise zu erhalten und einzugeben.
   * Wenn Sie kein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) haben, [registrieren Sie sich für ein Konto](../vmonic/signing_softlayer_account.html). Befolgen Sie anschließend die Anweisungen in der Konsole, um die Berechtigungsnachweise abzurufen und einzugeben.
4. Klicken Sie auf **Berechtigungsnachweise speichern**.

## Ergebnisse

Wenn das {{site.data.keyword.cloud_notm}}-Konto und das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) verknüpft sind, ruft die Konsole die Berechtigungsnachweise des Kontos der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) automatisch ab, um mit Ihrer VMware-Umgebung in {{site.data.keyword.cloud_notm}} zu kommunizieren.

Die gespeicherten Berechtigungsnachweise für das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) werden bei zukünftigen Operationen verwendet, die eine Interaktion mit der {{site.data.keyword.cloud_notm}}-Infrastruktur erfordern.

Falls für bestimmte Instanzereignisse E-Mail- oder Konsolenbenachrichtigungen aktiviert sind, werden Sie per E-Mail oder in der Konsole benachrichtigt, wenn diese Ereignisse stattfinden.

### Zugehörige Links

* [Häufig gestellte Fragen](faq.html)
* [Cloud Foundation-Instanzen bestellen](../sddc/sd_orderinginstance.html)
* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html)
* [Benachrichtigungen](notifications.html)
* [SoftLayer-API](../../../customer-portal/cpapi.html){:new_window}
