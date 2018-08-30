---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-11"

---

# Außerhalb der Konsole erstellte Cluster skalieren

Mit dem VMware vSphere-Angebot können Sie vorhandene vSphere-Cluster skalieren, die außerhalb der {{site.data.keyword.vmwaresolutions_full}}-Konsole erstellt werden. Zum Skalieren eines vSphere-Clusters, der außerhalb der Konsole erstellt wird, müssen Sie den Cluster mit den gleichen Einstellungen mit der Konsole erneut erstellen und dann skalieren.

## Voraussetzungen

Stellen Sie sicher, dass Sie die folgenden Tasks ausgeführt haben:
*  Sie haben die Berechtigungsnachweise für die {{site.data.keyword.cloud_notm}}-Infrastruktur auf der Seite **Einstellungen** konfiguriert. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen verwalten](../vmonic/useraccount.html).
*  Sie haben sich mit den Voraussetzungen und Hinweisen im Abschnitt [Voraussetzungen und Planung für VMware vSphere on {{site.data.keyword.cloud_notm}}](vs_planning.html) vertraut gemacht.

## Vorgehensweise

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog im linken Navigationsfenster auf **VMware** und anschließend im Abschnitt **Virtuelle Rechenzentren** auf **VMware vSphere**.
2. Klicken Sie auf der Seite **VMware vSphere on IBM Cloud** auf **Erstellen**.  
   Vergewissern Sie sich, dass Sie sich auf der Registerkarte **Neue erstellen** befinden und dass in der Liste **Clusterkonfigurationen** der Eintrag **Neuer Cluster** angezeigt wird.
3. Erstellen Sie einen Cluster mit denselben Einstellungen wie Ihr vorhandener Cluster, der außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole erstellt wird. Weitere Informationen finden Sie unter [Neue vSphere-Cluster bestellen](vs_orderinginstances.html).  
   **Hinweis**: Zum Skalieren eines Clusters, der außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole erstellt wird, müssen Sie im Falle der Netzschnittstelle die vorhandenen VLANs für den Cluster auswählen.  
4. Überprüfen Sie im Fenster **Bestellübersicht** die Clusterkonfiguration und klicken Sie dann auf **Konfiguration speichern**.   
5. Klicken Sie auf der Seite **Einführung** auf die Karte **VMware vSphere on IBM Cloud**.
6. Klicken Sie auf der Seite **VMware vSphere on IBM Cloud** auf **Erstellen**.
7. Klicken Sie auf die Registerkarte **Vorhandenen skalieren**. Wählen Sie in der Liste **Clusterkonfigurationen** den zuvor erstellten Cluster aus. 
8. Geben Sie im Abschnitt **{{site.data.keyword.baremetal_short}}-Instanzen** die Anzahl der {{site.data.keyword.baremetal_short}}-Instanzen an, die zum Cluster hinzugefügt werden sollen.
9. Wenn der Cluster in seinem öffentlichen VLAN nicht das HA-Paar von FortiGate 300 Series Security Appliance enthält, können Sie ein solches Paar bestellen, indem Sie die Option **In Kauf einbeziehen** unter **HA-Paar von FortiGate Physical Appliance 300 Series** auswählen.
10. Überprüfen Sie im Fenster **Bestellübersicht** die Instanzkonfiguration und die geschätzten Kosten. Vergewissern Sie sich, dass das zu belastende Konto korrekt ist, überprüfen und akzeptieren Sie die Bedingungen und klicken Sie dann auf **Bereitstellung**.

## Ergebnisse

Die Bereitstellung des Clusters beginnt automatisch und Sie empfangen eine E-Mail-Bestätigung, dass die Bestellung bearbeitet wird. Sobald der Cluster einsatzbereit ist, werden Sie per E-Mail benachrichtigt.

**Hinweis:** Die vSphere-Cluster werden auf der Seite **Bereitgestellte Instanzen** nicht zusammen mit den vCenter Server- und Cloud Foundation-Instanzen angezeigt.

### Zugehörige Links

* [Neue vSphere-Cluster bestellen](vs_orderinginstances.html)
* [Auf vorhandenen Konfigurationen basierenden vSphere-Cluster bestellen](vs_orderingbasedonexistingconfig.html)
* [Vorhandene vSphere-Cluster skalieren](vs_scalingexistingclusters.html)
