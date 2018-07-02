---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# Gegenmaßnahmen für Sicherheitslücken "Spectre" und "Meltdown"

Als Gegenmaßnahmen für die mit "Spectre" und "Meltdown" bezeichneten Sicherheitslücken müssen Sie eine Reihe von Patches in einer bestimmten Reihenfolge anwenden.

## Firmware aktualisieren

Die neuesten Informationen zum Aktualisieren der Firmware finden Sie im Blogbeitrag [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/).

## In V2.0 oder höher bereitgestellte Instanzen aktualisieren

Instanzen aus V2.0 oder höher wurden mit VMware vSphere 6.5 und VMware vCenter Server 6.5 bereitgestellt. Für beide Softwarekomponenten ist ein Patch erforderlich.

### In V2.0 oder höher bereitgestellte vCenter Server-Instanzen

Bei VMware vSphere 6.5:
* Für alle neuen V2.3-Instanzen wird vSphere mit den folgenden angewendeten Patches bereitgestellt: ESXi650-201712101-SG, ESXi650-201803401-BG und ESXi650-201803402-BG.  
* Für alle vorhandenen und vor V2.3 bereitgestellten Instanzen werden alle neuen Cluster und ESXi-Server mit den folgenden Patches aktualisiert: ESXi650-201712101-SG, ESXi650-201803401-BG und ESXi650-201803402-BG.
* Für alle vorhandenen ESXi-Server sowie alle Cluster oder ESXi-Server, die Sie weiterhin bereitstellen, bevor Sie ein Upgrade auf V2.3 durchführen, müssen Sie die folgenden Patches anwenden: ESXi650-201712101-SG, ESXi650-201803401-BG und ESXi650-201803402-BG von der [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch).

Bei VMware vCenter Server 6.5:
* Für alle neuen Instanzen aus V2.3 wird vCenter Server mit angewendetem Patch vCenter 6.5 U1g bereitgestellt.
* Für alle vorhandenen und vor V2.3 bereitgestellten Instanzen müssen Sie das Patch vCenter 6.5 U1g anwenden, das auf der [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) verfügbar ist.

### In V2.0 oder höher bereitgestellte Cloud Foundation-Instanzen

Um die erforderlichen Patches für VMware vSphere 6.5 und VMware vCenter Server 6.5 anzuwenden, müssen Sie für Ihre Cloud Foundation-Instanzen ein Upgrade auf die aktuelle Version (V2.3) durchführen.

Für alle vorhandenen Instanzen und ESXi-Server werden Sie aufgefordert, die Patches (ESXi650-201712101-SG, ESXi650-201803401-BG und ESXi650-201803402-BG für vSphere und vCenter 6.5 U1g für vCenter Server) auf der Seite **Update und Patch** in der {{site.data.keyword.vmwaresolutions_full}}-Konsole anzuwenden. Weitere Informationen finden Sie unter [Updates auf Cloud Foundation-Instanzen anwenden](../sddc/sd_applyingupdates.html).

### In V2.0 oder höher bereitgestellte VMware vSphere-Cluster

Für VMware vSphere 6.5 müssen Sie die Patches ESXi650-201712101-SG, ESXi650-201803401-BG und ESXi650-201803402-BG von der [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) auf alle vSphere-Cluster und ESXi-Server anwenden, die neu bereitgestellt wurden oder bereits vorhanden sind.

Für VMware vCenter Server 6.5 müssen Sie das Patch vCenter 6.5 U1g von der [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) auf alle vCenter-Server anwenden, die neu bereitgestellt wurden oder bereits vorhanden sind.

## In V1.9 oder einem früheren Release bereitgestellte Instanzen

Cloud Foundation- und vCenter Server-Instanzen sowie alle VMware vSphere-Cluster aus V1.9 oder einem früheren Release wurden mit VMware vSphere 6.0 und VMware vCenter Server 6.0 bereitgestellt.

### In V1.9 oder einem früheren Release bereitgestellte vCenter Server-Instanzen

Für VMware vSphere 6.0 und VMware vCenter Server 6.0 müssen Sie die Patches (ESXi600-201711101-SG, ESXi600-201803401-BG und ESXi600-201803402-BG für vSphere und vCenter 6.0 U3e für vCenter Server) von der [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) auf alle neu bereitgestellten oder vorhandenen Instanzen und ESXi-Server anwenden.

### In V1.9 oder einem früheren Release bereitgestellte Cloud Foundation-Instanzen

Updates für diese Instanzen sind verfügbar, sobald die erforderlichen Anbieterupdates freigegeben werden, von denen diese Instanzen abhängig sind.

### In V1.9 oder früheren Releases bereitgestellte VMware vSphere-Cluster

Für VMware vSphere 6.0 und VMware vCenter Server 6.0 müssen Sie die Patches (ESXi600-201711101-SG, ESXi600-201803401-BG und ESXi600-201803402-BG für vSphere und vCenter 6.0 U3e für vCenter Server) von der [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) auf alle neu bereitgestellten oder vorhandenen vSphere-Cluster und ESXi-Server anwenden.

## Zugehörige Links

* [Updates auf Cloud Foundation-Instanzen anwenden](../sddc/sd_applyingupdates.html)
* [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch)
