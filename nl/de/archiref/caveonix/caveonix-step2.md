---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Schritt 2 - Bereitstellung der virtuellen Maschine
{: #caveonix-step2}

Die {{site.data.keyword.vmwaresolutions_full}}-Automatisierung fordert ein zusätzliches portierbares privates IP-Teilnetz an und die umfassende virtuelle Maschine (VM) wird mit einer IP-Adresse aus diesem Teilnetz konfiguriert, um den Caveonix RiskForesight-Komponenten Folgendes zu ermöglichen:

- Herstellen einer Verbindung zu vCenter und zum NSX-Manager über den BCR.
- Herstellen einer Verbindung zu fernen Kollektoren, sei es über VXLANs oder Off-Premises-Hosting.
- Ermöglichen der Verwaltung des IP-Adressbereichs durch den Client bei der Skalierung.
