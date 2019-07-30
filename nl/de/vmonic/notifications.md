---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: notifications console, filter notifications, system notification

subcollection: vmware-solutions


---

# Systembenachrichtigungen verwalten
{: #notifications}

Sie können Benachrichtigungen über den Status von System- oder Benutzeroperationen überprüfen. Mithilfe der Informationen können Sie darüber hinaus potenzielle Probleme überprüfen.

## Benachrichtigungen anzeigen
{: #notifications-view}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_full}}-Konsole im linken Navigationsfenster auf **Benachrichtigungen**.
2. Zeigen Sie die Zusammenfassung zu allen Benachrichtigungen an.

| Spalte | Beschreibung |
|:------ |:----------- |
| Bewertung | Die Dringlichkeit des Ereignisses, das durch die Benachrichtigung gemeldet wird.<br>**Kritisch**: Ein kritisches Ereignis hat möglicherweise Auswirkungen auf das gesamte System oder den gesamten Service.<br>**Fehler**: Während einer Operation ist ein Fehlerereignis aufgetreten, das möglicherweise das Eingreifen des Administrators oder Benutzers erfordert.<br>**Warnung**: Eine Komponente ist fehlgeschlagen oder funktioniert nicht ordnungsgemäß. Der Fehler führt jedoch nicht zu einer Unterbrechung des laufenden Komponentenprozesses.<br>**Information**: Eine System- oder Benutzeroperation wurde ausgeführt. Benachrichtigungen mit der Prioritätsstufe "Information" werden in der Regel durch die folgenden Ereignisse gemeldet:<br>Installation eines Service<br>Upgrade eines Service<br>Löschung eines Service<br>Rekonfiguration aller Services für hinzugefügte ESXi-Server<br>Rekonfiguration aller Services für entfernte ESXi-Server |
| Typ | Der Typ der Komponente, auf die sich das gemeldete Ereignis bezieht: vCenter Server-Instanzen, Services oder das System. |
| Ressource | Der Name der Instanz oder des Service, von der/dem die Benachrichtigung gesendet wird. |
| Beschreibung | Eine kurze Beschreibung der Benachrichtigung. |
| Datum | Der Zeitpunkt (Datum und Uhrzeit), zu dem die Benachrichtigung gesendet wird. |
{: caption="Tabelle 1. Benachrichtigungsprotokoll" caption-side="top"}

3. Klicken Sie auf die Zeile für eine Benachrichtigung, um die Details der Benachrichtigung anzuzeigen.

## Benachrichtigungen filtern
{: #notifications-filter}

Standardmäßig werden alle nicht gelesenen Benachrichtigungen angezeigt. Sie können die Benachrichtigungen nach Status, Prioritätsstufe und Typ filtern. Wählen Sie zum Filtern der Benachrichtigungen in den Listen **Status**, **Prioritätsstufe** oder **Typ** nur die Kontrollkästchen für die Elemente aus, die angezeigt werden sollen.

## Zugehörige Links
{: #notifications-related}

* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Benutzerkonten und -einstellungen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
