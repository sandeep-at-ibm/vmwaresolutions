---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrade von Lizenzen für vCenter Server-Instanzen durchführen
{: #vc_upgrade-lic}

Sie können für Ihre VMware vCenter Server-Instanzen nur ein Upgrade auf vCenter Server with Hybridity Bundle durchführen, wenn Ihre Instanz mindestens die Version 2.3 aufweist.

IBM Business Partner-Benutzer haben nicht die Möglichkeit, ein Upgrade auf Hybridity Bundle durchzuführen.
{:note}

## Vor dem Upgrade Ihrer Lizenz auf Hybridity Bundle
{: #vc_upgrade-lic-upgrade-prereq}

Sehen Sie sich die folgenden Aktionen an, die beim Upgrade auf Hybridity Bundle ausgeführt werden:

* Wenn für Ihre vCenter Server-Instanz VMware NSX Base Edition installiert ist, wird für Ihre NSX-Lizenz automatisch ein Upgrade auf NSX Advanced Edition durchgeführt.
* Wenn Ihre vCenter Server-Instanz über NFS-Speicher verfügt, fallen für Sie für den VMware vSAN-Speicher keine Gebühren an. Es entstehen jedoch Gebühren für die vSAN-Lizenz, die im Lieferumfang von Hybridity Bundle enthalten ist.

## Vorgehensweise beim Upgrade auf Hybridity Bundle (Instanzen der Version 2.3 oder höher)
{: #vc_upgrade-lic-procedure-upgrade-to-hybridity}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die Sie ein Upgrade auf Hybridity Bundle durchführen wollen.
3. Überprüfen Sie auf der Seite **Zusammenfassung**, ob alle Instanzdetails korrekt angezeigt werden. Klicken Sie dann im linken Navigationsfenster auf **Infrastruktur**, um die Details auf der Seite **Infrastruktur** zu prüfen.

   Wenn die Details nicht angezeigt werden, kann dies auf ein Konnektivitätsproblem mit der IBM CloudDriver-VSI hinweisen, das aufgrund eines Problems mit einer Firewallregel oder aufgrund eines anderen Netzproblems aufgetreten ist. Lösen Sie das Problem, bevor Sie mit dem nächsten Schritt fortfahren, da das Upgrade andernfalls fehlschlagen könnte.

4. Klicken Sie im linken Navigationsfenster auf **Update und Patch**.
5. Klicken Sie in der Tabelle **Aktualisierungen der Lizenz** in der Spalte **Aktion** auf **Upgrade**, um das Upgrade der Hybridity Bundle-Lizenz anzuwenden. Überprüfen Sie die geschätzten Kosten und klicken Sie auf **Upgrade**.
6. Optional können Sie den Service "VMware HCX on {{site.data.keyword.cloud_notm}}" bereitstellen. Wenn Hybridity Bundle in der Tabelle **Aktualisierungen der Lizenz** aktiviert ist, führen Sie die folgenden Schritte aus:
  1. Klicken Sie in der Tabelle **Aktualisierungen der Lizenz** in der Spalte **Aktion** auf **HCX on {{site.data.keyword.cloud_notm}} bereitstellen**.
  2. Blättern Sie zur Karte **HCX on {{site.data.keyword.cloud_notm}}** und klicken Sie dann auf **Service auswählen**.
  3. Blättern Sie abwärts und geben Sie die erforderlichen Einstellungen für den Service an. Klicken Sie dann auf **Weiter**.
  4. Überprüfen Sie die Bedingungen, die für den Service gelten, überprüfen Sie die geschätzten Kosten und klicken Sie dann auf **Bestellung aufgeben**.

## Vorgehensweise zum Durchführen eines Upgrades für Ihre NSX-Lizenz (Instanzen von Version 2.1 oder höher)
{: #vc_upgrade-lic-nsx}

Dieses Verfahren gilt für Instanzen, die in V2.1 oder höher bereitgestellt werden. Bei Instanzen, die in V2.0 und früheren Versionen bereitgestellt wurden, müssen Sie die Upgrades für NSX-Lizenzen manuell durchführen.

Sie können ein Upgrade der NSX-Lizenz für Ihre Instanz auf eine spätere Edition durchführen. Downgrades für Lizenzeditionen werden nicht unterstützt.

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die ein Upgrade der NSX-Lizenz durchgeführt werden soll.
3. Überprüfen Sie auf der Seite **Zusammenfassung**, ob alle Instanzdetails korrekt angezeigt werden. Klicken Sie dann im linken Navigationsfenster auf **Infrastruktur**, um die Details auf der Seite **Infrastruktur** zu prüfen.

   Wenn die Details nicht angezeigt werden, kann dies auf ein Konnektivitätsproblem mit der virtuellen Serverinstanz (VSI) von IBM CloudDriver hinweisen, das aufgrund eines Problems mit einer Firewallregel oder aufgrund eines Netzproblems aufgetreten ist. Lösen Sie das Problem, bevor Sie mit dem nächsten Schritt fortfahren, da das Upgrade andernfalls fehlschlagen könnte.

4. Klicken Sie im linken Navigationsfenster auf **Update und Patch** und dann auf **Upgrade**. Wählen Sie im Fenster für das Upgrade von NSX-Lizenzeditionen ****die Edition aus, auf die das Upgrade durchgeführt werden soll, und klicken Sie dann auf **Upgrade**.

   Die Aktualisierung der Lizenz ersetzt alle vorhandenen NSX-Lizenzen in der Instanz. Zusätzliche Gebühren können bei einer Überschneidung von alten und neuen Lizenzen entstehen, wenn Sie ein Upgrade in der Mitte eines Abrechnungszyklus durchführen. Um zusätzliche Gebühren zu vermeiden, wird empfohlen, die Lizenz am Ende des Abrechnungszyklus zu aktualisieren.
   {:note}

## Zugehörige Links
{: #vc_upgrade-lic-related}

* [Übersicht über vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
