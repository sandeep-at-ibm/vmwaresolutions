---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-07"

---

# Management der Infrastruktur für angehängten Speicher

Das Infrastrukturmanagement bezieht sich auf die VMware-Komponenten, die zum Management der vSphere ESXi-Infrastruktur eingesetzt werden.

Weitere Informationen zu den Komponenten finden Sie in Abbildung 2. NSX Manager-Netzübersicht in [Design der virtuellen Infrastruktur](../solution/design_virtualinfrastructure.html).

## Design des virtuellen Netzbetriebs

Die Netzvirtualisierung, die in diesem Design eingesetzt wird, nutzt einen bereits vorhandenen vSphere Distributed Switch (vDS), der dem privaten Netz zugeordnet und in der [{{site.data.keyword.vmwaresolutions_full}}-Architektur](../solution/solution_overview.html) angegeben ist.

## vSphere Distributed Switch (vDS)

Wie bereits erwähnt, wird in der vCenter Server-Lösung ein weiteres VLAN erstellt und zum Anhängen des NFS-Mountpunkts an die ESXi-Hosts im vorhandenen Cluster verwendet. Da die vCenter Server-Lösung bereits über einen vDS verfügt, der dem privaten Netz zugeordnet ist, wird eine weitere Portgruppe erstellt und mit der Nummer für zusätzliche VLANs markiert, da es sich bei diesem zusätzlichen VLAN nicht um ein natives VLAN handelt.

In der folgenden Tabelle werden die Standardeinstellungen für die neue Portgruppe beschrieben.

**Wichtig:** Diese Standardeinstellungen dürfen nicht geändert werden.

Tabelle 1. Zusammenfassung zur NFS-Portgruppe

| Portgruppenname | SDDC-DPG-NFS |
|:--------------- |:------------ |
| Portbindung | Statisch |
| VLAN-Typ | Privates VLAN B |
| Lastausgleich | Route basierend auf virtuellem Ursprungsport |
| Aktive Uplinks | uplink1 und uplink2 |

Zusätzlich zur Erstellung der vDS-Portgruppe für den NFS-Speicherdatenverkehr wird auf jedem vSphere ESXi-Host in der Bereitstellung ein VMkernel-Port erstellt und der Portgruppe SDDC-DPG-NFS zugewiesen. Darüber hinaus wird dem VMkernel-Port eine IP-Adresse aus dem privaten portierbaren Teilnetz zugewiesen, das dem VLAN für den angehängten Speicher zugeordnet ist. Dies bedeutet, dass das private VLAN B und die zugehörige MTU auf den Wert "9000" gesetzt wird, um Jumbo-Frames zu unterstützen.

Abbildung 1. Private vDS-Portgruppen und Uplinks

![Private vDS-Portgruppen und Uplinks](private_vds_portgroups_and_uplinks.svg "Private vDS-Portgruppen und Uplinks")

### Statisches Routing für vSphere-Host

Obwohl der vDS mit einer neuen Portgruppe konfiguriert und der Portgruppe ein VMkernel-Port zugewiesen wurde, erstellt die Lösung eine statische Route auf jedem vSphere ESXi-Host in der Bereitstellung, sodass der gesamte NFS-Datenverkehr das VLAN und das Teilnetz für NFS durchläuft. Die statische Route wird in `/etc/rc.local.d/local.sh` erstellt, sodass sie auch nach einem Neustart des Hosts erhalten bleibt.

### Zugehörige Links

* [Lösungsübersicht](../solution/solution_overview.html)
