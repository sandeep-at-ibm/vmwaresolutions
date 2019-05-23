---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-14"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Hinweise zum Ändern von vCenter Server-Artefakten
{: #vcenter_chg_impact}

Das Ändern von Benutzern, Ressourcen oder Teilnetzen, die für {{site.data.keyword.vmwaresolutions_full}} reserviert sind, kann sich auf Managementoperationen auswirken.

Bearbeiten Sie keine globalen Berechtigungen der Gruppe **ic4v-vCenter** auf der Seite **Benutzer und Gruppen** auf dem VMware vSphere-Web-Client. Zu solchen Änderungen gehören das Ändern des Benutzernamens, das Löschen des Benutzers oder das Ändern seines Kennworts.
Verwenden Sie die Hostbenutzer-ID **root**. Die Hostbenutzer-ID **ic4vroot** wurde ausschließlich zur Verwendung durch IBM erstellt.
{:important}

## ID "automation"
{: #vcenter_chg_impact-automation-id}
{: faq}

Die ID **automation** ist ein Benutzerkonto, das von den automatisierten Operationen verwendet wird, die in der {{site.data.keyword.vmwaresolutions_short}}-Konsole bereitgestellt werden.

Benutzer und Kennwörter für die automatisierten Operationen in der Konsole dürfen nicht geändert werden, da die Konsolenoperationen, die von diesen Berechtigungsnachweisen abhängig sind, fehlschlagen könnten.

## Servicespezifische Benutzerkonten
{: #vcenter_chg_impact-service-usr-account}
{: faq}

Jeder Service erstellt ein internes Benutzerkonto in vCenter Server. Dieses Konto ist erforderlich, damit Managementoperationen, die einem Service zugeordnet sind, eine vCenter Server-Verbindung herstellen können, um die Operationen für den Service ausführen zu können.

Um Ausfälle und Verbindungsprobleme zu vermeiden, sollten Sie beim Ändern der Benutzer-ID, des Kennworts oder der Einstellungen für den Ablauf des Kennworts für dieses Benutzerkonto sicherstellen, dass auch die Informationen im zugeordneten Service geändert werden.
{:important}

Die Benutzer-ID für dieses Konto weist das Format `<service_name>-<truncated service_uuid>@test.local` oder `<service_name>-<truncated service_uuid>@example-domain.local` auf. Die Benutzer-ID, die vom Service "Veeam on {{site.data.keyword.cloud_notm}}" verwendet wird, um eine vCenter Server-Verbindung zur Durchführung geplanter Sicherungen herzustellen, lautet z. B. `Veeam-<Veeam_uuid>@test.local`.

Die aus `<service_name>` und `<service_uuid>` zusammengesetzte Zeichenfolge wird bei einer Länge von 20 Zeichen abgeschnitten.
{:note}

## VMware-Ressourcen für vCenter Server-Instanzen (V1.9 und höher)
{: #vcenter_chg_impact-vmware-resources-for-inst-v1.9-and-later}
{: faq}

Für Instanzen, die in V1.9 und höher bereitgestellt werden, können Sie das virtuelle VMware-Rechenzentrum, den Cluster, die Switches, die Portgruppen und die Namen von Kundendatenspeichern in VMware vSphere Web Client ändern, falls sich die vCenter Server-Instanz im Status **Bereit** befindet.

Der Standardname des Managementdatenspeichers darf jedoch nicht geändert werden. Der Standardwert lautet **vsanDatastore** für vSAN-Instanzen und **management-share** für NFS-Instanzen (NFS = Network File System). Außerdem dürfen Sie den Namen der Netzuplinks nicht ändern, die während der Bereitstellung erstellt wurden.

## VMware-Ressourcen für vCenter Server-Instanzen (V1.8 und früher)
{: #vcenter_chg_impact-vmware-resources-for-inst-v1.8-and-earlier}
{: faq}

In der folgenden Tabelle sind die Operationen aufgelistet, die betroffen sein könnten, wenn VMware vCenter Server-Ressourcen vom SSO-Administrator außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole geändert werden. Wenn eine Lösung zur Wiederherstellung verfügbar ist, ist sie ebenfalls angegeben.

Diese Tabelle gilt für Instanzen, die in V1.8 und älteren Versionen bereitgestellt wurden, und zusätzlich für Instanzen, die in V1.8 und älteren Versionen bereitgestellt und für die dann ein Upgrade auf V1.9 oder eine höhere Version durchgeführt wurde.

Tabelle 1. Bei Änderungen von VMware-Ressourcen betroffene Operationen

| Versuchte Änderung  | Betroffene Operationen  | Bewertung  | Wiederherstellungsmethode  |
|:------------- |:------------- |:--------------|:--------------|
| Name des virtuellen VMware-Rechenzentrums ändern. | Das Hinzufügen eines virtuellen VMware-Rechenzentrums kann fehlschlagen, weil der neue ESXi-Server nicht mit dem geänderten virtuellen Rechenzentrum verknüpft werden kann. | Wichtig | Ändern Sie den Namen des virtuellen VMware-Rechenzentrums wieder in den ursprünglichen Namen. |
| Portgruppennamen ändern.    | Das Hinzufügen eines ESXi-Servers schlägt möglicherweise fehl. | Wichtig | Ändern Sie den Portgruppennamen wieder in den ursprünglichen Namen. |
| Clusternamen ändern. | Das Hinzufügen eines ESXi-Servers schlägt möglicherweise fehl. | Wichtig | Ändern Sie den Clusternamen wieder in den ursprünglichen Namen.
| Namen des öffentlichen oder privaten verteilten virtuellen Switches (Distributed Virtual Switch, DVS) ändern. | Das Hinzufügen eines ESXi-Servers schlägt möglicherweise fehl. | Wichtig | Ändern Sie den Namen des öffentlichen oder privaten verteilten virtuellen Switches (Distributed Virtual Switch, DVS) in den ursprünglichen Namen.
| Ändern Sie den Namen des vSAN-Datenspeichers in der Instanz, die vSAN verwendet. | Das Hinzufügen eines ESXi-Servers schlägt möglicherweise fehl.<br><br>Das Upgrade für die Instanz kann fehlschlagen. | Wichtig | Ändern Sie den Namen des vSAN-Datenspeichers wieder in den ursprünglichen Namen **vsanDatastore**.
| Ändern Sie den Namen des NFS-Managementdatenspeichers in der Instanz, die NFS verwendet. | Das Hinzufügen eines ESXi-Servers schlägt möglicherweise fehl.<br><br>Das Upgrade für die Instanz kann fehlschlagen. | Wichtig | Ändern Sie den Namen des NFS-Managementdatenspeichers zurück in den ursprünglichen Namen (**management-share**) und hängen Sie den NFS-Datenspeicher wieder als schreibgeschützt an den ESXi-Server an.

In der folgenden Tabelle sind die Operationen aufgelistet, die betroffen sein könnten, wenn SSH- oder Shell-Zugriff für verschiedene Ressourcen inaktiviert ist.

Tabelle 2. Operationen, die vom SSH und Shell-Zugriff betroffen sind (lokal)

| Versuchte Änderung  | Betroffene Operationen  | Bewertung  | Wiederherstellungsmethode  |
|:------------- |:------------- |:--------------|:--------------|
| SSH- oder Shell-Zugriffs für vCenter Server oder PSC inaktivieren. | Die Paarung einer primären und sekundären Instanz kann fehlschlagen.    | Wichtig    | Nicht verfügbar.    |

Wenn Sie den SSH- oder Shell-Zugriff inaktivieren, sollten Sie ihn vorübergehend erneut aktivieren, bevor Sie die angegebenen Operationen ausführen.

## Managementteilnetze für vCenter Server-Instanzen
{: #vcenter_chg_impact-mgmt-subnets}
{: faq}

Nachfolgend sind die Teilnetze beschrieben, die von {{site.data.keyword.vmwaresolutions_short}} bestellt werden. Außerdem werden Sie über die Optionen für die Bestellung von zusätzlichen Teilnetzen für Ihre eigene Verwendung informiert.

**VORSICHT:** Verwenden Sie diese Komponenten nicht für andere Zwecke, da die Stabilität Ihrer Umgebung andernfalls erheblich beeinträchtigt wird.

Mit jeder {{site.data.keyword.cloud_notm}} Bare Metal Server-Bestellung werden standardmäßig die folgenden IP-Adressbereiche bestellt:
*  1 primärer öffentlicher Bereich von 32 IP-Adressen
*  1 primärer privater Bereich von 64 IP-Adressen

Darüber hinaus sind die folgenden Managementteilnetze ebenfalls für {{site.data.keyword.vmwaresolutions_short}} reserviert:
*  2 portierbare private Teilnetze mit 64 IP-Adressen im ersten VLAN; eines für das Management und das andere für VTEPS.
*  2 portierbare private Teilnetze mit 64 IP-Adressen im zweiten VLAN; eines für vMotion und das andere für vSAN.
*  1 portierbares öffentliches Teilnetz mit 16 IP-Adressen im öffentlichen VLAN.

Wenn Sie weitere Teilnetze verwenden müssen, können Sie zu verwendende IP-Adressen mit einem der folgenden Verfahren anfordern:
*  **Option 1 (empfohlen)**: Verwenden Sie VMware NSX-Vorlagen (Overlays) für virtuelle Netze. Bei der Bestellung erhalten Sie eine VXLAN-Beispielvorlage. Diese VXLAN-Vorlage können Sie als Ausgangspunkt bei der Erstellung von SDN (Software-Defined Networking) verwenden. Weitere Informationen finden Sie unter [Netz zur Verwendung des vom Kunden verwalteten NSX Edge konfigurieren](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config).
*  **Option 2**: Bestellen Sie Ihre eigenen portierbaren öffentlichen oder privaten Teilnetze, um IP-Adressen zu erhalten. Um die bestellten Teilnetze von den Managementteilnetzen zu unterscheiden, können Sie Hinweise zu allen bestellten Teilnetzen hinzufügen.
