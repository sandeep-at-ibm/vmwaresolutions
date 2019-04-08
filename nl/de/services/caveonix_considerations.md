---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations}

Der Caveonix RiskForesight on {{site.data.keyword.cloud}}-Service kann Sie durch proaktive Überwachung und automatisierte Abwehrkontrollen bei der Verwaltung von Cyber- und Konformitätsrisiken unterstützen, um vor Bedrohungen zu schützen und die Branchenvorschriften oder Regierungsverordnungen zu erfüllen.

Dieser Service ist nur für VMware vCenter Server on {{site.data.keyword.cloud_notm}}-Instanzen verfügbar, die in V2.9 und höheren Releases bereitgestellt werden.
{:note}

## Technische Spezifikationen für Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-specs}

Mit dem Service "Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen.

### vCenter-Ressourcen
{: #caveonix_considerations-tech-specs-vcenter}

* CPU: 8 vCPU
* RAM: 32 GB
* Festplatte: 80 GB

### Netz
{: #caveonix_considerations-tech-specs-network}

Ein dediziertes privates Teilnetz mit 64 IP-Adressen wird bestellt.

### Lizenzen und Gebühren
{: #caveonix_considerations-tech-specs-license-fee}

Für jede Instanz des Service wird ein Caveonix RiskForesight-Lizenzschlüssel bestellt.

## Hinweise zur Installation von Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-install}

Stellen Sie vor der Installation des Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}-Service sicher, dass die CPU und der Speicher im Standardcluster Ihrer Serviceinstanz für die virtuelle Maschine von Caveonix RiskForesight ausreichen.

## Hinweise zum Entfernen von Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-remove}

Lesen Sie die folgenden Hinweise, bevor Sie den Service "Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}" entfernen:
* Beim Entfernen des Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}-Service wird nicht die Lizenz für Caveonix RiskForesight storniert. Sie müssen die Caveonix RiskForesight-Lizenz in der Tabelle **Caveonix RiskForesight-Lizenzen** auf der Seite **Ressourcen** in der {{site.data.keyword.vmwaresolutions_short}}-Konsole löschen.
* Wenn Sie den Service entfernen, löscht die {{site.data.keyword.vmwaresolutions_short}}-Automatisierung nur die einzige, umfassende Caveonix-VM, die bereitgestellt wurde, und das dedizierte private Teilnetz, das für diese bestellt wurde. Dies bedeutet Folgendes:
   * Wenn Sie die Caveonix-VM auf mehrere VMs horizontal skaliert haben, werden diese zusätzlichen VMs nicht entfernt.
   * Wenn Sie die IP-Adressen des dedizierten privaten Teilnetzes für zusätzliche VMs verwendet haben, müssen diesen VMs neue IP-Adressen zugeordnet werden, damit sie weiter funktionieren.
   * Löschen Sie die vCenter Server-Instanz A mit dem installierten Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}-Service und haben Sie die IP-Adressen des für den Service bestellten dedizierten privaten Teilnetzes in vCenter Server-Instanz B verwendet, wird das dedizierte private Teilnetz bei der Löschung der vCenter Server-Instanz A storniert.

## Zugehörige Links
{: #caveonix_considerations-related}

* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingcaveonix)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
