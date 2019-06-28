---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-16"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Hybridity Bundle aus einer vCenter Server-Instanz entfernen
{: #vc_hybrid_deletingbundle}

Zum Entfernen der Hybridity Bundle-Lizenz aus Ihrer vCenter Server-Instanz müssen Sie die Schlüssel der VMware NSX- und VMware vSAN-Mietlizenzen in VMware vSphere Web Client durch Schlüssel eigener Lizenzen (BYOL - Bring Your Own License) ersetzen. Darüber hinaus müssen Sie ein Support-Ticket öffnen, um die Gebühren für die Mietlizenzen zu stornieren.

Wenn Sie für Ihre Lizenz ein Downgrade durchführen, kann dies zum Fehlschlagen Ihrer vCenter Server-Instanz führen. Sie können auswählen, auf eigenes Risiko ein Downgrade für Ihre Lizenz durchzuführen; betrachten Sie jedoch zunächst die Funktionen, die nach einem Downgrade nicht verfügbar sein werden. Weitere Informationen finden Sie im [Vergleichsdiagramm für VMware-Komponenteneditionen](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution-appendix).
{:important}

## Wichtige Hinweise, bevor Sie das Hybridity Bundle aus einer Umgebung mit mehreren Standorten entfernen:
{: #vc_hybrid_deletingbundle-considerations}

Lesen Sie die folgenden Hinweise, bevor Sie das Hybridity Bundle aus einer Umgebung mit mehreren Standorten entfernen:

* Sie müssen BYOL-Lizenzen auf alle Bereitstellungen mit mehreren Standorten anwenden, bevor Sie Mietlizenzen entfernen.
* Sie müssen VMware NSX-Lizenzen kombinieren und über genügend Kapazität zur Nutzung über alle Bereitstellungen mit mehreren Standorten verfügen.
* Sie müssen ein einzelnes Support-Ticket erstellen, um das Hybridity Bundle aus allen Bereitstellungen mit mehreren Standorten zu entfernen.

Beim Entfernen des Hybridity Bundle aus einer Umgebung mit mehreren Standorten werden BYOL-Lizenzen angewendet. Es liegt in Ihrer Verantwortung sicherstellen, dass die Lizenzeditionen über alle Standorten hinweg in der Konfiguration mit mehreren Standorten konsistent sind.
{:note}

## Vor dem Entfernen von Hybridity Bundle
{: #vc_hybrid_deletingbundle-prereq}

Überprüfen Sie folgende Voraussetzungen, bevor Sie Hybridity Bundle entfernen:

* Sie verfügen über eine vCenter Server-Instanz mit Version 2.4 oder höher, in der Hybridity Bundle aktiviert ist.
* In Ihrer vCenter Server-Instanz ist nicht der Service "VMware HCX on {{site.data.keyword.cloud_notm}}" installiert.
* Sie haben als Administrator Zugriff auf VMware vSphere Web Client.
* Falls noch nicht angewendet, verfügen Sie über BYOL-Schlüssel, die für das VMware NSX-Cluster und jedes VMware vSAN-Cluster verfügbar sind.
* Optional und falls noch nicht angewendet, verfügen Sie über BYOL-Schlüssel, die für die Anwendung auf die Lizenzen von VMware vCenter Server und VMware vSphere Enterprise Plus verfügbar sind.

## Vorgehensweise zum Entfernen von Hybridity Bundle
{: #vc_hybrid_deletingbundle-procedure}

1. Melden Sie sich als **Administrator** bei dem VMware vSphere Web Client an, für den Sie das Hybridity Bundle entfernen möchten.
2. Klicken Sie auf die Optionen für **Home > Administration > Lizenzierung > Lizenzen**.
3. Klicken Sie auf die Registerkarte für **Assets**.
4. Führen Sie folgende Schritte aus, um für VMware NSX eine eigene Lizenz (BYOL) zu installieren:
   1. Klicken Sie auf die Registerkarte **Lösungen**.
   2. Wählen Sie "NSX for vSphere" aus und klicken Sie auf die Optionen für **Alle Aktionen > Lizenz zuordnen**.
   3. Klicken Sie auf das Symbol für **Hinzufügen** und geben Sie den Lizenzschlüssel ein. Klicken Sie auf **Weiter**.
   4. Geben Sie den Namen für die Lizenz ein und klicken Sie auf **Weiter**. Klicken Sie auf **Fertigstellen**, um die Lizenz hinzuzufügen.
   5. Wählen Sie den neuen Lizenzschlüssel aus.
   6. Notieren Sie sich die vollständigen Lizenzschlüssel für sowohl die angewendete Lizenz als auch die ersetzte Lizenz.

   Halten Sie die Lizenzdetails für eine spätere Verwendung in diesem Verfahren bereit.
   {:important}
   7. Klicken Sie auf **OK**, damit die Lizenz zugeordnet wird.
5. Führen Sie folgende Schritte aus, um für VMware vSAN eine eigene Lizenz (BYOL) zu installieren:
   1. Klicken Sie auf die Registerkarte **Cluster**.
   2. Führen Sie folgende Schritte für jeden vSAN-Cluster aus, der Ihrer vCenter Server-Instanz zugeordnet ist:
    1. Wählen Sie ein vSAN-Cluster aus und klicken Sie auf die Optionen für **Alle Aktionen > Lizenz zuordnen**.
    2. Klicken Sie auf das Symbol für **Hinzufügen** und geben Sie den Lizenzschlüssel ein. Klicken Sie auf **Weiter**.
    3. Geben Sie den Namen für die Lizenz ein und klicken Sie auf **Weiter**. Klicken Sie auf **Fertigstellen**, um die Lizenz hinzuzufügen.
    4. Wählen Sie den neuen Lizenzschlüssel aus.
    5. Notieren Sie sich den Clusternamen und die Volllizenzschlüssel sowohl der angewendeten als auch der ersetzten Lizenz.

    Halten Sie die Lizenzdetails für eine spätere Verwendung in diesem Verfahren bereit.
    {:important}
    6. Klicken Sie auf **OK**, damit die Lizenz zugeordnet wird.
6. Führen Sie optional folgende Schritte aus, um für VMware vCenter Server eine eigene Lizenz (BYOL) zu installieren:
   1. Klicken Sie auf die Registerkarte für **vCenter Server-Systeme**.
   2. Wählen Sie "vCenter Server" aus und klicken Sie auf die Optionen für **Alle Aktionen > Lizenz zuordnen**.
   3. Klicken Sie auf das Symbol für **Hinzufügen** und geben Sie den Lizenzschlüssel ein. Klicken Sie auf **Weiter**.
   4. Geben Sie den Namen für die Lizenz ein und klicken Sie auf **Weiter**. Klicken Sie auf **Fertigstellen**, um die Lizenz hinzuzufügen.
   5. Wählen Sie den neuen Lizenzschlüssel aus.
   6. Notieren Sie sich die Volllizenzschlüssel sowohl der angewendeten als auch der ersetzten Lizenz.

   Halten Sie die Lizenzdetails für eine spätere Verwendung in diesem Verfahren bereit.
   {:important}

   7. Klicken Sie auf **OK**, damit die Lizenz zugeordnet wird.
7. Führen Sie optional folgende Schritte aus, um für VMware vSphere Enterprise Plus eine eigene Lizenz (BYOL) zu installieren:
  1. Klicken Sie auf die Registerkarte für **Hosts**.
  2. Führen Sie folgende Schritte für jeden Cluster aus, der Ihrer vCenter Server-Instanz zugeordnet ist, oder führen Sie folgende Schritte gleichzeitig für alle Cluster aus, wenn dieselbe Lizenz auf alle Cluster angewendet wird, die Ihrem vCenter-Server zugeordnet sind:
    1. Wählen Sie alle Ihrem Cluster zugeordneten Hosts aus und klicken Sie auf die Optionen für **Alle Aktionen > Lizenz zuordnen**.
    2. Klicken Sie auf das Symbol für **Hinzufügen** und geben Sie den Lizenzschlüssel ein. Klicken Sie auf **Weiter**.
    3. Geben Sie den Namen für die Lizenz ein und klicken Sie auf **Weiter**. Klicken Sie auf **Fertigstellen**, um die Lizenz hinzuzufügen.
    4. Wählen Sie den neuen Lizenzschlüssel aus.
    5. Notieren Sie sich den Clusternamen und die Volllizenzschlüssel sowohl der angewendeten als auch der ersetzten Lizenz.

    Halten Sie die Lizenzdetails für eine spätere Verwendung in diesem Verfahren bereit. Schreiben Sie die den einzelnen Lizenzschlüsseln zugeordneten Clusternamen auf, falls die Lizenzschlüssel nicht für alle Cluster gleich sind.
    {:important}

    6. Klicken Sie auf **OK**, damit die Lizenz zugeordnet wird.
8. Entfernen Sie die Mietlizenzen.
   1. Klicken Sie auf die Registerkarte **Lizenzen**.
   2. Wählen Sie die Lizenzen aus, die Sie in den Schritten 4 bis 7 ersetzt haben.
   3. Klicken Sie auf das Symbol **Lizenzen entfernen**.
9. Öffnen Sie ein Support-Ticket und geben Sie folgende Informationen an, um die Gebühren für die Mietlizenzen zu stornieren:
  * Der Name Ihrer vCenter Server-Instanz(en).
  * Die Ihrer/Ihren vCenter Server-Instanz(en) zugeordnete ID.
  * Eine Liste der BYOL-Lizenzschlüssel, die Sie in diesem Verfahren installiert haben. Geben Sie, soweit zutreffend, den Instanz- und Clusternamen mit den Lizenzschlüsseln für das vSphere-Cluster und die vSAN-Cluster an.
  * Eine Liste der Mietlizenzschlüssel, die Sie in diesem Verfahren entfernt haben. Geben Sie, soweit zutreffend, den Instanz- und Clusternamen mit den Lizenzschlüsseln für das vSphere-Cluster und die vSAN-Cluster an.

  Die IBM Support- und Operationsteams greifen auf die vCenter-Managementschicht Ihres Kontos der {{site.data.keyword.cloud_notm}}-Infrastruktur zu, um zu prüfen, dass die Mietlizenzen entfernt wurden, bevor die Gebühren für die Hybridity Bundle-Mietlizenz storniert werden.
  {:note}

## Zugehörige Links
{: #vc_hybrid_deletingbundle-related}

* [vCenter Server with Hybridity Bundle-Instanzen bestellen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [vCenter Server with Hybridity Bundle-Instanzen anzeigen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
