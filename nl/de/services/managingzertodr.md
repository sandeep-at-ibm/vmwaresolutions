---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Zerto on IBM Cloud verwalten

Nachdem der Service "Zerto on {{site.data.keyword.cloud}}" in Ihrer Instanz bereitgestellt wurde, können Sie Zerto Virtual Replication konfigurieren oder aktualisieren und weitere Virtual Replication Appliances (VRAs; dies sind Appliances für die virtuelle Replikation) auf neu hinzugefügten ESXi-Servern bereitstellen.

## Eigenes Zertifikat für Zerto verwenden

Als bewährtes Verfahren sollten Sie Ihr eigenes SSL-Zertifikat für Zerto Virtual Manager (ZVM) verwenden. Nachdem Sie Zerto on {{site.data.keyword.cloud_notm}} bereitgestellt haben, ersetzen Sie das SSL-Zertifikat für Zerto durch Ihr eigenes Zertifikat. Führen Sie hierzu die Anweisungen im Abschnitt [How to use a CER SSL Certificate to Replace the Self-Signed Certificate for the ZVM, ZSSP, or ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window} aus.

## Konfiguration von Zerto-Replikationen verwalten

Zum Verwalten der Konfiguration von Zerto-Replikationen (z. B. zum Reparieren von Zerto-Instanzen oder zum Konfigurieren von virtuellen Schutzgruppen zur Replikation virtueller Maschinen) melden Sie sich bei der Konsole von Zerto Virtual Replication unter Verwendung der vCenter-Berechtigungsnachweise mit Administratorberechtigungen an.

Wenn Sie Replikationen zwischen unterschiedlichen {{site.data.keyword.cloud_notm}} Zerto-Instanzen durchführen, können Sie die Replikation direkt zwischen den Zerto-Instanzen konfigurieren. Falls Sie die Replikation zwischen der {{site.data.keyword.cloud_notm}} Zerto-Instanz und Ihrem eigenen Rechenzentrum durchführen, müssen Sie Zerto selbst in Ihrem eigenen Rechenzentrum installieren. Diese Instanz kann sich selbst automatisch lizenzieren, wenn Sie sie in einem Paar mit der {{site.data.keyword.cloud_notm}} Zerto-Instanz verbinden.

Die Zerto-Replikation unterstützt die NAT-Traversierung (NAT – Network Address Translation) nicht. Zum Aufbau der Konnektivität zwischen der {{site.data.keyword.cloud_notm}} Zerto-Instanz und Ihrem eigenen Rechenzentrum müssen möglicherweise Routen für Appliances von Zerto Virtual Manager (ZVM) oder von Zerto Virtual Replication Appliances (VRAs) auf beiden Seiten angepasst werden. Zum Aufbau der Konnektivität ist unter Umständen auch eine sichere Tunnelung zwischen den Standorten erforderlich. Wenn Sie Routen für ZVM-Appliances konfigurieren oder rekonfigurieren, müssen Sie sicherstellen, dass alle ZVM-Appliances zur Erstellung von Nutzungsberichten erfolgreich eine Verbindung zu `zerto.com` herstellen können. Diese Verbindung können Sie überprüfen, indem Sie von der ZVM-Appliance aus eine Browsersitzung für `https://www.zerto.com` öffnen.

**Hinweis**: Das VMware NSX Edge Services Gateway (ESG) für das Management von Cloud Foundation-Instanzen und vCenter Server-Instanzen in {{site.data.keyword.cloud_notm}} ist so vorkonfiguriert, dass abgehende HTTPS-Kommunikation (TCP-Port 443) zulässig ist, die aus ZVM stammt.

## Zerto Virtual Replication aktualisieren

Zur Aktualisierung von Zerto Virtual Replication melden Sie sich bei der Konsole von Zerto Virtual Replication an.

## VRAs auf neu hinzugefügten ESXi-Servern bereitstellen

Wenn Sie ESXi-Server für den primären Cluster Ihrer Instanz hinzufügen oder entfernen, werden VRAs automatisch bereitgestellt oder entfernt. Auf den ESXi-Servern in den sekundären Clustern Ihrer Instanz werden VRAs nicht automatisch bereitgestellt. Sie können VRAs jedoch selbst über die Konsole von Zerto Virtual Replication bereitstellen.

### Zugehörige Links

* [Übersicht über Zerto on {{site.data.keyword.cloud_notm}}](addingzertodr.html)
* [Verwaltete Services für Zerto on {{site.data.keyword.cloud_notm}} anfordern](managing_zerto_services.html)
* [Website "zerto.com"](https://www.zerto.com){:new_window}
* [Technische Dokumentation zu Zerto (englisch)](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Disaster-Recovery mit Zerto](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:new_window}
* [Erläuterung von Zerto Virtual Replication-Alerts (englisch)](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)
