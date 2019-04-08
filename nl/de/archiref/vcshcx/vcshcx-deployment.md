---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

subcollection: vmwaresolutions


---

# Cloud- und Clientbereitstellung
{: #vcshcx-deployment}

Eine HCX-Mindestinstallation besteht aus einer einzigen Bereitstellung auf Cloud- und Clientseite. Die HCX-Clientseite kann in jeder Version von vSphere bereitgestellt werden, die von HCX unterstützt wird, vorausgesetzt, dass zwischen der Client- und der Cloudseite eine Netzkonnektivität besteht.

## Voraussetzungen
{: #vcshcx-deployment-req}

- HCX-Manager – CPU-Anz. 4, Speicher 12 G, Platte 60 G
- CGW – CPU-Anz. 8, Speicher 3 G, Platte 2 G
- L2C – CPU-Anz. 8, Speicher 3 G, Platte 2 G
- WAN-Opt. – CPU-Anz. 8, Speicher 14 G, Platte 100 G

## Cloud
{: #vcshcx-deployment-cloud}

Die cloudseitige HCX-Bereitstellung wird von der {{site.data.keyword.vmwaresolutions_full}}-Automatisierung abgewickelt. In der Standardkonfiguration wird die öffentliche Portgruppe für die Konfiguration der Endpunktkonnektivität aller Paketkomponenten verwendet. Die Paketkomponenten auf der Cloudseite werden mit ihren Endpunktschnittstellen bereitgestellt, die mit öffentlichen IP-Adressen konfiguriert sind, da es sich um sicherheitsgehärtete Appliances handelt. Es ist möglich, sie hinter einer Firewall bereitzustellen. Die Verbindung von Client- und Cloudseite zueinander über einen vorhandenen VPN-Tunnel wird nicht unterstützt. Wenn Sie für die HCX-Endpunktkonnektivität das private Netz verwenden möchten, können Sie eine Bereitstellung des HCX-Produktpakets für die Cloudseite für privates Netz bestellen, die über einen dedizierten Link hinweg verwendet wird, z. B. MPLS.

## Client
{: #vcshcx-deployment-client}

Das clientseitige HCX wird vom Benutzer bereitgestellt und erfordert für die vCenter-Quelleninstanz Berechtigungen auf Administratorebene. Gegenwärtig umfasst die clientseitige HCX-Manager-OVA ca. 1,7 GB. Wenn Sie zur Bestellung von HCX die {{site.data.keyword.vmwaresolutions_short}}-Konsole verwenden, wird eine URL mit einem Link zum Download der HCX-Version für die Clientseite angegeben, die mit der Version von HCX übereinstimmt, die auf der Cloudseite angegeben wurde. Dieser Link wird in der Benutzerschnittstelle (UI) des cloudseitigen HCX-Managers bereitgestellt.

Außerdem wird ein Registrierungsschlüssel für die einmalige Verwendung angegeben. Führen Sie die folgenden Schritte aus, um die Benutzerregistrierung zu konfigurieren.

1. Laden Sie die HCX-Client- (Unternehmens-) OVA über den Link herunter, der in der cloudseitigen HCX-Benutzerschnittstelle angegeben wird.
    1. Melden Sie sich über die von IBM bereitgestellte HCX-Registrierungs-Benutzerschnittstelle an der cloudseitigen HCX-Benutzerschnittstelle an.
    2. Verwenden Sie die Cloud-vCenter-ID und das Cloud-Kennwort, um sich bei der Benutzerschnittstelle anzumelden.
    3. In der Registerkarte **Verwaltung** wählen Sie **Download-Link anfordern** aus, um die clientseitige OVA herunterzuladen. Verwenden Sie ein für die vCenter-Quelleninstanz, in der die OVA bereitgestellt ist, lokales "Sprungfeld", um diesen Schritt auszuführen.
2. Melden Sie sich beim vSphere C++-Client (oder bei dem Web-Client mit funktionierendem Snap-in für die Clientintegration) an und importieren Sie die OVA, die den vCenter-Importassistenten verwendet.
    1. Stellen Sie sicher, dass das Netz, für das der HCX-Manager konfiguriert ist, Zugriff sowohl auf die vCenter-Quelleninstanz als auch auf das Internet hat.  
    2. Geben Sie auf Aufforderung den Registrierungsschlüssel ein. (Wenn Sie über die Snap-in-Konfiguration für Clienttools verfügen, verwenden Sie den Web-Client.)  
3. Melden Sie sich beim vCenter-Web-Client ab und wieder an. Das Menüauswahlsymbol **HCX** wird unter dem Hauptanzeigenmenü angezeigt.
4. Bei selbst signierten Zertifikaten wählen Sie das Menüelement "HCX" aus, um die HCX-Snap-in-Benutzerschnittstelle zu öffnen. Wählen Sie die Registerkarte **Verwaltung** aus.
    1. Wählen Sie den Import von Zertifikaten von der URL aus und geben Sie die cloudseitige HCX-Registrierungs-URL ein, die in der {{site.data.keyword.vmwaresolutions_short}}-Konsole für HCX angegeben ist.
    2. Wählen Sie im Fensterbereich **Standortpaarungen** in der Registerkarte **Dashboard** die Option **Neue Standortpaarung** aus.
    3. Befolgen Sie die Eingabeaufforderungen und geben Sie die HCX-cloudseitige Registrierungs-URL sowie die Administrator-ID und das Kennwort für die cloudseitige vCenter-Instanz an.
    4. Folgen Sie weiter den Eingabeaufforderungen im Assistenten für die Standortregistrierung zur Konfiguration der Paketkomponenten, einschließlich Cloud-Gateway, Layer-2-Konzentrator und WAN-Optimierungsprogramm.  

Für die Clientseite verwenden Sie das Menü **Tasks**, um die Bereitstellung der Paketkomponenten zu überwachen. Für die cloudseitige Bereitstellung verwenden Sie das Menü **Tasks** in der vCenter-Webbenutzerschnittstelle für die jeweilige vCenter Server-Instanz.

Wenn auf beiden Seiten ein Bereitstellungsfehler aufgetreten ist, werden die Bereitstellungen der Paketkomponenten abgebrochen und gelöscht. Nachdem Sie die Fehlerursache ermittelt haben, klicken Sie in der vCenter-Webbenutzerschnittstelle von HCX auf Clientseite auf die Registerkarte **Verbindung** und wählen Sie dann oben im Bildschirm **HCX-Komponenten installieren** aus.

Nach erfolgreicher Bereitstellung der Paketkomponenten und nach einigen Minuten wird für den Tunnel für die CGW- und die L2C-Komponente auf der Registerkarte **Verbindung** der Status **Aktiv** angezeigt.

## Zugehörige Links
{: #vcshcx-deployment-related}

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
