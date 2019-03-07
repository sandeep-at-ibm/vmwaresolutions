---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Skalierungskapazität
{: #solution_scaling}

Nach der Erstimplementierung können Sie die Rechenkapazität über die Konsole von {{site.data.keyword.vmwaresolutions_full}} skalieren. Das Design unterstützt die folgenden Scale-out-Pfade:
* Hinzufügen neuer Standorte (Sites), die von separaten vCenter-Servern verwaltet werden
* Hinzufügen neuer Cluster
* Hinzufügen neuer Hosts zu einem vorhandenen Cluster

## Weitere Standorte (Sites) hinzufügen
{: #solution_scaling-sites}

{{site.data.keyword.vmwaresolutions_short}} kann dank der weltweiten Verfügbarkeit von {{site.data.keyword.cloud_notm}}-Rechenzentren und des integrierten Netzbackbones die Bereitstellung und Funktion verschiedener Anwendungsfälle in unterschiedlichsten Regionen unterstützen, und dies unter einem Bruchteil des Zeitaufwands, der ansonsten zum Neuaufbau einer solchen Infrastruktur erforderlich wäre.

In diesem Design besteht die Definition einer Bereitstellung mit mehreren Standorten aus folgenden Komponenten:
* Eine erste oder primäre VMware-Bereitstellung, die eine neue DNS/AD-Rootdomäne, eine Unterdomäne, eine SSO-Domäne und einen SSO-Standortnamen enthält, die zur Verfügung gestellt werden sollen.
* Ein oder mehrere sekundäre Standorte, die in der SSO-Domäne des primären Standorts bereitgestellt werden und die folgende Konfiguration erfordern:
   * Neuer SSO-Standortname
   * Neuer DNS-Standort bzw. neue DNS-Unterdomäne mit Bindung an das Stammelement (Root) der primären Domäne
   * DNS- und AD-Replikationskonfiguration zwischen den AD-VMs der sekundären Standorte und des primären Standorts
   * Bereitgestellter und für die Synchronisation mit dem PSC des primären Standorts konfigurierter PSC
   * vCenter-Konfiguration mit erweitertem Verbindungsmodus zum vCenter des primären Standorts

Darüber hinaus kann der NSX-Manager an sekundären Standorten als sekundärer NSX-Manager für den NSX-Manager am primären Standort konfiguriert werden.

## Neue Cluster hinzufügen
{: #solution_scaling-clusters}

Sie können die Rechenkapazität auch dadurch skalieren, dass Sie einen neuen Cluster über die Konsole von {{site.data.keyword.vmwaresolutions_short}} erstellen und neue Hosts bestellen, die dem neuen Cluster automatisch hinzugefügt werden.

Durch diese Methode lassen sich folgende Zwecke realisieren:
* Erstellen eines zusätzlichen, separaten Clusters in der Umgebung
* Physische und logische Trennung von Management-Workloads von Anwendungsworkloads
* Trennung von Workloads nach anderen Merkmalen, zum Beispiel Microsoft SQL-Datenbankcluster
* Bereitstellung von Anwendungen in hoch verfügbaren Topologien

Wenn der erste Cluster in einen reinen Management-Cluster konvertiert wird, erfordert die Migration vorhandener Workloads manuelle Schritte, die der Benutzer ausführen muss. Es kann zum Beispiel eine erneute Herstellung von Verbindungen von Datenspeichern zu dem neuen Cluster oder, alternativ, eine Speichermigration erforderlich sein. Die IP-Adressen der Workloads müssen möglicherweise geändert werden, wenn sich der neue Cluster in einem anderen {{site.data.keyword.cloud_notm}}-Pod befindet oder dem Cluster eine andere VLAN-ID zugeordnet wird.
{:note}

## ESXi-Hosts in vorhandenen Clustern hinzufügen
{: #solution_scaling-hosts}

Sie können einen vorhandenen Cluster skalieren, indem Sie Hosts über die Konsole von {{site.data.keyword.vmwaresolutions_short}} bestellen.  Die neuen Hosts werden dem Cluster automatisch hinzugefügt. Beachten Sie, dass Sie die Reservierungsrichtlinie für Hochverfügbarkeit (HA) für den Cluster entsprechend Ihren Reservierungsanforderungen möglicherweise anpassen müssen.

## Zugehörige Links
{: #solution_scaling-related}

* [Lösungsübersicht](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [Übersicht über das Design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [Komponenten sichern](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)
