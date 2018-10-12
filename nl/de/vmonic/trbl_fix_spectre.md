---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Gegenmaßnahmen für Sicherheitslücken "Spectre" und "Meltdown"

Als Gegenmaßnahmen für die mit "Spectre" und "Meltdown" bezeichneten Sicherheitslücken müssen Sie eine Reihe von Patches in einer bestimmten Reihenfolge anwenden.

## Firmware aktualisieren

Die neuesten Informationen zum Aktualisieren der Firmware finden Sie im Blogbeitrag [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/).

## In V2.0 oder einem höheren Release bereitgestellte Instanzen aktualisieren

Instanzen aus V2.0 oder höher wurden mit VMware vSphere 6.5 und VMware vCenter Server 6.5 bereitgestellt. Für beide Softwarekomponenten ist ein Patch erforderlich.

### In V2.0 oder einem höheren Release bereitgestellte vCenter Server-Instanzen

#### VMware vSphere 6.5

* Für alle neuen V2.6-Instanzen wird vSphere mit den folgenden angewendeten Patches bereitgestellt: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG und ESXi650-201808403-BG.
* Für alle vorhandenen Instanzen, die vor V2.5 bereitgestellt wurden und für die ein Upgrade auf V2.5 durchgeführt wurde, werden alle neuen Cluster und ESXi-Server mit den folgenden Patches aktualisiert: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG und ESXi650-201808403-BG.
* Auf alle vorhandenen ESXi-Server und auf alle Cluster oder ESXi-Server, die Sie weiterhin bereitstellen, bevor Sie ein Upgrade auf V2.5 durchführen, müssen Sie folgende Patches der [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) anwenden: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG und ESXi650-201808403-BG.

#### VMware vCenter Server 6.5

* Für alle neuen Instanzen aus V2.6 wird vCenter Server mit den angewendeten kumulativen Patches aus vCenter 6.5 U2c bereitgestellt.
* Auf alle vorhandenen und vor V2.6 bereitgestellten Instanzen müssen Sie das Patch vCenter 6.5 U2c anwenden, das auf der [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) verfügbar ist.

### In V2.0 oder einem höheren Release bereitgestellte Cloud Foundation-Instanzen

Um die erforderlichen Patches für VMware vSphere 6.5 und VMware vCenter Server 6.5 anzuwenden, müssen Sie für Ihre Cloud Foundation-Instanzen ein Upgrade auf das neueste Patch-Bundle von VMware durchführen. Für alle vorhandenen Instanzen und ESXi-Server werden Sie aufgefordert, die Patches auf der Seite **Update und Patch** in der {{site.data.keyword.vmwaresolutions_full}}-Konsole anzuwenden. Weitere Informationen finden Sie unter [Updates auf Cloud Foundation-Instanzen anwenden](../sddc/sd_applyingupdates.html).

### In V2.0 oder einem höheren Release bereitgestellte VMware vSphere-Instanzen

Auf alle neuen VMware vSphere 6.5-Cluster und ESXi-Server müssen Sie folgende Patches der [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) anwenden: ESXi650-201808401-BG, ESXi650-201808402-BG und ESXi650-201808403-BG.

Auf alle vorhandenen VMware vSphere 6.5-Cluster müssen Sie folgende Patches der [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) anwenden: ESXi650-201712101-SG, ESXi650-201803401-BG, ESXi650-201803402-BG, ESXi650-201808401-BG, ESXi650-201808402-BG und ESXi650-201808403-BG.

Bei VMware vCenter Server 6.5 müssen Sie das Patch vCenter 6.5 U2c der [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) auf alle vCenter-Server anwenden, die neu bereitgestellt wurden oder bereits vorhanden sind.

## In V1.9 oder einem früheren Release bereitgestellte Instanzen

Cloud Foundation-Instanzen, vCenter Server-Instanzen und VMware vSphere-Cluster aus V1.9 oder einem früheren Release wurden mit VMware vSphere 6.0 und VMware vCenter Server 6.0 bereitgestellt.

### In V1.9 oder einem früheren Release bereitgestellte vCenter Server-Instanzen

Bei VMware vSphere 6.0 und VMware vCenter Server 6.0 müssen Sie die Patches (ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG, ESXi600-201808401-BG, ESXi600-201808402-BG und ESXi600-201808403-BG für vSphere und vCenter 6.0 U3h für vCenter Server) der Site [Site der VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) auf alle Instanzen und ESXi-Server anwenden, die neu bereitgestellt wurden oder bereits vorhanden sind.

### In V1.9 oder einem früheren Release bereitgestellte Cloud Foundation-Instanzen

Updates für diese Instanzen sind verfügbar, sobald die erforderlichen Anbieterupdates freigegeben werden, von denen diese Instanzen abhängig sind.

### In V1.9 oder einem früheren Release bereitgestellte VMware vSphere-Cluster

Bei VMware vSphere 6.0 und VMware vCenter Server 6.0 müssen Sie die Patches (ESXi600-201711101-SG, ESXi600-201803401-BG, ESXi600-201803402-BG, ESXi600-201808401-BG, ESXi600-201808402-BG und ESXi600-201808403-BG für vSphere und vCenter 6.0 U3h für vCenter Server) der Site [Site der VMware-Produktpatches](https://my.vmware.com/group/vmware/patch) auf alle vSphere-Cluster und ESXi-Server anwenden, die neu bereitgestellt wurden oder bereits vorhanden sind.

### Zugehörige Links

* [Updates auf Cloud Foundation-Instanzen anwenden](../sddc/sd_applyingupdates.html)
* [Secure against recent security vulnerabilities](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [Site für VMware-Produktpatches](https://my.vmware.com/group/vmware/patch)
