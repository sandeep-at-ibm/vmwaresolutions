---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Native NIC-Treiber anwenden
{: #vum-applying-nic}

ESXi 6.5 enthält viele neue native Treiber, die die älteren vmklinux-Treiber ersetzen. Während die meisten der neuen nativen Treiber nach der Installation oder dem Upgrade standardmäßig aktiviert werden, sind drei der neuen nativen Treiber standardmäßig inaktiviert, da sie die Funktionen der entsprechenden vmklinux-Treiber nicht vollständig unterstützen.

"ixgben" ist ein nativer Treiber, der den Treiber "vmklinux net-ixgbe" ersetzt, aber keine Unterstützung für SR-IOV und SW FcOE bietet. Die ICVS-Automation aktiviert diesen Treiber nicht, wenn der vSphere ESXi-Host bereitgestellt wurde. Es wird empfohlen, diesen Treiber zu aktivieren, da er verbesserte Leistung ermöglicht. Die im Folgenden beschriebene Prozedur zeigt, wie Sie die nativen Treiber mithilfe der vSphere-Befehlszeile (vCLI) aktivieren und inaktivieren können.

Bevor Sie diese Task starten, rufen Sie alle physischen IPMI-IP-Adressen, Anmelde-IDs und Kennwörter aus dem [{{site.data.keyword.cloud}}-Infrastrukturkundenportal](https://control.softlayer.com/devices) ab. Dies ist bei einem Backout erforderlich oder zum Überprüfen des Fortschritts eines Upgrades, bei dem kein direkter Netzzugriff auf den Host möglich ist.

Führen Sie die folgenden Schritte für jeden Host in der angegebenen Reihenfolge aus:
1. Verwenden Sie den vSphere Web Client, um den vSphere ESXi-Host in den Wartungsmodus zu versetzen, indem Sie **Home** > **Hosts und Cluster** auswählen. Wählen Sie im Navigatorfenster den vSphere ESXi-Host aus, klicken Sie mit der rechten Maustaste auf den Host und wählen Sie **Wartungsmodus** > **In Wartungsmodus wechseln** aus. Da der Host Teil eines automatisierten DRS-Clusters ist, werden virtuelle Maschinen auf verschiedene Hosts migriert, wenn der Host in den Wartungsmodus wechselt.
2. Greifen Sie über SSH auf den vSphere ESXi-Host zu und verwenden Sie dabei die Details von der IC4VS-Konsole.
3. Führen Sie den folgenden vCLI-Befehl aus, um die nativen ixgben-Treiber zu aktivieren:
  `esxcli system module set --enabled=true --module=ixgben`
4. Führen Sie den folgenden vCLI-Befehl aus, um den vSphere ESXi-Host erneut zu starten:
  `system shutdown reboot --reason “Install ixgben driver”`
5. Nachdem der vSphere ESXI-Host mittels erneuter Anmeldung beim Host neu gestartet wurde, geben Sie den folgenden vCLI-Befehl aus und prüfen Sie, ob der ixgben-Treiber "geladen" (erste Spalte) und "aktiviert" (zweite Spalte) wurde:
  `esxcli system module list |grep ixg`
6. Wenn die Treiber aktiviert sind, wählen Sie mithilfe des vSphere Web Client den Host im Navigatorfenster aus, klicken Sie mit der rechten Maustaste und wählen Sie **Wartungsmodus** > **Wartungsmodus beenden** aus. Wählen Sie den nächsten Host aus und aktivieren Sie die Treiber, bis alle Hosts an der Reihe waren.
7. Wenn die Änderung nicht richtig ausgeführt wird, führen Sie den folgenden Befehl aus, um den Vorgang rückgängig zu machen:
  `esxcli system module set --enabled=false --module=ixgben`

8. Wenn Sie keine Verbindung zum Host über das Netz herstellen können, führen Sie den vorherigen Befehl über die IPMI-Konsole aus, indem Sie das {{site.data.keyword.cloud_notm}}-Steuerfenster verwenden.
9. Nachdem Sie den vSphere ESXi-Host neu gestartet haben, beobachten Sie nun den geladenen und aktivierten ixgbe-Standardtreiber.

Wenn Sie den Vorgang rückgängig machen müssen und Sie nicht über SSH auf den vSphere ESXi-Host zugreifen können, müssen Sie sich bei der KVM-Konsole für den Host anmelden, der über das {{site.data.keyword.cloud_notm}}-Steuerfenster zurückgesetzt werden muss.

Verwenden Sie die ID und das Kennwort, die im {{site.data.keyword.cloud_notm}}-Steuerfenster mit der IPMI-IP-Adresse aufgelistet sind, um sich an der IPMI-Webschnittstelle anzumelden. Sie müssen mit dem Rechenzentrum, in dem sich der Host befindet, über VPN verbunden sein. Weitere Informationen finden Sie unter [Einführung in die Arbeit mit VPN](/docs/infrastructure/iaas-vpn?topic=VPN-gettingstarted-with-virtual-private-networking#gettingstarted-with-virtual-private-networking).

1. Wechseln Sie zur Seite "Gerätedetails, Fernverwaltung" für den vSphere ESXi-Host und wählen Sie **Aktionen** > **KVM-Konsole** aus. Ein anderes Fenster wird geöffnet, in dem Sie den IPMI-Benutzer und das zugehörige Kennwort eingeben können.
2. Wählen Sie **Fernsteuerung** > **iKVM/HTML5** aus und klicken Sie auf **iKVM/HTML5**, um neu zu starten. Sie können nun auf die Konsole des vSphere ESXi-Hosts zugreifen.
3. Wenn der Host auf Befehle antwortet, verwenden Sie **ALT-F1** in der Konsole, um auf die ESXi-Hostkonsole zuzugreifen. Verwenden Sie die Berechtigungsnachweise des Hosts, um sich anzumelden.
4. Wenn der Host nicht antwortet, verwenden Sie die IPMI-Menüs, um den Host aus- und wieder einzuschalten.
5. Beobachten Sie die HTML5-Konsole genau, wenn der Host erneut gestartet wird. Sie haben nur ein paar Sekunden Zeit, um den Wiederherstellungsmodus zu starten, wenn ESXi neu gestartet wird.
6. Drücken Sie gleichzeitig die Tasten **CMD + R**, um den Wiederherstellungsmodus zu aktivieren.
7. Geben Sie **"Y"** (Ja) ein, um den Wiederherstellungsmodus zu aktivieren, und starten Sie den ESXi-Server mit der vorherigen Version.
8. Überwachen Sie den Fortschritt über die Konsole. Der Bootvorgang kann 10-20 Minuten dauern.

## Zugehörige Links
{: #vum-applying-nic-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (Demonstrationen)
