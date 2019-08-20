---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-24"

keywords: NSX license upgrade, upgrade license hybridity, hybridity license

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Upgrade von Lizenzen für vCenter Server-Instanzen durchführen
{: #vc_upgrade-lic}

Sie können ein Upgrade für Ihre NSX-Lizenz (Instanzen von Version 2.1 oder höher) durchführen.

## Vorgehensweise zum Durchführen eines Upgrades für Ihre NSX-Lizenz
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

* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
