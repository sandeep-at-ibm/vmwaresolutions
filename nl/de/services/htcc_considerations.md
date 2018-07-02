---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Überblick zu HyTrust CloudControl on IBM Cloud

Der Service "HyTrust CloudControl on {{site.data.keyword.cloud}}" erzwingt und steuert die Einhaltung der Sicherheitsstandards und stellt detaillierte Funktionen für die rollenbasierte Zugriffssteuerung (RBAC = Role-Based Access Control) sowie für die Genehmigung und Überprüfung zur Verfügung. In Kombination mit HyTrust DataControl kann der Service sicherstellen, dass virtuelle Maschinen und Workloaddaten eine bestimmte Region, einen bestimmten Cluster oder einen bestimmten ESXi-Server innerhalb von {{site.data.keyword.CloudDataCent_notm}} nicht verlassen.

**Verfügbarkeit:** Dieser Service ist nur für Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.3 oder höheren Releases bereitgestellt werden oder für die ein Upgrade auf diese Releases durchgeführt wird.

## Komponenten von HyTrust CloudControl on IBM Cloud

Im Standardcluster wird ein HA-Paar (HA = High Availability; Hochverfügbarkeit) von HTCC-Appliances (HTCC = HyTrust CloudControl) im Aktiv-/Passiv-Modus bereitgestellt.

Jedes Paar der HTCC-Appliances wird in demselben privaten portierbaren Teilnetz bereitgestellt, das auch für die virtuellen Maschinen (VMs) für das Management (z. B. für den NSX-Manager, vCenter Server Appliances und für Platform Services Controller) angegeben wurde. Das Paar der Appliances dient als Proxy für die vSphere-Hosts, für vCenter Server Appliance und für den NSX-Manager einer Instanz. Benutzer greifen daher auf die vSphere-Hosts, auf vCenter Server Appliance und auf NSX-Manager über eine vom Administrator zugewiesene, veröffentlichte IP-Adresse (Published IP - PIP) zu und nicht über die reale IP-Adresse (RIP-Adresse), die von IBM Cloud zugewiesen wird.

Die HTCC-Appliances sind in das Microsoft Active Directory integriert, um die rollenbasierte Zugriffssteuerung zu erzwingen.

## Hinweise zum Entfernen von HyTrust CloudControl on IBM Cloud

Vor dem Entfernen des Service "HyTrust CloudControl on {{site.data.keyword.cloud_notm}}" müssen Sie sicherstellen, dass das **Root Password Vaulting** inaktiviert wurde, falls diese Funktion konfiguriert wurde, und dass alle geschützten Hosts aus CloudControl gelöscht wurden.

## Zugehörige Links

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} bestellen](htcc_ordering.html)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} verwalten](managinghtcc.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [HyTrust-Website](https://www.hytrust.com/)
