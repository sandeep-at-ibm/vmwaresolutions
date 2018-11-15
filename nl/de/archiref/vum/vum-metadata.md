---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

#	Metadaten erfassen

VUM lädt Metadaten zu den Upgrades, Patches oder Erweiterungen über einen vordefinierten automatischen Prozess herunter, den Sie ändern können. In regelmäßigen konfigurierbaren Intervallen nimmt VUM Kontakt zu VMware oder Drittanbieterquellen auf, um die aktuellen Metadaten zu verfügbaren Upgrades, Patches oder Erweiterungen zu erfassen. Die Standardeinstellungen von VMware sind für die Verwendung in der VCS-Instanz akzeptabel, Sie können sie aber bei Bedarf an die Anforderungen Ihres Unternehmens anpassen.

VUM zeigt systemverwaltete, von vSAN generierte Baselines an. Die systemverwalteten Baselines aktualisieren ihren Inhalt in regelmäßigen Zeitabständen automatisch. Dies setzt voraus, dass VUM permanent Zugriff auf das Internet hat. Die vSAN-Systembaselines werden normalerweise alle 24 Stunden aktualisiert.

Sie können die systemverwalteten Baselines verwenden, um Ihre vSAN-Cluster mit den empfohlenen kritischen Patches, Treibern, Updates oder auf die neueste unterstützte ESXi-Hostversion für vSAN zu aktualisieren.

Die VMware-Standardeinstellungen für VUM sind für die meisten Unternehmen geeignet. Im Folgenden wird beschrieben, wie Sie diese Einstellungen ändern können, wenn Ihr Unternehmen andere Einstellungen verwenden möchte.

##	Zeitplan für Downloads
Unter Updates sind Upgrades für virtuelle Appliances, Host-Patches und Erweiterungen zu verstehen. Standardmäßig lädt VUM Downloads täglich herunter. Dies kann durch Zugriff auf den vSphere Web Client geändert werden. Navigieren Sie zu **Home** > **Update Manager** > **Verwalten** > **Einstellungen** und wählen Sie **Zeitplan für Downloads** aus und klicken Sie anschließend auf **Bearbeiten**.

##	Zeitplan für Benachrichtigungen
Benachrichtigungen sind Informationen über Patchrückrufe, neue Fixes und Alerts. Standardmäßig lädt VUM die Benachrichtigungen auf Stundenbasis herunter. Diese Änderung kann durch Zugriff auf den vSphere Web Client geändert werden. Navigieren Sie zu **Home** > **Update Manager** > **Verwalten** > **Einstellungen** und wählen Sie **Zeitplan für Benachrichtigungen** aus und klicken Sie anschließend auf **Bearbeiten**.

##	VM-Einstellungen
Um die VM-Einstellungen zu ändern, rufen Sie den vSphere Web Client auf, navigieren Sie zu **Home** > **Update Manager** > **Verwalten** > **Einstellungen** und **VM-Einstellungen** und klicken Sie dann auf **Bearbeiten**.

##	Host-/Clustereinstellungen
Um die Host-/Clustereinstellungen zu ändern, rufen Sie den vSphere Web Client auf, navigieren Sie zu **Home** > **Update Manager** > **Verwalten** > **Einstellungen** und **Host-/Clustereinstellungen** und klicken Sie dann auf **Bearbeiten**.

### Zugehörige Links

* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
