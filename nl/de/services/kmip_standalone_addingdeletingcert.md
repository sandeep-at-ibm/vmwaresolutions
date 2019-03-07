---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zertifikate für KMIP for VMware on IBM Cloud-Instanzen hinzufügen, anzeigen und löschen
{: #kmip_standalone_addingdeletingcert}

Wenn Ihre KMIP for VMware on {{site.data.keyword.cloud}}-Instanz bereit ist, müssen Sie ihr Zertifikate hinzufügen. Wenn Sie ein Zertifikat nicht mehr benötigen, löschen Sie es aus Ihrer Instanz.

## Vorgehensweise zum Hinzufügen von Zertifikaten zu KMIP for VMware on IBM Cloud-Instanzen
{: #kmip_standalone_addingdeletingcert-add}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Blättern Sie in der Tabelle **KMIP for VMware on IBM Cloud-Instanzen** zu der Instanz, für die Sie Zertifikate hinzufügen wollen.
3. Klicken Sie auf **Hinzufügen**.
4. Geben Sie im Fenster **Client-SSL-Zertifikat hinzufügen** den Namen und Inhalt des Zertifikats an.

   Der Zertifikatsname kann innerhalb der ausgewählten Instanz nicht wiederverwendet werden. Der Zertifikatsname muss gültig sein und die Tags BEGIN CERTIFICATE und END CERTIFICATE enthalten. Zudem kann das Zertifikat nicht in der ausgewählten Region wiederverwendet werden, in der die Instanz bereitgestellt ist.
   {:note}
5. Klicken Sie auf **Hinzufügen**.

## Vorgehensweise zum Anzeigen von Zertifikaten für KMIP for VMware on IBM Cloud-Instanzen
{: #kmip_standalone_addingdeletingcert-view}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Blättern Sie in der Tabelle **KMIP for VMware on IBM Cloud-Instanzen** zu der Instanz, für die die Zertifikate angezeigt werden sollen.
3. Zeigen Sie die Liste der hinzugefügten Zertifikate unter dem Abschnitt **Client-SSL-Zertifikate** an.
4. Zum Anzeigen des Inhalts eines bestimmten Zertifikats klicken Sie auf **Download**.

## Vorgehensweise zum Löschen von Zertifikaten aus KMIP for VMware on IBM Cloud-Instanzen
{: #kmip_standalone_addingdeletingcert-delete}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Blättern Sie in der Tabelle **KMIP for VMware on IBM Cloud-Instanzen** auf die Instanz, aus der Sie Zertifikate löschen möchten.
3. Suchen Sie in der Tabelle **Client-SSL-Zertifikate** das zu löschende Zertifikat und klicken Sie auf das Symbol **Löschen**.

   Der Client verliert unverzüglich den Zugriff auf alle Schlüssel zum Ver- und Entschlüsseln von Daten oder Sicherungsdaten. Damit der Client den Zugriff wiedererhält, müssen Sie das Client-SSL-Zertifikat wieder hinzufügen.
   {:note}

## Zugehörige Links
{: #kmip_standalone_addingdeletingcert-related}

* [KMIP for VMware on IBM Cloud-Instanzen anzeigen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [KMIP for VMware on IBM Cloud-Instanzen bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [KMIP for VMware on IBM Cloud-Instanzen löschen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker-Ereignisse](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
