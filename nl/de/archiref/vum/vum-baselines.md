---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# Baselines erstellen und an Bestandsobjekte anhängen

Baselines enthalten eine Sammlung von Patches, Erweiterungen, Service-Packs, Fehlerkorrekturen oder Upgrades und können als Patch-, Erweiterungs- oder Upgrade-Baselines klassifiziert werden. Baselinegruppen setzen sich aus vorhandenen Baselines zusammen. Host-Baseline-Gruppen können eine einzelne Upgrade-Baseline und verschiedene Patch- und Erweiterungsbaselines enthalten. Die Baselinegruppen für virtuelle Maschinen und virtuelle Appliances können bis zu drei Upgrade-Baselines enthalten: eine VMware Tools-Upgrade-Baseline, eine Hardware-Upgrade-Baseline für virtuelle Maschinen und eine Upgrade-Baseline für virtuelle Appliances.

VUM enthält vordefinierte Baselines, die Sie nicht bearbeiten oder löschen können. Sie können die vordefinierten Baselines verwenden oder Patch-, Erweiterungs- und Upgrade-Baselines erstellen, die Ihren Kriterien entsprechen. Die von Ihnen erstellten angepassten Baselines und die vordefinierten Baselines können in Baselinegruppen kombiniert werden.

VUM enthält Standardbaselines, mit denen Sie beliebige der folgenden Geräte prüfen können, um festzustellen, ob die Hosts in Ihrer Umgebung mit den neuesten Patches aktualisiert sind oder ob die virtuellen Appliances und virtuellen Maschinen auf die neueste Version aktualisiert sind:
* Beliebige virtuelle Maschine
* Beliebige virtuelle Appliance
* Beliebiger Host

Es gibt die folgenden vordefinierten Baselines:
* **Kritische Host-Patches (Vordefiniert)** - Prüft die ESXi-Hosts auf Konformität mit allen kritischen Patches.
* **Nicht kritische Host-Patches (Vordefiniert)** - Prüft die ESXi-Hosts auf Konformität mit allen optionalen Patches.
* **VMware Tools-Upgrade übereinstimmend mit Host (Vordefiniert)** - Prüft die virtuellen Maschinen auf Konformität mit der neuesten VMware Tools-Version auf dem Host. Der Update Manager unterstützt das Upgrade von VMware Tools für virtuelle Maschinen auf Hosts, auf denen ESXi 5.5.x und höher ausgeführt wird.
* **VM-Hardware-Upgrade übereinstimmend mit Host (Vordefiniert)** - Prüft die virtuelle Hardware einer virtuellen Maschine auf Konformität mit der neuesten Version, die vom Host unterstützt wird. Update Manager unterstützt das Upgrade auf Version vmx-13 der virtuellen Hardware auf Hosts, auf denen ESXi 6.5 ausgeführt wird.
* **VA-Upgrade auf neueste Version (Vordefiniert)** - Prüft die Konformität der virtuellen Appliance mit dem neuesten Release der virtuellen Appliance.

Wenn Sie Baselines und Baselinegruppen verwenden möchten, müssen Sie sie an ausgewählte Bestandsobjekte wie Containerobjekte, virtuelle Maschinen, virtuelle Appliances oder Hosts anhängen. Sie können Baselines und Baselinegruppen an einzelne Objekte anhängen, doch ist es effizienter, sie an Containerobjekte wie z. B. Ordner, vApps, Cluster oder Rechenzentren anzuhängen. In diesem Schritt werden die vordefinierten Baselines für die Hosts im Cluster verwendet.

1. Bei Verwendung des vSphere Web Client wechseln Sie zu **Home** > **Hosts und Cluster**.
2. Klicken Sie auf das Clusterobjekt, das Sie prüfen möchten.
3. Klicken Sie auf **Baseline anhängen**, wählen Sie dann die beiden vordefinierten Patch-Baselines aus und klicken Sie anschließend auf **OK**.

### Zugehörige Links

* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
