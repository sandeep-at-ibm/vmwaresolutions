---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Upgrade für Instanzen ausgehend von älteren Releases als V1.4 durchführen

## Problem

Die Instanznetztopologie in V1.4 und höheren Releases unterscheidet sich von den Releases vor V1.4. Aufgrund dieser Änderung können die Instanzen, die in Releases vor V1.4 bereitgestellt wurden, in ihrem Zustand nicht im aktuellen Release verwendet werden.

## Lösung

In V1.4 und höheren Releases sind verschiedene Netztopologieerweiterungen für Ihre Instanzen verfügbar:
* (Alle Instanzen): Es gibt eine optimierte Netzkonfiguration. Da das von Ihnen verwendete {{site.data.keyword.cloud}}-Konto entweder ein Konto des Typs "VRF" (Virtual Routing and Forwarding) sein muss oder bei einem klassischen Konto (ohne VRF) die VLAN Spanning-Funktion aktiviert sein muss, wird eine zweite portierbare IP-Adresse nicht benötigt. Zur Bereitstellung ist nur die primäre portierbare IP-Adresse für die {{site.data.keyword.cloud_notm}}-Infrastruktur erforderlich.
* (Nur für Cloud Foundation-Instanzen): Es gibt eine Funktion zur Bereitstellung mit mehreren Standorten mit Servern für Microsoft Windows AD SSO (Active Directory Single Sign-On) und DNS.

Falls Sie Ihre Instanzen aus Releases vor V1.4 nicht migriert oder gelöscht haben, sind sie möglicherweise weiterhin im Lesezugriffsmodus in der {{site.data.keyword.vmwaresolutions_short}}-Konsole sichtbar. Solche Instanzen sind in der Benutzerschnittstelle durch ein Warnsymbol als **Veraltet** gekennzeichnet.

**Hinweis:** Die in den Instanzeigenschaften angezeigten Informationen geben die Daten gemäß dem Release V1.4 wieder und werden nicht mehr aktualisiert.

Für die Instanzen aus einem Release vor V1.4 sind die folgenden Aktionen verfügbar:
*  Sie können die Informationen auf der Seite mit den Instanzdetails anzeigen.
*  Sie können Informationen zur Instanzsicherung anzeigen.
*  Sie können vSphere Web Client öffnen und die Instanz in vCenter verwenden.
*  Sie können die Instanzwiederherstellung anfordern, indem Sie ein {{site.data.keyword.cloud_notm}}-Support-Ticket öffnen.
*  Sie können die Instanz löschen.

Alle anderen Aktionen sind für Instanzen aus Releases vor V1.4 nicht mehr verfügbar.

Falls Sie Instanzen aus Releases vor V1.4 verwenden und auch weiterhin verwenden wollen, können Sie für diese Instanzen ein Upgrade durchführen, indem Sie neue Instanzen erstellen und anschließend Ihre vorhandenen Konfigurationen in diese neuen Instanzen versetzen.

Führen Sie zum Versetzen Ihrer Instanzen aus Releases vor V1.4 auf neue Instanzen die folgenden Schritte in vSphere Web Client aus:
1. Exportieren Sie alle virtuellen Maschinen (VMs) aus der Instanz aus einem Release vor V1.4.
2. Erstellen Sie im aktuellen Release eine Instanz.
3. Importieren Sie alle VMs, die Sie in **Schritt 1** exportiert haben.
4. Verwenden Sie die neue Instanz.

Weitere Informationen zum Exportieren und Importieren von VMs finden Sie in der VMware vSphere-Dokumentation.

Falls Sie bei der Verwendung von {{site.data.keyword.vmwaresolutions_short}} Hilfe benötigen, setzen Sie sich über einen der Unterstützungskanäle mit dem [IBM Support](trbl_support.html) in Verbindung.
