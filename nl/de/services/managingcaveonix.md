---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: Caveonix console, Caveonix RiskForesight license, login Caveonix console

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight on IBM Cloud verwalten
{: #managingcaveonix}

## Auf die Caveonix RiskForesight-Konsole zugreifen
{: #managingcaveonix-access-console}

Zum Verwalten des Service "Caveonix RiskForesight on {{site.data.keyword.cloud}}" müssen Sie auf die Caveonix RiskForesight-Konsole zugreifen. Führen Sie dazu die folgenden Schritte aus:

1. Verwenden Sie das virtuelle private Netz der IBM Cloud-Infrastruktur oder einen Jump-Server, um den Zugriff auf die IP-Adresse der virtuellen Maschine (VM) von Caveonix RiskForesight zuzulassen. Die IP-Adresse finden Sie auf der Seite mit den Details für den Service "Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}" in der {{site.data.keyword.vmwaresolutions_short}}-Konsole. Gehen Sie im Einzelnen wie folgt vor:
   1. Erstellen Sie im Kundenportal für die {{site.data.keyword.cloud_notm}}-Infrastruktur ein VPN-Kennwort.
   2. Melden Sie sich beim VPN-Portal für das Rechenzentrum mit den VPN-Berechtigungsnachweisen der {{site.data.keyword.cloud_notm}}-Infrastruktur an.
   3. Fügen Sie die Zuordnung von IP-Adresse und Hostname in der Datei `hosts` auf Ihrem lokalen Computer hinzu. Verwenden Sie das folgende Format:

      ```javascript
      RiskForesight_VM_IP_Address      RiskForesight_FQDN
      ```
2. Für den Zugriff auf die Caveonix RiskForesight-Konsole klicken Sie auf **RiskForesight-Konsole anzeigen** auf der Servicedetailseite für Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} und melden Sie sich dann mit den Berechtigungsnachweisen an, die auf derselben Servicedetailseite aufgeführt sind.

## Updates auf Caveonix RiskForesight on IBM Cloud anwenden
{: #managingcaveonix-update}

Sie sind dafür verantwortlich, dass sich Caveonix RiskForesight immer auf dem aktuellsten Versionsstand befindet. Die erforderlichen Updates können Sie vom [Caveonix Service Provider Portal](https://support.caveonix.com) herunterladen.

## Caveonix RiskForesight-Lizenzen aktualisieren

Die Caveonix RiskForesight-Lizenz ist ein Jahr lang gültig. Mit der folgenden Vorgehensweise können Sie die Caveonix RiskForesight-Lizenz aktualisieren, wenn sie abläuft:
1. Bestellen Sie eine neue Caveonix RiskForesight-Lizenz und kopieren Sie sie in die Caveonix RiskForesight-Konsole. Weitere Informationen finden Sie unter [Vorgehensweise zum Bestellen von Caveonix RiskForesight-Lizenzen](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_ordering#caveonix_license_ordering-procedure).
2. Löschen Sie die abgelaufene Lizenz in der Tabelle **Caveonix RiskForesight-Lizenzen** in der {{site.data.keyword.vmwaresolutions_short}}-Konsole. Weitere Informationen finden Sie unter [Vorgehensweise zum Löschen von Caveonix RiskForesight-Lizenzen](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_managing#caveonix_license_managing_procedure-delete).

## Zugehörige Links
{: #managingcaveonix-related}

* [Übersicht über Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
