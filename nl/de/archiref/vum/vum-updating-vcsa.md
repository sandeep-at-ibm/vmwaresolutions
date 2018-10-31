---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-05"

---

#	VCSA-Update und über SSO angebundene vCenter

## VCSA-Update

VUM aktualisiert die VCSA nicht. Im folgenden Abschnitt wird der Prozess der Aktualisierung dieser Appliance beschrieben. Die VCSA, die in einer VCS-Instanz bereitgestellt wird, hat keinen Zugriff auf das Internet. Deshalb sollte das Update-Bundle zuerst auf einen Jump-Server heruntergeladen werden.

Die VCSA wird über die Appliance-Managementkonsole aktualisiert, nicht über den vSphere Web Client. Der Zugriff auf die VCSA-Appliance-Managementkonsole erfolgt über einen Browser, die VCSA-IP-Adresse und den Port 5480.

Es wird empfohlen, vor dem Update einen Snapshot der Appliance oder eine Sicherung der VCSA zu erstellen. Wenn Sie sichergestellt haben, dass das Update ordnungsgemäß angewendet wurde, entfernen Sie den Snapshot innerhalb weniger Tage, um Leistungseinbußen zu vermeiden. Lesen Sie außerdem die Releaseinformationen, bevor Sie versuchen, ein Upgrade durchzuführen.

Führen Sie die folgenden Schritte aus, um die VCSA zu aktualisieren:
1. Sie können Updates herunterladen, indem Sie zum VMware Patch [Download Center](https://my.vmware.com/group/vmware/patch#search) wechseln, sich anmelden und VC im Menü für die **Suche nach Produkt** auswählen. Wählen Sie das entsprechende Patch aus und klicken Sie auf **Herunterladen**.
2. Laden Sie die ISO-Datei mit dem vSphere Web Client in das vCenter-Datenspeicherrepository hoch.
3. Hängen Sie die Update-ISO-Datei an den vCenter Server an.
4. Erstellen Sie einen Snapshot Ihres vCenter Server.
5. Melden Sie sich bei der vCenter-Appliance-Managementkonsole an unter: `https://vcenterip:5480`
6. Wechseln Sie zum Abschnitt **Update** und wählen Sie **Updates prüfen** und dann **CDROM prüfen** aus. Das Update sollte aufgelistet werden.
7. Wählen Sie **Updates installieren** und akzeptieren**** Sie die Endbenutzerlizenzvereinbarung (EULA). Das Update wird installiert.
8. Wenn die Aktualisierung abgeschlossen ist, müssen Sie wieder zur Appliance-Managementkonsole wechseln und die Konsole erneut starten.
9. Melden Sie sich wieder beim vSphere Web Client an und prüfen Sie, ob Fehler aufgetreten sind. Führen Sie eine manuelle VUM-Prüfung durch (**Home** > **Hosts und Cluster**), wählen Sie dann ein Rechenzentrum oder einen Cluster aus, wählen Sie die Registerkarte **Update Manager** aus und klicken Sie auf **Auf Updates prüfen**. Wenn dies zu einem Fehler führt, finden Sie weitere Informationen unter [Zurücksetzen der VMware Update Manager-Datenbank in vCenter Server Appliance 6.5 (2147284)](https://kb.vmware.com/s/article/2147284).
10. Wenn Sie den Vorgang nach dem Test rückgängig machen müssen, können Sie auf einen Snapshot zurücksetzen oder das vCenter anhand einer vorherigen Sicherung wiederherstellen.

## Über SSO angebundene vCenter

Wenn Sie über primäre und sekundäre VCS-Instanzen verfügen, sind Ihre VCSAs für eine Single-Sign-on-Domäne (SSO) von vCenter konfiguriert. Für jede VCSA wird eine VUM-Instanz bereitgestellt. Die Konfigurationseigenschaften, die Sie ändern, werden nur auf die von Ihnen angegebene VUM-Instanz angewendet und sie werden nicht an die anderen Instanzen in der Gruppe weitergegeben.

Sie können eine VUM-Instanz angeben, indem Sie den Namen der VCSA auswählen, mit dem die VUM-Instanz in der Navigationsleiste registriert ist. Sie haben außerdem die Möglichkeit, Baselines und Baselinegruppen zu verwalten, Sie können ausschließlich die Bestandsobjekte prüfen und korrigieren, die von der VCSA verwaltet werden, bei der die VUM-Instanz registriert ist.

### Zugehörige Links

* [VMware HCX on IBM Cloud Solution](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
