---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---
# Installation und Konfiguration von HCX für die Quelle
{: #hcx-archi-install-cfg-src}

Die lokale Installation umfasst die Bereitstellung der HCX-Management-Appliance und ihre Registrierung bei vCenter und mindestens einem für VCS HCX aktivierten Cloudendpunkt.

## HCX Manager-Appliance installieren
{: #hcx-archi-install-cfg-src-install-hma}

Installieren Sie die HCX-Manager-Appliance in der lokalen vCenter-Instanz.

1. Melden Sie sich bei **Meine VMware** an und laden Sie die OVA-Datei für Hybrid-Cloud-Services von der Produktdownloadseite herunter.
2. Öffnen Sie einen Browser und melden Sie sich bei vSphere Web Client an. Diese Task kann nicht über den vSphere-Client ausgeführt werden. Zeigen Sie die Registerkarte **Home** an.
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
  * Als Netzeigenschaften geben Sie den Hostnamen für die HCX-Manager-VM ein. Geben Sie die Netz-IPv4-Adresse, das IPv4-Präfix (CIDR) und das Standardgateway ein. In der folgenden Tabelle sind Beispielwerte aufgeführt:

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
  * Zeigen Sie die Registerkarte **Zusammenfassung** an. In der Konsole wird **Eingeschaltet** angezeigt und die Schaltfläche **Wiedergabe** ist grün.
10. Der HCX-Manager ist eingeschaltet und bereit für die Registrierung bei vCenter.

## Zugehörige Links
{: #hcx-archi-install-cfg-src-related}

* [Installationsumgebung vorbereiten](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-prep-install)
