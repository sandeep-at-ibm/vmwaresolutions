---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrade von NSX-Lizenzen für vCenter Server mit Hybridity Bundle-Instanzen durchführen
{: #vc_hybrid_upgrade-lic}

Sie können für die VMware NSX-Lizenz für Ihre Instanz ein Upgrade auf eine höhere Edition durchführen. Downgrades für Lizenzeditionen werden nicht unterstützt.

## Vorgehensweise zum Durchführen eines Upgrades für Ihre NSX-Lizenz
{: #vc_hybrid_upgrade-lic-nsx}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf die Instanz, für die ein Upgrade der NSX-Lizenz durchgeführt werden soll.
3. Überprüfen Sie auf der Seite **Zusammenfassung**, ob alle Instanzdetails korrekt angezeigt werden. Klicken Sie dann im linken Navigationsfenster auf **Infrastruktur**, um die Details auf der Seite **Infrastruktur** zu prüfen.

   Wenn die Details nicht angezeigt werden, kann dies auf ein Konnektivitätsproblem mit der virtuellen Serverinstanz (VSI) von IBM CloudDriver hinweisen, das aufgrund eines Problems mit einer Firewallregel oder aufgrund eines Netzproblems aufgetreten ist. Lösen Sie das Problem, bevor Sie mit dem nächsten Schritt fortfahren, da das Upgrade andernfalls fehlschlagen könnte.

4. Klicken Sie im linken Navigationsfenster auf **Update und Patch** und dann auf **Upgrade**. Wählen Sie im Fenster für das Upgrade von NSX-Lizenzeditionen ****die Edition aus, auf die das Upgrade durchgeführt werden soll, und klicken Sie dann auf **Upgrade**.

   Die Aktualisierung der Lizenz ersetzt alle vorhandenen NSX-Lizenzen in der Instanz. Zusätzliche Gebühren können bei einer Überschneidung von alten und neuen Lizenzen entstehen, wenn Sie ein Upgrade in der Mitte eines Abrechnungszyklus durchführen. Um zusätzliche Gebühren zu vermeiden, wird empfohlen, die Lizenz am Ende des Abrechnungszyklus zu aktualisieren.
   {:note}

## Zugehörige Links
{: #vc_hybrid_upgrade-lic-related}

* [Übersicht über vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
