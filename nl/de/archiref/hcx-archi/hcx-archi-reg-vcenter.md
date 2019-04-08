---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

subcollection: vmwaresolutions


---
# HCX Manager bei vCenter registrieren
{: #hcx-archi-reg-vcenter}

Sie können das Hybrid-Cloud-Services-Plug-in bei VMware vSphere Web Client registrieren und den Management-Service für Hybrid-Cloud-Services starten.

## Vorbereitende Schritte
{: #hcx-archi-reg-vcenter-prereq}

Damit die virtuelle Hybrid-Cloud-Services-Appliance registriert werden kann, muss sie erst eingeschaltet werden.

## Vorgehensweise zum Registrieren von HCX Manager bei vCenter
{: #hcx-archi-reg-vcenter-proc-register}

1. Melden Sie sich bei der virtuellen Hybrid-Cloud-Services-Appliance an.
2. Klicken Sie auf die Kachel **Einstellungen verwalten**.
  1. Wählen Sie im linken Teilfenster unter **Systeme konfigurieren** die Option "vCenter" aus.
  2. Klicken Sie oben rechts auf **vCenter hinzufügen**.
  3. Geben Sie die IP-Adresse von vCenter Server in der Form `https:vCenter-host-name` oder `https:vCenter-IP-address` ein. Beispiel: `https:My-vCenter` oder `https:10.108.26.211`.
  4. Geben Sie Benutzername und Kennwort für vCenter Server ein. Das verwendete Konto muss über die Rolle des vCenter-Administrators verfügen.
  5. Klicken Sie auf **OK**. Wenn die Nachricht _Die Anwendung muss neu gestartet werden_ angezeigt wird, führen Sie keinen Neustart aus.
3. Konfigurieren Sie den Suchservice.
  1. Klicken Sie auf die Registerkarte **Verwalten**.
  2. Klicken Sie auf die Schaltfläche **Bearbeiten** ganz rechts von dem Textfeld **URL des Suchservice**.
  3. Geben Sie den Netzserviceendpunkt für die Suche im folgenden Format an:
    * Für vCenter Server 5.5u3: `https://ssoip:/7444/lookupservice/sdk`
    * Für vCenter Server 6.0 Update 2: `https://ssoip/lookupservice/sdk`
  4. Klicken Sie auf **OK**. Führen Sie keinen Neustart aus, wenn eine Nachricht zum Neustart der Web-Engine angezeigt wird.
4. Klicken Sie auf die Registerkarte **Zusammenfassung** und suchen Sie den Abschnitt **Hybriditäts-Managementkomponenten**. Stoppen und starten Sie sowohl die Anwendungsengine als auch die Web-Engine.
5. Um die Registrierung abzuschließen, melden Sie sich von vSphere Web Client ab. Melden Sie sich wieder an, um zu überprüfen, ob die Aktualisierung des Bildschirms erfolgt ist.

## Ergebnisse
{: #hcx-archi-reg-vcenter-results}

Beachten Sie, dass jetzt das Symbol für **Hybrid-Cloud** vorhanden ist, sowie das Menüelement **Hybrid-Cloud-Services** auf der linken Seite. Durch die Registrierung von Hybrid-Cloud-Services werden diese Bezeichnungen aktualisiert. Im Bestand ändert sich die Symbolbezeichnung in **Hybrid-Cloud-Services**.

## Zugehörige Links
{: #hcx-archi-reg-vcenter-related}

* [Hybrid-Services installieren und konfigurieren](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-hybrid)
