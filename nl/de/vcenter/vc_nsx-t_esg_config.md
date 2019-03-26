---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Netz zur Verwendung des vom Kunden verwalteten NSX-T ESG mit eigenen virtuellen Maschinen konfigurieren
{: #vc_nsx-t_esg_config}

Konfigurieren Sie das Netz für Ihre virtuellen Maschinen so, dass Sie die Vorteile von VMware NSX-T Edge Services Gateway (ESG) nutzen können, das in Ihren VMware vCenter Server-Instanzen bereitgestellt wird. Weitere Informationen zu den bestehenden Sicherheitsmaßnahmen, die Sicherheitsrisiken verringern, finden Sie im Abschnitt [Stellt das NSX Edge für Management-Services ein Sicherheitsrisiko dar?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX-T ist eine Netzvirtualisierungsplattform, die eine Virtualisierung von isolierten Netzen ermöglicht und verschiedene Netzservices wie Switches, Routing und Firewalls zur Verfügung stellt. Weitere Informationen zu NSX finden Sie unter [Overview of NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}.

Im Rahmen des Bestellablaufs für Ihre vCenter Server with NSX-T-Instanz werden die folgenden Aktionen automatisch für Sie ausgeführt: 
* Ein privates Kundenteilnetz wird für die Verwendung durch Ihre virtuellen Maschinen (VMs) für den Zugriff auf das private Netz der {{site.data.keyword.cloud}}-Infrastruktur bestellt.
* Ein öffentliches Kundenteilnetz wird für den Zugriff Ihrer VMs auf das Internet bestellt.
* NSX-T wird in Ihrer vCenter Server with NSX-T-Instanz bereitgestellt und konfiguriert. 
* Ein Beispiel für einen logischen NSX-T-Switch wird zur Verwendung durch die VMs für die Kundenworkload bereitgestellt. 
* Ein Beispiel für einen verteilten logischen NSX-T-Router (Distributed Logical Router, DLR) wird für die potenzielle Ost-West-Kommunikation zwischen lokalen Workloads bereitgestellt, die mit Layer-2-Netzen (L2) verbunden sind. 
* Eine NSX-T Edge-Appliance wird zur Ausführung der Netzadressumsetzung (Network Address Translation, NAT) aus dem Bereich der IP-Adressen eines logischen Workload-Switch in eine öffentliche IP-Adresse nach den NAT-Regeln bereitgestellt und konfiguriert. 

  NSX-T Edge wird für ausschließlich private Instanzen nicht bereitgestellt.
  {:note}

## Vorgehensweise zum Konfigurieren der Netzeinstellungen für Ihre VMs
{: #vc_nsx-t_esg_config-procedure-config-networking}

Um die Vorteile von NSX-T für Ihre Workload-VMs nutzen zu können, müssen Sie eine Reihe von Einstellungen konfigurieren, indem Sie bei der Erstellung Ihrer VMs die folgenden Schritte ausführen: 

1. Legen Sie den logischen Workload-Switch als Netzadapter der VM fest:
   1. Klicken Sie im Dialogfenster **Neue virtuelle Maschine** auf die Registerkarte **Hardware anpassen**.
   2. Wählen Sie im Menü **Neue Einheit** die Option **Netz** aus und klicken Sie auf **Hinzufügen**.
   3. Wählen Sie für den neu hinzugefügten Netzadapter den logischen Workload-Switch im Menü aus. Ein Beispielname für den logischen Workload-Switch ist **vxw-dvs-17-virtualwire-1-sid-6000-Workload**.

   Achten Sie darauf, nicht den Switch **Workloadtransit** auszuwählen.
   {:important}

2. Geben Sie eine verfügbare IP-Adresse für die VM an:
   *  Die IP-Adresse muss im Bereich `192.168.10.0/24` liegen. Bitte beachten Sie, dass die IP-Adresse `192.168.10.1` reserviert ist (siehe **Schritt 3**).
   *  Wenn Sie den Netzbetrieb des Betriebssystems konfigurieren, das auf der VM ausgeführt wird, verwenden Sie die ausgewählte IP-Adresse und die Netzmaske `255.255.255.0`.

   Für das Management des Bereiches von IP-Adressen, denen Sie Ihre VMs zugeordnet haben, sind Sie selbst zuständig.
   {:note}

3. Ordnen Sie das Standardgateway der VM als `192.168.10.1` zu. Diese Adresse ist die IP-Adresse des NSX-DLR auf demselben logischen Switch wie die Workload-VMs.

## Vorgehensweise zum Aktivieren der SNAT-Regel
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

Falls Ihre Workload-VMs abgehenden Zugriff auf das Internet besitzen sollen, müssen Sie die zugehörige Regel für SNAT (Source Network Address Translation) aktivieren. Durch die Aktivierung der SNAT-Regel kann der Internetzugriff von Ihren VMs in eine einzige öffentliche IP-Adresse umgesetzt werden. Führen Sie die folgenden Schritte in VMware vSphere Web Client aus:

1. Klicken Sie auf **Home > Networking & Security**.
2. Klicken Sie im Navigatorfenster auf **NSX Edges** und doppelklicken Sie auf die Edge namens **customer-nsx-edge**.
3. Klicken Sie auf **Management > NAT**, um die Registerkarte **NAT** zu öffnen.
4. Wählen Sie die SNAT-Standardregel in der Tabelle aus und klicken Sie auf das grüne Häkchen über der Tabelle, um die Regel zu aktivieren.

Weitere Informationen zu NAT-Regeln für NSX-T Edge finden Sie unter [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}. 

## Vorgehensweise zum Angeben von Details für Kundenteilnetze
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

Die Edge **customer-nsx-edge** ist für Ihre eigene Verwendung vorgesehen. Sie können sie daher ändern, um weitere NAT-Regeln für eingehenden oder abgehenden Datenverkehr zu definieren. Diese Regeln dürfen nur die IP-Adressen im öffentlichen oder privaten Kundenteilnetz verwenden, die in Ihrem Namen bestellt worden sind.

Führen Sie die folgenden Schritte in VMware vSphere Web Client aus, um die Details für die Kundenteilnetze anzugeben, damit Sie die bestellten IP-Adressen verwenden können:

1. Klicken Sie auf **Home > Networking & Security**.
2. Klicken Sie im Navigatorfenster auf **NSX Edges** und suchen Sie **customer-nsx-edge edge** in der Liste der Edges im rechten Fenster. 
3. Bewegen Sie den Mauszeiger in der Spalte **Description** über die Edge-Beschreibung für **customer-nsx-edge**, um die Teilnetz-IDs für das private und das öffentliche Kundenteilnetz anzuzeigen. 

Weitere Details über die Kundenteilnetze können Sie außerdem mit den folgenden Schritten im {{site.data.keyword.slportal}} ermitteln:

1. Klicken Sie auf **Networking > IP-Management > Teilnetze**.
2. Klicken Sie auf das Filtermenü und geben Sie im Feld "Teilnetz" die ID an, die Sie in der Beschreibung der Edge **customer-nsx-edge** auf der Registerkarte **Summary** in VMware vSphere Web Client ermittelt haben.
3. Lesen Sie die Hinweise, die für die IP-Adressen angezeigt werden. Diese Hinweise geben an, welche der Teilnetze und IP-Adressen bestellt und während der Erstkonfiguration verwendet werden.

   Verwenden Sie nicht die IP-Adressen, die bestellt und während der Erstkonfiguration verwendet werden. Sie können jedoch nach Bedarf andere IP-Adressen in diesen Teilnetzen verwenden. Informationen zum Konfigurieren zusätzlicher Regeln für die Netzadressumsetzung finden Sie auf der Seite [Managing NAT rules](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.
   {:important}

## Zugehörige Links
{: #vc_nsx-t_esg_config-related}

* [Hinweise zum Ändern von vCenter Server-Artefakten](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
