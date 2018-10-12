---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Nach der Bereitstellung zu beachtende Aspekte für Ihre VMware-Instanz

Bei den Produktangeboten {{site.data.keyword.vmwaresolutions_full}}, VMware vCenter Server und VMware Cloud Foundation handelt es sich um nicht verwaltetes Services. Sie selbst sind für die Konfiguration, Sicherheit, Verwaltung und Überwachung sämtlicher Softwarekomponenten verantwortlich. Aufgrund Ihres vollständigen Verwaltungszugriffs auf die Lösung verfügen Sie über großes Potenzial und Flexibilität, für die fundiertes technisches, verwaltungstechnisches und operatives Fachwissen zu mehreren Domänen erforderlich ist. Die Verwaltung einer VMware-Instanz in {{site.data.keyword.cloud_notm}} erfordert dieselbe Planung und dasselbe Fachwissen, wie sie auch für eine lokale Instanz erforderlich sind. Softwaredefinierte Technologien wie VMware NSX und VMware vSAN vereinfachen einige Aspekte der Instanzenverwaltung erheblich, erfordern jedoch neue Kenntnisse zur ordnungsgemäßen Verwaltung sowie den Betrieb von Tools. Durch die Kombination aus Leistung, Geschwindigkeit sowie Zuverlässigkeit der durch {{site.data.keyword.cloud_notm}} automatisierten VMware-Bereitstellung und der entsprechenden Betriebsplanung und Tests wird eine schnelle und erfolgreiche Navigation zur Hybrid-Cloud sichergestellt.

Lesen Sie die folgenden Hinweise, denen Sie die Verantwortlichkeiten des Kunden bei Verwaltung und Betrieb der Instanz vor und nach der Bereitstellung entnehmen können. 

**Anmerkung:** Die folgende Liste ist nicht vollständig. Weitere Informationen finden Sie in [Von IBM verwaltete Services](../../services/managing_imi.html).

## Zugriff auf das IBM Cloud-Konto

Berechtigen Sie zur Verwaltung des Zugriffs auf Ihr {{site.data.keyword.cloud_notm}}-Konto andere Mitglieder Ihres Teams, in der {{site.data.keyword.vmwaresolutions_short}}-Konsole auf Ihre Instanz zuzugreifen. Weitere Informationen finden Sie unter [Benutzer für den Zugriff auf Services und Ressourcen einladen](../../vmonic/iamuserinvite.html).

## Einschränkungen

Machen Sie sich mit den folgenden für Ihre Instanz geltenden Einschränkungen vertraut:

- [Ändern von vCenter-Artefakten – Auswirkung](../../vcenter/vcenter_chg_impact.html)
- [Für das Netz geltende Aspekte und Einschränkungen](../../vcenter/vc_networkingonvcenterserver.html)
- [Häufig gestellte Fragen](../../vmonic/faq.html)

## Netzdesign und Konnektivität

Führen Sie folgende Schritte aus, um den Zugriff auf Ihr {{site.data.keyword.cloud_notm}}-Netz und Ihre VMware-Managementkomponenten zu verwalten und Ihre {{site.data.keyword.cloud_notm}}-Netztopologie zu planen.

- Greifen Sie mithilfe des [{{site.data.keyword.cloud_notm}}-VPNs](https://www.softlayer.com/vpn-access) oder Ihrer [{{site.data.keyword.cloud_notm}} Direct Link-Verbindung](https://www.ibm.com/cloud/direct-link) auf die Endpunkte des Instanzmanagements zu.
- Erarbeiten Sie eine Strategie für die Konnektivität zum öffentlichen Netz aus Ihrer Instanz heraus. Zu Ihren Optionen gehören Folgende: das VMware NSX Edge Services Beispiel-Gateway (ESG) für Kunden, Gateway-Appliances wie Vyatta und FortiGate sowie Proxy-Server, die über Direct Link im {{site.data.keyword.cloud_notm}}-Netz oder Ihrem eigenen Netz bereitgestellt werden.
- Planen Sie, ob Ihre Workload in {{site.data.keyword.cloud_notm}}-VLANs mit [portierbaren {{site.data.keyword.cloud_notm}}-IP-Adressen](https://console.bluemix.net/docs/infrastructure/subnets/getting-started.html) oder [unter Verwendung Ihrer eigenen IP-Adresse über logische NSX-Switches (VXLANs)](../nsx/nsx_overview.html) bereitgestellt werden soll. Beachten Sie, dass die Verwendung von Software-Defined Networking (SDN) von NSX Ihnen größte Flexibilität bei der Verwaltung und Sicherung Ihres Workload-Netzes in {{site.data.keyword.cloud_notm}} bietet.
- Verwenden Sie NSX Edge Services Gateways (ESGs), [IBM Cloud Vyatta](https://console.bluemix.net/catalog/infrastructure/virtual-router-appliance) und das Direct Link-Peering, um die Konnektivität zu Workloads (Netzadressumsetzung, Virtual Private Network, Routing) zu planen.
- Wenn Sie Cross-vCenter NSX implementieren, müssen Sie vor der Bereitstellung lokaler Workloads sicherstellen, dass sich die Bereiche der IDs lokaler Segmente nicht überschneiden.

## Sicherheitsplanung und Abschottung des Systems

Sie selbst sind dafür verantwortlich, dass Ihre VMware-Instanz und -Workloads gesichert, verschlüsselt und überwacht werden, um Unternehmens-, Branchen- und gesetzliche Bestimmungen einzuhalten. Führen Sie folgende Schritte aus, um eine ordnungsgemäße Sicherheit sicherzustellen.

- Ändern Sie alle Kennwörter, die in der {{site.data.keyword.vmwaresolutions_short}}-Konsole angezeigt werden und verwenden Sie Ihr eigenes Kennwortmanagementsystem. Beachten Sie, dass IBM eigene Benutzer-IDs beibehält, die für die laufende Automatisierung und Unterstützung benötigt werden.
- Beachten Sie für alle Komponenten die geltenden Kennwortrichtlinien, wie z. B. für Komplexität und Ablaufzeitraum.
- Beachten Sie die für die einzelnen Komponenten geltenden Verschlüsselungseinstellungen.
- Planen und implementieren Sie geeignete physische oder virtuelle Firewalllösungen wie z. B. NSX Distributed Firewall (DFW), NSX Edge Services Gateways (ESGs), [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../../services/fortinetvm_considerations.html) und [IBM Cloud Vyatta](https://console.bluemix.net/catalog/infrastructure/virtual-router-appliance).
- Planen und implementieren Sie geeignete Lösungen für den Anwendungslastausgleich und die Sicherheit, wie z. B. [F5 on {{site.data.keyword.cloud_notm}}](../../services/f5_considerations.html).
- Planen und implementieren Sie geeignete SIEM-Lösungen (SIEM – Security Information and Event Management, Sicherheitsinformationen und Ereignismanagement) wie z. B. [IBM QRadar](https://www.ibm.com/us-en/marketplace/hosted-security-intelligence).
- Planen und implementieren Sie geeignete Möglichkeiten zum Ermitteln von Sicherheitslücken.
- Planen und implementieren Sie für Ihre Instanz geeignete Möglichkeiten für das Änderungsmanagement, für Genehmigungen, Überprüfungen und die Zugriffssteuerung und verwenden Sie dazu Lösungen wie z. B. [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../../services/htcc_considerations.html).

## Anpassung

Führen Sie folgende Schritte aus, um die Basisinstallation der VMware-Instanz an Ihre Anforderungen anzupassen.

- Verwenden Sie Ihre eigene Zertifizierungsstelle, um Zertifikate für Komponenten wie vCenter, VMware Platform Services Controller (PSC) und den NSX-Manager zu generieren.
- Konfigurieren Sie bereitgestellte Services. Beispiel:
  - Konfigurieren Sie für HyTrust CloudControl on {{site.data.keyword.cloud_notm}} die Active Directory-Integration, die Zugriffssteuerung, die Einstellungen für Simple Mail Transfer Protocol (SMTP) und die Konformitätsrichtlinien.
  - Planen Sie für Zerto on {{site.data.keyword.cloud_notm}} die IP-Adressierung und das Routing der Virtual Replication Appliance-Kommunikation (VRA) für Zerto ein, da die NAT-Traversierung nicht unterstützt wird. Damit die Adressierung und das Routing geeignet sind, müssen Sie möglicherweise die Tunnelung oder die erneute Bereitstellung Ihrer Virtual Replication Appliances (VRAs) in Betracht ziehen.
  - Konfigurieren Sie für Sicherungsservices wie beispielsweise Veeam on {{site.data.keyword.cloud_notm}} und IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Sicherungsjobs; konfigurieren Sie optional weiteren Speicher sowie Überwachungsalerts.
  - Konfigurieren Sie für Netz- und Sicherungsservices wie beispielsweise F5 on {{site.data.keyword.cloud_notm}} und FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} Netzschnittstellen, Zertifikate, die Hochverfügbarkeitskonfiguration und Regeln, die Ihrer Netztopologie sowie anderen Anforderungen entsprechen.

## Active Directory

Führen Sie folgende Schritte aus, um eine ordnungsgemäße Konfiguration und Verwaltung von Single Sign-on (SSO) sicherzustellen.

- Konfigurieren Sie die Serveraktualisierung und den Warmstart für Active Directory (AD).
- Wenn Sie die Option für die Bereitstellung von AD-Servern im vSphere-Cluster ausgewählt haben, müssen Sie die Lizenzierung und Aktivierung von Microsoft Windows für die Server bereitstellen, um die Konformität und Verfügbarkeit sicherzustellen.
- Richten Sie gegenseitiges Vertrauen zwischen der Instanz und Ihrem lokalen AD-Server ein.
- Integrieren Sie NSX VPN, falls zutreffend, mit AD SSO.
- Integrieren Sie ESXi-Hosts mit AD SSO.

## Wartungsplanung

Führen Sie folgende Schritte aus, um eine ordnungsgemäße Planung der Softwarewartung sicherzustellen.

- Richten Sie VMware Update Manager (VUM) über einen Proxy ein, um VMware-Aktualisierungen zu erhalten.
- Konfigurieren Sie, falls zutreffend, vSAN über einen Proxy, um die vSAN-HCL-Datenbank (HCL – Hardware Compatibility List) zu warten.
- Planen Sie für VMware-Komponenten, die nicht von VUM unterstützt werden, eine regelmäßige Wartung ein. Beispiel: VMware vCenter, PSC und NSX.
- Überprüfen Sie die vSphere-EVC-Konfiguration (EVC – Enhanced Motion Compatibility). Ihr Cluster wird möglicherweise nicht mit aktivierter EVC konfiguriert, wenn die aktuelle Version von vSphere EVC für Ihre Hardwarestufe nicht unterstützt.
- Planen Sie eine regelmäßige Wartung für Add-on-Services wie Veeam on {{site.data.keyword.cloud_notm}}, Zerto on {{site.data.keyword.cloud_notm}} und F5 on {{site.data.keyword.cloud_notm}} ein.

## Überwachung

Stellen Sie sicher, dass die folgenden Lösungen zur Überwachung Ihrer Instanz- und Instanzkomponenten eingeplant und implementiert werden:

- Ein Protokollierungsserver, der die Protokollweiterleitung oder -erfassung für alle Instanzkomponenten sowie eine angemessene Protokollaufbewahrung einschließt.
- Eine Alert-Infrastruktur, die nach Bedarf die Konfiguration des SMTP-Servers und des SMS-Gateways (SMS – Short Message Service) einschließt.
- Proaktive Überwachung von Hosts, Laufwerken, Verwaltungssoftware und Netz.
- vSAN-Überwachung, falls zutreffend.
- Kapazitätsüberwachung und -planung. Sie können für Ihre Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole [Cluster hinzufügen und entfernen](../../vcenter/vc_addingviewingclusters.html) und [Hosts hinzufügen und entfernen](../../vcenter/vc_addingremovingservers.html).
- Überwachung Ihrer Sicherungsinfrastruktur und Sicherungsjobs.

## Business-Continuity und Verfügbarkeit

Ihre VMware-Instanz wird auf Bare Metal Servern in {{site.data.keyword.cloud_notm}} ausgeführt. Führen Sie folgende Schritte aus, um sicherzustellen, dass Sie für die Hochverfügbarkeit und die Business-Continuity angemessene Pläne erstellen.

- Überprüfen Sie, ob die Konfiguration von vSphere HA und vSphere Distributed Resource Scheduler (DRS) Ihren Anforderungen entspricht.
- Überprüfen Sie, ob die Konfiguration der E/A-Steuerung für das Netz und den Speicher Ihren Anforderungen entspricht.
- Konfigurieren Sie die Startreihenfolge der virtuellen Maschinen entsprechend Ihren Anforderungen.
- Konfigurieren Sie nach Bedarf Ressourcenpools für das Management und die Workload.
- Planen, implementieren und überwachen Sie eine Sicherungslösung für die [Managementkomponenten der Instanz](solution_backingup.html) und die Workload.
- Planen Sie die Hochverfügbarkeit des Instanzmanagements, einschließlich der Möglichkeit, über mehrere Instanzen, mehrere Cluster und Hochverfügbarkeit für vCenter und PSC zu verfügen.
- Planen Sie Business-Continuity für Ihre Workloads mithilfe von Lösungen wie [Zerto Disaster Recovery](../../services/addingzertodr.html), [Veeam Backup and Replication](../../services/veeam_considerations.html) und [IBM Spectrum Protect Plus](../../services/spp_considerations.html).

## Speicherplanung

Führen Sie zusätzlich zur Kapazitätsplanung die folgenden Maßnahmen aus, um sicherzustellen, dass Ihre Speicherkonfiguration Ihren Leistungs- und Verfügbarkeitsanforderungen entspricht.

- Die Speicherleistung hängt von verschiedenen Faktoren ab; dazu gehören folgende: RAID-Konfiguration, Plattenstriping, Netzkonfiguration, Blockgröße, Anzahl konfigurierte IOPS (Ein-/Ausgabeoperationen pro Sekunde) für den NAS-Speicher (NAS – Network-attached Storage), VM-Hardwarekonfiguration und Konfigurationsmethode für Speicheranhänge, Clustering- und Replikationsmethoden sowie die Verwendung von Speicherrichtlinien, wie z. B. für Verschlüsselung, Deduplizierung und Komprimierung. Planen Sie Zeit ein, um Ihre Konfiguration zu testen und zu optimieren, sodass sie Ihren Anforderungen an die Speicherleistung entspricht.
- Überprüfen Sie Ihre vSAN-Speicherrichtlinie.
  - RAID 1 bietet eine bessere Leistung, ist weniger anfällig für nachfolgende Ausfälle und benötigt weniger Zeit für einen erneuten Build als RAID 5. Der Systemaufwand für den Speicher ist bei RAID 5 jedoch geringer.
  - RAID 6 bietet Schutz vor dual auftretenden Ausfällen, erfordert jedoch mindestens sechs Hosts im Vergleich zu vier Hosts für RAID 5.
- Wenn Sie Ihrem vSAN-Cluster mehr Speicher hinzufügen möchten, müssen Sie dem Cluster neue Hosts hinzufügen oder stattdessen den {{site.data.keyword.cloud_notm}}-Endurance-NFS-Speicher hinzufügen. Das Hinzufügen von Platten zu den vorhandenen Hosts wird aktuell nicht unterstützt.
- Wenn Sie in Ihrem Cluster zusätzlichen {{site.data.keyword.cloud_notm}}-Endurance-NFS-Speicher anhängen, müssen Sie sicherstellen, dass Sie die Architekturanleitung beachten und Hostrouten zum Speicher mithilfe der `SDDC-DPortGroup-NFS`-Portgruppenadressierung konfigurieren. Sie müssen diese Adressen und nicht die Hosts selbst für den Speicher autorisieren. Weitere Informationen finden Sie in [Management der Infrastruktur für angehängten Speicher](../attached-storage/storage-infra-mgmt.html#vsphere-host-static-routing). Lesen Sie auch die developerWorks-Anleitung, in der beschrieben ist, wie [Sie Ihrem VMware-Cluster weiteren Endurance-Speicher hinzufügen](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/), beispielsweise, indem Sie IBM Spectrum Protect Plus verwenden.

### Zugehörige Links

* [Lösungsübersicht](solution_overview.html)
* [Übersicht über das Design](design_overview.html)
* [Skalierungskapazität](solution_scaling.html)

