---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# Bereitstellung des HCX-Clients
{: #hcxclient-vcs-client-deployment}

Eine HCX-Mindestinstallation besteht aus einer einzigen Bereitstellung auf Cloud- und Clientseite.

Die HCX-Clientseite kann in jeder Version von vSphere bereitgestellt werden, die von HCX unterstützt wird, vorausgesetzt, dass zwischen der Client- und der Cloudseite eine Netzkonnektivität besteht.

## Voraussetzungen
{: #hcxclient-vcs-client-deployment-req}

| Komponente | CPU-Anzahl | Speicher (GB) | Platte (GB) |
|--------|--------|---------|-------|
| HCX Manager | 4 | 12 GB |  60 GB |
| HCX Interconnect (HCX-IX) | 4 | 3 GB |  2 GB |
| HCX Network Extension (HCX-NE) | 4 | 3 GB |  2 GB |
| HCX WAN Optimizer (HCX-WAN) | 8 | 14 GB |  100 GB |

## Lizenzierung der Clients
{: #hcxclient-vcs-client-deployment-licensing}

HCX ist ein Service. HCX wird pro Standort und pro virtuelle Maschine (VM) lizenziert, die über Lizenzserver verwaltet wird, die von VMware verwaltet werden. Die cloud- und clientseitigen Instanzen von HCX erfordern eine Kommunikation mit der VMware-Registrierungsstandort über ihren gesamten Lebenszyklus.
- Der Datenverkehr für 80 und 443 muss auf `https://connect.hybridity.vmware.com` zugreifen können.
- Ein Registrierungsschlüssel für die einmalige Verwendung wird von der {{site.data.keyword.vmwaresolutions_full}}-Konsole für die clientseitige Installation angegeben. Für jede clientseitige HCX-Installation ist ein Schlüssel erforderlich.

### Vorgehensweise zum Bestellen lokaler HCX-Lizenzen
{: #hcxclient-vcs-client-deployment-license-ordering-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Blättern Sie abwärts zur Tabelle **Lokale HCX-Lizenzen** und klicken Sie dann auf **Neu bereitstellen**.
3. Geben Sie den Lizenznamen an.
4. Klicken Sie auf den Link bzw. die Links für die Bedingungen, die für Ihre Bestellung gelten, und stellen Sie sicher, dass Sie mit diesen Bedingungen einverstanden sind, bevor Sie die Lizenz bestellen.
5. Klicken Sie auf **Bereitstellung**.

## Anforderungen an IP-Adressen
{: #hcxclient-vcs-client-deployment-client-ip-reqs}

Für die Bereitstellung von HCX muss sowohl lokal als auch in der Zielinstanz von IBM Cloud die richtige Anzahl von IP-Adressen verfügbar sein.

* vMotion-Adresse
  Die Verwaltung eines separaten Netzes für vMotion ist im lokalen Rechenzentrum gängige Praxis. Das Cloud-Gateway muss Zugriff auf das vMotion-Netz haben. Ist dies nicht der Fall, wird für die Kommunikation mit dem vMotion-Netz eine zusätzliche IP-Adresse benötigt.

* Lokal
  * Eine IP-Adresse für HCX Manager Appliance.
  * Eine für jede Interconnect Appliance; wenn ein separates vMotion-Netz vorhanden ist, muss eine hinzugefügt werden.
  * Eine für jede Standardnetzerweiterung

* IBM Cloud
  * Zwei IP-Adressen pro HCX Manager-Appliance, die mit IBM Cloud verbunden ist. Die Adressen können verwendet werden, um eine Verbindung zum Internet oder zu einer oder mehreren Direktverbindungen herzustellen.
  * Wenn eine separate vMotion-Netzverbindung vorhanden ist, muss eine hinzugefügt werden.

## Clientseitiger OVA-Download
{: #hcxclient-vcs-client-deployment-client-ova}

HCX wird auf der Clientseite vom Benutzer bereitgestellt; hierfür sind für die vCenter-Quelleninstanz Berechtigungen auf Administratorebene erforderlich. Gegenwärtig umfasst die clientseitige HCX Manager-OVA ca. 1,7 GB. Wenn Sie zur Bestellung von HCX die {{site.data.keyword.vmwaresolutions_short}}-Konsole verwenden, wird eine URL mit einem Link zum Download der HCX-Version für die Clientseite angegeben, die mit der Version von HCX übereinstimmt, die auf der Cloudseite angegeben wurde. Dieser Link wird in der Benutzerschnittstelle (UI) der cloudseitigen HCX Manager-Instanz bereitgestellt.

Außerdem wird ein Registrierungsschlüssel für die einmalige Verwendung angegeben. Führen Sie die folgenden Schritte aus, um die Benutzerregistrierung zu konfigurieren.

1. Laden Sie die HCX-Client- (Unternehmens-) OVA über den Link herunter, der in der cloudseitigen HCX-Benutzerschnittstelle angegeben wird.
    1. Melden Sie sich über die von IBM bereitgestellte HCX-Registrierungs-Benutzerschnittstelle an der cloudseitigen HCX-Benutzerschnittstelle an.
    2. Verwenden Sie die Cloud-vCenter-ID und das Cloud-Kennwort, um sich bei der Benutzerschnittstelle anzumelden.
    3. In der Registerkarte **Verwaltung** wählen Sie **Download-Link anfordern** aus, um die clientseitige OVA herunterzuladen. Verwenden Sie ein für die vCenter-Quelleninstanz, in der die OVA bereitgestellt ist, lokales "Sprungfeld", um diesen Schritt auszuführen.

## Installation und Konfiguration von HCX für die Quelle
{: #hcxclient-vcs-client-deployment-install-cfg-src}

Die lokale Installation umfasst die Bereitstellung der HCX-Management-Appliance und ihre Registrierung in der vCenter-Umgebung.

### HCX Manager-Appliance installieren
{: #hcxclient-vcs-client-deployment-install-cfg-src-install-hma}

Installieren Sie die HCX Manager-Appliance in der lokalen vCenter-Instanz.
1. Melden Sie sich bei **Meine VMware** an und laden Sie die OVA-Datei für Hybrid-Cloud-Services von der Produktdownloadseite herunter.
2. Öffnen Sie einen Browser und melden Sie sich bei vSphere Web Client an. Zeigen Sie die Registerkarte **Home** an.
3. Klicken Sie in der Liste **Bestands-Baumstrukturen** auf **Host und Cluster**.
4. Erweitern Sie die Hierarchie, sodass die Rechenzentren angezeigt werden.
5. Klicken Sie mit der rechten Maustaste auf das Ziel-Rechenzentrum und wählen Sie im Menü die Option **OVF-Vorlage bereitstellen** aus. Es kann einige Sekunden dauern, bis das Menüelement **OVF-Vorlage bereitstellen** angezeigt wird.
6. Wählen Sie **OVF-Vorlage bereitstellen** aus.
  1. Wählen Sie **Lokale Datei** aus und klicken Sie auf **Durchsuchen**, um die OVA-Datei zu suchen, die auf den Computer heruntergeladen wurde. Klicken Sie auf **Weiter**.
  2. Aktivieren Sie auf der Seite **Details prüfen** das Kontrollkästchen **Zusätzliche Konfigurationsoptionen akzeptieren** und klicken Sie auf **Weiter**.
  3. Blättern Sie auf der Seite **EULAs akzeptieren** nach unten, um die VMware-Benutzerlizenz zu überprüfen. Klicken Sie auf **Akzeptieren** und dann auf **Weiter**.
  4. Bearbeiten Sie auf der Seite **Name und Ordner auswählen** bei Bedarf den Namen und wählen Sie den Ort für Hybrid-Cloud-Services aus. Klicken Sie auf **Weiter**.
  5. Wählen Sie auf der Seite **Ressource auswählen** die Installationsposition aus.
  6. Wählen Sie auf der Seite **Speicher auswählen** den Speicher für Hybrid-Cloud-Services aus und klicken Sie auf **Weiter**. In der Liste **Format der virtuellen Platte auswählen** können Sie entweder **Thin Provisioning** oder **Thick Provisioning** auswählen.
  7. Ordnen Sie auf der Seite **Netze einrichten** den Adapter für Hybrid-Cloud-Services einem Hostnetz zu, das Sie aus der Liste **Ziel** ausgewählt haben.
7. Geben Sie auf der Seite **Angepasste Vorlagen** die für die Umgebung spezifischen Werte ein:
  * Verwenden Sie als Kennwort sowohl für die Befehlszeilenschnittstelle (CLI) als auch für die Webbenutzerschnittstelle den Standardbenutzernamen **admin**. Erforderlich sind die Rolle des **admin**-Benutzers und ein Kennwort für die Anmeldung bei der Webbenutzerschnittstelle sowie auch ein **root**-Benutzerkonto, dessen Kennwort festgelegt werden kann.
  * Geben Sie das Kennwort für den **admin**-Benutzer der CLI ein und wiederholen Sie es.
  * Geben Sie das Kennwort für den **root**-Benutzer ein und wiederholen Sie es. Wenn zu einem späteren Zeitpunkt Unterstützung von VMware Global Support Services (GSS) benötigt wird, muss dieses Kennwort möglicherweise weitergegeben werden, damit Systemfehler behoben werden können.
  * Als Netzeigenschaften geben Sie den Hostnamen für die HCX Manager-VM ein. Geben Sie die Netz-IPv4-Adresse, das IPv4-Präfix (CIDR) und das Standardgateway ein. In der folgenden Tabelle sind Beispielwerte aufgeführt:

Tabelle 1. Beispielwerte für Netzeigenschaften

| Feld                    | Wert           |
|--------------------------|-----------------|
| Hostname                 | HCM_1           |
| IPv4-Adresse für Netz 1   | 192.168.200.101 |
| IPv4-Präfix für Netz 1    | 24              |
| Standard-IPv4-Gateway     | 192.168.200.1   |
| IPv6-Adresse für Netz 1   |                 |
| IPv6-Präfix für Netz 1    |                 |

8. Zeigen Sie die Seite für vService-Bindungen an. Klicken Sie auf **Weiter**, um fortzufahren.
9. Befolgen Sie auf der Seite **Bereit zum Abschließen** die folgenden Schritte:
  * Aktivieren Sie das Kontrollkästchen **Nach Bereitstellung einschalten**.
  * Überprüfen Sie die Einstellung für Hybrid-Cloud-Services und klicken Sie auf **Fertigstellen**. Es kann einige Minuten dauern, bis die Hybrid-Cloud-Services-Appliance eingeschaltet ist.
  * Zur Überprüfung des Status wechseln Sie zur Homepage von vSphere Web Client, gehen Sie in der Registerkarte **Home** zu **Bestand** und klicken Sie auf **Hosts und Cluster**. Erweitern Sie die Hierarchie der Rechenzentren und klicken Sie auf die virtuelle Hybrid-Cloud-Services-Maschine, um im mittleren Teilfenster eine Zusammenfassung anzuzeigen.
  * Zeigen Sie die Registerkarte **Zusammenfassung** an. In der Konsole wird **Eingeschaltet** angezeigt und das Symbol **Wiedergabe** ist grün.
10. HCX Manager ist eingeschaltet und bereit für die Registrierung beim lokalen vCenter.

## Erstkonfiguration der HCX Manager-Appliance
{: #hcxclient-vcs-client-deployment-inital-config}

1. Stellen Sie sicher, dass die virtuelle Appliance des Hybrid-Cloud-Service über abgehenden Zugriff auf `https://connect.hcx.vmware.com` verfügt.
2. Melden Sie sich an der Administratorschnittstelle für die virtuelle Appliance des Hybrid-Cloud-Service `https://<IP>:9443` unter Verwendung von **admin** an.
3. Geben Sie den Lizenzschlüssel an, der in den clientseitigen Voraussetzungen erfasst wurde.
4. Position des HCX-Cloud-Rechenzentrums
    - Geben Sie die Stadt ein, deren Entfernung zu dem Rechenzentrum am niedrigsten ist, in dem sich die HCX-Cloud-Instanz befindet. Wenn die Stadt nicht angegeben ist, wählen Sie nächstgrößere Stadt aus.
5. Geben Sie den Systemnamen an.

## Zertifikat des vSphere-Servers importieren
{: #hcxclient-vcs-client-deployment-import-cert}

1. Melden Sie sich an der Administratorschnittstelle `https://<IP>:9443` von HCX Manager an.
2. Wählen Sie die Registerkarte **Verwaltung** unter **Zertifikat** -> **Anerkanntes CA-Zertifikat** aus.
3. Importieren Sie die Website mit dem vSphere-Server.
   1. Wählen Sie den Import von Zertifikaten von der URL aus und geben Sie die cloudseitige HCX-Registrierungs-URL ein.
     * Sao Paulo: `https://ssao01dirhcx01.vmware-solutions.cloud.ibm.com`.

## Vorgehensweise zum Registrieren von HCX Manager bei vCenter/SSO/NSX
{: #hcxclient-vcs-client-deployment-reg-vcenter}

1. Melden Sie sich bei der virtuellen Hybrid-Cloud-Services-Appliance an.
2. Führen Sie in der **Dashboardanzeige** die folgenden Schritte aus:
  1. Wählen Sie im linken Teilfenster unter **Systeme konfigurieren** die Option "vCenter" aus.
  2. Klicken Sie oben rechts auf **vCenter hinzufügen**.
  3. Geben Sie die IP-Adresse von vCenter Server im Format `https://vCenter-host-name` oder `https://vCenter-IP-address` ein. Beispiel: `https://My-vCenter` oder `https://10.108.26.211`
  4. Geben Sie Benutzername und Kennwort für vCenter Server ein. Das verwendete Konto muss über die Rolle des vCenter-Administrators verfügen.
  5. Klicken Sie auf **OK**. Wenn die Nachricht _Die Anwendung muss neu gestartet werden_ angezeigt wird, führen Sie keinen Neustart aus.
3. Konfigurieren Sie SSO bzw. den Suchservice.
  6. Klicken Sie auf die Registerkarte **Verwalten**.
  7. Klicken Sie auf **Bearbeiten** neben dem Textfeld **URL des Suchservice**.
  8. Geben Sie den Netzserviceendpunkt für die Suche im folgenden Format an:
    * Für vCenter Server 6.5: `https://psc/`.
  9.  Geben Sie bei Bedarf NSX-Details an.
  10. Klicken Sie auf **OK**. Führen Sie keinen Neustart aus, wenn eine Nachricht zum Neustart der Web-Engine angezeigt wird.
4. Klicken Sie auf die Registerkarte **Zusammenfassung** und suchen Sie den Abschnitt **Hybriditäts-Managementkomponenten**. Stoppen und starten Sie sowohl die Anwendungsengine als auch die Web-Engine.
5. Um die Registrierung abzuschließen, melden Sie sich von vSphere Web Client ab. Melden Sie sich wieder an vSphere Web Client an und stellen Sie sicher, dass die HCX-Registerkarte angezeigt wird.

## Ergebnisse
{: #hcxclient-vcs-client-deployment-reg-vcenter-results}

Beachten Sie, dass jetzt das Symbol für **Hybrid-Cloud** vorhanden ist, sowie das Menüelement **Hybrid-Cloud-Services** auf der linken Seite. Durch die Registrierung von Hybrid-Cloud-Services werden diese Bezeichnungen aktualisiert. Im Bestand ändert sich die Symbolbezeichnung in **Hybrid-Cloud-Services**.

## Zugehörige Links
{: #hcxclient-vcs-client-deployment-related}

* [Glossar der HCX-Komponenten und -Begriffe](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Installationsumgebung vorbereiten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Lokales HCX-Servicenetz](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud-Migrationen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Überwachung von Parametern und Komponenten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Fehlerbehebung für HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
