---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Benutzerkonten und -einstellungen verwalten
{: #useraccount}

{{site.data.keyword.vmwaresolutions_full}} kommuniziert mit der {{site.data.keyword.cloud_notm}}-Infrastruktur über {{site.data.keyword.slapi_short}}-Aufrufe. Für den sicheren Zugriff auf die {{site.data.keyword.slapi_short}} müssen Sie die Berechtigungsnachweise Ihres Kontos für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) mit Ihrem {{site.data.keyword.cloud_notm}}-Konto verknüpfen.

Das Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) wurde früher als IBM SoftLayer-Konto bezeichnet.
{:note}

Sie können außerdem angeben, ob Sie E-Mail- und Konsolenbenachrichtigungen für verschiedene Ereignisse empfangen wollen.

## Vorbereitende Schritte
{: #useraccount-reqs}

* Sie können nur ein Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) mit einem {{site.data.keyword.cloud_notm}}-Benutzerkonto verknüpfen.
* Das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer), das Sie verwenden, muss bestimmte Anforderungen erfüllen. Weitere Informationen finden Sie in [Anforderungen an das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement). 
* Wenn der API-Schlüssel für Ihr Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) geändert wird, müssen Sie den Schlüssel auf der Seite **Einstellungen** in der Konsole von {{site.data.keyword.vmwaresolutions_short}} aktualisieren.

   **Wichtig:** Sie müssen dafür sorgen, dass der auf der Seite **Einstellungen** gespeicherte API-Schlüssel richtig und aktuell ist. Andernfalls können Operationen fehlschlagen, die eine Validierung des API-Schlüssels erforderlich machen.

## Vorgehensweise zum Verwalten von Benutzerkonten und -einstellungen
{: #useraccount-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Einstellungen**.
2. Geben Sie im Bereich **Benachrichtigungen** Ihre Benachrichtigungseinstellungen an.
   * Wenn Sie bei Auftreten von Ereignissen per E-Mail benachrichtigt werden wollen, klicken Sie auf **E-Mail-Benachrichtigungen aktivieren**.
   * Wenn Sie in der Konsole bei Auftreten von Ereignissen benachrichtigt werden wollen, klicken Sie auf **Konsolenbenachrichtigungen aktivieren**.
3. Geben Sie im Bereich **Berechtigungsnachweise für IBM Cloud-Infrastruktur** den Benutzernamen und den API-Schlüssel Ihres Kontos der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) ein:
   * Wenn Ihr Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) und Ihr {{site.data.keyword.cloud_notm}}-Konto verknüpft sind, klicken Sie auf **Abrufen**, um die Berechtigungsnachweise automatisch eintragen zu lassen.
   * Wenn Ihr Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) und Ihr {{site.data.keyword.cloud_notm}}-Konto nicht verknüpft sind, stellen Sie die Verknüpfung her. Melden Sie sich im [Kundenportal der {{site.data.keyword.cloud_notm}}](https://control.softlayer.com/) an und rufen Sie die Berechtigungsnachweise wie in der Konsole angegeben ab. Geben Sie die Berechtigungsnachweise anschließend ein.
   * Wenn Sie kein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) haben, [registrieren Sie sich für ein Konto](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account). Befolgen Sie dann die Anweisungen in der Konsole, um die Berechtigungsnachweise abzurufen, und geben Sie die Berechtigungsnachweise anschließend ein.
4. Klicken Sie auf **Berechtigungsnachweise speichern**.

## Ergebnisse
{: #useraccount-results}

Wenn das {{site.data.keyword.cloud_notm}}-Konto und das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) verknüpft sind, ruft die Konsole die Berechtigungsnachweise des Kontos der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) automatisch ab, um mit Ihrer VMware-Umgebung in {{site.data.keyword.cloud_notm}} zu kommunizieren.

Die gespeicherten Berechtigungsnachweise für das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) werden bei zukünftigen Operationen verwendet, die eine Interaktion mit der {{site.data.keyword.cloud_notm}}-Infrastruktur erfordern.

Falls für bestimmte Instanzereignisse E-Mail- oder Konsolenbenachrichtigungen aktiviert sind, werden Sie per E-Mail oder über Konsolennachrichten benachrichtigt, wenn diese Ereignisse stattfinden.

## Zugehörige Links
{: #useraccount-related}

* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Cloud Foundation-Instanzen bestellen](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Benachrichtigungen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [SoftLayer-API](/docs/customer-portal?topic=customer-portal-customerportal_api){:new_window}
