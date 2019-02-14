---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

# VCSA-Update und über SSO angebundene vCenter

## Aktualisierung für PSC und VCSA

Dieser Abschnitt bezieht sich sowohl auf vCentre Server Appliance (VCSA) als auch auf Platform Services Controller (PSC). Bei beiden Appliances handelt es sich um VCSA-Appliances, die jedoch unterschiedliche Rollen übernehmen. Wenn Sie ein Upgrade für vSphere mit einem externen PSC durchführen, führen Sie zuerst das Upgrade für den PSC durch, dann für die VCSA, dann für die ESXi-Hosts und schließlich für die Hardwareversionen und VMware-Tools der virtuellen Maschinen. 

VUM aktualisiert den PSC/die VCSA nicht. Die folgenden Informationen beschreiben die Aktualisierung dieser Appliances. Der PSC/die VCSA, der bzw. die in einer VMware vCenter Server on {{site.data.keyword.cloud}}-Instanz bereitgestellt wird, verfügt nicht über Zugriff auf das Internet. Deshalb sollte das Update-Bundle zuerst auf einen Jump-Server heruntergeladen werden.

Der PSC/die VCSA wird über die Appliance-Management-Konsole aktualisiert, nicht über den vSphere Web Client. Der Zugriff auf die PSC-/VCSA-Appliance-Management-Konsole erfolgt über einen Browser, die PSC-/VCSA-IP-Adresse und den Port 5480. 

Initiieren Sie vor der Aktualisierung einen Snapshot der Appliance oder eine Sicherung des PSC bzw. der VCSA. Wenn Sie sichergestellt haben, dass das Update ordnungsgemäß angewendet wurde, entfernen Sie den Snapshot innerhalb weniger Tage, um Leistungseinbußen zu vermeiden. Lesen Sie darüber hinaus vor dem Durchführen eines Upgrades die VMware-Releaseinformationen, um sich mit spezifischen Anweisungen vertraut zu machen, die gegebenenfalls für das jeweilige Release gelten. 

Führen Sie die folgenden Schritte aus, um den PSC/die VCSA zu aktualisieren: 
1. Sie können Updates herunterladen, indem Sie zum VMware Patch [Download Center](https://my.vmware.com/group/vmware/patch#search) wechseln, sich anmelden und VC im Menü für die **Suche nach Produkt** auswählen. Wählen Sie das entsprechende Patch aus und klicken Sie auf **Herunterladen**.
2. Laden Sie die ISO-Datei mit dem vSphere Web Client in das vCenter-Datenspeicherrepository hoch.
3. Hängen Sie die Update-ISO-Datei an den vCenter Server an.
4. Erstellen Sie einen Snapshot Ihres vCenter Server.
5. Melden Sie sich bei der vCenter-Appliance-Management-Konsole unter `https://pscip:5480` (für den PSC) oder unter `https://vcenterip:5480` (für die VCSA) an. 
6. Wechseln Sie zum Abschnitt **Update** und wählen Sie **Updates prüfen** und dann **CDROM prüfen** aus. Das Update wird aufgelistet.
7. Wählen Sie **Updates installieren** und akzeptieren**** Sie die Endbenutzerlizenzvereinbarung (EULA). Das Update wird installiert.
8. Wenn die Aktualisierung abgeschlossen ist, müssen Sie wieder zur Appliance-Managementkonsole wechseln und die Konsole erneut starten.
9. Melden Sie sich wieder beim vSphere Web Client an und prüfen Sie, ob Fehler aufgetreten sind. Führen Sie eine manuelle VUM-Prüfung durch (**Home** > **Hosts und Cluster**), wählen Sie dann ein Rechenzentrum oder einen Cluster aus, wählen Sie die Registerkarte **Update Manager** aus und klicken Sie auf **Auf Updates prüfen**. Wenn die manuelle Prüfung zu einem Fehler führt, finden Sie weitere Informationen unter [Zurücksetzen der VMware Update Manager-Datenbank in vCenter Server Appliance 6.5 (2147284)](https://kb.vmware.com/s/article/2147284).
10. Wenn Sie den Vorgang nach dem Test rückgängig machen müssen, können Sie auf einen Snapshot zurücksetzen oder das vCenter anhand einer vorherigen Sicherung wiederherstellen.

## Über SSO angebundene vCenter

Wenn Sie über primäre und sekundäre vCenter Server-Instanzen verfügen, sind Ihre VCSAs für eine Single-Sign-on-Domäne (SSO) von vCenter konfiguriert. Für jede VCSA wird eine VUM-Instanz bereitgestellt. Die Konfigurationseigenschaften, die Sie ändern, werden nur auf die von Ihnen angegebene VUM-Instanz angewendet und sie werden nicht an die anderen Instanzen in der Gruppe weitergegeben.

Sie können eine VUM-Instanz angeben, indem Sie den Namen der VCSA auswählen, mit dem die VUM-Instanz in der Navigationsleiste registriert ist. Sie haben außerdem die Möglichkeit, Baselines und Baselinegruppen zu verwalten, Sie können ausschließlich die Bestandsobjekte prüfen und korrigieren, die von der VCSA verwaltet werden, bei der die VUM-Instanz registriert ist.

### Zugehörige Links

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demonstrationen)
