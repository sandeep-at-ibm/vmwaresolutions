---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-30"

subcollection: vmwaresolutions


---

# Releaseinformationen für V1.5
{: #relnotes_v15}

Dieses Release stellt neue Funktionen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Voraussetzungen für VRF- und klassisches SoftLayer-Konto im Vergleich
{: #relnotes_v15-vrf}

Bei klassischen SoftLayer®-Konten kann die Einstellung für die VLAN-Spanning-Funktion auf Kontoebene aktiviert werden. {{site.data.keyword.vmwaresolutions_short}} macht eine Aktivierung der VLAN-Spanning-Funktion erforderlich.

Bei VRF-SoftLayer-Konten (VRF = Virtual Routing and Forwarding, virtuelle Routenwahl und Weiterleitung) besteht die funktionale Entsprechung zur VLAN-Spanning-Funktion in einer permanenten Einstellung, die nicht geändert werden kann. Für VRF-Konten ist keine Benutzerkonfiguration erforderlich.

Stellen Sie vor dem Aufgeben einer Instanzbestellung sicher, dass Ihr SoftLayer-Konto entweder ein VRF-Konto oder ein klassisches Konto (also ohne VRF) mit aktivierter VLAN-Spanning-Funktion ist. Andernfalls kann die Bestellung fehlschlagen.

Um festzustellen, ob Ihr SoftLayer-Konto ein VRF-Konto ist, prüfen Sie dies zusammen mit dem IBM Bluemix-Support. Bei klassischen Konten müssen Sie die VLAN-Spanning-Funktion anhand der Anweisungen aktivieren, die im Abschnitt [VLAN-Spanning aktivieren oder inaktivieren](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window} verfügbar sind.

## Updates des Servicegebührenmodells
{: #relnotes_v15-svc-charge}

Für Cloud Foundation-Instanztypen wird eine neue Lizenz des Typs _SDDC Manager_ eingeführt. Hierbei handelt es sich um eine für jeden Knoten anfallende monatliche Gebühr.

## Erweiterungen beim Bedienungskomfort
{: #relnotes_v15-ui}

In der gesamten Benutzerschnittstelle wurden Verbesserungen vorgenommen:

* In der Benutzerschnittstelle ist eindeutig angegeben, welche {{site.data.keyword.CloudDataCents_notm}} verfügbar sind und ob der Bestand in diesen Rechenzentren zur Erfüllung der Bestellung ausreicht. Verwenden Sie diese Details, um während der Instanzbestellung eine fundierte Entscheidung über das auszuwählende {{site.data.keyword.CloudDataCent_notm}} treffen zu können. Weitere Informationen finden Sie unter [Voraussetzungen und Planung für vCenter Server-Instanzen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).
* Für Cloud Foundation-Instanzen werden Informationen wie der Instanzname, der Domänen- und Unterdomänenname sowie der Standort des Rechenzentrums automatisch im Grafikformat angezeigt, während Sie die erforderlichen Informationen in die Eingabefelder eingeben.
