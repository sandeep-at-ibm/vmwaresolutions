---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware - Bereitstellung und Verwaltung
{: #kmip-implementation}

## Schlüsselmanagementserver verbinden
{: #kmip-implementation-connecting-kms}

Um die vSphere- oder die vSAN-Verschlüsselung mithilfe von KMIP for VMware on {{site.data.keyword.cloud_notm}} zu aktivieren, müssen Sie die folgenden Tasks ausführen:

1. [Konto für Serviceendpunkte aktivieren](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started).
2. Erstellen Sie eine [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial)-Instanz.
3. Erstellen Sie einen Stammschlüssel für Kunden (customer root key, CRK) innerhalb von IBM Key Protect.
4. Erstellen Sie [Serivce-ID und API-Schlüssel](/docs/iam?topic=iam-serviceidapikeys) für Identity and Access Management (IAM) zur Verwendung mit KMIP for VMware. Erteilen Sie dieser Service-ID Zugriff auf die Plattformanzeigefunktion und Service-Schreibzugriff für Ihre Key Protect-Instanz.
5. Erstellen Sie über den {{site.data.keyword.cloud_notm}}-Katalog eine [KMIP for VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)-Instanz.
6. Erstellen Sie in VMware vCenter einen KMS-Cluster (Key Management Server) mit zwei Servern, jeweils einem für jeden KMIP for VMware-Endpunkt in Ihrer ausgewählten Region.
7. Wählen Sie eine der of VMware-Methoden aus, um ein KMS-Clientzertifikat in vCenter zu generieren oder zu installieren.
8. Exportieren Sie die öffentliche Version des Zertifikats und konfigurieren Sie sie als zulässiges Clientzertifikat in Ihrer KMIP for VMware-Instanz.

## Verschlüsselung aktivieren
{: #kmip-implementation-enable-encrypt}

Wenn Sie die vSAN-Verschlüsselung verwenden möchten, bearbeiten Sie die allgemeinen vSAN-Einstellungen in Ihrem vCenter-Cluster und aktivieren Sie das Kontrollkästchen für die Verschlüsselung.

Bei der vSAN-Statusprüfung werden möglicherweise in regelmäßigem Abstand Warnungen ausgegeben, die besagen, dass von keinem Ihrer vSphere-Hosts eine Verbindung zum KMS-Cluster hergestellt werden kann. Diese Warnungen treten auf, da es für die Verbindung der vSAN-Statusprüfung zu schnell zu einer Zeitlimitüberschreitung kommt. Sie können diese Warnungen ignorieren.{:note}

Wenn Sie die vSphere-Verschlüsselung verwenden möchten, bearbeiten Sie die Speicherrichtlinien für virtuelle Maschinen so, dass eine Plattenverschlüsselung erforderlich ist.

## Schlüsselrotation
{: #kmip-implementation-key-rotation}

[Aktivieren Sie die Rotation Ihres Stammschlüssels für Kunden (Customer Root Key, CRK) für Key Protect](/docs/services/key-protect?topic=key-protect-rotating-keys) über die {{site.data.keyword.cloud_notm}}-Konsole oder die API.

Für eine VMware vSAN-Verschlüsselung lassen Sie die Ihre VMware-Schlüsselverschlüsselungsschlüssel (key encrypting keys, KEK) und optional die Datenverschlüsselungsschlüssel (data encrypting keys, DEK) über die allgemeinen vSAN-Einstellungen in Ihrem vCenter-Cluster rotieren.

Für eine VMware vSphere-Verschlüsselung lassen Sie Ihre VMware-KEKs und (optional) -DEKs rotieren, indem Sie den PowerShell-Befehl **Set-VMEncryptionKey** verwenden.

## Schlüsselwiderruf
{: #kmip-implementation-key-revocation}

Sie können alle Schlüssel, die von KMIP for VMware verwendet werden, widerrufen, indem Sie den ausgewählten CRK aus Key Protect löschen.

Wenn Schlüssel widerrufen werden, werden alle Daten, die durch diese Schlüssel und Ihre KMIP for VMware-Instanz geschützt sind, durch diese Methode geschreddert. VMware behält beim Einschalten eines ESXi-Hosts einige Schlüssel bei, weshalb Sie Ihren vSphere-Cluster neu starten müssen, um sicherzustellen, dass keine verschlüsselten Daten mehr verwendet werden.
{:important}

KMIP for VMware speichert einzelne eingeschlossene KEK in Ihrer Key Protect-Instanz unter Verwendung von Namen, die den VMware bekannten Schlüssel-IDs zugeordnet sind. Sie können einzelne Schlüssel löschen, um die Verschlüsselung einzelner Platten oder Laufwerke zu widerrufen.

VMware löscht keine Schlüssel vom KMS, wenn eine VM mit verschlüsselten Platten aus dem Bestand entfernt wird. Dies ermöglicht die Wiederherstellung dieser VM aus dem Backup oder bei ihrer Wiederherstellung im Bestand. Wenn Sie diese Schlüssel widerrufen und alle Sicherungen durch Verschlüsselung ungültig machen möchten, müssen Sie die Schlüssel nach dem Löschen Ihrer VMs aus Key Protect löschen.
{:note}

## Zugehörige Links
{: #kmip-implementation-related}

* [Lösungsübersicht](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)
* [Lösungsdesign](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-design)
* [IBM Key Protect](/docs/services/key-protect?topic=key-protect-getting-started-tutorial)
