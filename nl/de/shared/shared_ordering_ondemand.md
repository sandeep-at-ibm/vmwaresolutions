---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: shared order resource, order on demand shared, order on demand resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Shared On-demand - Bestellverfahren
{: #shared_ordering_ondemand}

{{site.data.keyword.vmwaresolutions_full}} Shared wird als experimentelles Angebot bereitgestellt.
{:note}

Für On-demand werden vCPU und RAM des virtuellen Rechenzentrums nach Bedarf zugeordnet. Die für die Zuordnung beanspruchte Zeit kann abhängig von der globalen Nutzung des vCPU- und RAM-Verbrauchs des virtuellen Rechenzentrums variieren.
* Die Begrenzungen für die Menge an vCPU und RAM sind Maximalwerte für den Verbrauch zu einem beliebigen Zeitpunkt.
* Die vCPU-und RAM-Ressourcen können später bei Bedarf erhöht oder reduziert werden.
* Die Kosten werden stündlich berechnet und basieren auf der Ressourcennutzung in virtuellen Rechenzentrum.
* Die Menge an Speicher, die im virtuellen Rechenzentrum zugeordnet und verwendet werden kann, ist unbegrenzt. Die Gebühren werden stündlich auf Basis von GB des zugeordneten Speichers berechnet.
* Es gibt keine Grenzen für den Umfang des eingehenden und ausgehenden öffentlichen Netzbetriebs. Die öffentliche Bandbreite wird pro GB berechnet.

## IBM Cloud for VMware Solutions Shared - Voraussetzungen
{: #shared_ordering_ondemand-req}

### IBM Cloud-Infrastrukturkonto
{: #shared_ordering_ondemand-account-req}

Zur Verwendung von {{site.data.keyword.vmwaresolutions_short}} für die Bestellung von IBM Cloud for VMware Solutions Shared müssen Sie über ein **nutzungsabhängiges** oder ein **Abonnement**-{{site.data.keyword.cloud_notm}}-Konto verfügen. Die Kosten für die bestellten Ressourcen werden diesem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt.

### Benennungsanforderungen für das virtuelle Rechenzentrum
{: #shared_ordering_ondemand-vdc-name-req}

Der Name des virtuellen Rechenzentrums *sollte* den folgenden Anforderungen entsprechen. Später werden diese Namensanforderungen erzwungen.
* Es sind nur Kleinbuchstaben, Ziffern und Gedankenstriche (-) zulässig.
* Der Name muss mit einem Kleinbuchstaben beginnen.
* Der Name muss entweder auf einen Kleinbuchstaben oder auf eine Ziffer enden.
* Die maximale Länge des Namens für das virtuelle Rechenzentrum beträgt 10 Zeichen.
* Der Name des virtuellen Rechenzentrums muss innerhalb Ihres Kontos eindeutig sein.

## Vorgehensweise zur Bestellung von Shared On-demand
{: #shared_ordering_ondemand-procedure}

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf das Symbol **VMware** und anschließend im Abschnitt **Virtuelle VMware-Rechenzentren** auf die Karte **IBM Cloud for VMware Solutions Shared** .
2. Klicken Sie auf der Seite **IBM Cloud for VMware Solutions Shared** auf die Karte **On-demand** und dann auf **Erstellen**.
3. Geben Sie auf der Seite **IBM Cloud for VMware Solutions Shared - On-demand** den Namen des virtuellen Rechenzentrums ein. Das {{site.data.keyword.CloudDataCent_notm}}, an dem das Angebot verfügbar ist, ist vorausgewählt.
4. Wählen Sie die vCPU- und RAM-Grenzwerte entsprechend Ihren Anforderungen aus.
5. Überprüfen Sie im Fenster **Bestellübersicht** die Konfiguration und die geschätzten Kosten, bevor Sie die Bestellung aufgeben.
6. Klicken Sie auf **Bereitstellung**.

## Ergebnisse nach der Bestellung von Shared On-demand
{: #shared_ordering_ondemand-results}

* Die Bereitstellung der Ressourcen beginnt automatisch und Sie empfangen eine Bestätigung, dass die Bestellung bearbeitet wird. Sie können den Bereitstellungsstatus, einschließlich aller Probleme, die eventuell Ihre Aufmerksamkeit erfordern, durch Anzeigen des Abschnitts **Status des virtuellen Rechenzentrums** überprüfen.
* Nachdem die Ressourcen erfolgreich bereitgestellt wurden, werden die in [Technische Spezifikationen für {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs) beschriebenen Komponenten auf Ihrer virtuellen VMware-Plattform installiert.
* Wenn die Ressourcen für die Verwendung bereit sind, ändert sich der Status in **Bereit**.

## Zugehörige Links
{: #shared_ordering_ondemand-related}

* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Shared Reserved - Bestellverfahren](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared - Verwaltung](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
