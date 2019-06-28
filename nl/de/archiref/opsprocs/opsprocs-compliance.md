---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-16"

---

# Konformität
{: #opsprocs-compliance}

Konformität wird durch einen Satz von Anforderungen realisiert, die befolgt werden müssen, um die Mindestvorgaben einer Zulassungsbehörde oder von branchenspezifischen Best Practices zu erfüllen. Frameworks zur Einhaltung einer gesetzlich vorgegebenen Konformität sind üblicherweise breit gefasste Frameworks, die Anleitungen für eine große Auswahl an Technologien bereitstellen, wohingegen branchenspezifische Best Practices von Anbietern typischerweise für eine bestimmte Technologie gelten, um die entsprechenden Risiken abzufangen. 

Für Ihre vCenter Server-Instanz empfehlen wir, die Sicherheit von einem dedizierten Team im Anschluss an die Implementierung verwalten zu lassen. Diese Trennung von Aufgabenbereichen soll das Sicherheitsniveau Ihrer Instanz erhöhen und überwachen. HyTrust CloudControl kann Ihre Teams bei der rollenbasierten Trennung von Aufgabenbereichen unterstützen. 

HyTrust DataControl und KeyControl können Sie bei der Bereitstellung des Schutzes von Workloads wie Verschlüsselung ruhender Daten und Geofencing unterstützen. Möglicherweise sind Sie an einer Bereitstellung des Caveonix RiskForesight-Service interessiert, um Sie nicht nur bei Ihren Konformitätsanforderungen zu unterstützen, sondern auch bei Cyberrisiken und forensischem Management. 

Die VMware-Richtlinien zur Sicherheitshärtung stellen bindende Anleitungen für die sichere Bereitstellung und den sicheren Betrieb von VMware-Produkten bereit. Richtlinien für vSphere werden in einem einfach zu lesenden Tabellenformat bereitgestellt, mit umfangreichen Metadaten, um eine Klassifizierung der Richtlinien und eine Risikobewertung zu ermöglichen. Sie enthalten auch Scriptbeispiele zur Aktivierung der Automatisierung von Sicherheit. Es werden Vergleichsdokumente bereitgestellt, in denen die Änderungen an den Anleitungen in den aufeinander folgenden Versionen des Handbuchs aufgelistet sind. 

Es wurden zwar viele der Kontrollinstrumente, die in den VMware-Richtlinien zur Sicherheitshärtung dokumentiert sind, in die {{site.data.keyword.vmwaresolutions_full}}-Referenzarchitektur aufgenommen und werden damit automatisch bereitgestellt, stellen Sie aber trotzdem sicher, dass Sie das Sicherheitsniveau der Plattform an Ihre spezifischen Anforderungen und an die Unternehmensrichtlinie angepasst haben. Die VMware-Richtlinien zur Sicherheitshärtung stellen die technologiespezifischen Kontrollinstrumente bereit, die Sie für diese Überprüfung benötigen. Caveonix RiskForesight unter {{site.data.keyword.cloud_notm}} automatisiert diese Konformitätstask und stellt zusätzliche Richtlinien von Zulassungsbehörden bereit. 

vRealize Operations Manager ermöglicht Ihnen, VMware-Objekte auf Verstöße gegen die im Handbuch zur vSphere-Sicherheitskonfiguration aufgeführten Konformitätsregeln zu überwachen. Die Konformitätsalerts werden in der vCenter Server-Instanz, auf Hosts, virtuellen Maschinen, verteilten Portgruppen oder verteilten Switches ausgelöst und ermöglichen die Untersuchung des Konformitätsverstoßes. Darüber hinaus können Kunden, die an einer Konformität nach dem Health Insurance Portability and Accountability Act (HIPAA) und dem Payment Card Industry Data Security Standard (PCI DSS) interessiert sind, vRealize Operations Manager Compliance Packs von der VMWare Solutions Exchange-Website herunterladen, lizenzieren und installieren. Diese Compliance Packs stellen Alerts, Richtlinien und Berichte zur Validierung der vSphere-Ressourcen gegen die HIPAA- und PCI-Härtungsregeln bereit. 


## Zugehörige Links
{: #opsprocs-compliance-links}

* [VMware-Richtlinien zur Sicherheitshärtung](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Handbuch zur vSphere-Sicherheit](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-security-guide.pdf){:new_window}
* [Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-fsa_considerations#fsa_considerations)
* [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)
* [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-f5_considerations#f5_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htcc_considerations.html#hytrust-cloudcontrol-on-ibm-cloud-overview)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_considerations.html#hytrust-datacontrol-on-ibm-cloud-overview)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htkc_considerations.html#hytrust-keycontrol-on-ibm-cloud-overview)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/caveonix/caveonix-intro.html#caveonix-riskforesight)
* [Operations Management unter {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
