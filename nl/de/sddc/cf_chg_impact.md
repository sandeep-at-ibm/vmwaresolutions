---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

# Hinweise zum Ändern von Cloud Foundation-Artefakten

Das Ändern von Benutzern, Ressourcen oder Teilnetzen, die für {{site.data.keyword.vmwaresolutions_full}} reserviert sind, kann sich auf Managementoperationen für Instanzen von VMware Cloud Foundation auswirken.

**Wichtig:** Ändern Sie nicht die globalen Berechtigungen der Gruppe **ic4v-vCenter** auf der Seite **Benutzer und Gruppen** auf dem VMware vSphere-Web-Client. Folgende Beispiele gehören zu den globalen Berechtigungsänderungen: Ändern des Benutzernamens, Löschen des Benutzers oder Ändern seines Kennworts.

## Servicespezifische Benutzerkonten

Jeder Service erstellt ein internes Benutzerkonto in vCenter Server. Dieses Konto ist erforderlich, damit Managementoperationen, die einem Service zugeordnet sind, eine vCenter Server-Verbindung herstellen können, um die Operationen für den Service ausführen zu können.

**Wichtig:** Um Ausfälle und Verbindungsprobleme zu vermeiden, sollten Sie beim Ändern der Benutzer-ID, des Kennworts oder der Einstellungen für den Ablauf des Kennworts für dieses Benutzerkonto sicherstellen, dass auch die Informationen im zugeordneten Service geändert werden.

Die Benutzer-ID für dieses Konto ist im Format `<service_name>-<truncated service_uuid>@test.local` oder `<service_name>-<truncated service_uuid>@example-domain.local` angegeben. Die Benutzer-ID, die vom Service "Veeam on {{site.data.keyword.cloud_notm}}" verwendet wird, um eine vCenter Server-Verbindung zur Durchführung geplanter Sicherungen herzustellen, lautet z. B. `Veeam-<Veeam_uuid>@test.local`.

**Hinweis:** Die aus `<service_name>` und `<service_uuid>` zusammengesetzte Zeichenfolge wird bei einer Länge von 20 Zeichen abgeschnitten.

## VMware-Ressourcen für Cloud Foundation-Instanzen

In der folgenden Tabelle sind die Operationen aufgelistet, die betroffen sein könnten, wenn Sie VMware-Ressourcen außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern. Wenn eine Lösung zur Wiederherstellung verfügbar ist, ist sie ebenfalls angegeben.

Tabelle 1. Betroffene Operationen für den SSO-Administrator (Kunde)

| Versuchte Änderung  | Betroffene Operationen  | Bewertung  | Wiederherstellungsmethode  |
|:------------- |:------------- |:--------------|:--------------|
| Name des virtuellen VMware-Rechenzentrums ändern. | Das Hinzufügen eines VMware-Rechenzentrums kann fehlschlagen, weil der neue ESXi-Server nicht mit dem geänderten Rechenzentrum verknüpft werden kann. | Wichtig | Ändern Sie den Namen des virtuellen VMware-Rechenzentrums wieder in den ursprünglichen Namen. |
| Portgruppennamen ändern.    | Das Hinzufügen eines ESXi-Servers schlägt möglicherweise fehl. | Wichtig | Ändern Sie den Portgruppennamen wieder in den ursprünglichen Namen. |
| Clusternamen ändern. | Das Hinzufügen eines ESXi-Servers schlägt möglicherweise fehl. | Wichtig | Ändern Sie den Clusternamen wieder in den ursprünglichen Namen.
| Namen des öffentlichen oder privaten verteilten virtuellen Switches (Distributed Virtual Switch, DVS) ändern. | Das Hinzufügen eines ESXi-Servers schlägt möglicherweise fehl. | Wichtig | Ändern Sie den DVS-Namen wieder in den ursprünglichen Namen.
| Namen des VSAN-Datenspeichers ändern. | Das Hinzufügen eines ESXi-Servers schlägt möglicherweise fehl.<br><br>Das Upgrade für die Instanz kann fehlschlagen. | Wichtig | Ändern Sie den Namen des VSAN-Datenspeichers wieder in den ursprünglichen Namen **vsanDatastore**.
| Instanznamen oder Domänennamen ändern. | Die Instanz ist nicht verwendbar. | Kritisch | Nicht verfügbar.

In der folgenden Tabelle sind die Operationen aufgelistet, die betroffen sein könnten, wenn SSH- oder Shell-Zugriff für verschiedene Ressourcen inaktiviert ist.

Tabelle 2. Operationen, die vom SSH und Shell-Zugriff betroffen sind (lokal)

| Versuchte Änderung  | Betroffene Operationen  | Bewertung  | Wiederherstellungsmethode  |
|:------------- |:------------- |:--------------|:--------------|
| SSH- oder Shell-Zugriffs für vCenter Server oder PSC inaktivieren.    | Die Paarung einer primären und sekundären Instanz kann fehlschlagen. Das Anwenden von Programmkorrekturen auf die Ressourcen kann fehlschlagen.    | Wichtig    | Nicht verfügbar.    |
| SSH- oder Shell-Zugriff für ESXi inaktivieren.    | Das Hinzufügen und Entfernen von Hosts, Services und Netzspeicher für die Instanz kann fehlschlagen. Das Anwenden von Programmkorrekturen auf die Ressourcen kann fehlschlagen.    | Wichtig    | Nicht verfügbar.    |

Wenn Sie den SSH- oder Shell-Zugriff inaktivieren, sollten Sie ihn vorübergehend erneut aktivieren, bevor Sie die angegebenen Operationen ausführen.

## Managementteilnetze für Cloud Foundation-Instanzen

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

* **Option 1 (empfohlen):** Verwenden Sie VMware NSX-Vorlagen (Overlays) für virtuelle Netze. Bei der Bestellung erhalten Sie eine VXLAN-Beispielvorlage. Diese VXLAN-Vorlage können Sie als Ausgangspunkt bei der SDN-Erstellung verwenden.
* **Option 2:** Bestellen Sie Ihre eigenen portierbaren öffentlichen oder privaten Teilnetze, um IP-Adressen zu erhalten. Um die bestellten Teilnetze von den Managementteilnetzen zu unterscheiden, können Sie Hinweise zu allen bestellten Teilnetzen hinzufügen.
