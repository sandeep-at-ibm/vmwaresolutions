---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-05"

---

# Typen von VMware-Software-Updates

VMware verwendet die folgenden Begriffe, um Software-Updates zu beschreiben.

Tabelle 1. VMware-Software-Updates - Begriffsbestimmungen

| Begriff | Definition |
|:------- |:----------- |
| Bulletin |	Eine Gruppierung von ein oder mehr VIBs. Bulletins werden in Metadaten definiert. |
| Depot |	Eine logische Gruppierung von VIBs und zugehörigen Metadaten, die online veröffentlicht werden. |
| Host-Upgrade-Image |	Ein ESXi-Image, das Sie in das Update-Manager-Repository importieren und für das Upgrade von ESXi 5.5- oder ESXi 6.0-Hosts auf ESXi 6.5 verwenden können. |
| Erweiterung | 	Ein Bulletin, das eine Gruppe von VIBs definiert, um eine optionale Komponente zu einem ESXi-Host hinzuzufügen. Eine Erweiterung wird normalerweise von einem Drittanbieter bereitgestellt, der auch für Patches oder Updates für die Erweiterung verantwortlich ist. |
| Metadaten |	Zusätzliche Daten, die Abhängigkeitsinformationen, Textbeschreibungen, Systemvoraussetzungen und Bulletins definieren. |
| Offline-Bundle-ZIP-Datei |	Ein Archiv, das VIBs und die entsprechenden Metadaten in einem eigenständigen Paket zusammenfasst, mit dem ein Offline-Patching möglich ist. Sie können keine Offlinepakete oder Offline-Bundles von Drittanbietern verwenden, die Sie aus angepassten VIB-Gruppen für das Host-Upgrade von ESXi 5.5 oder ESXi 6.0 auf ESXi 6.5 generiert haben. |
| Patch |	Ein Bulletin, das ein oder mehr VIBs gruppiert, um ein bestimmtes Problem oder eine bestimmte Erweiterung zu beheben. |
| Roll-up |	Eine Reihe von Patches, die zur Vereinfachung von Download und Bereitstellung zusammengefasst wurden. |
| VA-Upgrade |	Updates für eine virtuelle Appliance, die der Anbieter als Upgrade erachtet. |
| VIB |	Ein VIB (vSphere Installation Bundle) ist ein einzelnes Softwarepaket. |

### Zugehörige Links

* [VMware HCX on IBM Cloud Solution](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
