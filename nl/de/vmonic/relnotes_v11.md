---

copyright:

  years:  2016

lastupdated: "2016-11-04"

---

# Releaseinformationen für V1.1
{: #relnotes_v11}

Dieses Release stellt neue Funktionen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VLAN-Spanning als Voraussetzung

Falls Sie ein klassisches SoftLayer®-Konto verwenden (also kein VRF-Konto), muss die VLAN-Spanning-Funktion aktiviert sein. Wenn die VLAN-Spanning-Funktion bei klassischen Konten nicht aktiviert ist, sind die verschiedenen Komponenten der VMware-Virtualisierungsumgebung möglicherweise nicht in der Lage, miteinander zu kommunizieren. Informationen zum Aktivieren der VLAN-Spanning-Funktion in Ihrem SoftLayer-Konto finden Sie unter [VLAN-Spanning aktivieren oder inaktivieren](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}.

## E-Mail-Einstellungen und -Benachrichtigungen

Sie können E-Mail-Benachrichtigungen auf der Seite **Einstellungen** konfigurieren. Standardmäßig ist die Einstellung aktiviert. Dies bedeutet, dass Sie für jede neu bestellte Instanz eine Benachrichtigung per E-Mail erhalten, wenn diese Instanz bereitgestellt wird und einsatzbereit ist. Auf der Seite **Einstellungen** können Sie E-Mail-Benachrichtigungen auch inaktivieren. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).

## Detaillierte Statusinformationen

Für Cloud Foundation-Instanzen stehen jetzt detaillierte Statusinformationen zur Verfügung. Wenn Sie auf einen Instanznamen klicken, vermitteln Ihnen die angezeigten Statusinformationen weitere Details über den Bereitstellungsprozess. Falls ein Fehler auftritt, werden Nachrichten angezeigt, die Ihnen bei der Behandlung des Problems helfen. Entsprechende Informationen finden Sie im Abschnitt [Cloud Foundation-Instanzen anzeigen](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_viewinginstances).
