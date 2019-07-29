---

copyright:

  years:  2016, 2017

lastupdated: "2017-05-22"

subcollection: vmware-solutions


---

# Releaseinformationen für V1.6
{: #relnotes_v16}

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Updates für VMware Cloud Foundation-Instanzen
{: #relnotes_v16-vcf}

Die folgenden Komponenten sind neu verfügbar oder wurden aktualisiert:

*  SDDC Manager 2.2.1
*  IBM Managementkomponenten V1.6
*  Neue Hardwarespezifikationen: **S (Klein)** oder **Standard**, abhängig von Ihren Anforderungen.
*  Neue verfügbare Rechenzentren für die Bereitstellung: **HKG02 - Hongkong**, **OSL01 - Oslo**, **SEO01 - Seoul**, **SNG01 - Singapur** und **SYD04 - Sydney**.

## Updates für VMware vCenter Server-Instanzen
{: #relnotes_v16-vcs}

### Hardwareerweiterungen für vCenter Server-Instanzen
{: #relnotes_v16-hw-vcs}

Ab dem Release V1.6 sind mehrere Erweiterungen für Ihre vCenter Server-Instanzen verfügbar.

*  Vollständige Implementierung der Spezifikation von V2.0 für das vCenter Server-Angebot.
*  Neue Hardwarespezifikationen: **S (Klein)**, **M (Mittel)** oder **L (Groß)**, abhängig von Ihren Anforderungen.
*  Neue verfügbare Rechenzentren für die Bereitstellung: **HKG02 - Hongkong**, **OSL01 - Oslo**, **SEO01 - Seoul**, **SNG01 - Singapur** und **SYD04 - Sydney**.
*  In Ihrer Instanzbestellung sind mindestens zwei ESXi-Server mit VMware vSphere DRS (Distributed Resource Scheduler) und VMware HA (High Availability) standardmäßig aktiviert.
*  Bei der Instanzbestellung können bis zu sieben gemeinsam genutzte NFS-Dateiressourcen hinzugefügt werden. Die Managementkomponenten (vCenter, PSC, NSX-Manager und -Controller, CloudDriver) werden nun zur Hochverfügbarkeit in einer gemeinsam genutzten NFS-Dateiressource ausgeführt.
*  Das vom Kunden verwaltete VMware NSX Edge Services Gateway wird automatisch bereitgestellt und konfiguriert.

Aufgrund dieser Änderungen können Sie die vorhandenen vCenter Server-Instanzen im aktuellen Release nicht im vorliegenden Zustand verwenden oder ein Upgrade durchführen. vCenter Server-Instanzen aus älteren Releases als V1.6 sind jedoch in der {{site.data.keyword.vmwaresolutions_short}}-Konsole weiterhin im Lesezugriffsmodus sichtbar. Solche Instanzen sind in der Benutzerschnittstelle durch ein Warnsymbol als **Veraltet** gekennzeichnet.

Für die vCenter Server-Instanzen aus einem Release vor V1.6 sind die folgenden Aktionen verfügbar:

*  Sie können die Informationen auf der Seite mit den Instanzdetails anzeigen. Die in den Instanzeigenschaften angezeigten Informationen geben die Daten gemäß dem Release V1.6 wieder und werden nicht mehr aktualisiert.
*  Sie können VMware vSphere Web Client öffnen und die Instanz in vCenter verwenden.
*  Sie können die Instanz löschen.

Alle anderen Aktionen sind für Instanzen aus Releases vor V1.6 nicht mehr verfügbar.

### Netzbetriebserweiterungen für vCenter Server-Instanzen
{: #relnotes_v16-network-vcs}

*  1 öffentliches Teilnetz mit 16 IP-Adressen im öffentlichen VLAN wird für Sie bestellt, um den Zugriff Ihrer VMs (virtuellen Maschinen) auf das Internet zu ermöglichen.
*  1 privates Teilnetz mit 64 IP-Adressen im privaten VLAN wird für Sie bestellt, um den Zugriff Ihrer VMs auf das interne SoftLayer®-Netz zu ermöglichen.
*  NSX-Controller werden mit Anti-Affinitätsregeln bereitgestellt und in einer Bereitstellungskonfiguration mit drei Knoten auf separaten ESXi-Servern ausgeführt.
*  Neues VMware NSX Edge Services Gateway für die Nutzung durch den Kunden.

   Als Bestandteil von neu bestellten vCenter Server-Instanzen wird nun ein zusätzliches NSX Edge Services Gateway (ESG) bereitgestellt.

   Dieses ESG wird zur Verwendung mit Ihren eigenen VMs für die Kommunikation zwischen den privaten und öffentlichen Teilnetzen bereitgestellt, die in Ihrem
   Namen bestellt werden und enthält zwei Schnittstellen. Eine Schnittstelle ist mit den virtualisierten VXLANs verbunden, die Ihren VMs zugeordnet sind, und die
   andere Schnittstelle ist mit dem öffentlichen VLAN verbunden. Außerdem sind die folgenden Einstellungen konfiguriert:
   *  Es ist eine Firewall-Regel vorhanden, die nur den abgehenden Datenverkehr aus dem privaten Teilnetzbereich von IP-Adressen zulässt.
   *  Durch eine (standardmäßig inaktivierte) SNAT-Regel werden alle IP-Adressen aus dem privaten Teilnetz in eine einzige IP-Adresse für das öffentliche Teilnetz umgesetzt.
   * VMware HA (HA steht für "High Availability", also Hochverfügbarkeit) ist so konfiguriert, dass eine neue Portgruppe genutzt wird, die von dem Management-ESG und dem vom Kunden verwalteten ESG gemeinsam genutzt wird.

   Dieses ESG wird für alle Instanzhardwaretypen bereitgestellt; die Konfiguration kann vom Kunden geändert werden. Weitere Informationen finden Sie in den folgenden Abschnitten:
   *  [Netz zur Verwendung des vom Kunden verwalteten NSX Edge Services Gateway mit eigenen virtuellen Maschinen konfigurieren](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config)
   *  [VMware NSX-Dokumentation](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Erweiterungen beim Bedienungskomfort
{: #relnotes_v16-ui}

In der gesamten Benutzerschnittstelle wurden Verbesserungen vorgenommen:

*  Die Hauptnavigation in der Konsole wird durch die Einführung des linken Navigationsfensters erheblich verbessert, in dem Sie auf alle Bereiche der Benutzerschnittstelle zugreifen können. Hierdurch können Sie ohne Zeitaufwand eine neue Instanz bestellen, Ihre bereitgestellten Instanzen anzeigen, Systembenachrichtigungen prüfen, Einstellungen ändern und auf die Onlinedokumentation zugreifen.
*  Auf der neuen, über das linke Navigationsfenster zugänglichen Seite **Einführung** erhalten Sie direkt in der Konsole genügend Details, um eine fundierte Entscheidung über die Komponenten der bestellten Instanz zu treffen. Auf der Seite **Einführung** werden Sie darüber hinaus Schritt für Schritt durch den Bestellprozess einer Instanz geführt, von der zu Beginn stattfindenden Überprüfung aller Voraussetzungen für die Bestellung einer Instanz (z. B. erforderliche Benutzerkonten) bis zur abschließenden Aufgabe einer Bestellung.
*  Die Zusammenfassungsdetails für Cloud Foundation-Instanzen und vCenter Server-Instanzen werden auf einer einzigen Seite konsolidiert, auf die über das Menü **Ressourcen** im linken Navigationsfenster zugegriffen werden kann. Von dieser Seite aus können Sie durch die Auswahl der entsprechenden Registerkarte entweder Cloud Foundation-Instanzen oder vCenter Server-Instanzen herausfiltern.
* Wenn in Ihrer Instanz die Disaster-Recovery mit Zerto installiert ist, können Sie von der Seite mit den Servicedetails mit einem einzigen Klick direkt auf die Zerto-Konsole zugreifen. Weitere Informationen finden Sie unter [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).
