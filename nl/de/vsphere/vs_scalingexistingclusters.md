---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Vorhandene vSphere-Cluster skalieren
{: #vs_scalingexistingclusters}

Sie können einen vorhandenen VMware vSphere-Cluster, den Sie bestellt oder gespeichert haben, in der {{site.data.keyword.vmwaresolutions_full}}-Konsole skalieren. Fügen Sie dazu ESXi-Server hinzu oder bestellen Sie ein HA-Paar (HA = High Availability) für FortiGate 300 Series Security Appliance für den Cluster.

## Voraussetzungen
{: #vs_scalingexistingclusters-req}

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
*  Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount#managing-user-accounts-and-settings).
*  Sie haben sich mit den Voraussetzungen und Hinweisen im Abschnitt [Voraussetzungen und Planung für vSphere-Cluster](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning) vertraut gemacht.
*  Sie haben eine E-Mail mit der Bestätigung erhalten, dass der Cluster, den Sie skalieren möchten, zur Verwendung bereit ist.

## Vorgehensweise beim Skalieren vorhandener Cluster
{: #vs_scalingexistingclusters-procedure}

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf **VMware** und anschließend im Abschnitt **Virtuelle Rechenzentren** auf **VMware vSphere**.
2. Klicken Sie auf der Seite **VMware vSphere on IBM Cloud** auf **Erstellen**.  
3. Klicken Sie auf die Registerkarte **Vorhandene skalieren** und wählen Sie den zu skalierenden Cluster in der Liste **Clusterkonfigurationen** aus.
4. Überprüfen Sie die automatisch eingetragenen Clustereinstellungen.
5. Geben Sie im Abschnitt **{{site.data.keyword.baremetal_short}}-Instanzen** die Anzahl der {{site.data.keyword.baremetal_short}}-Instanzen an, die zum Cluster hinzugefügt werden sollen.
6. Wenn der Cluster in seinem öffentlichen VLAN nicht das HA-Paar von FortiGate 300 Series Security Appliance enthält, können Sie die Appliance bestellen. Wählen Sie dazu die Option **In Kauf einbeziehen** unter **HA-Paar von FortiGate Physical Appliance 300 Series** aus.
7. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration und die geschätzten Kosten.
   * Wenn Sie die Konfiguration als Vorlage speichern wollen, ohne eine Bestellung aufzugeben, klicken Sie auf **Konfiguration speichern**.
   * Wenn Sie die Bestellung aufgeben wollen, dann vergewissern Sie sich, dass das zu belastende Konto korrekt ist, überprüfen und akzeptieren Sie die Bedingungen und klicken Sie dann auf **Bereitstellung**.

### Ergebnisse
{: #vs_scalingexistingclusters-results}

Die Clusterskalierung wird automatisch gestartet. Sie erhalten eine E-Mail, in der die Bearbeitung der Bestellung bestätigt wird. Sobald der Cluster einsatzbereit ist, werden Sie per E-Mail benachrichtigt.

Wenn der Cluster, den Sie skalieren möchten, nicht zur Verwendung bereit ist, erhalten Sie möglicherweise eine Fehlernachricht.

Die vSphere-Cluster werden (im Gegensatz zu den vCenter Server- und Cloud Foundation-Instanzen) auf der Seite **Ressourcen** nicht angezeigt.
{:note}

## Zugehörige Links
{: #vs_scalingexistingclusters-related}

* [Neue vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Auf vorhandenen Konfigurationen basierenden vSphere-Cluster bestellen](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Außerhalb der Konsole erstellte Cluster skalieren](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
