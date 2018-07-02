---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# vCenter Server with Hybridity Bundle-Instanzen anzeigen

Mit dem hier beschriebenen Verfahren können Sie die von Ihnen bestellten VMware vCenter Server with Hybridity Bundle-Instanzen sowie zugehörige detaillierte Informationen anzeigen.

## Zusammenfassung der vCenter Server with Hybridity Bundle-Instanzen anzeigen

Führen Sie die folgenden Schritte aus, um eine Zusammenfassung aller vCenter Server with Hybridity Bundle-Instanzen in Ihrer Umgebung anzuzeigen:
1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Zeigen Sie in der Tabelle **vCenter Server** die Liste Ihrer Instanzen an.

Tabelle 1. Elemente von vCenter Server with Hybridity Bundle-Instanzen

| Element        | Beschreibung       |  
|:------------- |:------------- |
| Name | Der Name der Instanz. |
| Version | Die Releaseversion, in der die Instanz bereitgestellt wurde oder auf die ein Upgrade durchgeführt wurde. |  
| Standort | Das {{site.data.keyword.CloudDataCent}}, in dem die Instanz gehostet wird. |  
| Erstellungszeit | Der Zeitpunkt (Datum und Uhrzeit), zu dem die Instanz erstellt wurde. |  
| Status | Der Status der Instanz. |  

Für die Instanz gibt es eine Reihe von Statuswerten.

Tabelle 2. Statusbeschreibungen der vCenter Server with Hybridity Bundle-Instanzen

| Status        | Beschreibung       |
|:------------- |:------------- |
| Wird erstellt | Die Instanz wird gerade erstellt. |
| Wird aufgebaut | Die Instanz wird gerade konfiguriert. |
| Bereit | Die Instanz ist zur Verwendung bereit. |
| Wird geändert | Die Instanz wird gerade geändert. |
| Fehlgeschlagen | Der Erstellungs-, Konfigurations- oder Änderungsprozess ist fehlgeschlagen. |
| Wird gelöscht | Die Instanz wird gerade gelöscht. |
| Fehler beim Löschvorgang | Beim Löschen der Instanz ist ein Fehler aufgetreten. |
| Gelöscht | Die Instanz wurde gelöscht. |

## Eigenschaftsdetails von vCenter Server with Hybridity Bundle-Instanzen anzeigen

Gehen Sie wie folgt vor, um die Eigenschaftsdetails einer vCenter Server with Hybridity Bundle-Instanz anzuzeigen:
1. Klicken Sie in der Tabelle **vCenter Server-Instanzen** auf einen Instanznamen.
2. Zeigen Sie unter **Eigenschaften** die Details für die Instanz an.

Tabelle 3. Eigenschaften der vCenter Server with Hybridity Bundle-Instanzen

| Eigenschaft        | Beschreibung       |
|:------------- |:------------- |
| Name | Der Name der Instanz. |
| ID | Die ID der Instanz. |
| Standort | Das {{site.data.keyword.CloudDataCent_notm}}, in dem die Instanz gehostet wird. |
| Aktuelle Version | Die aktuelle Version von {{site.data.keyword.vmwaresolutions_short}}. |
| vCenter-Version | Die Version von VMware vCenter Server with Hybridity Bundle.<br><br>**Hinweis:** Die Versionen von vCenter Server, die in der {{site.data.keyword.vmwaresolutions_short}}-Konsole und in VMware vSphere Web Client angezeigt werden, weichen etwas voneinander ab. Beide Angaben sind richtig. |
| NSX for vSphere | Die Produktversion von VMware NSX for vSphere. |
| NSX-Lizenzedition | Die Version und Edition der VMware NSX-Lizenz. |
| DNS, Rootdomäne | Der Rootdomänenname ist der Domänenname von DNS (Domain Name System) und der Gesamtstrukturrootname von Microsoft Active Directory (AD). |
| DNS, SSO-Domäne | Die SSO-Domäne ist die Single-Sign-on-Domäne von vSphere. Der SSO-Domänenname wird für alle bereitgestellten vCenter Server with Hybridity Bundle-Instanzen auf den Wert <samp class="ph codeph">vsphere.local</samp> festgelegt. |
| DNS, Unterdomäne | Die Unterdomäne ist im DNS-Unterdomänennamen des Namens der Rootdomäne angegeben, in der sich die Hostnamen der lokalen vCenter Server with Hybridity Bundle-Instanz befinden. Der Unterdomänenname hat das Format <samp class="ph codeph"><var class="keyword varname">name_der_vcenter_server-instanz</var>.<var class="keyword varname">root.domänenname</var></samp>. |
| Hybridity Bundle | Gibt an, ob vCenter Server with Hybridity Bundle installiert ist. |
| Status  | Der Status der Instanz.<br><br>Die angezeigten Informationen aktualisieren den Verarbeitungsfortschritt bei der Bereitstellung bzw. der für die Instanz ausgeführten Aktion. Falls Probleme auftreten, wird möglicherweise eine Nachricht angezeigt, die Sie bei der Untersuchung und Lösung des Problems unterstützt. |

## Zugriffsinformationen für vCenter Server with Hybridity Bundle-Instanzen anzeigen

Zeigen Sie unter **Zugriffsinformationen** die Zugriffsinformationen für die instanzbezogenen Komponenten an. Bei den angezeigten Kennwörtern handelt es sich um Anfangskennwörter, die vom System generiert werden. Wenn Sie sie außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden sie auf der Seite mit der Instanzzusammenfassung nicht aktualisiert.

Tabelle 4. vCenter Server with Hybridity Bundle-Zugriffsinformationen für instanzbezogene Komponenten

| Komponente        | Beschreibung       |
|:------------- |:------------- |
| AD/DNS-IPs | Die IP-Adressen der beiden AD-Server. |
| Vollständig qualifizierte Domänennamen für AD/DNS | Die vollständig qualifizierten Domänennamen des AD/DNS-Servers.<br><br>**Hinweis:** Zur Herstellung einer Verbindung zu allen AD/DNS-Servern über eine Remote-Desktop-Verbindung kann dasselbe Administratorkennwort verwendet werden. |
| AD/DNS ADMIN (Remote Desktop)  | Für primäre Instanzen werden der Benutzername und das Kennwort für den Zugriff auf den AD-Server über eine Remote-Desktop-Verbindung angezeigt.<br><br>Klicken Sie für sekundäre Instanzen auf den Link **Für primäre Instanz anzeigen**, um zu den Informationen zu Benutzername und Kennwort in der primären Instanz weitergeleitet zu werden.<br><br>**Hinweis**: Wenn die sekundäre Instanz zur primären DNS-Domäne hinzugefügt wurde und die Replikation stattfindet, überschreibt das lokale Administratorkennwort für die primäre Instanz möglicherweise das lokale Administratorkennwort für die sekundäre Instanz. Wenn Sie auf den Link **Für primäre Instanz anzeigen** klicken, erhalten Sie Zugriff auf das richtige Administratorkennwort.  
| NSX-Manager-IP  | Die IP-Adresse des NSX-Managers.  |
| Vollständig qualifizierter Domänenname für NSX-Manager  | Der vollständig qualifizierte Domänenname des NSX-Managers.  |
| NSX-Manager-HTTP  | Der Benutzername und das Kennwort für den Zugriff auf die Webkonsole des NSX-Managers. |
| PSC-IP  | Die IP-Adresse von Platform Services Controller (PSC).  |
| Vollständig qualifizierter Domänenname für PSC  | Der vollständig qualifizierte Domänenname von PSC.  |    
| PSC-ADMIN  | Der SSO-Benutzername und das Kennwort für VMware vCenter, mit dem Sie auf die PSC-Webkonsole zugreifen können.  |
| PSC-SSH  | Der Benutzername und das Kennwort, die Sie für den Zugriff auf die PSC-VM über eine SSH-Verbindung verwenden können.  |
| vCenter-IP  | Die IP-Adresse von vCenter Server.  |
| Vollständig qualifizierter Domänenname für vCenter  | Der vollständig qualifizierte Domänenname von vCenter Server.  |
| vCenter-ADMIN  | Der SSO-Benutzername und das Kennwort für VMware vCenter, mit dem Sie sich unter Verwendung von vSphere Web Client bei vCenter Server anmelden können.  |
| vCenter-SSH  | Der Benutzername und das Kennwort, die Sie für den Zugriff auf die VM für vCenter Server über eine SSH-Verbindung verwenden können.  |

## Bereitstellungsverlauf für vCenter Server with Hybridity Bundle-Instanzen anzeigen

Zeigen Sie den Bereitstellungsverlauf der Instanz unter **Bereitstellungsverlauf** an.

Tabelle 5. Bereitstellungsverlauf für vCenter Server with Hybridity Bundle-Instanz

| Element        | Beschreibung       |  
|:------------- |:------------- |
| Datum | Der Zeitpunkt (Datum und Uhrzeit), zu dem sich der Instanzstatus geändert hat. |
| Zusammenfassung | Die Details der Änderung. |

## Nächste Schritte bei aufgetretenen Fehlern

Wenn bei der Bereitstellung oder beim Löschen von Instanzen Fehler auftreten, wird automatisch das {{site.data.keyword.cloud_notm}}-Support-Team benachrichtigt. Um den Status Ihres Tickets abzufragen, können Sie den [IBM Support kontaktieren](../vmonic/trbl_support.html).

## Nächste Schritte

Nun können Sie Ihre Instanzen in der {{site.data.keyword.vmwaresolutions_short}}-Konsole oder in VMware vSphere Web Client verwalten.

**Wichtig**: Bevor Sie auf der Seite mit der Instanzzusammenfassung auf **vCenter-Konsole** klicken, um vSphere Web Client aufzurufen und Ihre ESXi-Server zu verwalten, müssen Sie sich beim VPN-Portal des {{site.data.keyword.CloudDataCent_notm}} anmelden. Bewegen Sie den Mauszeiger über die Schaltfläche **vCenter-Konsole** und befolgen Sie die Anweisungen, um sicherzustellen, dass Sie alle Voraussetzungen erfüllen und Sie alle erforderlichen Schritte ausgeführt haben, bevor Sie auf vSphere Web Client zugreifen.

In den folgenden Abschnitten finden Sie Informationen, die Sie bei der Ausführung der Anmeldeanweisungen unterstützen:
*  Informationen zu den Voraussetzungen und erforderlichen Schritten vor dem Zugriff auf vSphere Web Client finden Sie unter [Zeitlimitüberschreitung beim Herstellen einer Verbindung zu vSphere Web Client](../vmonic/trbl_timeout_vc_console.html).
*  Eine Liste der Zugriffspunkte für die Anmeldung beim privaten Netz der {{site.data.keyword.cloud_notm}}-Infrastruktur mittels VPN finden Sie unter [VPN-Zugriff](http://www.softlayer.com/vpn-access){:new_window}.
*  Falls Sie beim Bereitstellen einer Datei im Format "OVF" (Open Virtualization Format) mit vSphere Web Client Probleme feststellen, finden Sie unter [OVF-Datei mit vSphere Web Client bereitstellen](../vmonic/trbl_deploy_ovf.html) weitere Informationen.

## Zugehörige Links

* [vCenter Server with Hybridity Bundle-Instanzen bestellen](vc_hybrid_orderinginstance.html)
* [Cluster für vCenter Server with Hybridity Bundle-Instanzen hinzufügen, anzeigen und löschen](vc_hybrid_addingviewingclusters.html)
* [Kapazität für vCenter Server with Hybridity Bundle-Instanzen erweitern und verringern](vc_hybrid_addingremovingservers.html)
* [vCenter Server with Hybridity Bundle-Instanzen löschen](vc_hybrid_deletinginstance.html)
