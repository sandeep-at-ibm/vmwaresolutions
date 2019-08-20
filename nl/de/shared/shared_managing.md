---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gemeinsam genutzte Ressource verwalten
{: #shared_managing}

{{site.data.keyword.vmwaresolutions_full}} Shared wird als experimentelles Angebot bereitgestellt.
{:note}

Kunden verwalten den Lebenszyklus virtueller Rechenzentren mit dem {{site.data.keyword.vmwaresolutions_short}}-Angebot.

Die folgenden Funktionen werden unterstützt, entweder über die Webbenutzerschnittstelle oder die öffentliche API:
- Instanzen des virtuellen Rechenzentrums anzeigen
- Auf vCloud Management-Konsole zugreifen
- Größe von Instanzen des virtuellen Rechenzentrums ändern
- Instanzen des virtuellen Rechenzentrums löschen
- VMware Services zu Instanzen des virtuellen Rechenzentrums hinzufügen und daraus entfernen (**in Kürze**)

## Instanzen des virtuellen Rechenzentrums anzeigen
{: #shared_managing-viewing}

Zum Anzeigen einer Zusammenfassung aller Instanzen eines virtuellen Rechenzentrums, die für ein Benutzerkonto bereitgestellt wurden, führen Sie die folgenden Schritte aus:

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie im Konsolenbanner auf das Symbol Ihres Benutzerkontos und klicken Sie anschließend auf das Feld **Konto**, um das Benutzerkonto auszuwählen, für das Sie Instanzen prüfen wollen.  
3. Prüfen Sie in der Tabelle **IBM Cloud VMware Solutions Shared** die Liste der Instanzen, die in dem ausgewählten Benutzerkonto bereitgestellt sind.

| Element        | Beschreibung       |  
|:------------- |:------------- |
| Name | Der Name der Instanz. |
| Typ | Typ des virtuellen Rechenzentrums |
| Standort | Das {{site.data.keyword.CloudDataCent_notm}}, in dem die Instanz gehostet wird. |  
| Erstellungszeit | Der Zeitpunkt (Datum und Uhrzeit), zu dem die Instanz erstellt wurde. |
| Status | Der Status der Instanz. |

{: caption="Tabelle 1. Elemente von Instanzen des virtuellen Rechenzentrums" caption-side="top"}

Für die Instanz gibt es eine Reihe von Statuswerten.

| Status        | Beschreibung       |
|:------------- |:------------- |
| Wird erstellt | Die Instanz wird gerade erstellt. |
| Bereit | Die Instanz ist zur Verwendung bereit. |
| Wird geändert | Die Instanz wird gerade geändert. |
| Wird gelöscht | Die Instanz wird gerade gelöscht. |
| Gelöscht | Die Instanz wurde gelöscht. |

{: caption="Tabelle 2. Statusbeschreibungen für Instanzen des virtuellen Rechenzentrums" caption-side="top"}

## Vorgehensweise zum Anzeigen von Details des virtuellen Rechenzentrums
{: #vc_viewinginstances-procedure-view-vdc-details}

Gehen Sie wie folgt vor, um die Eigenschaftsdetails einer Instanz anzuzeigen:

1. Klicken Sie in der Tabelle **IBM Cloud VMware Solutions Shared** auf einen Instanznamen.
2. Zeigen Sie unter **Eigenschaften** die Details für die Instanz an.

| Eigenschaft        | Beschreibung       |
|:------------- |:------------- |
| Name | Der Name der Instanz. |
| Typ | Der Typ des virtuellen Rechenzentrums. |
| Standort | Das {{site.data.keyword.CloudDataCent_notm}}, in dem die Instanz gehostet wird. |
| ID | Die ID der Instanz. |
| Erstellungszeit | Der Zeitpunkt (Datum und Uhrzeit), zu dem die Instanz erstellt wurde und an dem auch die Abrechnung beginnt. |
| vCPU | Die Begrenzung oder die reservierte Menge an CPU, die zu einem beliebigen Zeitpunkt vom virtuellen Rechenzentrum verwendet werden kann. |
| RAM | Die Begrenzung oder die reservierte Menge an Speicher, die zu einem beliebigen Zeitpunkt vom virtuellen Rechenzentrum verwendet werden kann. |
| Öffentliche IP | Jedes virtuelle Rechenzentrum umfasst fünf öffentliche IP-Adressen, mit denen eine Verbindung von vApps und VMs zum Internet hergestellt werden kann. |

{: caption="Tabelle 3. Eigenschaften des virtuellen Rechenzentrums" caption-side="top"}

## Zugriff auf die vCloud Director Management-Konsole
{: #shared_managing-accessing}

Verwalten Sie das virtuelle Rechenzentrum über die vCloud Director Management-Konsole.

Der erste Zugriff auf die vCloud Director Management-Konsole erfolgt mit dem **admin**-Berechtigungsnachweis. Generieren Sie ein Kennwort auf der Detailseite des virtuellen Rechenzentrums mit dem Link **Kennwort zum Zurücksetzen des Standorts**. Mit dieser Aktion wird ein erstes komplexes automatisch generiertes Kennwort generiert, das jederzeit zurückgesetzt werden kann.

Im {{site.data.keyword.vmwaresolutions_short}}-Angebot wird das **admin**-Kennwort nicht gespeichert. Nachdem Sie ein Kennwort generiert haben, müssen Sie es aufzeichnen. Wenn das Kennwort verloren geht, sollte ein neues Kennwort generiert werden.

Alle virtuellen Rechenzentren am selben Standort haben dasselbe **admin**-Kennwort. Durch Zurücksetzen des Kennworts in einer Instanz des virtuellen Rechenzentrums wird das **admin**-Kennwort für den Zugriff auf die vCloud Director Management-Konsole für alle Instanzen des virtuellen Rechenzentrums am selben Standort zurückgesetzt.

Nach dem Generieren des ersten **admin**-Kennworts wird die Schaltfläche **vCloud Director-Portal** in der oberen rechten Ecke der Detailseite verfügbar. Klicken Sie auf **vCloud Director-Portal**, um auf die vCloud Director Management-Konsole zuzugreifen. Zum Anmelden verwenden Sie den Benutzernamen **admin** und das Kennwort, das Sie mit dem Link **Kennwort zum Zurücksetzen des Standorts** erhalten haben.

## Größe der Instanzen des virtuellen Rechenzentrums ändern
{: #shared_managing-resizing}

Zu jedem Zeitpunkt, wenn sich eine Instanz des virtuellen Rechenzentrums im Status **Bereit** befindet, können Sie die Menge der Ressourcen ändern, die einem virtuellen Rechenzentrum zugeordnet sind. 

Ändern Sie die Größe der vCPU- oder RAM-Ressourcen für eine Instanz des virtuellen Rechenzentrums auf der Detailseite des virtuellen Rechenzentrums. Klicken Sie auf das Stiftsymbol neben **Ressourcen** auf der Detailseite und ändern Sie die Werte der vCPU- oder RAM-Eigenschaften.

Überprüfen Sie abschließend die Konfiguration und die geschätzten Kosten, bevor Sie die Bestellung aufgeben.

  Wenn die vCPU- und RAM-Ressourcen während des Senkens verwendet werden, schlägt die Konfigurationsänderung fehl, weil die Ressourcen des virtuellen Rechenzentrums nicht auf einen Wert unter der derzeit aktiven Ressourcennutzung gesenkt werden können.
{:note}

Die Instanz des virtuellen Rechenzentrums tritt in den Status **Wird geändert** ein, während die Änderung vorgenommen wird. Wenn die Ressourcen für die Verwendung bereit sind, ändert sich der Status in **Bereit**.

## Instanzen des virtuellen Rechenzentrums löschen
{: #shared_managing-deleting}

Eine Instanz des virtuellen Rechenzentrums kann gelöscht werden, wenn sie sich im Status **Bereit** befindet. Führen Sie die Löschoperation über die Detailseite des virtuellen Rechenzentrums oder über die IBM Cloud VMware Solutions-Tabelle für gemeinsam genutzte Ressourcen durch.

Klicken Sie auf der Detailseite auf das Symbol **Löschen** in der Überlaufmenüoption ganz rechts oben auf der Detailseite. Bestätigen Sie anschließend, dass die Instanz gelöscht werden soll.

Suchen Sie in der Tabelle für gemeinsam genutzte Ressourcen von IBM Cloud VMware Solutions die zu löschende Instanz und klicken Sie in der Spalte **Aktionen** auf das Symbol **Löschen**. Bestätigen Sie anschließend, dass die Instanz gelöscht werden soll.

## Zugehörige Links
{: #shared_managing-related}

* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Shared On-demand - Bestellverfahren](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Shared Reserved - Bestellverfahren](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
