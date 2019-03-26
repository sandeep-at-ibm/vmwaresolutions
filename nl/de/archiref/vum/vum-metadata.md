---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

#	Metadaten erfassen
{: #vum-metadata}

VUM lädt Metadaten zu den Upgrades, Patches oder Erweiterungen über einen vordefinierten automatischen Prozess herunter, den Sie ändern können. In regelmäßigen konfigurierbaren Intervallen nimmt VUM Kontakt zu VMware oder Drittanbieterquellen auf, um die aktuellen Metadaten zu verfügbaren Upgrades, Patches oder Erweiterungen zu erfassen. Die Standardeinstellungen von VMware sind für die Verwendung in der VMware vCenter Server on {{site.data.keyword.cloud}}-Instanz akzeptabel, Sie können sie aber bei Bedarf an die Anforderungen Ihres Unternehmens anpassen.

VUM zeigt systemverwaltete, von vSAN generierte Baselines an. Die systemverwalteten Baselines aktualisieren ihren Inhalt in regelmäßigen Zeitabständen automatisch. Dies setzt voraus, dass VUM permanent Zugriff auf das Internet hat. Die vSAN-Systembaselines werden normalerweise alle 24 Stunden aktualisiert.

Sie können die systemverwalteten Baselines verwenden, um Ihre vSAN-Cluster mit den empfohlenen kritischen Patches, Treibern, Updates oder auf die neueste unterstützte ESXi-Hostversion für vSAN zu aktualisieren.

Die VMware-Standardeinstellungen für VUM sind für die meisten Unternehmen geeignet. Im Folgenden wird beschrieben, wie Sie diese Einstellungen ändern können, wenn Ihr Unternehmen andere Einstellungen verwenden möchte.

##	Zeitplan für Downloads
{: #vum-metadata-download-schedule}

Unter Updates sind Upgrades für virtuelle Appliances, Host-Patches und Erweiterungen zu verstehen. Standardmäßig lädt VUM Downloads täglich herunter. Der Zeitplan für Downloads kann durch Zugriff auf den vSphere Web Client geändert werden. Navigieren Sie zu **Home** > **Update Manager** > **Verwalten** > **Einstellungen** und wählen Sie **Zeitplan für Downloads** aus und klicken Sie anschließend auf **Bearbeiten**.

##	Zeitplan für Benachrichtigungen
{: #vum-metadata-notif-check-schedule}

Benachrichtigungen sind Informationen über Patchrückrufe, neue Fixes und Alerts. Standardmäßig lädt VUM die Benachrichtigungen auf Stundenbasis herunter. Diese Änderung kann durch Zugriff auf den vSphere Web Client geändert werden. Navigieren Sie zu **Home** > **Update Manager** > **Verwalten** > **Einstellungen** und wählen Sie **Zeitplan für Benachrichtigungen** aus und klicken Sie anschließend auf **Bearbeiten**.

##	Einstellungen für virtuelle Maschinen
{: #vum-metadata-vm-settings}

Um die Einstellungen für eine virtuelle Maschine (VM) zu ändern, rufen Sie den vSphere Web Client auf, navigieren Sie zu **Home** > **Update Manager** > **Verwalten** > **Einstellungen** und **VM-Einstellungen** und klicken Sie dann auf **Bearbeiten**.

##	Host-/Clustereinstellungen
{: #vum-metadata-host-settings}

Um die Host-/Clustereinstellungen zu ändern, rufen Sie den vSphere Web Client auf, navigieren Sie zu **Home** > **Update Manager** > **Verwalten** > **Einstellungen** und **Host-/Clustereinstellungen** und klicken Sie dann auf **Bearbeiten**.

## Zugehörige Links
{: #vum-metadata-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demonstrationen)
