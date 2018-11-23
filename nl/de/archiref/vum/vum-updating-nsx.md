---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# NSX aktualisieren

Dieser Abschnitt wurde zu diesem Dokument hinzugefügt, um Ihnen einen Eindruck vom Aktualisierungsprozess für NSX zu geben. Weitere Informationen zum Aktualisierungsprozess finden Sie in dem VMware-Handbuch für die NSX-Version, auf die Sie das Upgrade durchführen.

Wenn Sie ein Upgrade für NSX und vSphere durchführen müssen, sollte zunächst das NSX-Upgrade und dann das vSphere-Upgrade durchgeführt werden, da die NSX-VIBs für die Version von ESXi spezifisch sind, die auf dem Host installiert ist. Es wird allerdings empfohlen, VUM zu verwenden, wie dies in diesem Dokument dokumentiert ist. Beim manuellen Verfahren ist wie folgt Host für Host vorzugehen:

1. **Upgrade von ESXi** - Nach Abschluss des ESXi-Upgrades beendet der Host den Wartungsmodus. Sie können die mit logischen Switches verbundenen VMs jedoch erst auf den Host verschieben, wenn der nächste Schritt durchgeführt wurde.
2. **Upgrade der NSX-VIBs** - Nachdem ein Upgrade der VIBs erfolgt ist und sich der Host nicht mehr im Wartungsmodus befindet, können Sie die mit logischen Switches verbundenen VMs auf den Host verschieben.

NSX wird durch ein Update von NSX Manager unter Verwendung eines Downloads von _my.vmware.com_ aktualisiert. Daher benötigen Sie ein Konto, um das Update herunterladen zu können. Wenn Sie die {{site.data.keyword.cloud}}-Abonnementlizenzierung mit Ihrer VMware vCenter Server on {{site.data.keyword.cloud_notm}}-Instanz nutzen, können Sie die Aktualisierungen nicht mit Ihrem **my.vmware.com**-Konto herunterladen. Daher müssen Sie den [IBM Support kontaktieren](../../vmonic/trbl_support.html).

Bevor Sie mit dem Upgrade beginnen, lesen Sie die NSX-Releaseinformationen, da dort die bekannten Upgradeprobleme und Problemumgehungen dokumentiert sind. Prüfen Sie anhand der Releaseinformationen, ob vCenter die neuen Systemvoraussetzungen für NSX erfüllt.

Wenn Sie zusätzliche Software von VMware-Partnern installiert haben, ziehen Sie die Partnerdokumentation bei Fragen zu Kompatibilität und Upgradedetails zurate. Wenn Sie primären und sekundären Instanzen von vCenter Server bereitgestellt haben und über eine Cross-vCenter NSX-Umgebung verfügen, finden Sie in den Releaseinformationen den richtigen Upgradeprozess.

In einer Cross-vCenter NSX-Umgebung wird die primäre NSX Manager-Appliance zuerst aktualisiert, gefolgt von allen sekundären NSX Manager-Appliances.
**Herabstufungen (Downgrades) werden nicht unterstützt:** Führen Sie vor der Durchführung eines Upgrades immer eine Sicherung von NSX Manager durch. Alle NSX Edge-Konfigurationen, logischen Router und Edge Services Gateways werden im Rahmen der NSX Manager-Sicherung gesichert.

Nach einem erfolgreichen Upgrade von NSX Manager kann NSX nicht herabgestuft werden. Es wird empfohlen, die Wartungsaktivitäten in einem vereinbarten Wartungsfenster durchzuführen, das den Richtlinien Ihres Unternehmens entspricht. Es wird empfohlen, das Upgrade aller NSX-Komponenten gemeinsam in einem Wartungsfenster durchzuführen, um die Ausfallzeit und funktionelle Probleme zu minimieren. Der Upgradevorgang für NSX kann einige Zeit in Anspruch nehmen. Daher ist es wichtig, die Upgradefolge bei der NSX-Bereitstellung zu beachten:
* NSX Manager
* NSX Controller-Cluster
* NSX Host-Cluster
* Edge Services Gateways können jederzeit nach dem NSX Manager-Upgrade aufgerüstet werden
* Guest Introspection (bei Verwendung sind die Anweisungen in den Releaseinformationen zu beachten)

Es gilt folgender Workflow:
1. Melden Sie sich bei Ihrem Jump-Server an und öffnen Sie dann einen Browser.
2. Verwenden Sie Ihre _my.vmware.com_-Berechtigungsnachweise, navigieren Sie zum Downloadabschnitt und suchen Sie nach _NSX for vSphere_.
3. Wählen Sie die Version aus, die Sie benötigen.
4. Wählen Sie auf der Downloadseite **Upgrade-Bundle, Jetzt herunterladen** aus.
5. Wählen Sie einen geeigneten Ordner für den Download.
6. **Upgrade von NSX Manager**:
  - Melden Sie sich bei der virtuellen Appliance von NSX Manager an, indem Sie die IP-Adresse und die Berechtigungsnachweise verwenden, die in der IC4VS-Konsole dokumentiert sind, und klicken Sie auf die Schaltfläche 'Upgrade' auf der Startseite.
  - Melden Sie sich bei NSX Manager an.
  - Klicken Sie unter **Appliance-Management** auf **Sicherung und Wiederherstellung**.
  - Klicken Sie auf 'Sichern' und geben Sie einen entsprechenden Dateinamen ein. Beachten Sie, dass VMware die erneute Installation der NSX Manager-Appliance empfiehlt, bevor NSX Manager-Daten wiederhergestellt werden. Auch wenn eine Wiederherstellungsoperation für eine vorhandene NSX Manager-Appliance möglicherweise ausgeführt werden kann, wird dies doch offiziell nicht unterstützt. Am besten ist es, sich die IP-Einstellungen für die NSX Manager-Appliance zu notieren, sodass sie verwendet werden können, um Informationen zu IP-Adressen und Sicherungsposition für die neu bereitgestellte NSX Manager-Appliance anzugeben.
  - Klicken Sie in der rechten oberen Ecke auf **Bundle hochladen** und laden Sie die Datei hoch, die Sie von _my.vmware.com_ heruntergeladen haben.
  - Lesen Sie die Upgradeinformationen und wählen Sie, ob Sie SSH aktivieren und am VMware Customer Experience Improvement Program teilnehmen möchten.
  - Klicken Sie auf **Upgrade**.
  - Wenn der Upload abgeschlossen ist, werden Sie auf die NSX Manager-Anmeldeseite umgeleitet. Melden Sie sich erneut an und überprüfen Sie, ob die aktuelle Softwareversion korrekt angezeigt wird.
7. **Upgrade von NSX Controller-Cluster**:
  - Öffnen Sie den vSphere Web Client und melden Sie sich bei der VCSA an.
  - Navigieren Sie zu **Home** > **Vernetzung & Sicherheit** > **Installation**, wählen Sie die Registerkarte **Management** aus und klicken Sie auf **Upgrade verfügbar** in der Spalte 'Status des Controller-Clusters'.
  - Für die einzelnen Controller in Ihrer Umgebung wird nacheinander ein Upgrade und ein Neustart durchgeführt. Nachdem Sie das Upgrade initiiert haben, lädt das System die Upgradedatei herunter, führt ein Upgrade für die einzelnen Controller durch, startet die einzelnen Controller erneut und aktualisiert den Upgradestatus jedes einzelnen Controllers.
8. **Upgrade von NSX Host-Clustern**:
  - Nach dem Upgrade von NSX Manager und der NSX Controller werden die Host-Cluster mit den NSX-VIBs auf den vSphere ESXi-Hosts aktualisiert.
  - Navigieren Sie im vSphere Web Client zu **Home** > **Vernetzung & Sicherheit** > **Installation** und wählen Sie die Registerkarte **Hostvorbereitung** aus. Klicken Sie für jeden Cluster, für den Sie ein Upgrade durchführen möchten, auf **Upgrade verfügbar**. Der Installationsstatus zeigt 'Wird Installiert' an.
  - Der Installationsstatus des Clusters zeigt _Nicht bereit_ an. Klicken Sie auf **Nicht bereit**, um weitere Informationen anzuzeigen, und klicken Sie auf **Alle auflösen**, um die VIB-Installation abzuschließen. Der Host wird in den Wartungsmodus versetzt und bei Bedarf neu gebootet, um das Upgrade durchzuführen. Die Spalte 'Installationsstatus' zeigt 'Wird installiert' an. Nachdem das Upgrade abgeschlossen ist, wird in der Spalte 'Installationsstatus' ein grünes Häkchen und die aktualisierte NSX-Version angezeigt.
9. **Edge Services Gateways**:
  - Während des Upgradeprozesses wird eine neue virtuelle Edge-Appliance neben der bereits vorhandenen virtuellen Appliance bereitgestellt. Wenn die neue Edge bereit ist, werden die vNICs der alten Edge getrennt und die vNICs der neuen Edge werden verbunden. Die neue Edge sendet dann Gratuitous ARP-Pakete (GARP), um den ARP-Cache verbundener Switches zu aktualisieren. Bei Bereitstellung von HA wird der Upgradeprozess zweimal ausgeführt. Dieser Prozess kann die Paketweiterleitung vorübergehend beeinträchtigen.
  - Wählen Sie im vSphere Web Client die Optionen **Vernetzung & Sicherheit** > **NSX Edges** aus. Wählen Sie für jede NSX Edge-Instanz **Upgrade-Version** im Menü **Aktionen** aus.
  - Nach dem erfolgreichen Upgrade der NSX Edge lautet der Status 'Bereitgestellt' und in der Spalte 'Version' wird die neue NSX-Version angezeigt. Falls das Upgrade einer Edge fehlschlägt und kein Rollback auf die alte Version erfolgt, klicken Sie auf das Symbol **NSX Edge erneut bereitstellen** und führen Sie dann das Upgrade erneut durch.

### Zugehörige Links

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
