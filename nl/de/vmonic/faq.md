---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# Allgemeine häufig gestellte Fragen zu IBM Cloud for VMware Solutions

Hier finden Sie Antworten auf häufig gestellte Fragen zu {{site.data.keyword.vmwaresolutions_full}}.

## Welche Benutzerkonten benötige ich für IBM Cloud for VMware Solutions?

* **IBMid-Konto**. Dieses Konto ist für den Zugriff auf die {{site.data.keyword.vmwaresolutions_short}}-Konsole erforderlich. Die Konsole ist eine eigenständige und vom {{site.data.keyword.slportal_full}} getrennte Benutzerschnittstelle. Weitere Informationen finden Sie unter [Einführung](../index.html).
* **{{site.data.keyword.cloud_notm}}-Konto**. Dieses Konto ist für die Bereitstellung erforderlich. Sie können sich für ein {{site.data.keyword.cloud_notm}}-Konto registrieren, indem Sie ein Upgrade Ihres **IBMid-Kontos** auf ein nutzungsabhängiges Konto durchführen. Das {{site.data.keyword.cloud_notm}}-Konto, das Sie verwenden, muss bestimmte Voraussetzungen erfüllen. Weitere Informationen finden Sie unter [Für ein {{site.data.keyword.cloud_notm}}-Konto registrieren](signing_softlayer_account.html) und [Voraussetzungen für {{site.data.keyword.cloud_notm}}-Konto](slaccountrequirement.html).

## Wie kann ich meine Berechtigungsnachweise für die IBM Cloud-Infrastruktur zur IBM Cloud for VMware Solutions-Konsole zuordnen?

Wenn Sie Ihre Instanz erstmalig bestellen, befolgen Sie die Anweisungen auf der Seite mit den Berechtigungsnachweisen für die {{site.data.keyword.cloud_notm}}-Infrastruktur und kopieren Sie den {{site.data.keyword.cloud_notm}}-Benutzernamen sowie den API-Schlüssel aus dem {{site.data.keyword.slportal}}. Die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur werden nach der ersten Bestellung in der {{site.data.keyword.vmwaresolutions_short}}-Konsole gespeichert. Anschließende Bestellungen verwenden automatisch die gespeicherten Berechtigungsnachweise.

## Wie wird meine Nutzung der virtuellen VMware-Plattform abgerechnet?

Alle Kosten für die physische und virtuelle Infrastruktur sowie die aus der Instanz resultierenden Lizenzen werden Ihrem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt. Wenn Sie eine Instanz bestellen, müssen Sie über ein {{site.data.keyword.cloud_notm}}-Konto verfügen und den {{site.data.keyword.slapi_short}}-Schlüssel angeben, der dem Konto zugeordnet ist.

## Was sind die Unterschiede zwischen einer vCenter Server-Instanz, einer Cloud Foundation-Instanz und einem VMware vSphere-Cluster?

Alle Instanztypen bieten Bereitstellungsoptionen für virtuelle VMware-Umgebungen. Der Unterschied liegt dabei im Maß der Anpassungsfähigkeit und Automatisierung.

* Wenn Sie eine VMware vCenter Server-Instanz bestellen, stellen Sie eine virtuelle VMware-Umgebung mit angepassten Berechnungs-, Speicher- und Netzressourcen bereit. Weitere Informationen zu den bereitgestellten Komponenten finden Sie im Abschnitt _Technische Spezifikationen für vCenter Server_ im [Überblick zu vCenter Server](../vcenter/vc_vcenterserveroverview.html).
* Wenn Sie eine VMware Cloud Foundation-Instanz bestellen, stellen Sie eine einheitliche Plattform für ein softwaredefiniertes Rechenzentrum (Software-defined Data Center, SDDC) bereit. Weitere Informationen zu den bereitgestellten Komponenten finden Sie unter [Komponenten der Cloud Foundation-Instanz](../sddc/sd_cloudfoundationoverview.html#cloud-foundation-instance-components).
* Wenn Sie einen VMware vSphere-Cluster bestellen, erhalten Sie hinsichtlich des Designs und Aufbaus Ihrer gehosteteten VMware-Umgebung maximale Flexibilität beim Integrieren der VMware-kompatiblen Hardware. {{site.data.keyword.cloud_notm}} automatisiert jedoch weder Installation noch Konfiguration oder Inbetriebnahme der optionalen VMware-Komponenten für den VMware vSphere-Cluster.
* Die Funktionen, die für vCenter Server-Instanzen, Cloud Foundation-Instanzen und vSphere-Cluster unterstützt werden, sind unterschiedlich. Weitere Informationen finden Sie im [Angebotsvergleichsdiagramm](inst_comp_chart.html).

## Was beinhaltet eine vCenter Server-Instanz?

Weitere Informationen finden Sie im Abschnitt _Technische Spezifikationen für vCenter Server_ im [Überblick zu vCenter Server](../vcenter/vc_vcenterserveroverview.html).

## Was beinhaltet eine Cloud Foundation-Instanz?

Entsprechende Informationen finden Sie im Abschnitt [Komponenten der Cloud Foundation-Instanz](../sddc/sd_cloudfoundationoverview.html).

## Was beinhaltet ein vSphere-Cluster?
Weitere Informationen enthält der Abschnitt [Komponenten für VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html).

## Ist eine vCenter Server-Instanz mit zwei Knoten hoch verfügbar?

Es wird dringend empfohlen, Produktionsworkloads in Umgebungen bereitzustellen, in denen mindestens drei Knoten vorhanden sind.

VMware vSphere DRS (Distributed Resource Scheduler) und VMware HA (High Availability) sind zwar standardmäßig aktiviert, aber die bewährten Verfahren für VMware raten dazu, für jeden der drei NSX-Controller einen separaten Knoten zu verwenden.

In der Minimalbereitstellung mit zwei Knoten befindet sich auf einem Knoten einer der NSX-Controller, der andere Knoten enthält zwei NSX-Controller. Falls der Knoten mit den zwei NSX-Controllern ausfällt, werden NSX-Controlleroperationen in den Lesezugriffsmodus versetzt und für neue virtuelle Maschinen (VMs) oder vMotion-VMs könnten Netzprobleme auftreten.

Wenn zu einem Cluster mit zwei Knoten ein dritter Knoten hinzugefügt wird, verteilt vCenter Server die drei NSX-Controller automatisch gleichmäßig auf die drei Knoten und erstellt eine hoch verfügbare Umgebung.

## Kann ich eine HA-Konfiguration für VMware vCenter 6.5 einrichten?

Nein, dies ist nicht zu empfehlen. Es könnte zu Störungen bei den {{site.data.keyword.vmwaresolutions_short}}-Funktionen kommen.

## Können Cluster umbenannt werden?

Bei vCenter Server-Instanzen hat der erste Cluster, der während der Bereitstellung erstellt wird, den Standardnamen **cluster1**. Sie können den Standardcluster in VMware vSphere Client umbenennen. Wenn Sie einen neuen Cluster zu einer vCenter Server-Instanz hinzufügen, können Sie den gewünschten Namen in der {{site.data.keyword.vmwaresolutions_short}}-Konsole angeben.

**Hinweis**: Bei Cloud Foundation-Instanzen kann der Standardclustername nicht geändert werden.

##Wie werden Patches verwaltet?

IBM stellt kontinuierliche Updates für die IBM CloudDriver-Komponente bereit, die in der {{site.data.keyword.cloud_notm}} for VMware Solutions-Konsole verfügbar gemacht werden. Für Add-on-Services wie Zerto on {{site.data.keyword.cloud_notm}} oder Veeam on {{site.data.keyword.cloud_notm}} werden von IBM keine kontinuierlichen Updates bereitgestellt. Für den Abruf und die Installation solcher Updates müssen Sie selbst sorgen.

VMware-Updates werden abhängig vom Typ der bereitgestellten VMware-Instanz unterschiedlich angewendet:

* Bei VMware Cloud Foundation-Instanzen werden Updates für vSphere ESXi, NSX, vCenter, Platform Services Controller und SDDC Manager über die {{site.data.keyword.vmwaresolutions_short}}-Konsole zur Verfügung gestellt.
* Bei VMware vCenter Server-Instanzen gilt Folgendes:
  * Bei Instanzen, die in V2.1 oder höher bereitgestellt wurden bzw. für die ein Upgrade auf eine entsprechende Version durchgeführt wurde, werden als Patches für neu bereitgestellte ESXi-Server und Cluster aktuelle, jedoch nicht zwingend die neuesten ESXi-Updates von VMware verwendet.
  * Für alle anderen Updates von VMware-Komponenten sind Sie selbst verantwortlich; in diesem Zusammenhang müssen Sie auch gewährleisten, dass neu bereitgestellte ESXi-Server und Cluster über die notwendigen neuesten Updates verfügen.
  * Bei Instanzen, die in V2.0 oder höher bereitgestellt wurden, ist VMware Update Manager (VUM) in Ihre vCenter Server-Instanz integriert. Sie können VUM auf Wunsch so konfigurieren, dass ESXi-Updates von VMware huerntergeladen werden.

Weitere Informationen enthalten die folgenden Abschnitte:
* [VMware Support](https://www.vmware.com/support.html)
* [Updates auf vCenter Server-Instanzen anwenden](../vcenter/vc_applyingupdates.html)
* [Updates auf Cloud Foundation-Instanzen anwenden](../sddc/sd_applyingupdates.html)

## Stellt das NSX Edge für Management-Services ein Sicherheitsrisiko dar?

VMware NSX Edge für Management-Services befindet sich zwar in einem öffentlichen Teilnetz, aber die bestehenden Sicherheitsmaßnahmen gewährleisten, dass dies kein Sicherheitsrisiko verursacht. Es handelt sich um folgende Maßnahmen:
*  Die NSX Edge-Firewall ist so konfiguriert, dass nur der abgehende HTTPS-Datenverkehr (TCP-Port 443) zugelassen wird, der von den virtuellen Maschinen für das Management eingeleitet wird.
*  Durch die Verwendung von SNAT (Source Network Address Translation) sind private IP-Adressen außerhalb des privaten Netzes nicht sichtbar.
*  Der Fernzugriff der NSX Edge-Appliance für die Management-Services ist inaktiviert.
*  Die Kennwörter für den Zugriff auf das NSX Edge für Management-Services aus dem privaten Netz sind randomisiert und verschlüsselt.

## Stellt das vom Kunden verwaltete NSX Edge ein Sicherheitsrisiko dar?

Das vom Kunden verwaltete NSX Edge befindet sich zwar im öffentlichen VLAN, aber die bestehenden Sicherheitsmaßnahmen gewährleisten, dass dies kein Sicherheitsrisiko verursacht. Es handelt sich um folgende Maßnahmen:
*  Es ist eine Firewall-Regel vorhanden, die nur den abgehenden Datenverkehr aus dem privaten Teilnetzbereich von IP-Adressen zulässt.
*  Durch eine (standardmäßig inaktivierte) SNAT-Regel werden alle IIP-Adressen aus dem privaten Teilnetz in eine einzige IP-Adresse für das öffentliche Teilnetz umgesetzt.
*  Der Fernzugriff der Appliance für das vom Kunden verwaltete NSX Edge ist inaktiviert.
*  Die Kennwörter für den Zugriff auf das vom Kunden verwaltete NSX Edge aus dem privaten Netz sind randomisiert und verschlüsselt.

## Wie wähle ich die Rechenzentren für meine Instanzen aus?

Die Instanzbereitstellungen stellen strenge Anforderungen an die physische Infrastruktur, die bei den verschiedenen {{site.data.keyword.CloudDataCents_notm}} variieren. Wenn Sie Ihre Instanzen bestellen, werden die verfügbaren Rechenzentren innerhalb von Regionen aufgelistet und Sie können das gewünschte Rechenzentrum in der Liste auswählen.

Weitere Informationen enthalten die Abschnitte zur _Verfügbarkeit des IBM Cloud-Rechenzentrums_ unter:
* [Voraussetzungen und Planung für vCenter Server-Instanzen](../vcenter/vc_planning.html)
* [Voraussetzungen und Planung für vCenter Server with Hybridity Bundle-Instanzen](../vcenter/vc_hybrid_planning.html)
* [Voraussetzungen und Planung für Cloud Foundation-Instanzen](../sddc/sd_planning.html)
* [Voraussetzungen und Planung für VMware vSphere on IBM Cloud](../vsphere/vs_planning.html)
* [Voraussetzungen und Planung für NetApp ONTAP Select-Instanzen](../netapp/np_planning.html)
* [Voraussetzungen und Planung für VMware Federal-Instanzen](../vcenter/vc_fed_planning.html)

## Wie lange dauert es, bis meine Instanz bereitgestellt wird?

Sie können den Status der Instanzbereitstellung überprüfen, indem Sie den Bereitstellungsverlauf auf der Seite mit den Instanzdetails in der {{site.data.keyword.vmwaresolutions_short}}-Konsole prüfen.

## Verwendet VMware vSphere on IBM Cloud automatisierte Prozeduren, um den VMware-Stack zu installieren, zu konfigurieren und zu aktivieren?

Nein. VMware vSphere on {{site.data.keyword.cloud_notm}} nutzt nicht die bei Cloud Foundation- und vCenter Server-Plattformen verfügbare erweiterte Automatisierung. Basierend auf Ihrer Bestellung stellt die Plattform optionale VMware-Lizenzen, ESXi-Server und optional ein HA-Paar von physischen FortiGate-Firewalls bereit. Wenn ein neuer Cluster erstellt wird, werden auch drei neue VLANs (ein öffentliches und zwei private) bereitgestellt.

VMware ESXi wird automatisch auf jedem Bare Metal Server installiert. Für die Installation aller weiteren VMware-Komponenten wie vCenter Server oder NSX sind jedoch Sie selbst zuständig. vSphere on {{site.data.keyword.cloud_notm}} stellt zwar sicher, dass basierend auf den ausgewählten VMware-Komponenten auch VMware-kompatible Hardware bestellt wird, aber es gibt keine Automatisierung für die Konfiguration und Inbetriebnahme der VMware-Umgebung. Entwurf und Architekturgestaltung für die von IBM gehostete Umgebung liegen in Ihrer Zuständigkeit.

## Wie kann ich eine Liste aller Benachrichtigungen anzeigen?

Das vollständige Benachrichtigungsprotokoll können Sie anzeigen, indem Sie im linken Navigationsfenster auf **Benachrichtigungen** klicken.

## Wie verhalte ich mich, wenn ein Problem mit IBM Cloud for VMware Solutions auftritt?

Falls Sie bei der Verwendung von {{site.data.keyword.vmwaresolutions_short}} Hilfe benötigen, setzen Sie sich über einen der Unterstützungskanäle mit dem IBM Support in Verbindung. Weitere Informationen finden Sie unter [Kontaktaufnahme mit dem IBM Support](trbl_support.html).

### Zugehörige Links

* [Benachrichtigungen](notifications.html)
* [Cloud Foundation-Instanzen](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server-Instanzen](../vcenter/vc_vcenterserveroverview.html)
* [Auf die Konsole zugreifen](loginmethod.html)
* [Benutzerkonten und -einstellungen](useraccount.html)
