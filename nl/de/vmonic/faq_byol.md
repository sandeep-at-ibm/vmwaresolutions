---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# Häufig gestellte Fragen zur Lizenzierung und zu eigenen Lizenzen (BYOL)

Hier finden Sie Antworten auf häufig gestellte Fragen zur Lizenzierung, einschließlich der {{site.data.keyword.vmwaresolutions_full}}-Funktion, die Ihnen die Verwendung von eigenen Lizenzen ermöglicht (Bring Your Own License, BYOL).

## Was bedeutet BYOL?

BYOL steht für "Bring Your Own License", also die mögliche Verwendung Ihrer eigenen Lizenzen, und ist als Funktion für VMware Cloud Foundation-Instanzen in V1.8 und höheren Releases sowie für vCenter Server- und vSphere-Cluster in V2.0 und höheren Releases verfügbar. Mit BYOL können Sie Ihre eigenen VMware-Lizenzen für folgende VMware-Softwarekomponenten verwenden, wenn Sie Instanzen bestellen:
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

Wenn Sie die Verwendung Ihrer eigenen Lizenz für eine VMware-Komponente auswählen und einen gültigen Lizenzschlüssel dafür angeben, wird für diese Komponente keine Lizenz von IBM bestellt und es fallen keine monatlichen Lizenzgebühren im Konto Ihrer {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) für diese Komponente an.

**Hinweis:** Die BYOL-Funktion (BYOL = Bring Your Own License) ist für Benutzer der Kategorie "Business Partner" nicht verfügbar.

## Wo verwalte ich die über VMware vSphere on IBM Cloud bestellten Lizenzen und Komponenten?

Nachdem Sie die Erstellung eines neuen Clusters für VMware vSphere on {{site.data.keyword.cloud_notm}} bestellt haben, werden die VMware-Lizenzen, die ESXi-Server und weiteren Netzkomponenten geliefert und können im {{site.data.keyword.slportal}} verwaltet werden.

Rufen Sie nach der Bereitstellung die {{site.data.keyword.vmwaresolutions_short}}-Konsole auf, um den neuen Cluster unter Verwendung der gespeicherten Konfiguration zu skalieren. Weitere Informationen zur Skalierung finden Sie unter [Vorhandene vSphere-Cluster skalieren](../vsphere/vs_scalingexistingclusters.html).

## Welche Lizenzeditionen und CPU-Mengen sind für BYOL erforderlich?

Bei den Lizenzeditionen für BYOL gelten die folgenden Anforderungen.

### BYOL-Anforderungen für vCenter Server-Instanzen

Tabelle 1. Lizenzeditionen und CPU-Mindestvoraussetzungen für vCenter Server-Instanzen

  | VMware-Komponente | Erforderliche Lizenzedition | Erforderliches CPU-Minimum
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard                | Nicht zutreffend |
  | vSphere        | Enterprise Plus | 8 CPUs |
  | vSAN           | Advanced oder Enterprise | 8 CPUs |
  | NSX            | Standard, Advanced oder Enterprise | 8 CPUs |

### BYOL-Anforderungen für Cloud Foundation-Instanzen

Tabelle 2. Lizenzeditionen und CPU-Mindestvoraussetzungen für Cloud Foundation-Instanzen

  | VMware-Komponente | Erforderliche Lizenzedition | Erforderliches CPU-Minimum
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Standard | Nicht zutreffend |
  | vSphere        | Enterprise Plus | 8 CPUs |
  | vSAN           | Advanced oder Enterprise | 8 CPUs |
  | NSX            | Enterprise | 8 CPUs |

## Was passiert, wenn der von mir angegebene Lizenzschlüssel nicht korrekt ist?

Alle von Ihnen angegebenen Lizenzschlüssel werden validiert. Hierdurch wird sichergestellt, dass sie für die entsprechenden VMware-Komponenten richtig sind und die Mindestvoraussetzungen der VMware-Komponenten hinsichtlich Edition und CPU erfüllen. Falls die Validierung eines Lizenzschlüssels fehlschlägt, erhalten Sie eine Benachrichtigung und können nicht mit der Instanzbestellung fortfahren.

## Kann ich einen Lizenzschlüssel mit mehr als 8 CPUs bereitstellen?

Ja. Für jede VMware-Komponente ist eine Lizenz pro CPU erforderlich. Gegenwärtig sind alle Server für vCenter Server- und Cloud Foundation mit zwei CPUs ausgestattet. Somit sind für jeden Server zwei Lizenzen erforderlich. Es wird empfohlen, einen Lizenzschlüssel bereitzustellen, der die Basisinstanz und alle Erweiterungsknoten unterstützt, die Sie der Instanz später hinzufügen wollen.

## Kann ich bei Verwendung der BYOL-Funktion die Lizenz für SDDC Manager angeben?

Nein. Unsere Vereinbarung mit VMware erfordert, dass wir den tatsächlichen Lizenzschlüssel eines Kunden akzeptieren müssen. Die Cloud Foundation-Bereitstellung beinhaltet zwar Lizenzen für SDDC Manager, es werden jedoch keine Lizenzschlüsseldateien für SDDC Manager akzeptiert und für BYOL validiert. Aus diesem Grund werden die Lizenzen für SDDC Manager von IBM für alle Instanzen in Rechnung gestellt. Lizenzen für SDDC Manager tragen einen geringen Anteil zu den Gesamtlizenzgebühren für eine Cloud Foundation-Instanz bei.

## Kann ich die BYOL-Funktion für einige VMware-Komponenten verwenden und für andere Komponenten monatliche Lizenzen erwerben?

Ja. Sie können die BYOL-Funktion oder erworbene Lizenzen in jeder gewünschten Kombination für die vier VMware-Komponenten verwenden. In der {{site.data.keyword.vmwaresolutions_short}}-Konsole können Sie direkt die Lizenzierungsoption auswählen, wenn Sie die vCenter Server- oder Cloud Foundation-Instanz bestellen. Die Lizenzierungsoption, die Sie bei der erstmaligen Instanzbestellung auswählen, gilt für die Laufzeit dieser Instanz.

## Kann ich bei einer bestimmten VMware-Komponente BYOL für einige Lizenzen verwenden und die übrigen Lizenzen bei IBM erwerben?

Ja. Wenn Sie BYOL für eine bestimmte VMware-Komponente ausgewählt haben, erhalten Sie bei der Erstellung eines neuen Clusters die Möglichkeit, einen neuen BYOL-Schlüssel einzugeben, weiter einen vorhandenen BYOL-Schlüssel zu verwenden oder eine von IBM bereitgestellte Lizenzierung für diesen Cluster zu erwerben. Die Lizenzierung für einzelne Cluster ist derzeit nur mit VMware vSphere Enterprise und VMware vSAN möglich.

## Kann ich BYOL beim Erstellen eines neuen Clusters verwenden?

Ja. Sie können BYOL aus vorhandenen BYOL-Lizenzen verwenden oder beim Erstellen eines neuen Clusters BYOL neu eingeben. Beim Erstellen eines neuen Clusters können Sie auch eine von IBM bereitgestellte Abonnementslizenz erwerben. Die Lizenzierung für einzelne Cluster ist derzeit nur mit VMware vSphere Enterprise und VMware vSAN möglich.

## Wie verwalte ich meine BYOL-Lizenzen?

Zur Verwaltung Ihrer BYOL-Lizenzen verwenden Sie VMware vSphere Web Client, nachdem die Instanzbereitstellung ausgeführt wurde.

## Validiert die Instanz, ob die Kapazität meiner BYOL-Lizenz ausreichend ist, wenn ich später weitere ESXi-Server zu meiner Instanz hinzufüge?

Ja. Sobald Sie weitere ESXi-Server zu einer bereitgestellten Instanz hinzufügen, wird die Kapazität Ihrer BYOL-Lizenzen automatisch für die angegebene Anzahl von ESXi-Servern überprüft. Falls die Kapazität nicht ausreicht, werden die ESXi-Server nicht hinzugefügt und Sie empfangen eine Benachrichtigung in der Konsole.

## Wie kann ich die verfügbare Lizenzkapazität für einen Cluster mit BYOL feststellen?

Führen Sie die folgenden Schritte aus, um die über Ihren Lizenzschlüssel verfügbare CPU-Anzahl zu ermitteln:
1. Rufen Sie die Seite **Bereitgestellte Instanzen** auf.
2. Suchen Sie die Instanz und klicken Sie auf die Instanz.
3. Klicken Sie auf der Registerkarte **Infrastruktur** auf den Cluster, für den die Lizenzkapazität geprüft werden soll. Die Anzahl der verfügbaren CPUs ist in der Tabelle **Vom Benutzer bereitgestellte Lizenz** angegeben.

## Stellt IBM Unterstützung bereit, wenn ich die BYOL-Lizenzierungsoption auswähle?

IBM Support bleibt weiter Ihr Ansprechpartner für alle Aspekte der Instanzkonfiguration. Falls jedoch festgestellt wird, dass ein gemeldetes Problem auf eine BYOL-VMware-Komponente zurückzuführen ist, werden Sie an den VMware-Support verwiesen.

## Warum werden vSphere-Lizenzgebühren in der Kostenschätzung aufgeführt, wenn ich BYOL verwende? Werden sie mir in Rechnung gestellt?

{{site.data.keyword.baremetal_short}}-Instanzen werden mit bereits installiertem VMware vSphere und mit bereits enthaltenen vSphere-Lizenzen bereitgestellt. Wenn Sie BYOL für vSphere ausgewählt haben, wird bei der Instanzbereitstellung automatisch ein Prozess eingeleitet, der die enthaltenen vSphere-Lizenzen entfernt. Anschließend werden die Lizenzgebühren Ihrem {{site.data.keyword.cloud_notm}}-Konto gutgeschrieben. Ihr Eingreifen ist bei diesem Prozess nicht erforderlich.

## Kann ich weiterhin den bestehenden manuellen Prozess für BYOL verwenden?

Ab der Einführung der BYOL-Funktion wird von einer weiteren Verwendung des manuellen Prozesses abgeraten. Wenn Sie BYOL verwenden möchten, geben Sie Ihre eigenen Lizenzen beim Bestellen der Instanz an.

## Wird BYOL für andere VMware-Produkte wie VMware vRealize Automation, VMware vRealize Operations oder VMware vRealize Log Insight unterstützt?

Nein. Dies liegt daran, dass diese VMware-Produkte nicht Bestandteil der Instanzbereitstellung sind. Diese VMware-Produkte können zusätzlich zur Erstbereitstellung installiert werden, wobei Installation und Lizenzierung durch den Kunden bzw. eine hiermit beauftragte Person durchgeführt werden müssen.

## Kann ich NFS-Speicher mit vCenter Server with Hybridity Bundle bestellen?

Für neu bereitgestellte Instanzen wird ausschließlich vSAN-Flashspeicher unterstützt. Das vCenter Server with Hybridity Bundle-Produktangebot beinhaltet die Lizenzierung für vSAN Advanced oder Enterprise.

Wenn Sie eine vCenter Server-Instanz mit NFS-Speicher besitzen, können Sie für die vorhandene Instanz ein Upgrade auf vCenter Server with Hybridity Bundle durchführen. Während des Upgrades wird die Lizenzierung für vSAN Advanced bestellt, Sie müssen jedoch keinen reinen vSAN-Flash-Cluster bereitstellen.

## Kann ich BYOL mit vCenter Server with Hybridity Bundle verwenden?

Sie können nicht Ihre eigene VMware-Lizenz (BYOL) für {{site.data.keyword.cloud_notm}} verwenden. vCenter Server with Hybridity Bundle erfordert, dass alle VMware-Lizenzen von IBM bereitgestellt werden.

## Was ist der Unterschied zwischen einer vCenter Server with Hybridity Bundle-Lizenz und einer vCenter Server-Lizenz?

Die einzelnen VMware-Lizenzen, die in vCenter Server verfügbar sind, werden pro CPU abgerechnet. Wie bei allen von IBM bereitgestellten, pro CPU berechneten VMware-Lizenzen fällt ein 1,3-facher Zuschlag für alle Server an, die mehr als 16 Kerne pro CPU haben (zum Beispiel für Dual Intel Xeon Gold 6140).

Bei vCenter Server with Hybridity Bundle handelt es sich um eine vorgegebene Gruppe von VMware-Lizenzen und -Editionen, die pro Kern und nicht pro CPU lizenziert werden. Daher ändert sich der Lizenzpreis für diese Instanzen nicht.

## Welche von IBM bereitgestellten VMware-Lizenzkomponenten und -Editionen sind für vCenter Server with Hybridity Bundle verfügbar?

Zu den neuen Instanzen von vCenter Server with Hybridity Bundle gehören VMware vSphere Enterprise Plus, VMware vCenter Standard, VMware NSX Advanced oder Enterprise, VMware vSAN Advanced oder Enterprise und VMware Hybrid Cloud Extension (HCX).

Wenn Sie eine vCenter Server-Instanz mit NSX Base Edition besitzen, wird automatisch ein Upgrade auf NSX Advanced durchgeführt, wenn Sie vCenter Server with Hybridity Bundle bestellen.

## Kann ich ein Upgrade der in vCenter Server with Hybridity Bundle enthaltenen NSX Advanced Edition auf NSX Enterprise Edition durchführen?

vCenter Server with Hybridity Bundle beinhaltet NSX Advanced. Sie können nach dem Bestellen von vCenter Server with Hybridity Bundle jedoch ein Upgrade auf die NSX Enterprise Edition durchführen. Verwenden Sie dazu die Registerkarte **Update und Patch** auf der Seite mit den Instanzdetails der {{site.data.keyword.vmwaresolutions_short}}-Konsole.

### Zugehörige Links

* [Cloud Foundation-Instanzen bestellen](../sddc/sd_orderinginstance.html)
* [Cloud Foundation-Instanzen](../sddc/sd_cloudfoundationoverview.html)
* [Auf die Konsole zugreifen](loginmethod.html)
* [Kontaktaufnahme mit dem IBM Support](trbl_support.html)
* [vRealize Automation](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/vRealizeAutomation){:new_window}
