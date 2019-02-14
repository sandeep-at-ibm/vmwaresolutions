---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Auf vorhandenen Konfigurationen basierenden vSphere-Cluster bestellen

Sie können einen VMware vSphere-Cluster bestellen, der auf einer von Ihnen gespeicherten Konfigurationsvorlage basiert. In diesem Abschnitt ist beschrieben, wie Sie auf der Grundlage einer vorhandenen Clusterkonfiguration eine neue Clusterkonfiguration definieren.

## Voraussetzungen

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
*  Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen](/docs/services/vmwaresolutions/vmonic/useraccount.html).
*  Sie haben sich mit den Voraussetzungen und Hinweisen im Abschnitt [Voraussetzungen und Planung für vSphere-Cluster](/docs/services/vmwaresolutions/vsphere/vs_planning.html) vertraut gemacht.
*  Sie haben eine Konfigurationsvorlage für die Wiederverwendung erstellt.

## Vorgehensweise zum Bestellen von vSphere-Clustern, die auf vorhandenen Konfigurationen basieren

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf **VMware** und anschließend im Abschnitt **Virtuelle Rechenzentren** auf **VMware vSphere**.
2. Klicken Sie auf der Seite **VMware vSphere on IBM Cloud** auf **Erstellen**.  
3. Klicken Sie auf die Registerkarte **Neue erstellen** und wählen Sie eine Konfigurationsvorlage in der Liste **Clusterkonfigurationen** aus.
4. Geben Sie einen neuen Clusternamen ein.
5. Überprüfen Sie die automatisch eingetragenen Clustereinstellungen und aktualisieren Sie die Einstellungen nach Bedarf. Weitere Informationen zu den Einstellungen finden Sie unter [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html).
6. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration und die geschätzten Kosten.
   * Wenn Sie die Konfiguration als Vorlage speichern wollen, ohne eine Bestellung aufzugeben, klicken Sie auf **Konfiguration speichern**.
   * Wenn Sie die Bestellung aufgeben wollen, dann vergewissern Sie sich, dass das zu belastende Konto korrekt ist, überprüfen und akzeptieren Sie die Bedingungen und klicken Sie dann auf **Bereitstellung**.

   Nur die {{site.data.keyword.baremetal_short}}-Instanzen werden installiert. Für die Installation und Konfiguration verschiedener Komponenten nach der Clusterbereitstellung (z. B. VMware vCenter, VMware NSX, VMware vSAN) sind Sie selbst zuständig.
   {:note}

## Ergebnisse

Falls Sie die Clusterkonfiguration als Vorlage gespeichert haben, erhalten Sie in der Konsole eine Benachrichtigung, dass die Konfiguration gespeichert worden ist. Die Vorlage ist danach in der Liste **Clusterkonfigurationen** enthalten.

Falls Sie eine Bestellung aufgegeben haben, beginnt die Bereitstellung des Clusters automatisch. Sie erhalten eine E-Mail, in der die Bearbeitung der Bestellung bestätigt wird. Sobald der Cluster einsatzbereit ist, werden Sie ebenfalls per E-Mail benachrichtigt.

Die vSphere-Cluster werden (anders als die vCenter Server- und Cloud Foundation-Instanzen) auf der Seite **Bereitgestellte Instanzen** nicht angezeigt.
{:note}

### Zugehörige Links

* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere/vs_orderinginstances.html)
* [Vorhandene vSphere-Cluster skalieren](/docs/services/vmwaresolutions/vsphere/vs_scalingexistingclusters.html)
* [Außerhalb der Konsole erstellte Cluster skalieren](/docs/services/vmwaresolutions/vsphere/vs_orderingforclustersoutside.html)
