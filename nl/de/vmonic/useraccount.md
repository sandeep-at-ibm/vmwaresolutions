---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: set credentials, user credentials, set notifications

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Benutzerkonten und -einstellungen verwalten
{: #useraccount}

{{site.data.keyword.vmwaresolutions_full}} kommuniziert mit der {{site.data.keyword.cloud_notm}}-Infrastruktur über {{site.data.keyword.slapi_short}}-Aufrufe. Für den sicheren Zugriff auf die {{site.data.keyword.slapi_short}} müssen Sie die Berechtigungsnachweise Ihres Kontos für die {{site.data.keyword.cloud_notm}}-Infrastruktur mit Ihrem {{site.data.keyword.cloud_notm}}-Konto verknüpfen.

Sie können außerdem angeben, ob Sie E-Mail- und Konsolenbenachrichtigungen für verschiedene Ereignisse empfangen wollen.

## Vorbereitende Schritte
{: #useraccount-reqs}

* Sie können nur ein Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur mit einem {{site.data.keyword.cloud_notm}}-Benutzerkonto verknüpfen.
* Das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur, das Sie verwenden, muss bestimmte Anforderungen erfüllen. Weitere Informationen finden Sie in [Anforderungen an das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).
* Wenn der API-Schlüssel für Ihr Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur geändert wird, müssen Sie den Schlüssel auf der Seite **Einstellungen** in der Konsole von {{site.data.keyword.vmwaresolutions_short}} aktualisieren.

   Sie müssen dafür sorgen, dass der auf der Seite **Einstellungen** gespeicherte API-Schlüssel richtig und aktuell ist. Andernfalls können Operationen fehlschlagen, die eine Validierung des API-Schlüssels erforderlich machen.
   {:important}

## Vorgehensweise zum Festlegen von Benachrichtigungen
{: #useraccount-set-notif}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Einstellungen**.
2. Wenn Sie bei Auftreten von Ereignissen per E-Mail benachrichtigt werden wollen, klicken Sie auf **E-Mail-Benachrichtigungen aktivieren**.
3. Wenn Sie in der Konsole bei Auftreten von Ereignissen benachrichtigt werden wollen, klicken Sie auf **Konsolenbenachrichtigungen aktivieren**.

## Vorgehensweise zum Festlegen der Benutzerkontoberechtigungsnachweise
{: #useraccount-set-cred}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Einstellungen**.
2. Überprüfen Sie im Bereich **Berechtigungsnachweise für IBM Cloud-Infrastruktur** die Informationen für die Schritte, die Sie ausführen müssen.
3. Wenn Sie über ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto und ein {{site.data.keyword.cloud_notm}}-Konto verfügen, die miteinander verknüpft sind, klicken Sie auf **Abrufen**, damit die Berechtigungsnachweise automatisch ausgefüllt werden.
4. Wenn Sie über ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto und ein {{site.data.keyword.cloud_notm}}-Konto verfügen, beide jedoch nicht miteinander verknüpft sind, müssen Sie diese miteinander verknüpfen. Gehen Sie gemäß den Anweisungen in [IBMid-Konten verknüpfen](/docs/account?topic=account-unifyingaccounts#link_accounts) vor und klicken Sie anschließend auf **Abrufen**, damit die Berechtigungsnachweise automatisch ausgefüllt werden.
5. Wenn Sie nicht über ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto und nicht über ein gebührenpflichtiges {{site.data.keyword.cloud_notm}}-Konto verfügen, führen Sie zuerst [ein Upgrade für Ihr Konto](/docs/account?topic=account-upgrading-account) durch und [erstellen einen API-Schlüssel für die klassische Infrastruktur](/docs/iam?topic=iam-classic_keys).
6. Wenn Sie nicht über ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto, jedoch über ein gebührenpflichtiges {{site.data.keyword.cloud_notm}}-Konto verfügen, müssen Sie [einen API-Schlüssel für die klassische Infrastruktur erstellen](/docs/iam?topic=iam-classic_keys).
7. Klicken Sie auf **Berechtigungsnachweise speichern**.

## Ergebnisse
{: #useraccount-results}

Wenn das {{site.data.keyword.cloud_notm}}-Konto und das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur verknüpft sind, ruft die Konsole die Berechtigungsnachweise des Kontos der {{site.data.keyword.cloud_notm}}-Infrastruktur automatisch ab, um mit Ihrer VMware-Umgebung in {{site.data.keyword.cloud_notm}} zu kommunizieren.

Die gespeicherten Berechtigungsnachweise für das Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur werden bei zukünftigen Operationen verwendet, die eine Interaktion mit der {{site.data.keyword.cloud_notm}}-Infrastruktur erfordern.

Falls für bestimmte Instanzereignisse E-Mail- oder Konsolenbenachrichtigungen aktiviert sind, werden Sie per E-Mail oder über Konsolennachrichten benachrichtigt, wenn diese Ereignisse stattfinden.

## Zugehörige Links
{: #useraccount-related}

* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [vCenter Server-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Benachrichtigungen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [SoftLayer-API](/docs/customer-portal?topic=customer-portal-customerportal_api)
