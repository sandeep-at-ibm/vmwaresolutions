---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Updates der IBM Managementkomponenten auf vCenter Server-Instanzen anwenden
{: #vc_applyingupdates}

Die Prozedur in diesem Abschnitt bezieht sich auf das Durchführen von Updates für IBM Managementkomponenten für Instanzen, die in V2.1 bis V2.4 bereitgestellt werden.

Für Instanzen, die in V2.5 oder höheren Releases bereitgestellt wurden (oder für die Upgrades auf diese Releases durchgeführt wurden), werden Updates und Patches für die IBM Managementkomponenten bei Bedarf automatisch angewendet.

Bei Instanzen, die in V2.0 und früheren Versionen bereitgestellt wurden, müssen Sie die Updates manuell anwenden.

Beachten Sie außerdem das folgende Verhalten, wenn Sie bestimmte Operationen für Ihre Instanz ausführen:
* Wenn Sie neue Services bestellen, wird für die Instanz ein Update auf die neueste Version ausgeführt.
* Wenn Sie neue Cluster hinzufügen, werden diese Cluster mit den neuesten VMware-Komponenten bereitgestellt; dies gilt jedoch nicht für vorhandene Cluster.
* Wenn Sie neue ESXi-Server hinzufügen, werden diese ESXi-Server mit den neuesten VMware-Komponenten bereitgestellt; dies gilt jedoch nicht für vorhandene ESXi-Server.

{{site.data.keyword.vmwaresolutions_short}} bietet keine Unterstützung für die Anwendung von Updates und Patches für VMware-Komponenten. Sie müssen diese Updates selbst überwachen und anwenden.
{:important}

## Bevor Sie Updates für IBM Managementkomponenten anwenden
{: #vc_applyingupdates-prereq}

Erweitern Sie den Updateeintrag, indem Sie auf den Abwärtspfeil klicken und die folgenden Informationen überprüfen:
* Überprüfen Sie die Version des Updates. Sie müssen die Updates in chronologischer Reihenfolge anwenden, also zuerst das älteste Update und zuletzt das neueste Update. Stellen Sie sicher, dass Sie alle vorherigen Updates angewendet haben, bevor Sie das aktuelle Update anwenden. Beispielsweise müssen Sie das Update für V2.3 anwenden, bevor Sie versuchen, das Update für V2.4 anzuwenden.
* Ermitteln Sie, ob eine Ausfallzeit erforderlich ist.
* Prüfen Sie die geschätzte Gesamtzeit für die Ausführung des Updates.
* Stellen Sie fest, wie sich das Update auf die virtuelle VMware-Umgebung auswirkt. Tabelle 1 zeigt, wie sich die verschiedenen Aktualisierungsstufen auf das System auswirken.
* Lesen Sie die Details über das Update.

Tabelle 1. Aktualisierungsstufen und Auswirkungen

<table>
  <tr>
    <th>Aktualisierungsstufe</th>
    <th>Auswirkung</th>
  </tr>
  <tr>
    <td>Niedrig</td>
    <td>Dieses Update hat keine Auswirkungen auf Systeme. Sie müssen es nicht während einer geplante Ausfallzeit anwenden.</td>
  </tr>
  <tr>
    <td>Mittel</td>
  <td>Dieses Update kann sich auf einige Systeme auswirken. Es empfiehlt sich, es während einer geplanten Ausfallzeit anzuwenden.</td>
  </tr>
    <tr>
    <td>Bedeutend</td>
  <td>Dieses Update wirkt sich auf einige oder alle Systeme aus. Sie müssen es während einer geplanten Ausfallzeit anwenden.</td>
  </tr>
</table>

## Vorgehensweise zum Anwenden von Updates für IBM Managementkomponenten (V2.1 bis V2.4-Instanzen)
{: #vc_applyingupdates-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, die Sie aktualisieren wollen.
3. Überprüfen Sie auf der Seite **Zusammenfassung**, ob alle Instanzdetails korrekt angezeigt werden. Klicken Sie dann im linken Navigationsfenster auf **Infrastruktur**, um die Details auf der Seite **Infrastruktur** zu prüfen.

   Wenn die Details nicht angezeigt werden, kann dies auf ein Konnektivitätsproblem mit der virtuellen Serverinstanz (VSI) von IBM CloudDriver hinweisen, das aufgrund eines Problems mit einer Firewallregel oder aufgrund eines Netzproblems aufgetreten ist. Lösen Sie das Problem, bevor Sie mit dem nächsten Schritt fortfahren, da das Update andernfalls fehlschlagen könnte.

4. Klicken Sie im linken Navigationsfenster auf **Update und Patch** und klicken Sie auf den Abwärtspfeil, um das IBM Management-Update zu erweitern, das Sie anwenden möchten, und führen Sie anschließend einen der folgenden Schritte aus:
   * Um das Update sofort zu starten, klicken Sie auf das Überlaufmenüsymbol in der Spalte **Aktionen** des Update-Eintrags und anschließend auf **Update jetzt ausführen**.
   * Um ein künftiges Update zu planen, klicken Sie auf das Überlaufmenüsymbol in der Spalte **Aktionen** des Update-Eintrags und anschließend auf **Update planen**. Wählen Sie das Datum, die Uhrzeit und die Zeitzone für den Start des Updates aus. Klicken Sie auf **OK**.
5. Wenn Sie Updates auf Instanzen in Bereitstellungskonfigurationen mit mehreren Standorten anwenden, wird ein Abschnitt namens **Für Update erforderliche Schritte** angezeigt. In diesem Abschnitt werden die Updateoperationen aufgelistet, die für alle Instanzen in der Bereitstellung mit mehreren Standorten erforderlich sind. Sie müssen die Schritte nacheinander ausführen, indem Sie für jeden Schritt auf **Update anwenden** klicken. Vor dem Starten des nächsten Schritts müssen Sie warten, bis der vorherige Schritt abgeschlossen wurde.

## Ergebnisse nach dem Anwenden von Updates für IBM Managementkomponenten
{: #vc_applyingupdates-results}

1. Nachdem Sie ein Update angewendet haben, wird in der Statusliste der Software-Updates ein Eintrag angezeigt, der Aufschluss über den detaillierten Verarbeitungsfortschritt und den Status des Updates gibt. Sobald das Update erfolgreich abgeschlossen wurde, wird in der Liste der installierten Software-Updates ein Eintrag angezeigt.

  Klicken Sie zum Abrufen des aktuellen Status für einen Update-Job auf das Aktualisierungssymbol in der rechten oberen Ecke der Seite.
  {:tip}

2. Details zu den Statuswerten für Updates finden Sie in der folgenden Tabelle.

   Tabelle 2. Details zu den Statuswerten für Updates

    <table>
      <tr>
        <th>Status</th>
        <th>Details</th>
      </tr>
      <tr>
        <td>Verfügbar</td>
        <td>Das Update ist für eine Anwendung verfügbar. Sie können ein verfügbares Update erst dann auswählen, nachdem alle zugehörigen vorherigen Updates angewendet wurden.</td>
      </tr>
      <tr>
        <td>In Bearbeitung</td>
      <td>Der Update-Job wurde initialisiert, ist aber noch nicht beendet. Sie können keine anderen Updates anwenden, bis der aktuelle Update-Job abgeschlossen ist. </td>
      </tr>
        <tr>
        <td>Installiert</td>
      <td>Der Update-Job ist abgeschlossen. Die entsprechende Komponente der VMware-Plattform wurde aktualisiert.</td>
      </tr>
        <tr>
        <td>Fehlgeschlagen</td>
      <td>Der Update-Job ist fehlschlagen. In der Konsole wird ein Fehler für das Fehlschlagen des Updates gemeldet. Überprüfen Sie den Fehler und lösen Sie das gemeldete Problem, bevor Sie das Update erneut anwenden.</td>
      </tr>
          <tr>
        <td>Geplant</td>
      <td>Der Update-Job ist für einen späteren Zeitpunkt geplant. Er wird am geplanten Zeitpunkt automatisch gestartet.</td>
      </tr>
          <tr>
        <td>Unbekannt</td>
      <td>Der Status des Update-Jobs kann nicht abgerufen werden. Bitten Sie den IBM Support um Unterstützung.</td>
      </tr>
    </table>

3. Falls der Updateprozess bei einem bestimmten Schritt fehlschlägt, [wenden Sie sich an den IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support), um Unterstützung zu erhalten. Sie erhalten Hilfe bei der Lösung des Problems und Anweisungen, wie Sie die Updates und Patches von dem Schritt aus ausführen können, der fehlgeschlagen ist.

## Zugehörige Links
{: #vc_applyingupdates-related}

* [Übersicht über vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Upgrade von Lizenzen für vCenter Server-Instanzen durchführen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_upgrade-lic)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
