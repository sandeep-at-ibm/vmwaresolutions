---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# Hinweise zu lokalen VMware HCX on IBM Cloud-Instanzen

Lesen Sie die folgenden Hinweise, bevor Sie die HCX on {{site.data.keyword.cloud}}-Instanzen installieren oder löschen, die Sie für die lokale Verwendung, also für die Verwendung in Ihrer lokalen Umgebung, bestellt haben.

**Hinweis:** Eine vCenter Server-Instanz mit HCX on {{site.data.keyword.cloud_notm}} ist auf drei simultane Verbindungen von lokalen Standorten begrenzt.

## Hinweise zur Installation von lokalen HCX on IBM Cloud-Instanzen

Die HCX on {{site.data.keyword.cloud_notm}}-Komponenten müssen sowohl in der {{site.data.keyword.cloud_notm}} als auch in Ihrer lokalen vSphere-Umgebung installiert sein. Es empfiehlt sich, den Service "HCX on {{site.data.keyword.cloud_notm}}" in Ihrer vCenter Server with Hybridity Bundle-Instanz in {{site.data.keyword.cloud_notm}} zu installieren, bevor Sie die lokale HCX on {{site.data.keyword.cloud_notm}}-Instanz installieren. Weitere Informationen finden Sie unter [Hinweise zu HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html).

### Anforderungen an IP-Adressen

Für die vollständige HCX-Funktionalität benötigen Sie mindestens fünf private IP-Adressen; der Internetzugriff muss für diese Adressen zulässig sein.

### Bereitstellungsprozess für lokale HCX on IBM Cloud-Instanzen

Zur erfolgreichen Installation auf der lokalen HCX on {{site.data.keyword.cloud_notm}}-Instanz müssen Sie die folgenden Tasks ausführen.
1. Führen Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole die folgenden Schritte aus:
    1. Klicken Sie im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
    2. Klicken Sie auf die vCenter Server with Hybridity Bundle-Instanz, in der der Service "HCX on {{site.data.keyword.cloud_notm}}" installiert ist. Dies ist die Cloudseite, zu der Sie von Ihrer lokalen vSphere-Umgebung aus eine Verbindung herstellen wollen.
    3. Klicken Sie auf der Registerkarte **Services** auf **Installierte Services**.
    4. Klicken Sie auf die Karte **HCX on {{site.data.keyword.cloud_notm}}**.
    5. Klicken Sie auf **HCX-Cloudkonsole anzeigen** und melden Sie sich dann unter Verwendung der vCenter Server-Berechtigungsnachweise bei der Konsole an, um die Details des cloudseitigen HCX on {{site.data.keyword.cloud_notm}}-Service anzuzeigen.
2. Führen Sie in der **HCX-Cloudkonsole** die folgenden Schritte aus:
    1. Klicken Sie auf die Registerkarte **Verwaltung**.
    2. Klicken Sie auf der Registerkarte **Systemupdates** auf **DOWNLOAD-LINK ANFORDERN**.
    3. Klicken Sie auf **LINK KOPIEREN** und verwenden Sie anschließend diesen Link, um HCX Enterprise Client in eine lokale Umgebung herunterzuladen, die Zugriff auf Ihre lokale vSphere-Umgebung besitzt.
3. Stellen Sie HCX Enterprise Client in VMware vSphere Web Client als virtuelle Appliance für den HCX-Manager (kurz "HCX-Manager") in Ihrer lokalen Umgebung bereit.

   **Hinweis**: Sie müssen den lokalen HCX-Manager in einem privaten Netz bereitstellen und ihm den Zugriff auf das öffentliche Netz ermöglichen. Sie können NSX Edge, Vyatta oder ähnliche Gateways verwenden, um dem lokalen HCX-Manager den Internetzugriff zu ermöglichen. Falls für den Zugriff auf das private Netz und auf das öffentliche Netz verschiedene Gateways verwendet werden, empfiehlt es sich, das Standardgateway für den Zugriff auf das öffentliche Netz zu verwenden und mit der lokalen **Administratorkonsole für den HCX-Manager** eine statische Route für den Zugriff auf das private Netz zu erstellen.
4. Verwenden Sie nach der Bereitstellung des HCX-Managers die **Administratorkonsole für den HCX-Manager**, um den lokalen HCX-Manager zu aktivieren. Einen Aktivierungsschlüssel für den lokalen HCX-Manager erhalten Sie, wenn Sie eine lokale HCX on {{site.data.keyword.cloud_notm}}-Instanz in der {{site.data.keyword.vmwaresolutions_short}}-Konsole bestellen. Weitere Informationen finden Sie unter [Lokale HCX-Instanzen bestellen](../services/standalone_orderingserviceinstances.html).
5. Falls Sie ein selbst signiertes SSL-Zertifikat verwendet haben, als Sie den Service "HCX on {{site.data.keyword.cloud_notm}}" bestellt haben, müssen Sie das Zertifikat in den lokalen HCX-Manager importieren, indem Sie die folgenden Schritte ausführen:
    1. Klicken Sie in der lokalen **Administratorkonsole für den HCX-Manager** auf die Registerkarte **Verwaltung**.
    2. Klicken Sie im linken Navigationsfenster auf **Anerkanntes CA-Zertifikat** und dann rechts auf **IMPORTIEREN**.
    3. Klicken Sie auf **URL** und geben Sie dann die URL des Zertifikats ein, das Sie anwenden möchten, also die **HCX-Cloud-IP** (``https://<cloud-side public IP>``), die auf der Seite mit den Details für den Service "HCX on {{site.data.keyword.cloud_notm}}" in der {{site.data.keyword.vmwaresolutions_short}}-Konsole zu finden ist.
    4. Klicken Sie auf **ANWENDEN**.

Die Basiskonfiguration für den lokalen HCX-Manager ist hiermit abgeschlossen. Sie können nun den lokalen HCX on {{site.data.keyword.cloud_notm}}-Standort mit dem cloudseitigen HCX-Standort verbinden.

Weitere Informationen finden Sie auf der Seite [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx).

## Hinweise zum Löschen von lokalen HCX on IBM Cloud-Instanzen

Lesen Sie die folgenden Hinweise, bevor Sie eine HCX on {{site.data.keyword.cloud_notm}}-Instanz löschen, die Sie für die lokale Verwendung bestellt haben.
1. Rufen Sie in VMware vSphere Web Client die HCX-Benutzerschnittstelle auf und prüfen Sie dann die folgenden Punkte:
    1. Vergewissern Sie sich, dass keine Operation für die HCX-Migration oder -Disaster-Recovery aktiv ist.
    2. Vergewissern Sie sich, dass alle erweiterten Netze entfernt wurden.
    3. Vergewissern Sie sich, dass alle Verbindungskomponenten mit paarweise verbundenen Cloudstandorten entfernt wurden.

   **Wichtig**: Sie müssen alle Überprüfungen ausführen, bevor Sie mit dem nächsten Schritt fortfahren. Andernfalls wird die Lizenz für die lokale HCX on {{site.data.keyword.cloud_notm}}-Instanz storniert, wodurch Migrationen nicht ausgeführt werden können und Fehler in den HCX-Komponenten auftreten können.  
2. Löschen Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole die lokale HCX on {{site.data.keyword.cloud_notm}}-Instanz, die bestellt wurde, um den Aktivierungsschlüssel für den lokalen HCX-Manager zu erhalten. Stellen Sie sicher, dass die gelöschte Instanz nicht mehr in der Konsole verfügbar ist, bevor Sie mit dem nächsten Schritt fortfahren.

   Weitere Informationen finden Sie unter [Lokale HCX on {{site.data.keyword.cloud_notm}}-Instanzen löschen](../services/standalone_deletingserviceinstances.html).
3. Löschen Sie den lokalen HCX-Manager in VMware vSphere Web Client.

Weitere Informationen finden Sie auf der Seite [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx).

## Zugehörige Links

* [Lokale HCX on {{site.data.keyword.cloud_notm}}-Instanzen anzeigen](../services/standalone_viewingserviceinstances.html)
* [Glossar der HCX-Begriffe](hcx_glossary.html)
* [VMware Hybrid Cloud Extension documentation](https://hcx.vmware.com/#vm-documentation)
* [VMware HCX Enterprise installation and user guide](https://hcx.vmware.com/content/docs/vmware-hcx-enterprise-install-guide.pdf){:new_window}
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
