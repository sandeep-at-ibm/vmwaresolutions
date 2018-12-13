---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-13"

---

# Allgemeine Servicekomponenten

Allgemeine Services stellen die Services bereit, die von anderen Services auf der Cloud-Management-Plattform verwendet werden. Zu den allgemeinen Services gehören Identitäts-und Zugriffsservices, Domänennamensservices und NTP-Services.

Abbildung 1. Allgemeine Services von {{site.data.keyword.cloud}} Private (ICP) ![Allgemeine ICP-Services](vcscar-common-services.svg)

## Identitäts- und Zugriffsservices

Im Rahmen der Automation von VMware vCenter Server on {{site.data.keyword.cloud_notm}} wird Microsoft Active Directory (AD) für das Identitätsmanagement verwendet. Es wird eine einzelne AD-VSI (Virtual Server Instance) bereitgestellt. Das vCenter ist für die Verwendung der AD-Authentifizierung konfiguriert und ICP kann auch für die LDAP-Authentifizierung konfiguriert werden.

## Domänennamensservices

Die Bereitstellung verwendet die bereitgestellten AD-VSIs als DNS-Server für die Instanz. Alle bereitgestellten Komponenten werden so konfiguriert, dass sie auf AD als Standard-DNS verweisen. Beispiele für die bereitgestellten Komponenten sind vCenter, PSC, NSX und ESXi-Hosts.

## Network Time Protocol-Services

Die vCenter Server-Bereitstellung nutzt die Server für Network Time Protocol (NTP) der {{site.data.keyword.cloud_notm}}-Infrastruktur. Alle bereitgestellten Komponenten werden so konfiguriert, dass sie diese NTP-Server verwenden. Dass alle Komponenten dieselben NTP-Server verwenden, ist für die korrekte Funktion von Zertifikaten und die AD-Authentifizierung von kritischer Bedeutung.

### Zugehörige Links

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
