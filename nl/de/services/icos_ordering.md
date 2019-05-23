---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud Object Storage mit Veeam bestellen und konfigurieren
{: #icos_ordering}

Mit dem Release von Veeam Availability Suite 9.5 Update 4 ist Veeam mit IBM Cloud Object Storage (ICOS) kompatibel. Die Bestellung von IBM Cloud Object Storage ist nicht automatisiert, wenn Sie Veeam on IBM Cloud bestellen, aber es kann nach der Bereitstellung hinzugefügt werden.

Um IBM Cloud Object Storage zu bestellen, führen Sie die folgenden Tasks in der angegebenen Reihenfolge aus.

## Object Storage-Instanz erstellen
{: #icos_ordering-obj}

Informationen zum Erstellen einer Object Storage-Instanz finden Sie unter [Neue Service-Instanz erstellen](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-order-storage#creating-a-new-service-instance). Führen Sie die Schritte aus und kehren Sie zu diesem Abschnitt zurück, um mit den folgenden Tasks fortzufahren.

## Einen Bucket erstellen
{: #icos_ordering-bucket}

Informationen zum Erstellen eines Buckets finden Sie unter [Einige Buckets zum Speichern Ihrer Daten erstellen](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-getting-started-tutorial#gs-create-buckets). Führen Sie die Schritte aus und kehren Sie zu diesem Abschnitt zurück, um mit den folgenden Tasks fortzufahren.

## Serviceberechtigungsnachweise erstellen
{: #icos_ordering-service-cred}

Informationen zum Erstellen von Serviceberechtigungsnachweisen, einschließlich HMAC-Berechtigungsnachweisen, finden Sie unter [Serviceberechtigungsnachweise](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials). Führen Sie die Schritte aus und kehren Sie zu diesem Abschnitt zurück, um mit den folgenden Tasks fortzufahren.

## Ein Scale-out-Repository hinzufügen
{: #icos_ordering-scale-repo}

Wenn Sie ein Scale-out-Repository in Veeam hinzufügen möchten, lesen Sie die Informationen im Abschnitt [Scale-Out-Repositorys hinzufügen](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:new_window}. Führen Sie die Schritte aus und kehren Sie zu diesem Abschnitt zurück, um mit den folgenden Tasks fortzufahren.

## Ihre Cloud-Tier warten und verwalten
{: #icos_ordering-manage-cloud}

Informationen zum Warten und Verwalten Ihrer Cloud-Tier finden Sie im Abschnitt [Kapazitäts-Tier-Daten verwalten](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:new_window}.
