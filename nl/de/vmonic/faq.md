---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-16"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Allgemeine häufig gestellte Fragen zu IBM Cloud for VMware Solutions
{: #faq}

Hier finden Sie Antworten auf häufig gestellte Fragen zu {{site.data.keyword.vmwaresolutions_full}}.

## Welche Benutzerkonten benötige ich für IBM Cloud for VMware Solutions?
{: #faq-user-accts}
{: faq}

* **IBMid-Konto**. Dieses Konto ist für den Zugriff auf die {{site.data.keyword.vmwaresolutions_short}}-Konsole erforderlich. Die Konsole ist eine eigenständige und vom {{site.data.keyword.slportal}} getrennte Benutzerschnittstelle. Weitere Informationen finden Sie unter [Einführung](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started).
* **{{site.data.keyword.cloud_notm}}-Konto**. Dieses Konto ist für die Bereitstellung erforderlich. Sie können sich für ein {{site.data.keyword.cloud_notm}}-Konto registrieren, indem Sie eine vorhandene **IBMid** verwenden oder eine neue **IBMid** erstellen.
* **{{site.data.keyword.cloud_notm}}-Infrastrukturkonto**. Dieses Konto wird zur Anmeldung am Kundenportal für die {{site.data.keyword.cloud_notm}}-Infrastruktur verwendet, das weitere Funktionen zur Verwaltung von Infrastrukturprodukten und -services zur Verfügung stellt. Sie erhalten ein {{site.data.keyword.cloud_notm}}-Infrastrukturkonto, indem Sie Ihr **{{site.data.keyword.cloud_notm}}-Konto** auf ein nutzungsabhängiges Konto aktualisieren oder indem Sie Ihr vorhandenes Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur mit Ihrem {{site.data.keyword.cloud_notm}}-Konto verknüpfen. Das {{site.data.keyword.cloud_notm}}-Infrastrukturkonto, das Sie verwenden, muss bestimmte Voraussetzungen erfüllen. Weitere Informationen finden Sie in [Für erforderliche Konten registrieren](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account) und in [Anforderungen für das {{site.data.keyword.cloud_notm}}-Infrastrukturkonto](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).

## Wie kann ich meine Berechtigungsnachweise für die IBM Cloud-Infrastruktur zur IBM Cloud for VMware Solutions-Konsole zuordnen?
{: #faq-associate-credentials}
{: faq}

Wenn Sie Ihre Instanz erstmalig bestellen, befolgen Sie die Anweisungen auf der Seite **Einstellungen** in der Konsole, um den Benutzernamen und den API-Schlüssel für die {{site.data.keyword.cloud_notm}}-Infrastruktur im {{site.data.keyword.slportal}} zu suchen und zu kopieren. Die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur werden nach der ersten Bestellung in der Konsole von {{site.data.keyword.vmwaresolutions_short}} gespeichert. Anschließende Bestellungen verwenden automatisch die gespeicherten Berechtigungsnachweise.

## Wie wird meine Nutzung der virtuellen VMware-Plattform abgerechnet?
{: #faq-billing}
{: faq}

Alle Kosten für die physische und virtuelle Infrastruktur sowie die aus der Instanz resultierenden Lizenzen werden Ihrem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt. Wenn Sie eine Instanz bestellen, müssen Sie über ein {{site.data.keyword.cloud_notm}}-Konto verfügen und den {{site.data.keyword.slapi_short}}-Schlüssel angeben, der dem Konto zugeordnet ist.

## Was sind die Unterschiede zwischen einer vCenter Server-Instanz und einem VMware vSphere-Cluster?
{: #faq-vcs-cf-vss}
{: faq}

Alle Instanztypen bieten Bereitstellungsoptionen für virtuelle VMware-Umgebungen. Der Unterschied liegt dabei im Maß der Anpassungsfähigkeit und Automatisierung.

* Wenn Sie eine VMware vCenter Server-Instanz bestellen, stellen Sie eine virtuelle VMware-Umgebung mit angepassten Rechen-, Speicher- und Netzressourcen bereit. Weitere Informationen zu den bereitgestellten Komponenten finden Sie unter [Technische Spezifikationen für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs).
* Wenn Sie einen VMware vSphere-Cluster bestellen, erhalten Sie hinsichtlich des Designs und Aufbaus Ihrer gehosteten VMware-Umgebung beim Integrieren der VMware-kompatiblen Hardware ein Maximum an Flexibilität. {{site.data.keyword.cloud_notm}} automatisiert jedoch weder Installation noch Konfiguration oder Inbetriebnahme der optionalen VMware-Komponenten für den VMware vSphere-Cluster.
* Die Funktionen, die für vCenter Server-Instanzen und vSphere-Cluster unterstützt werden, sind unterschiedlich. Weitere Informationen finden Sie im [Angebotsvergleichsdiagramm](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart).

## Was beinhaltet eine vCenter Server-Instanz?
{: #faq-vcs}
{: faq}

Weitere Informationen finden Sie unter [Technische Spezifikationen für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs).

## Was beinhaltet ein vSphere-Cluster?
{: #faq-vss}
{: faq}

Weitere Informationen enthält der Abschnitt [Komponenten von VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview).

## Ist eine vCenter Server-Instanz mit zwei Knoten hoch verfügbar?
{: #is-a-two-node-vcenter-server-instance-highly-available}
{: faq}

Es wird empfohlen, Produktionsworkloads in Umgebungen bereitzustellen, in denen mindestens drei Knoten vorhanden sind.

VMware vSphere DRS (Distributed Resource Scheduler) und VMware HA (High Availability) sind standardmäßig aktiviert. In der Praxis hat es sich bei VMware jedoch bewährt, für jeden der drei NSX-Controller einen separaten Knoten zu verwenden.

In der Minimalbereitstellung mit zwei Knoten befindet sich auf einem Knoten einer der NSX-Controller, der andere Knoten enthält zwei NSX-Controller. Falls der Knoten mit den zwei NSX-Controllern ausfällt, werden NSX-Controlleroperationen in den Lesezugriffsmodus versetzt und für neue virtuelle Maschinen (VMs) oder vMotion-VMs könnten Netzprobleme auftreten.

Wenn zu einem Cluster mit zwei Knoten ein dritter Knoten hinzugefügt wird, verteilt vCenter Server die drei NSX-Controller automatisch gleichmäßig auf die drei Knoten und erstellt eine hoch verfügbare Umgebung.

## Kann ich eine HA-Konfiguration für VMware vCenter 6.5 einrichten?
{: #faq-ha}
{: faq}

Nein, dies ist nicht zu empfehlen. Es könnte zu Störungen bei den {{site.data.keyword.vmwaresolutions_short}}-Funktionen kommen.

## Können Cluster umbenannt werden?
{: #faq-rename-cluster}
{: faq}

Bei einer neuen vCenter-Serverinstanz hat der erste Cluster, der während der Implementierung erstellt wird, den Standardnamen **cluster1**. Sie können den Standardcluster in VMware vSphere Client umbenennen. Wenn Sie einen Cluster zu einer vCenter Server-Instanz hinzufügen, können Sie den gewünschten Namen in der {{site.data.keyword.vmwaresolutions_short}}-Konsole angeben.

## Wie werden Patches verwaltet?
{: #faq-patches}
{: faq}

IBM stellt fortlaufend Updates für den IBM Code bereit, indem die virtuellen Serverinstanzen (VSI) für IBM CloudDriver bedarfsgesteuert bereitgestellt werden. Für Add-on-Services wie Zerto on {{site.data.keyword.cloud_notm}} oder Veeam on {{site.data.keyword.cloud_notm}} werden von IBM keine kontinuierlichen Updates bereitgestellt. Für den Abruf und die Installation solcher Updates müssen Sie selbst sorgen.

Für in Version 2.1 bereitgestellte oder darauf aktualisierte VMware vCenter Server-Instanzen werden als Patches für neu bereitgestellte ESXi-Server und -Cluster aktuelle, jedoch nicht zwingend die neuesten ESXi-Updates von VMware verwendet.

Für alle anderen Updates von VMware-Komponenten sind Sie selbst verantwortlich; in diesem Zusammenhang müssen Sie auch sicherstellen, dass neu bereitgestellte ESXi-Server und Cluster über die notwendigen neuesten Updates verfügen.
{:important}

Bei Instanzen, die in V2.0 oder höher bereitgestellt wurden, ist VMware Update Manager (VUM) in Ihre vCenter Server-Instanz integriert. Sie können VUM auf Wunsch so konfigurieren, dass ESXi-Updates von VMware heruntergeladen werden.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [VMware Support](https://www.vmware.com/support.html)
* [Updates auf vCenter Server-Instanzen anwenden](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates)
* [Updates auf vCenter Server with Hybridity Bundle-Instanzen anwenden](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_applyingupdates)

## Stellt das NSX Edge für Management-Services ein Sicherheitsrisiko dar?
{: #faq-mgmt-nsx}
{: faq}

Wenngleich sich VMware NSX Edge für Verwaltungsservices in einem öffentlichen Teilnetz befindet, werden folgende Sicherheitsmaßnahmen ergriffen, um sicherzustellen, dass es kein Sicherheitsrisiko darstellt:
*  Die NSX Edge-Firewall ist so konfiguriert, dass nur der abgehende HTTPS-Datenverkehr (TCP-Port 443) zugelassen wird, der von den virtuellen Maschinen für das Management eingeleitet wird.
*  Durch die Verwendung von SNAT (Source Network Address Translation) sind private IP-Adressen außerhalb des privaten Netzes nicht sichtbar.
*  Der Fernzugriff der NSX Edge-Appliance für die Management-Services ist inaktiviert.
*  Die Kennwörter für den Zugriff auf das NSX Edge für Management-Services aus dem privaten Netz sind randomisiert und verschlüsselt.

## Stellt das vom Kunden verwaltete NSX Edge ein Sicherheitsrisiko dar?
{: #faq-customer-nsx}
{: faq}

Das vom Kunden verwaltete NSX Edge befindet sich zwar im öffentlichen VLAN, aber durch entsprechende Sicherheitsmaßnahmen wird gewährleistet, dass dies kein Sicherheitsrisiko verursacht. Die folgenden Sicherheitsmaßnahmen werden angewendet:
*  Es ist eine Firewall-Regel vorhanden, die nur den abgehenden Datenverkehr aus dem privaten Teilnetzbereich von IP-Adressen zulässt.
*  Durch eine (standardmäßig inaktivierte) SNAT-Regel werden alle IP-Adressen aus dem privaten Teilnetz in eine einzige IP-Adresse für das öffentliche Teilnetz umgesetzt.
*  Der Fernzugriff der Appliance für das vom Kunden verwaltete NSX Edge ist inaktiviert.
*  Die Kennwörter für den Zugriff auf das vom Kunden verwaltete NSX Edge aus dem privaten Netz sind randomisiert und verschlüsselt.

## Wie wähle ich die Rechenzentren für meine Instanzen aus?
{: #faq-data-center}
{: faq}

Die Instanzbereitstellungen stellen strenge Anforderungen an die physische Infrastruktur, die bei den verschiedenen {{site.data.keyword.CloudDataCents_notm}} variieren. Wenn Sie Ihre Instanzen bestellen, werden die verfügbaren Rechenzentren innerhalb von Regionen aufgelistet und Sie können das gewünschte Rechenzentrum in der Liste auswählen.

Weitere Informationen enthalten die Abschnitte zur _Verfügbarkeit des IBM Cloud-Rechenzentrums_ unter:
* [Voraussetzungen und Planung für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Voraussetzungen und Planung für vCenter Server with Hybridity Bundle-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Voraussetzungen und Planung für VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)
* [Voraussetzungen und Planung für NetApp ONTAP Select-Instanzen](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning)

## Wie lange dauert es, bis meine Instanz bereitgestellt wird?
{: #faq-deploy}
{: faq}

Sie können den Status der Instanzbereitstellung überprüfen, indem Sie den Bereitstellungsverlauf auf der Seite mit den Instanzdetails in der {{site.data.keyword.vmwaresolutions_short}}-Konsole prüfen.

## Verwendet VMware vSphere on IBM Cloud automatisierte Prozeduren, um den VMware-Stack zu installieren, zu konfigurieren und zu aktivieren?
{: #faq-vss-automation}
{: faq}

Nein. VMware vSphere on {{site.data.keyword.cloud_notm}} verwendet nicht die erweiterte Automatisierung der vCenter Server-Plattform. Basierend auf Ihrer Bestellung stellt die Plattform optionale VMware-Lizenzen, ESXi-Server und optional ein HA-Paar von physischen FortiGate-Firewalls bereit. Wenn ein neuer Cluster erstellt wird, werden auch drei neue VLANs bereitgestellt: ein öffentliches VLAN und zwei private VLANs.

VMware ESXi wird automatisch auf jedem Bare Metal Server installiert. Für die Installation aller weiteren VMware-Komponenten wie vCenter Server oder NSX sind jedoch Sie selbst zuständig. vSphere on {{site.data.keyword.cloud_notm}} stellt zwar sicher, dass basierend auf den ausgewählten VMware-Komponenten auch VMware-kompatible Hardware bestellt wird, aber es gibt keine Automatisierung für die Konfiguration und Inbetriebnahme der VMware-Umgebung. Entwurf und Architekturgestaltung für die von IBM gehostete Umgebung liegen in Ihrer Zuständigkeit.

## Wie kann ich eine Liste aller Benachrichtigungen anzeigen?
{: #faq-notification}
{: faq}

Das vollständige Benachrichtigungsprotokoll können Sie anzeigen, indem Sie im linken Navigationsfenster auf **Benachrichtigungen** klicken.

## Wie verhalte ich mich, wenn ein Problem mit IBM Cloud for VMware Solutions auftritt?
{: #faq-support}
{: faq}

Falls Sie bei der Verwendung von {{site.data.keyword.vmwaresolutions_short}} Hilfe benötigen, setzen Sie sich über einen der Unterstützungskanäle mit dem IBM Support in Verbindung. Weitere Informationen finden Sie unter [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).

## Zugehörige Links
{: #faq-related}

* [Benachrichtigungen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Auf die Konsole zugreifen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-loginmethod)
* [Benutzerkonten und -einstellungen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
