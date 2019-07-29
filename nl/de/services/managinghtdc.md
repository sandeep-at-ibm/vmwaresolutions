---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: HTDC WebGUI, HTDC console, enable internet HTDC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust DataControl on IBM Cloud verwalten
{: #managinghtdc}

Zum Verwalten des Service "HyTrust DataControl on {{site.data.keyword.cloud}}" (HTDC) greifen Sie über die {{site.data.keyword.vmwaresolutions_short}}-Konsole auf die HTDC-Web-GUI zu oder greifen Sie über den vSphere Web Client auf die HTDC-Konsole zu.

## Über die IBM Cloud for VMware Solutions-Konsole auf die HyTrust DataControl-Web-GUI zugreifen
{: #managinghtdc-accessing-webgui}

Um sich bei der Web-GUI der primären oder sekundären HTDC-Appliance anzumelden, verwenden Sie die Web-GUI-Berechtigungsnachweise, die auf der Seite mit den Details zum Service "HyTrust DataControl on {{site.data.keyword.cloud_notm}}" enthalten sind.

## Über vSphere Web Client auf HyTrust DataControl-Konsole zugreifen
{: #managinghtdc-accessing-console}

Um über den vSphere Web Client auf die HTDC-Konsole zuzugreifen, führen Sie die folgende Prozedur aus:
1. Suchen Sie in vSphere Web Client die virtuellen Maschinen mit dem Namen **KC1** und **KC2**.
2. Klicken Sie mit der rechten Maustaste auf **KC1** oder **KC2** und dann auf **Konsole öffnen**.
3. Melden Sie sich bei der Konsole mit den Berechtigungsnachweisen der Konsole an, die auf der Seite mit den Details zum Service "HyTrust DataControl on {{site.data.keyword.cloud_notm}}" enthalten sind.

Weitere Informationen finden Sie unter [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Internetzugang für virtuelle HyTrust DataControl-Maschinen aktivieren
{: #managinghtdc-internet-access}

Für HTDC 4.3.2 und aktuellere Versionen wird von {{site.data.keyword.vmwaresolutions_short}} Unterstützung für die automatische Verlängerung von HyTrust-Lizenzen bereitgestellt, für die die Call-Home-Funktion aktiviert ist. Für vCenter Server-Instanzen, die nicht nur privat sind, wird HTDC mit Firewall- und SNAT-Regeln (SNAT - Source Network Address Translation) bereitgestellt, die für die ESG für Management-Services **mgmt-nsx-edge** definiert sind.

Anhand dieser Regeln können Sie den Internetzugang für die virtuellen HyTrust-Maschinen aktivieren. Wenn der Internetzugang nicht aktiviert ist, läuft die Lizenz, die auf Ihre HTDC-Installation angewendet wird, nach einem Jahr ab.

Da bei rein privaten vCenter Server-Umgebungen VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge** nicht hinzugefügt wird, sind die Firewall- und SNAT-Regeln nicht definiert. Somit kann die Internetkonnektivität für rein private Instanzen nicht aktiviert werden und die HyTrust-Lizenzen laufen jährlich ab.
{:note}

### Vorgehensweise zum Suchen der definierten Firewall- und SNAT-Regeln
{: #managinghtdc-proc-find-firewall}

1. Melden Sie sich an VMware vSphere Web Client (FLEX) an und suchen Sie ESG **mgmt-nsx-edge**.
2. Klicken Sie auf **Home > Netzbetrieb& Sicherheit > NSX Edges**.
3. Doppelklicken Sie auf ESG **mgmt-nsx-edge** und klicken Sie auf die Registerkarte **Verwalten**.
4. Wechseln Sie zur Registerkarte **Firewall** und suchen Sie die HyTrust-Regeln. Notieren Sie die Quellen-IP-Adressen. Hierbei handelt es sich um die IP-Adressen für die HyTrust-VMs.
5. Wechseln Sie zur Registerkarte **NAT** und suchen Sie die SNAT-Regeln, die für die HyTrust-VMs erstellt wurden. Die Quellen-IP-Adressen stimmen mit den IP-Adressen überein, die Sie im vorherigen Schritt notiert haben.

### Vorgehensweise zum Aktivieren der Internetkonnektivität für HTDC
{: #managinghtdc-proc-enable-internet}

1. Führen Sie die Schritte 1 - 3 in der vorherigen Prozedur aus.
2. Klicken Sie auf **Einstellungen** und danach auf **Schnittstellen**. Notieren Sie die IP-Adresse für den privaten Uplink. Diese Adresse wird zum neuen Standardgateway.
3. Klicken Sie auf **Home > Hosts und Cluster** und suchen Sie die virtuellen HyTrust-Maschinen. Klicken Sie mit der rechten Maustaste auf eine der virtuellen Maschinen und klicken Sie auf **Konsole öffnen**.
4. Melden Sie sich an der Konsole mithilfe der Konsolenberechtigungsnachweise an, die auf der Detailseite des Service 'HyTrust DataControl on IBM Cloud' in der {{site.data.keyword.vmwaresolutions_short}}-Konsole angegeben sind.
5. Klicken Sie zum Abrufen der IP-Adresse des aktuellen Standardgateways der virtuellen Maschine auf **Netzeinstellungen verwalten > Aktuelle Netzkonfiguration anzeigen**. Notieren Sie die IP-Adresse, die für **Gateway** aufgelistet ist. Diese Adresse wird das Gateway, das für die statische Route verwendet wird.
6. Klicken Sie zum Festlegen einer statischen Route für die virtuelle Maschine auf **Netzeinstellungen verwalten > Statische Routen verwalten > Statische Route hinzufügen**. Legen Sie für **Netzadresse** den Wert `10.0.0.0/8` und für **Gateway** die IP-Adresse fest, die Sie im vorherigen Schritt notiert haben.
7. Klicken Sie zum Festlegen der IP-Adresse für das Standardgateway für die VM auf **Netzeinstellungen verwalten > Aktuelle Netzkonfiguration ändern**. Falls eine Warnung auftritt, klicken Sie auf **OK** und anschließend auf **Angepasste Konfiguration**. Geben Sie im Feld **Gateway** die IP-Adresse für den privaten Uplink ein, die Sie in Schritt 2 notiert haben, und klicken Sie auf **OK**. Warten Sie, bis die neue Netzkonfiguration installiert ist und die Netzservices erneut gestartet werden.
8. Wenn eine Nachricht angezeigt wird, in der Sie zu einer erneuten Authentifizierung von HyTrust SecureOS aufgefordert werden, klicken Sie auf **OK** und geben die IP-Adresse der anderen HyTrust-VM für diese Installation ein. Wenn Sie zum Eingeben einer aus 16 Zeichen bestehenden Kennphrase aufgefordert werden, drücken Sie die Eingabetaste, um zum Hauptmenü zurückzukehren. Überprüfen Sie die aktuelle Netzkonfiguration, um sicherzustellen, dass die Änderungen angewendet werden.
9. Wenn Sie sich vergewissern möchten, dass die virtuelle Maschine über Internetzugriff verfügt, setzen Sie einen Pingbefehl für eine öffentliche IP-Adresse oder Website ab. Klicken Sie auf **Netzeinstellungen verwalten > Netzdiagnosetools > Pingsignal an weiteren Server absetzen**. Geben Sie eine Adresse für eine öffentliche Website wie zum Beispiel `www.ibm.com` ein, klicken Sie auf **OK** und warten Sie, bis eine Nachricht angezeigt wird; Beispiel: `www.ibm.com responds to ping`.
10. Wiederholen Sie die Schritte 3 bis 9 für weitere virtuelle HyTrust-Maschinen.


## Zugehörige Links
{: #managinghtdc-related}

* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust-Website](https://www.hytrust.com/)
