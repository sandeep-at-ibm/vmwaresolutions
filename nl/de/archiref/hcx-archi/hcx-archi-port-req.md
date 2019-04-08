---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---
# VMware HCX on IBM Cloud - Portzugriffsvoraussetzungen
{: #hcx-archi-port-req}

HCX muss das öffentliche Internet und Privatleitungen traversieren sowie Verbindungen zu Rechenzentrumskomponenten wie Netzwerke, Switches und Portgruppen herstellen.

In der folgenden Tabelle sind die Ports aufgelistet, die geöffnet werden müssen, damit die virtuellen Appliances von Hybrid-Cloud-Services erfolgreich installiert werden können. Sowohl die vSphere-Umgebung als auch die IBM Cloud-Umgebung müssen die Uhrzeitsynchronisation "Network Time Protocol" (NTP) zwischen den vSphere- und den IBM Cloud-Einheiten zulassen. UDP-Port 123 muss für die virtuellen Hybrid-Cloud-Services-Appliances und -Netze zugänglich sein. Installierte NTP-Server können angegeben werden, wenn die Hybrid-Cloud-Services-Appliance installiert ist.

Tabelle 1. Portzugriffsvoraussetzungen

| Quelle | Ziel       | Port | Protokoll | Zweck         | Services |
|--------|--------------|------|----------|-----------------|----------|
| HCX    | DNS des Kunden | 53   | TCP/UDP  | Namensauflösung | DNS      |
| HCX    | NSX LB in IBM Cloud | 443 | TCP | Registrierungsservice | HTTPS |
| HCX    | vCenter in IBM Cloud | 443 | TCP | HCX-REST-Service | HTTPS |
| HCX    | PSC in IBM Cloud | 443 | TCP | HCX-REST-Service | HTTPS |
| HCX    | connect.hcx.vmware.com | 443 | TCP | Registrierungsservice | HTTPS |
| Webbrowser | HCX | 9443 | TCP | Managementschnittstelle der virtuellen HCX-Appliance für die HCX-Systemkonfiguration | HTTPS |
| Admin-Netzwerk | HCX | 22 | SSH | Administrator-SSH-Zugriff auf Hybrid-Cloud-Services | SSH |
| HCX | ESXi-Hosts | 902 | TCP | Senden von Verwaltungs-und Bereitstellungsanweisungen von HCX an ESXi-Hosts in IBM Cloud. | Intern |
| HCX | vCenter-SSO-Server | 7444 | TCP | vSphere-Suchservice |  |
| HCX | NTP-Server | 123 | UDP | Zeitsynchronisation | |
| HCX | Syslog |   | Benutzerkonfiguriert | Verbindung zwischen HCX (dem Client) und dem Syslog-Server. Werte für Syslog-Port und -Protokoll sind in vSphere Web Client angegeben. Beispiel: Port 514 für das UDP-Protokoll. | |
| HCX | Cloud-Gateway | 8123 | TCP | Senden von hostbasierten Replikationsserviceanweisungen an das Hybrid-Cloud-Gateway. | HTTP |
| HCX | Cloud-Gateway | 9443 | TCP | Senden von Managementanweisungen an das lokale Hybrid-Cloud-Gateway über die REST-API. | HTTP</br>HTTPS |
| Cloud-Gateway | L2C | 443 | TCP | Senden von Managementanweisungen vom Cloud-Gateway an L2C, wenn L2C denselben Pfad wie das Hybrid-Cloud-Gateway verwendet. | HTTP</br>HTTPS |
| Cloud-Gateway | L2C | 8443 | TCP | Senden von bidirektionalen Managementanweisungen vom Cloud-Gateway an L2C, wenn L2C einen alternativen Datenpfad verwendet. | HTTP</br>HTTPS |
| L2C | L2C (fern) | 443 | TCP | Senden von bidirektionalen Managementanweisungen vom Cloud-Gateway an L2C, wenn L2C einen alternativen Datenpfad verwendet. | HTTP</br>HTTPS |
| Cloud-Gateway | ESXi-Hosts | 80, 902  | TCP | Management und OVF-Bereitstellung | Intern |
| ESXi-Hosts | Cloud-Gateway | 31031, 44046 | TCP | Interner hostbasierter Replikationsdatenverkehr | Intern |
| Cloud-Gateway | ESXi-Hosts | 8000  | TCP | vMotion (Migration ohne Ausfallzeit) |  |
| Cloud-Gateway (lokal) | Cloud-Gateway</br>(fern) | 4500  | UDP | Internet key exchange (IKEv2) zum Kapseln von Workloads für den bidirektionalen Tunnnel | IPSEC |
| Cloud-Gateway (lokal) | Cloud-Gateway</br>(fern) | 500  | UDP | Internet key exchange (ISAKMP) für den bidirektionalen Tunnel | IPSEC |

## Zugehörige Links
{: #hcx-archi-port-req-related}

* [Installation und Konfiguration von HCX für die Quelle](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
