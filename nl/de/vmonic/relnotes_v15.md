---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-30"

---

# Releaseinformationen für V1.5

Dieses Release stellt neue Funktionen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie zusätzlichen Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Voraussetzungen für VRF- und klassisches SoftLayer-Konto im Vergleich

Bei klassischen SoftLayer®-Konten kann die Einstellung für die VLAN Spanning-Funktion auf Kontoebene aktiviert werden. {{site.data.keyword.vmwaresolutions_short}} macht eine Aktivierung der VLAN Spanning-Funktion erforderlich.

Bei VRF-SoftLayer-Konten (VRF = Virtual Routing and Forwarding, virtuelle Routenwahl und Weiterleitung) besteht die funktionale Entsprechung zur VLAN Spanning-Funktion in einer permanenten Einstellung, die nicht geändert werden kann. Für VRF-Konten ist keine Benutzerkonfiguration erforderlich.

Stellen Sie vor dem Aufgeben einer Instanzbestellung sicher, dass Ihr SoftLayer-Konto entweder ein VRF-Konto oder ein klassisches Konto (also ohne VRF) mit aktivierter VLAN Spanning-Funktion ist. Andernfalls kann die Bestellung fehlschlagen.

Um festzustellen, ob Ihr SoftLayer-Konto ein VRF-Konto ist, prüfen Sie dies zusammen mit dem IBM Bluemix-Support. Bei klassischen Konten müssen Sie die VLAN Spanning-Funktion anhand der Anweisungen aktivieren, die im Abschnitt [VLAN Spanning aktivieren oder inaktivieren](../../../infrastructure/vlans/vlan-spanning.html){:new_window} verfügbar sind.

## Updates des Servicegebührenmodells

Für Cloud Foundation-Instanztypen wird eine neue Lizenz des Typs _SDDC Manager_ eingeführt. Hierbei handelt es sich um eine für jeden Knoten anfallende monatliche Gebühr. Weitere Informationen enthält der Abschnitt [Technische Spezifikationen für Cloud Foundation-Instanzen](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).

## Erweiterungen beim Bedienungskomfort

In der gesamten Benutzerschnittstelle wurden Verbesserungen vorgenommen:

* In der Benutzerschnittstelle ist eindeutig angegeben, welche Rechenzentren verfügbar sind und ob der Bestand in diesen Rechenzentren zur Erfüllung der Bestellung ausreicht, damit Sie während der Instanzbestellung eine fundierte Entscheidung über das auszuwählende Rechenzentrum treffen können. Weitere Informationen finden Sie unter [Voraussetzungen und Planung für Cloud Foundation-Instanzen](../sddc/sd_planning.html) und [Voraussetzungen und Planung für vCenter Server-Instanzen](../vcenter/vc_planning.html).
* Für Cloud Foundation-Instanzen werden Informationen wie der Instanzname, der Domänen- und Unterdomänenname sowie der Standort des Rechenzentrums automatisch im Grafikformat angezeigt, während Sie die erforderlichen Informationen in den Eingabefeldern eingeben. Weitere Informationen finden Sie im Abschnitt [Cloud Foundation-Instanzen bestellen](../sddc/sd_orderinginstance.html).
