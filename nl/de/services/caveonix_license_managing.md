---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: Caveonix view license, Caveonix manage license, delete Caveonix license

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight-Lizenzen verwalten
{: #caveonix_license_managing}

Sie können die Caveonix RiskForesight-Lizenzen, die Sie für den eigenständigen Gebrauch bestellt haben, anzeigen oder löschen oder Hinweise darin bearbeiten.

## Vorgehensweise zum Anzeigen von Caveonix RiskForesight-Lizenzen
{: #caveonix_license_managing_procedure-view}

1. Klicken Sie im linken Navigationsfenster auf **Ressourcen** und blättern Sie abwärts zur Tabelle **Caveonix RiskForesight-Lizenzen**.

   | Element | Beschreibung |
   |:-----|:------------|
   | Name | Der Name der Lizenz. |
   | Erstellungszeit | Der Zeitpunkt (Datum und Uhrzeit), zu dem die Lizenz erstellt wurde. |
   | Status | Der Status der Lizenz: <br>Wird geändert: Die Lizenz wird gerade erstellt.<br>Installiert: Die Lizenz ist zur Verwendung bereit.<br>Wird entfernt: Die Lizenz wird gerade gelöscht. |
   {: caption="Tabelle 1. Elemente von Caveonix RiskForesight-Lizenzen" caption-side="top"}

2. Klicken Sie auf die Lizenz, um die Details zu einer bestimmten Lizenz anzuzeigen.

## Vorgehensweise zur Hinweisbearbeitung für Caveonix RiskForesight-Lizenzen
{: #caveonix_license_managing_procedure-edit}

1. Klicken Sie im linken Navigationsfenster auf **Ressourcen**.
2. Blättern Sie abwärts zu der Tabelle **Caveonix RiskForesight-Lizenzen** und klicken Sie auf die Lizenz, für die Sie Hinweise bearbeiten möchten.
3. Bearbeiten Sie die Lizenzhinweise auf der Seite mit den Lizenzdetails und klicken Sie anschließend auf **Bestätigen**.

## Bekannte Probleme bei der Anzeige von Datumsangaben zu Lizenzen
{: #caveonix_license_considerations-date}

Wenn Sie Mozilla Firefox als Browser verwenden, werden die Datumsangaben zu Start und Ende der Lizenz möglicherweise ohne Werte in der Caveonix RiskForesight-Konsole angezeigt. Um das Problem zu beheben, sehen Sie sich die Lizenzinformationen in einem anderen Browser an, z. B. Google Chrome.

Wenn dieses Problem auftritt und Firefox der einzige Browser ist, den Sie verwenden können, wenden Sie sich zur Unterstützung an den [Caveonix-Support](https://www.caveonix.com/support/){:external}.
{:note}

## Vorgehensweise zum Löschen von Caveonix RiskForesight-Lizenzen
{: #caveonix_license_managing_procedure-delete}

Durch das Löschen einer Caveonix RiskForesight-Lizenz wird nicht der Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}-Service gelöscht, der auf einer vCenter Server-Instanz installiert ist. Das Entfernen des Service erfolgt in der {{site.data.keyword.vmwaresolutions_short}}-Konsole. Weitere Informationen finden Sie unter [Vorgehensweise zum Entfernen von Services für Center Server-Instanzen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-removing-procedure).
{:note:}

1. Klicken Sie im linken Navigationsfenster auf **Ressourcen**.
2. Blättern Sie abwärts zu der Tabelle **Caveonix RiskForesight-Lizenzen** und suchen Sie die Lizenz, die gelöscht werden soll.
3. Klicken Sie in der Spalte **Aktionen** auf das Symbol "Löschen".
4. Im Fenster **Lizenz löschen** klicken Sie auf **OK**.
   Der Status der Lizenz ändert sich in **Wird entfernt**. Nach Abschluss der Lizenzlöschung ist die Lizenz nicht mehr in der Tabelle **Caveonix RiskForesight-Lizenzen** verfügbar.

## Zugehörige Links
{: #caveonix_license_managing-related}

* [Caveonix RiskForesight - Übersicht]()
* [Caveonix RiskForesight-Lizenzen bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)
