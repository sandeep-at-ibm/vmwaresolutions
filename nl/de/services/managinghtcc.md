---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-23"

keywords: HTCC WebGUI, HTCC console, enable internet HTCC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust CloudControl on IBM Cloud verwalten
{: #managinghtcc}

Zum Verwalten des Service 'HyTrust CloudControl on {{site.data.keyword.cloud}}' (HTCC) greifen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole auf die HTCC-Web-GUI oder über den vSphere Web Client auf die HTCC-Konsole zu.

## Über die IBM Cloud for VMware Solutions-Konsole auf die HyTrust CloudControl-Web-GUI zugreifen
{: #managinghtcc-accessing-webgui}

Um sich bei der Web-GUI der primären oder sekundären HTCC-Appliance anzumelden, verwenden Sie die Web-GUI-Berechtigungsnachweise, die auf der Seite mit den Details zum Service 'HyTrust CloudControl on {{site.data.keyword.cloud_notm}}' enthalten sind.

## Über vSphere Web Client auf HyTrust CloudControl-Konsole zugreifen
{: #managinghtcc-accessing-console}

Um über den vSphere Web Client auf die HTCC-Konsole zuzugreifen, führen Sie die folgende Prozedur aus:
1. Suchen Sie in vSphere Web Client die virtuellen Maschinen mit dem Namen **CC1** und **CC2**.
2. Klicken Sie mit der rechten Maustaste auf **CC1** oder **CC2** und dann auf **Konsole öffnen**.
3. Melden Sie sich an der Konsole mit den Berechtigungsnachweisen der Konsole an, die auf der Seite mit den Details zum Service 'HyTrust CloudControl on {{site.data.keyword.cloud_notm}}' enthalten sind.

Weitere Informationen finden Sie unter [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Internetzugang für virtuelle HyTrust CloudControl-Maschinen aktivieren
{: #managinghtcc-internet-access}

Für HTCC 5.5.1 und aktuellere Versionen wird von {{site.data.keyword.vmwaresolutions_short}} Unterstützung für die automatische Verlängerung von HyTrust-Lizenzen bereitgestellt, für die die Call-Home-Funktion aktiviert ist. Für vCenter Server-Instanzen, die nicht nur privat sind, wird HTCC mit Firewall- und SNAT-Regeln (SNAT - Source Network Address Translation) bereitgestellt, die für die ESG für Management-Services **mgmt-nsx-edge** definiert sind.

Anhand dieser Regeln können Sie den Internetzugang für die virtuellen HyTrust-Maschinen aktivieren. Wenn der Internetzugang nicht aktiviert ist, läuft die Lizenz, die auf Ihre HTCC-Installation angewendet wird, nach einem Jahr ab.

Da bei rein privaten vCenter Server-Umgebungen VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge** nicht hinzugefügt wird, sind die Firewall- und SNAT-Regeln nicht definiert. Somit kann die Internetkonnektivität für rein private Instanzen nicht aktiviert werden und die HyTrust-Lizenzen laufen jährlich ab.
{:note}

### Vorgehensweise zum Suchen der definierten Firewall- und SNAT-Regeln
{: #managinghtcc-proc-find-firewall}

1. Melden Sie sich an VMware vSphere Web Client (FLEX) an und suchen Sie ESG **mgmt-nsx-edge**.
2. Klicken Sie auf **Home > Netzbetrieb & Sicherheit > NSX Edges**.
3. Doppelklicken Sie auf ESG **mgmt-nsx-edge** und klicken Sie auf die Registerkarte **Verwalten**.
4. Wechseln Sie zur Registerkarte **Firewall** und suchen Sie die HyTrust-Regeln. Notieren Sie die Quellen-IP-Adressen. Hierbei handelt es sich um die IP-Adressen für die HyTrust-VMs.
5. Wechseln Sie zur Registerkarte **NAT** und suchen Sie die SNAT-Regeln, die für die HyTrust-VMs erstellt wurden. Die Quellen-IP-Adressen stimmen mit den IP-Adressen überein, die Sie im vorherigen Schritt notiert haben.

### Vorgehensweise zum Aktivieren der Internetkonnektivität für HTCC
{: #managinghtcc-enable-internet}

Die folgenden Schritte gelten für die Aktualisierung der HTCC-Netzeinstellungen für die primäre virtuelle Maschine (VM), die für die Lizenzupgrades verwendet wird. Sie müssen die Einstellungen für die sekundäre VM nicht aktualisieren.
{:note}

1. Führen Sie die Schritte 1-3 in der vorherigen Prozedur aus.
2. Klicken Sie auf **Einstellungen** und danach auf **Schnittstellen**. Notieren Sie sich die IP-Adresse für den privaten Uplink, der zum neuen Standardgateway wird.
3. Wechseln Sie zur Detailseite für den Service 'HyTrust CloudControl on {{site.data.keyword.cloud_notm}}', klicken Sie auf **HTCC-Webbenutzerschnittstelle anzeigen** und melden Sie sich mit den Berechtigungsnachweisen der Servicedetailseite an.
4. Notieren Sie das vorhandene Standardgateway. Klicken Sie zum Beispiel für HTCC 5.5.1 auf **Konfiguration > Netz**. Notieren Sie die aufgelistete IP-Adresse des Gateways, das zum Gateway für die statische Route wird.
5. Fügen Sie eine statische Route hinzu. Klicken Sie zum Beispiel für HTCC 5.5.1 auf **Konfiguration > Statische Routen**. Klicken Sie auf **Hinzufügen**, geben Sie die folgenden Informationen ein und klicken Sie auf **OK**.

  ```
  Network Address: 10.0.0.0
  Mask: 255.0.0.0
  Gateway: IP noted in step 4
  Device: Network 1
  ```

6. Ändern Sie das Standardgateway. Klicken Sie zum Beispiel für HTCC 5.5.1 auf **Konfiguration > Netz** und ersetzen Sie die IP-Adresse im Feld **Gateway** durch die, die Sie in Schritt 3 notiert haben, und klicken Sie auf **Speichern**. 

  Stellen Sie sicher, dass Sie die statische Route festlegen, bevor Sie das Standardgateway ändern, da die Webkonsole andernfalls nicht mehr erreichbar sein kann.
  {:important}

  Die primäre virtuelle Maschine verfügt jetzt über Internetzugriff.

7. Wenn Sie sich vergewissern möchten, dass die primäre virtuelle Maschine über Internetzugriff verfügt, führen Sie den Befehl `wget` für eine öffentliche IP-Adresse oder Website aus. Wechseln Sie hierzu wieder zurück zu vCenter und klicken Sie mit der rechten Maustaste auf **CC1 > Konsole öffnen**. Melden Sie sich an der Konsole mithilfe der Konsolenberechtigungsdetails von der Detailseite des HyTrust CloudControl on {{site.data.keyword.cloud_notm}}-Service an. Führen Sie einen `wget`-Befehl aus, zum Beispiel `wget www.ibm.com`; darauf muss sofort eine Antwort zurückgegeben werden. Vergewissern Sie sich, dass die Anforderung gesendet wurde und die Antwort `200` empfangen wurde.

## Zugehörige Links
{: #managinghtcc-related}

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust-Website](https://www.hytrust.com/){:external}
