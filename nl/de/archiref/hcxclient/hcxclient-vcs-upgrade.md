---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Upgrade für HCX-Komponenten durchführen
{: #hcxclient-vcs-upgrade}

Das Upgrade von HCX ist ein einfacher Prozess, der die Client-Webbenutzerschnittstelle (UI) in der clientseitigen HCX-Manager-Aktualisierung und die Cloud-Webbenutzerschnittstelle für die cloudseitige HCX-Manager-Aktualisierung verwendet.

Sie müssen für beide Seiten ein Upgrade durchführen, da Aktualisierungen an Paketkomponenten auf beiden Seiten dazu führen, dass die Paketkomponenten mit der Codeversion erneut bereitgestellt werden, die für HCX Manager installiert ist.

Wenn von der VMware-Unterstützung die System-ID angefordert wird, geben Sie sowohl die clientseitige als auch die cloudseitige System-ID an. Stellen Sie mit SSH eine Verbindung zum HCX-Manager her (Client oder Cloud) und führen Sie `cat /common/location` aus, um die System-ID zu suchen.

## Zugehörige Links
{: #hcxclient-vcs-upgrade-related}

* [Glossar der HCX-Komponenten und -Begriffe](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Installationsumgebung vorbereiten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Bereitstellung des HCX-Clients](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Lokales HCX-Servicenetz](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud-Migrationen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Überwachung von Parametern und Komponenten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Fehlerbehebung für HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
