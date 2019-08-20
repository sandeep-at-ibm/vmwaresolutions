---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-06"

subcollection: vmware-solutions


---

# Erstkonfiguration
{: #vum-init-config}

Mit der {{site.data.keyword.vmwaresolutions_full}}-Automation wird die VCSA mit einem Standardgateway konfiguriert, das auf den {{site.data.keyword.cloud}} Backend Customer Router (BCR) eingestellt ist. Es gibt jedoch über den BCR keine Route zum Internet. Die Standardroute von der VMware vCenter Server on {{site.data.keyword.cloud_notm}}-Instanz zum Internet verläuft über das Management-ESG. Da es nicht ratsam ist, die Konfiguration der VCSA oder des Management-ESG zu ändern, wird eine Proxy-Server-Implementierung im Kundenteilnetz empfohlen, um VUM zu aktivieren.

Dieser Ansatz bedeutet, dass Sie die VCSA oder die Management-ESG nicht neu konfigurieren müssen, sondern es muss lediglich eine kleine virtuelle Maschine (VM) oder ein Gerät installiert sein. Ein Proxy-Server ist ein System, das sich zwischen zwei Endpunktgeräten befindet und als Zwischeneinheit dient. In diesem Fall befindet es sich zwischen VUM und den Update-Servern bei VMware.

Wenn VUM eine Ressource vom Update-Server bei VMware anfordert, wird die Anforderung zuerst an den Proxy-Server gesendet und der Proxy-Server sendet die Anforderung dann an den Update-Server. Sobald die Ressource vom Proxy-Server empfangen wurde, sendet er die Ressource an VUM. Ein Proxy-Server kann verwendet werden, um Sicherheitsfunktionen, Verwaltungssteuermechanismen und Caching-Services zu unterstützen.

Sie können einen Proxy-Server basierend auf CentOS und Squid verwenden. Squid Proxy ist ein Open-Source-Caching-Proxy für das Web, der zahlreiche Protokolle (wie z. B. HTTP und HTTPS) unterstützt. Es steht eine Reihe von VM- und Appliance-basierten Proxys zur Verfügung und Sie müssen den gewünschten Proxy entsprechend Ihren Unternehmensanforderungen auswählen und ihn nach der Anleitung des Anbieters installieren und konfigurieren. Kunden, die sich für eine CentOS/Squid-Implementierung entscheiden, sollten mit dem folgenden Prozess fortfahren.

* Laden Sie CentOS-ISO-Datei auf einen Jump-Server herunter.
* Erstellen Sie eine vCenter-Bibliothek.
* Laden Sie die ISO-Datei in die vCenter-Bibliothek hoch.
* Erstellen Sie eine VM, installieren und konfigurieren Sie CentOS und installieren Sie Squid.

## Teilnetzinformationen suchen
{: #vum-init-config-subnet}

Bevor Sie mit dieser Task beginnen, sammeln Sie die erforderlichen Informationen für die folgende Tabelle. Überprüfen Sie die vorgeschlagenen Werte und stellen Sie sicher, dass sie für Ihre Umgebung geeignet sind. Diese Konfiguration basiert auf einem weniger umfangreichen Proxy für VUM, der nur CentOS-Minimal und Squid verwendet.

Gehen Sie wie folgt vor, um das private portierbare Teilnetz des Kunden zu suchen:

1. Rufen Sie die Seite **Ressourcen** in der {{site.data.keyword.vmwaresolutions_short}}-Konsole auf.
2. Wählen Sie die erforderliche **Instanz** aus, wählen Sie **Infrastruktur** und anschließend den erforderlichen **Cluster** aus.
3. Wählen Sie **Privates VLAN** aus und suchen Sie das Teilnetz mit der Bezeichnung `Privates Teilnetz für Kundenworkload-Edges`.
4. Wählen Sie das **Teilnetz** aus; Sie werden zur Seite mit den Teilnetzdetails umgeleitet, auf der die IP-Adressen und ihre Zuordnungen angezeigt werden.
5. Wählen Sie anhand dieser Informationen eine nicht zugeordnete IP-Adresse aus und aktualisieren Sie die **Anmerkung** mit entsprechenden Kommentaren. Verwenden Sie diese IP-Adresse für den Parameter für die `Proxy-IP` in der folgenden Tabelle.

Tabelle 1. Werte für die Bereitstellung

| Parameter | Empfohlene Werte | Hinweise |
|:--------- |:-------------- |:------ |
| Proxy-CPU | 1 vCPU | Squid hat keine Mindestvoraussetzungen |
| Proxy-RAM | 2 GB | Squid hat keine Mindestvoraussetzungen |
| Proxy-Platte | 25 GB | Squid hat keine Mindestvoraussetzungen |
| Hostname | Proxy01 | |
| Adresse | proxy ip | Eine Ersatz-IP-Adresse sollte aus dem privaten portierbaren Teilnetz des Kunden verwendet werden, die während des Bereitstellungsprozesses zugewiesen wird. Nur zwei IP-Adressen werden für dieses Teilnetz reserviert; eine für den BCR und die andere für das Kunden-ESG.
| Netzmaske | 255.255.255.192 | |
| Gateway| customer-nsx-edge private uplink ip | Dies ist die Standardgateway-Einstellung für den Proxy-Server, nämlich die private Uplink-IP-Adresse "customer-nsx-edge". Die IP findet sich auf der Registerkarte **Einstellungen** für **customer-nsx-edge**. |
| DNS-Server | AD/DNS ip | Diese IP-Adresse befindet sich auf der Instanzseite in der {{site.data.keyword.vmwaresolutions_short}}-Konsole auf der Seite **Ressourcen**. |
| BCR-IP | bcr ip | Notieren Sie sich auf derselben Seite, auf der Sie die oben genannte Proxy-IP-Adresse ausgewählt haben, das mit der Adresse gekennzeichnete Gateway. Diese Adresse ist die IP-Adresse des {{site.data.keyword.cloud_notm}} Backend Customer Router und fungiert als Gateway für 10.0.0.0/8 und 161.26.0.0/16. Diese Adresse wird in einer statischen Route im Proxy-Server verwendet, sodass sie die VCSA und den AD/DNS-Server erreichen kann. |
| NAT-IP | customer-nsx-edge public uplink ip | Die öffentliche Adresse von NSX Edge Service Gateway des Kunden dient als öffentliche NAT-Adresse für den Proxy. Diese IP-Adresse wird in der Registerkarte **Einstellungen** für **customer-nsx-edge** angegeben. |

## NSX konfigurieren
{: #vum-init-config-config-nsx}

Einstellungen für NSX-Kunden-ESG-Firewall und NAT sind erforderlich, um den Datenverkehr des Proxy-Servers zu aktivieren.

### Firewall
{: #vum-init-config-firewall}

1. Wechseln Sie zu **Home** > **Vernetzung & Sicherheit**.
2. Wählen Sie **NSX Edges**, "customer-nsx-edge" und anschließend **Firewall** aus.
3. Klicken Sie auf das Symbol **+** und fügen Sie eine Firewallregel hinzu.
4. Geben Sie die erforderlichen Parameter entsprechend den Angaben in der folgenden Tabelle an. Die neue Firewallregel muss vor der letzten Regel, der "Default-Deny"-Regel (Standardverweigerung), stehen.

Tabelle 2. Firewallregel

| Parameter | Empfohlene Werte |
|:--------- |:-------------- |
| Name | Outbound Proxy01 |
| Typ | User |
| Quelle | proxy server ip |
| Ziel | beliebig |
| Service | HTTP/HTTPS/ICMP Echo |
| Aktion | Accept |

Klicken Sie nach der Angabe der Parameter auf **Änderungen veröffentlichen**.

### NAT
{: #vum-init-config-nat}

1. Wählen Sie **NAT** aus.
2. Klicken Sie auf das Symbol **+** und fügen Sie eine SNAT-Regel hinzu.
3. Geben Sie die erforderlichen Parameter entsprechend den Angaben in der folgenden Tabelle an und klicken Sie auf **OK**. Klicken Sie anschließend auf **Änderungen veröffentlichen**.

Tabelle 3. NAT-Regel

| Parameter | Empfohlene Werte |
|:--------- |:-------------- |
| Regeltyp | BENUTZER |
| Aktion | SNAT |
| Anwendet auf | Öffentlicher Uplink |
| Ursprüngliches Protokoll | beliebig |
| Ursprüngliche Quellen-IP | proxy server ip |
| Ursprüngliche Quellenports | beliebig |
| Ursprüngliche Ziel-IP-Adresse | beliebig |
| Ursprüngliche Zielports | beliebig |
| Übersetzte IP-Adresse | NAT-IP |
| Übersetzter Portbereich | beliebig |
| Status | Aktivieren |
| Protokollierung | Aktivieren |
| Beschreibung | Proxy01 SNAT |

### Proxy-Server installieren und konfigurieren
{: #vum-init-config-inst-cfg-proxy}

Der folgende Prozess stellt eine VM für CentOS und Squid aus der Inhaltsbibliothek bereit und setzt sich aus den im Folgenden aufgeführten Schritten zusammen. Es wird vorausgesetzt, dass Sie eine Windows-VSI als Jump-Box-Server bereitgestellt haben und das Remote Desktop Protocol verwenden, um eine Verbindung zur öffentlichen VSI-Schnittstelle herzustellen:

* CentOS-Minimal-ISO-Datei herunterladen
* vCenter-Inhaltsbibliothek konfigurieren und mit CentOS-ISO-Datei füllen
* Proxy-VM konfigurieren und CentOS und Squid installieren

### CentOS-Minimal-ISO-Datei herunterladen
{: #vum-init-config-downloading-centos}

Verwenden Sie einen Browser auf Ihrem Jump-Server, um die CentOS-Minimal-ISO-Datei von [CentOS](https://www.centos.org/download/) herunterzuladen. Beachten Sie, dass {{site.data.keyword.cloud_notm}} eine Spiegelung vieler gängiger Linux-Distributionen verwaltet. Diese Spiegelung ist nur im privaten Netz verfügbar und die CentOS-ISOs sind unter der folgenden Adresse verfügbar: `http://mirrors.service.softlayer.com/centos/7/isos/x86_64/`

### Inhaltsbibliothek konfigurieren und mit CentOS-ISO-Datei füllen
{: #vum-init-config-config-conent-library}

Erstellen Sie eine lokale vCenter-Inhaltsbibliothek. Auf die Bibliothek kann nur in der vCenter Serverinstanz zugegriffen werden, in der sie erstellt wurde. Füllen Sie die Bibliothek mit den Vorlagen und ISOs, die für die Bereitstellung virtueller Maschinen (VMs) erforderlich sind.

1. Navigieren Sie über den vSphere Web Client zu **Home** > **Inhaltsbibliothek** > **Objekte** > **Neue Inhaltsbibliothek erstellen** > **Abonnierte Bibliothek in vCenter erstellen**.
2. Geben Sie einen Namen für die Inhaltsbibliothek ein (z. B. ISO), geben Sie in das Textfeld "Hinweise" eine Beschreibung für die Bibliothek ein und klicken Sie auf **Weiter**.
3. Wählen Sie **Lokale Inhaltsbibliothek** aus und klicken Sie auf **Weiter**.
4. Wählen Sie einen Datenspeicher aus und klicken Sie anschließend auf einen geeigneten Datenspeicher (z. B. `vsanDatastore`).
5. Lesen Sie die Informationen auf der Seite **Bereit zum Abschließen** und klicken Sie auf **Fertigstellen**.

### Proxy-VM konfigurieren und CentOS und Squid installieren
{: #vum-init-config-config-proxy}

Diese Aktivität umfasst die folgenden Tasks:

*	Neue VM erstellen
*	CentOS installieren
*	Squid installieren

#### Neue VM erstellen
{: #vum-init-config-create-new-vm}

Mit dieser Task wird eine neue VM erstellt, die für den sofortigen Einsatz als Proxy-Server geeignet ist. Die Einstellungen von "Tabelle 1 - Werte für die Bereitstellung" sollten für die Konfiguration verwendet werden.

1.	Bei Verwendung von vSphere Web Client wechseln Sie zu **Home** > **VMs und Vorlagen**.
2.	Klicken Sie im Navigatorfenster auf **datacenter1**, klicken Sie anschließend mit der rechten Maustaste und wählen Sie **Neue virtuelle Maschine** > **Neue virtuelle Maschine** aus.
3.	Wählen Sie **Neue virtuelle Maschine erstellen** aus und klicken Sie auf **Weiter**.
4.	Geben Sie einen Namen für die VM ein (z. B. Proxy01), wählen Sie **datacenter1** aus und klicken Sie anschließend auf **Weiter**.
5.	Wählen Sie **cluster1** aus und klicken Sie auf **Weiter**.
6.	Wählen Sie einen geeigneten Datenspeicher aus (z. B. vsanDatastore), klicken Sie erneut auf **Weiter** und dann nochmals auf **Weiter**.
7.	Wählen Sie unter **Familie des Gastbetriebssystems** die Option **Linux** aus, wählen Sie unter **Version des Gastbetriebssystems** die Option **CentOS 7 (64 Bit)** aus und klicken Sie dann auf **Weiter**.
8.	Nehmen Sie auf der Registerkarte **Angepasste Hardware** für virtuelle Hardware die Einstellungen **CPU auf 1**, **Speicher auf 2048 MB** und **Neue Festplatte auf 25 GB** vor. Wählen Sie unter **Neues CD/DVD-Laufwerk** die Option **ISO-Datei für Inhaltsbibliothek** und anschließend **CentOS-7-x86_64-Minimal** aus, klicken Sie auf **OK** und aktivieren Sie das Feld **Verbunden**.
9.	Wählen Sie im Feld "Neues Gerät" die Option **Netz** aus und klicken Sie dann auf **Hinzufügen**.
10.	Wählen Sie das Netz **SDDC-DPortGroup-Mgmt** aus und stellen Sie sicher, dass das Kontrollkästchen "Verbinden" aktiviert ist. Klicken Sie auf **Weiter**.
11.	Prüfen Sie die Angaben und klicken Sie auf **Fertigstellen**.

#### CentOS installieren
{: #vum-init-config-install-centos}

Diese Task installiert und konfiguriert die neu erstellte VM, sodass sie für die Squid-Installation bereit ist.

1.	Wählen Sie im Navigatorfenster des vSphere Web Client die soeben erstellte **VM** aus (Proxy01) und wählen Sie dann die Registerkarte mit der **Zusammenfassung** aus.
2.	Klicken Sie auf **"Play"**, um die VM einzuschalten.
3.	Die VM wird eingeschaltet und vom CentOS 7-ISO-System aus gebootet. Starten Sie eine **ferne Konsole oder eine Webkonsole** für die VM. Die ferne Konsole muss installiert sein und das System, das den Web-Browser ausführt, muss die vSphere ESXi-Hosts nach Namen auflösen.
4.	Wählen Sie in der Willkommensanzeige von CentOS 7 die gewünschte Sprache aus und klicken Sie auf **Weiter**.
5.	Klicken Sie in der Anzeige **LOCALIZATION** auf **DATE & TIME**, wählen Sie Ihre Zeitzone aus und klicken Sie anschließend auf **Fertig**.
6.	Klicken Sie in der Anzeige **LOCALIZATION** auf **KEYBOARD**, um bei Bedarf die Standardeinstellung zu ändern, und klicken Sie anschließend auf **Fertig**.
7.	Klicken Sie in der Anzeige **LOCALIZATION** auf **INSTALLATION DESTINATION**, klicken Sie auf das Symbol **Virtuelle VMware-Platte** und klicken Sie dann auf **Done**.
8.	Klicken Sie in der Anzeige **LOCALIZATION** auf **NETWORK & HOSTNAME** und ändern Sie den Hostnamen in den von Ihnen gewünschten Hostnamen (z. B. Proxy01).
9.	Klicken Sie auf **Konfigurieren** und anschließend auf **IPv4-Einstellungen**. Wählen Sie im Feld **Methode** die Option **Manuell** aus.
10.	Verwenden Sie die Schaltfläche **Add**, um die _Adressnetzmaske_ und das _Gateway_ aus _Tabelle 1 - Werte für die Bereitstellung_ einzufügen.
11.	Geben Sie die _IP-Adresse des DNS-Servers_ aus "Tabelle 1 - Werte für die Bereitstellung" ein.
12.	Klicken Sie auf die Schaltfläche **Routes** und fügen Sie die folgenden statischen Routen hinzu: _10.0.0.0/8 und 161.26.0.0/16_ mit einer Gateway-IP-Adresse (_BCR-IP-Adresse_) aus Tabelle 1 (Werte für die Bereitstellung) als Gateway. Diese statische Route ermöglicht es dem Proxy-Server, den DNS-Server zu erreichen.
13.	Klicken Sie auf **Save** und stellen Sie dann sicher, dass die Ethernet-Schnittstelle aktiv ist und als verbunden angezeigt wird. Klicken Sie auf **Done** und **Begin Installation**.
14.	Legen Sie im weiteren Verlauf der Installation ein Rootkennwort fest und richten Sie einen Benutzer ein.
15.	Wenn die Installation abgeschlossen ist, melden Sie sich als Benutzer an und geben Sie dann den Befehl _ping vmware.com_ ein. Der Name wird in eine IP-Adresse aufgelöst und Sie erhalten eine Antwort. Wenn Sie keine Antwort erhalten, überprüfen Sie die IP-Adressen, Firewallregeln und NAT-Einstellungen.

#### Squid installieren und konfigurieren
{: #vum-init-config-install-cfg-squid}

Bei Squid bestehen keine Mindestvoraussetzungen an die Hardware, aber die Menge an RAM kann je nach den Benutzern, die über Ihren Proxy auf das Internet zugreifen, und den im Cache gespeicherten Objekten variieren. Da nur VUM auf den Proxy-Server zugreift und der Cache nicht aktiviert ist, wird nur eine weniger umfangreiche VM konfiguriert.

1. Melden Sie sich entweder über die Webkonsole oder über die ferne Konsole von vSphere Web Client beim Proxy-Server als Benutzer an und führen Sie dann `su` als Rootbenutzer aus.
2. Bevor Sie Pakete installieren, müssen Sie den folgenden Befehl verwenden, um das System und die Pakete zu aktualisieren:
  `yum -y update`

3. Um Squid zu installieren, müssen Sie das EPEL-Repository auf dem System installieren, da Squid im yum-Standardrepository nicht verfügbar ist. Führen Sie den folgenden Befehl aus, um das EPEL-Repository zu installieren:
  `yum -y install epel-release`

4. Für die Aktualisierung und Bereinigung sind folgende Befehle zu verwenden:

  `yum -y update`
  `yum clean all`

5. Squid wird mit dem folgenden Befehl installiert: `yum -y install squid`.
6. Starten Sie nach der Installation sofort Squid, indem Sie den folgenden Befehl verwenden: `systemctl start squid`.
7. Führen Sie den folgenden Befehl aus, um Squid automatisch beim Booten zu starten: `systemctl enable squid`.
8. Stellen Sie sicher, dass Squid ausgeführt wird, indem Sie den folgenden Befehl ausführen: `systemctl status squid`.
9. Die CentOS-Firewall muss den Zugriff auf den Squid-Port zulassen (TCP 3128); verwenden Sie dazu den folgenden Befehl: `firewall-cmd -add-port=3128/tcp -permanent`.
10. Wenn Sie die Regel speichern und den Service erneut starten möchten, verwenden Sie den folgenden Befehl: `firewall-cmd -reload`.

## Ersteinrichtung von VUM
{: #vum-init-config-init-setup-vum}

Konfigurieren Sie VUM so, dass der Proxy-Server für den Zugriff auf die Repositorys im Internet verwendet wird.
1. Verwenden Sie den vSphere Web Client, um zu **Home** > **Update Manager** zu navigieren. Klicken Sie auf Ihren vCenter Server.
2. Wählen Sie die Registerkarte **Verwalten** aus und klicken Sie auf **Einstellungen**.
3. Wählen Sie **Downloadeinstellungen** aus und klicken Sie dann unter _Proxy-Einstellungen_ auf **Bearbeiten**.
4. Aktivieren Sie das Feld **Proxy verwenden** und geben Sie die _IP-Adresse des Proxy-Servers_ und den _Port 3128_ ein. Klicken Sie dann auf **OK**. Der Konnektivitätsstatus ändert sich in _Wird geprüft_ und dann in _Verbunden_.
    **Hinweis**: Machen Sie sich keine Sorgen, wenn beim Testen der Verbindung zum Proxy-Server die Nachricht ``Some URLs have been accessed successfully, but others are inaccessible`` angezeigt wird.
5. Klicken Sie auf **Jetzt herunterladen**. Im Teilfenster _Letzte Tasks_ sollte diese Aktivität dann als abgeschlossen angezeigt werden.
6. Wenn diese Aktivität fehlschlägt, starten Sie die vCenter Server Appliance (vCSA) erneut:
  1. Melden Sie sich an der Managementschnittstelle für vCSA unter `https://vcsaFQDN:5480` als **root** an.
  2. Klicken Sie auf **Zusammenfassung** und anschließend auf **Warmstart**.
  3. Klicken Sie im Bestätigungsfenster auf **Ja**, um die Operation zu bestätigen.

## Zugehörige Links
{: #vum-init-config-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [{{site.data.keyword.vmwaresolutions_full}} Demos](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (Vorführungen)
