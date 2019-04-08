---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# Upgrade für HCX-Komponenten durchführen
{: #vcshcx-upgrade}

Das Upgrade von HCX ist ein einfacher Prozess, der die Client-Webbenutzerschnittstelle (UI) in der clientseitigen HCX-Manager-Aktualisierung und die Cloud-Webbenutzerschnittstelle für die cloudseitige HCX-Manager-Aktualisierung verwendet. Sie müssen für beide Seiten ein Upgrade durchführen, da Aktualisierungen an Paketkomponenten auf beiden Seiten dazu führen, dass die Paketkomponenten mit der Codeversion erneut bereitgestellt werden, die der Manager installiert hat. Wenn die VMware-Unterstützung die System-ID anfordert, geben Sie sowohl die clientseitige als auch die cloudseitige System-ID an. Stellen Sie mit SSH eine Verbindung zum HCX-Manager her (Client oder Cloud) und führen Sie `cat/common/location` aus, um die System-ID zu finden.

## Zugehörige Links
{: #vcshcx-upgrade-related}

* [Übersicht über vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
