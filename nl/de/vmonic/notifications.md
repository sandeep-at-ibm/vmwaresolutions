---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Systembenachrichtigungen verwalten

Sie können Benachrichtigungen über den Status von System- oder Benutzeroperationen überprüfen. Mithilfe der Informationen können Sie darüber hinaus potenzielle Probleme überprüfen.

## Benachrichtigungen anzeigen

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Benachrichtigungen**.
2. Zeigen Sie in der Tabelle **Benachrichtigungsprotokoll** die Zusammenfassung für alle Benachrichtigungen an.

   Tabelle 1. Benachrichtigungsprotokoll

    <table>
      <tr>
        <th>Spalte</th>
        <th>Beschreibung</th>
      </tr>
      <tr>
        <td>Bewertung</td>
        <td>Die Dringlichkeit des Ereignisses, das durch die Benachrichtigung gemeldet wird.
          <dl class="dl">
          <dt class="dt dlterm">Kritisch</dt>
          <dd class="dd">Ein kritisches Ereignis hat möglicherweise Auswirkungen auf das gesamte System oder den gesamten Service.</dd>
          <dt class="dt dlterm">Fehler</dt>
          <dd class="dd">Während einer Operation ist ein Fehlerereignis aufgetreten, dass möglicherweise das Eingreifen des Administrators oder Benutzers erfordert.</dd>
          <dt class="dt dlterm">Warnung</dt>
          <dd class="dd">Eine Komponente ist fehlgeschlagen oder funktioniert nicht ordnungsgemäß. Der Fehler führt jedoch nicht zu einer Unterbrechung des laufenden Komponentenprozesses.</dd>
            <dt class="dt dlterm">Information</dt>
            <dd class="dd">Eine System- oder Benutzeroperation wurde ausgeführt. Benachrichtigungen mit der Prioritätsstufe "Information" werden in der Regel durch die folgenden Ereignisse gemeldet:
              <ul class="ul">
                <li class="li">Installation eines Service</li>
                <li class="li">Upgrade eines Service</li>
                <li class="li">Löschung eines Service</li>
                <li class="li">Rekonfiguration aller Services für hinzugefügte ESXi-Server</li>
                <li class="li">Rekonfiguration aller Services für entfernte ESXi-Server</li>
              </ul>
            </dd>
          </dl>
        </td>
       </tr>
       <tr>
         <td>Typ</td>
         <td>Der Typ der Komponente, auf die sich das gemeldete Ereignis bezieht:<ul><li>vCenter Server-Instanzen</li><li>Cloud Foundation-Instanzen</li><li>Services</li><li>System</li></ul></td>
       </tr>
       <tr>
         <td>Ressource</td>
         <td>Der Name der Instanz oder des Service, von der/dem die Benachrichtigung gesendet wird.</td>
       </tr>
       <tr>
         <td>Beschreibung</td>
         <td>Eine kurze Beschreibung der Benachrichtigung.</td>
       </tr>
       <tr>
         <td>Datum</td>
         <td>Der Zeitpunkt (Datum und Uhrzeit), zu dem die Benachrichtigung gesendet wird.</td>
       </tr>
    </table>                                       

3. Klicken Sie auf die Zeile für eine Benachrichtigung, um die Details der Benachrichtigung anzuzeigen.

## Benachrichtigungen filtern

Standardmäßig werden alle nicht gelesenen Benachrichtigungen angezeigt. Sie können die Benachrichtigungen nach Status, Prioritätsstufe und Typ filtern. Wählen Sie zum Filtern der Benachrichtigungen in den Listen **Status**, **Prioritätsstufe** oder **Typ** nur die Kontrollkästchen für die Elemente aus, die angezeigt werden sollen.

### Zugehörige Links

* [Häufig gestellte Fragen](faq.html)
* [Benutzerkonten und -einstellungen](useraccount.html)
