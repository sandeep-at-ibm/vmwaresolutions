---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# NetApp ONTAP Select-Instanzen anzeigen

Sie können die Zusammenfassung und die detaillierten Informationen der NetApp ONTAP Select-Instanzen anzeigen, die für verschiedene Benutzerkonten bereitgestellt wurden.

## Vorgehensweise zum Anzeigen einer Zusammenfassung der NetApp ONTAP Select-Instanzen

Wenn Sie eine Zusammenfassung aller NetApp ONTAP Select-Instanzen, die für ein Benutzerkonto bereitgestellt wurden, anzeigen möchten, führen Sie die folgenden Schritte aus:

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_full}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie im Konsolenbanner auf das Symbol Ihres Benutzerkontos und klicken Sie anschließend auf das Feld **Konto**, um das Benutzerkonto auszuwählen, für das Sie Instanzen prüfen wollen.
3. Prüfen Sie in der Tabelle **NetApp ONTAP Select-Instanzen** die Liste der Instanzen, die in dem ausgewählten Benutzerkonto bereitgestellt sind.

Tabelle 1. Elemente von NetApp ONTAP Select-Instanzen

| Element        | Beschreibung       |  
|:------------- |:--------------- |
| Name | Der Name der Instanz. |
| Version | Die Version der Instanz. |  
| Standort | Das Rechenzentrum, in dem die Instanz gehostet wird. |
| Erstellungszeit | Der Zeitpunkt (Datum und Uhrzeit), zu dem die Instanz erstellt wurde. |   
| Status | Der Status der Instanz. Der Status kann einen der folgenden Werte aufweisen:<ul><li>Wird erstellt: Die Instanz wird gerade erstellt.</li><li>Wird aufgebaut: Die Instanz wird gerade konfiguriert.</li><li>Bereit: Die Instanz ist zur Verwendung bereit.</li><li>Wird geändert: Die Instanz wird gerade geändert.</li><li>Fehlgeschlagen: Der Erstellungs-, Konfigurations- oder Änderungsprozess ist fehlgeschlagen.</li><li>Wird gelöscht: Die Instanz wird gerade gelöscht.</li><li>Fehler beim Löschvorgang: Beim Löschen der Instanz ist ein Fehler aufgetreten.</li><li>Gelöscht: Die Instanz wurde gelöscht.</li></ul>|

## Vorgehensweise zum Anzeigen von Eigenschaftsdetails von NetApp ONTAP Select-Instanzen

Gehen Sie wie folgt vor, um die Eigenschaftsdetails einer Instanz anzuzeigen:

1. Klicken Sie in der Tabelle **NetApp ONTAP Select-Instanzen** auf einen Instanznamen.
2. Zeigen Sie unter **Eigenschaften** die Details für die Instanz an.

Tabelle 2. Eigenschaften von NetApp ONTAP Select-Instanzen

| Eigenschaft        | Beschreibung       |
|:--------------- |:----------------- |
| Name | Der Name der Instanz. |
| ID | Die ID der Instanz. |
| Standort | Das Rechenzentrum, in dem die Instanz gehostet wird. |
| Bereitgestellte Version | Die bereitgestellte Version von {{site.data.keyword.vmwaresolutions_short}}. |
| vCenter-Version | Die Version von VMware vCenter Server.<br><br>**Hinweis:** Die Versionen von vCenter Server, die in der {{site.data.keyword.vmwaresolutions_short}}-Konsole und in VMware vSphere Web Client angezeigt werden, weichen etwas voneinander ab. Beide Angaben sind richtig. |
| NSX for vSphere | Die Produktversion von VMware NSX for vSphere. |
| NSX-Lizenzedition | Die Version und Edition der VMware NSX-Lizenz. |
| NetApp-Version | Die Version von NetApp ONTAP Select. |
| NetApp-Lizenztyp | Der Typ der NetApp ONTAP Select-Lizenz. |
| DNS, Rootdomäne | Der Rootdomänenname ist der Domänenname des DNS (Domain Name System) und der Gesamtstrukturrootname von Microsoft Active Directory (AD) für die Instanz. |
| DNS, SSO-Domäne | Die SSO-Domäne ist die Single-Sign-on-Domäne von vSphere. Der SSO-Domänenname wird für alle bereitgestellten NetApp ONTAP Select-Instanzen mit dem Wert `vsphere.local` festgelegt. |
| DNS, Unterdomäne | Die Unterdomäne ist im DNS-Unterdomänennamen des Namens der Rootdomäne angegeben, in der sich die Hostnamen der lokalen NetApp ONTAP Select-Instanz befinden. Der Unterdomänenname hat das Format `<subdomain_label>.<root_domain>`. |
| Status | Der Status der Instanz. |

## Vorgehensweise zum Anzeigen von Zugriffsinformationen für NetApp ONTAP Select-Instanzen

Zeigen Sie unter **Zugriffsinformationen** die Zugriffsinformationen für die instanzbezogenen Komponenten an. Bei diesen Kennwörtern handelt es sich um Anfangskennwörter, die vom System generiert werden. Wenn Sie sie außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden sie auf der Seite mit der Instanzzusammenfassung nicht aktualisiert.

Tabelle 3. Zugriffsinformationen für instanzbezogene NetApp ONTAP Select-Komponenten

| Komponente        | Beschreibung       |
|:---------------- |:----------------- |
| AD/DNS-IPs | Die IP-Adressen der beiden AD-Server. |
| Vollständig qualifizierter Domänenname für AD/DNS | Der vollständig qualifizierte Domänenname des AD/DNS-Servers. |
| AD/DNS ADMIN (Remote Desktop) | Der Benutzername und das Kennwort, die Sie für den Zugriff auf den AD-Server über eine Remote-Desktop-Verbindung verwenden können. |
| NSX-Manager-IP | Die IP-Adresse des NSX-Managers. |
| Vollständig qualifizierter Domänenname für NSX-Manager | Der vollständig qualifizierte Domänenname des NSX-Managers. |
| NSX-Manager-HTTP | Der Benutzername und das Kennwort, mit denen Sie auf die NSX-Manager-Webkonsole zugreifen können. |
| NetApp-Cluster-IP | Die IP-Adresse des NetApp ONTAP Select-Clusters. |
| Vollständig qualifizierter Domänenname für NetApp-Cluster | Der vollständig qualifizierte Domänenname des NetApp ONTAP-Clusters. |
| NetApp-Cluster-HTTPS | Der Benutzername und das Kennwort, mit denen Sie auf den NetApp ONTAP Select-Cluster zugreifen können. |
| IP für NetApp-Bereitstellungstool | Die IP-Adresse der virtuellen Maschine für NetApp ONTAP Select Deploy. |
| Vollständig qualifizierter Domänenname für NetApp-Bereitstellungstool | Der vollständig qualifizierte Domänenname für NetApp ONTAP Select Deploy. |
| HTTPS für NetApp-Bereitstellungstool | Der Benutzername und das Kennwort, mit denen Sie auf die virtuelle Maschine für NetApp ONTAP Select Deploy zugreifen können. |
| PSC-IP | Die IP-Adresse von Platform Services Controller (PSC). |
| Vollständig qualifizierter Domänenname für PSC | Der vollständig qualifizierte Domänenname von PSC. |
| PSC-ADMIN | Der SSO-Benutzername und das Kennwort für VMware vCenter, mit dem Sie auf die PSC-Webkonsole zugreifen können. |
| PSC-SSH | Der Benutzername und das Kennwort, die Sie für den Zugriff auf die PSC-VM über eine SSH-Verbindung verwenden können. |
| vCenter-IP | Die IP-Adresse von vCenter Server. |
| Vollständig qualifizierter Domänenname für vCenter | Der vollständig qualifizierte Domänenname von vCenter Server. |
| vCenter-ADMIN | Der SSO-Benutzername und das Kennwort für VMware vCenter, mit dem Sie sich unter Verwendung von vSphere Web Client bei vCenter Server anmelden können. |
| vCenter-SSH | Der Benutzername und das Kennwort, die Sie für den Zugriff auf die VM für vCenter Server über eine SSH-Verbindung verwenden können. |

## Vorgehensweise zum Anzeigen des Bereitstellungsverlaufs für NetApp ONTAP Select-Instanzen

Klicken Sie im linken Navigationsfenster auf **Bereitstellungsverlauf**, um den Bereitstellungsverlauf für die Instanz anzuzeigen.

Tabelle 4. Bereitstellungsverlauf der NetApp ONTAP Select-Instanz

| Element        | Beschreibung       |  
|:------------|:------------- |
| Datum | Der Zeitpunkt (Datum und Uhrzeit), zu dem sich der Instanzstatus geändert hat. |
| Zusammenfassung | Die Details der Änderung. |

Wenn bei der Bereitstellung oder beim Löschen von Instanzen Fehler auftreten, wird automatisch das {{site.data.keyword.cloud_notm}}-Support-Team benachrichtigt. Um den Status Ihres Tickets abzufragen, können Sie den [IBM Support kontaktieren](../vmonic/trbl_support.html).

## NetApp ONTAP Select-Cluster anzeigen

1. Klicken Sie im linken Navigationsfenster auf **Infrastruktur**.
2. Zeigen Sie unter **CLUSTER** die Zusammenfassung zu den NetApp ONTAP Select-Clustern an.

	Tabelle 5. Elemente von NetApp ONTAP Select-Clustern

	 <table>
	   <tr>
	     <th>Element</th>
	     <th>Beschreibung</th>
	   </tr>
	   <tr>
	     <td>Name</td>
	     <td>Der Name des Clusters.</td>
	   </tr>
	   <tr>
	     <td>ESXi-Server</td>
	     <td>Die Anzahl der ESXi-Server im Cluster.</td>
	   </tr>
	   <tr>
	      <td>CPU</td>
	      <td>Die CPU-Spezifikation der ESXi-Server im Cluster.</td>
	   </tr>
	   <tr>
	      <td>Effektiver Speicher</td>
	      <td>Die Gesamtplattenkapazität der ESXi-Server im Cluster.</td>
	   </tr>
	   <tr>
	      <td>Speicher</td>
	      <td>Die Gesamtspeichergröße der ESXi-Server im Cluster.</td>
	   </tr>
	   <tr>
	      <td>Standort des Rechenzentrums</td>
	      <td>Das Rechenzentrum, in dem der Cluster gehostet wird. Dies ist mit der Position des Rechenzentrums für die Instanz identisch.</td>
	   </tr>
		 <tr>
		   <td>Pod</td>
			 <td>Der Pod, in dem der Cluster erstellt wird.</td>
		 </tr>
		 <tr>
		  <td>Status</td>
			<td>Der Status des Clusters. Der Status kann einen der folgenden Werte aufweisen:<ul><li>Wird initialisiert: Der Cluster wird gerade erstellt und konfiguriert.</li><li>Wird geändert: Der Cluster wird gerade geändert.</li><li>Bereit: Der Cluster ist zur Verwendung bereit.</li></ul></td>
		 </tr>
		 <tr>
		  <td>Aktionen</td>
			<td>Klicken Sie auf das Symbol **Löschen**, um den Cluster zu löschen.</td>
		 </tr>
	 </table>

3. Klicken Sie auf den Clusternamen, um die zugehörigen ESXi-Serverdetails anzuzeigen.

Tabelle 6. ESXi-Serverdetails eines NetApp ONTAP Select-Clusters

| Element        | Beschreibung       |  
|:------------|:----------------- |
| Name | Der Name des ESXi-Servers im Format `<host_prefix><n>.<subdomain_label>.<root_domain>`, wobei Folgendes gilt:<br><br>`host_prefix` ist das Hostnamenspräfix, `n` ist die Folgenummer des Servers, `subdomain_label` ist die Unterdomänenbezeichnung und `root_domain` ist der Rootdomänenname. |
| Version | Die Version des ESXi-Servers. |
| Berechtigungsnachweise | Der Benutzername und das Kennwort für den Zugriff auf den ESXi-Server. |
| Private IP | Die private IP-Adresse des ESXi-Servers. |
| Status | Der Status des ESXi-Servers, der einen der folgenden Werte aufweisen kann:<ul><li>Aktiv: Der ESXi-Server ist zur Verwendung bereit.</li><li>Wird gelöscht: Der ESXi-Server wird gerade gelöscht.</li></ul> |

## Nächste Schritte

Nun können Sie Ihre Instanzen in der {{site.data.keyword.vmwaresolutions_short}}-Konsole, in VMware vSphere Web Client oder in der NetApp-Konsole verwalten.

Bevor Sie auf der Seite mit der Instanzzusammenfassung auf **vCenter-Konsole** klicken, um vSphere Web Client aufzurufen und Ihre ESXi-Server zu verwalten, müssen Sie sich beim VPN-Portal des {{site.data.keyword.CloudDataCent_notm}} anmelden. Bewegen Sie den Mauszeiger über die Schaltfläche **vCenter-Konsole** und befolgen Sie die Anweisungen, um sicherzustellen, dass Sie alle Voraussetzungen erfüllen und Sie alle erforderlichen Schritte ausgeführt haben, bevor Sie auf vSphere Web Client zugreifen.
{:important}

Weitere Informationen, die Sie beim Umsetzen der Anmeldeanweisungen unterstützen, finden Sie in den folgenden Abschnitten:

*  Informationen zu den Voraussetzungen und erforderlichen Schritten vor dem Zugriff auf vSphere Web Client finden Sie unter [Zeitlimitüberschreitung beim Herstellen einer Verbindung zu vSphere Web Client](../vmonic/trbl_timeout_vc_console.html).
*  Eine Liste der Zugriffspunkte für die Anmeldung beim privaten Netz der {{site.data.keyword.cloud_notm}}-Infrastruktur mittels VPN finden Sie unter [VPN-Zugriff](http://www.softlayer.com/vpn-access){:new_window}.
*  Falls Sie beim Bereitstellen einer Datei im Format "OVF" (Open Virtualization Format) mit vSphere Web Client Probleme feststellen, finden Sie unter [OVF-Datei mit vSphere Web Client bereitstellen](../vmonic/trbl_deploy_ovf.html) weitere Informationen.

### Zugehörige Links

* [NetApp ONTAP Select-Instanzen bestellen](np_orderinginstances.html)
* [NetApp ONTAP Select-Instanzen löschen](np_deletinginstance.html)
* [Dedizierten Speicher für NetApp ONTAP Select-Bereitstellungen zuordnen](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)
