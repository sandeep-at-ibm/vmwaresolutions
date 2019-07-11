---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---
# Requisitos de acesso à porta para o VMware HCX on IBM Cloud
{: #hcx-archi-port-req}

O HCX deve atravessar a Internet pública e as linhas privadas e conectar-se a componentes do data center, como redes, comutadores e grupos de portas.

A tabela a seguir lista as portas que devem ser abertas para que os dispositivos virtuais do Hybrid Cloud Services possam ser instalados com êxito. O ambiente do vSphere e o ambiente do IBM Cloud devem permitir a sincronização de clock do Network Time Protocol (NTP) entre os dispositivos no local do vSphere e os dispositivos IBM Cloud. A porta UDP 123 deve estar acessível a dispositivos virtuais e redes do Hybrid Cloud Services. Os Servidores NTP instalados podem ser especificados quando o Hybrid Cloud Services Appliance está instalado.

Tabela 1. Requisitos de acesso à porta

| Origem | Destino       | Port | Protocolo | Propósito         | Serviços |
|--------|--------------|------|----------|-----------------|----------|
| HCX    | DNS do cliente | 53   | TCP/UDP  | Resolução de Nome | DNS      |
| HCX    | NSX LB no IBM Cloud | 443 | TCP | Serviço de registro | HTTPS |
| HCX    | vCenter no IBM Cloud | 443 | TCP | Serviço REST do HCX | HTTPS |
| HCX    | PSC no IBM Cloud | 443 | TCP | Serviço REST do HCX | HTTPS |
| HCX    | connect.hcx.vmware.com | 443 | TCP | Serviço de registro | HTTPS |
| Navegador da Web | HCX | 9443 | TCP | HCX Virtual Appliance Management Interface para configuração do sistema HCX | HTTPS |
| Rede administrativa | HCX | 22 | SSH | Acesso SSH do administrador para o Hybrid Cloud Services | SSH |
| HCX | Hosts ESXi | 902 | TCP | Enviar instruções de gerenciamento e fornecimento de HCX para Hosts ESXi no IBM Cloud. | Interno |
| HCX | vCenter SSO Server | 7444 | TCP | vSphere Lookup Service |  |
| HCX | Servidores NTP | 123 | UDP | Sincronização de | |
| HCX | Syslog |   | Usuário configurado | Conexão entre o HCX (o cliente) e o servidor Syslog. Os valores para a porta Syslog e o protocolo são especificados no vSphere Web Client. Por exemplo, a porta 514 para o protocolo UDP. | |
| HCX | Gateway em nuvem | 8123 | TCP | Enviar instruções de serviço de replicação baseada em host para o Hybrid Cloud Gateway. | HTTP |
| HCX | Gateway em nuvem | 9443 | TCP | Enviar instruções de gerenciamento para o Hybrid Cloud Gateway local usando a API de REST. | HTTP</br>HTTPS |
| Gateway em nuvem | L2C | 443 | TCP | Enviar instruções de gerenciamento do Cloud Gateway para o L2C quando o L2C usa o mesmo caminho que o Hybrid Cloud Gateway. | HTTP</br>HTTPS |
| Gateway em nuvem | L2C | 8443 | TCP | Instruções de gerenciamento bidirecional do Cloud Gateway para o L2C, quando o L2C usa um caminho de dados alternativo. | HTTP</br>HTTPS |
| L2C | L2C (remoto) | 443 | TCP | Instruções de gerenciamento bidirecional do Cloud Gateway para o L2C, quando o L2C usa um caminho de dados alternativo. | HTTP</br>HTTPS |
| Gateway em nuvem | Hosts ESXi | 80, 902  | TCP | Gerenciamento e implementação do OVF | Interno |
| Hosts ESXi | Gateway em nuvem | 31031, 44046 | TCP | Tráfego de replicação baseado em host interno | Interno |
| Gateway em nuvem | Hosts ESXi | 8000  | TCP | vMotion (zero de migração de tempo de inatividade) |  |
| Gateway de nuvem (local) | Gateway de nuvem</br>(remoto) | 4500  | UDP | Troca de chave da Internet (IKEv2) para encapsular cargas de trabalho para o túnel bidirecional | IPSEC |
| Gateway de nuvem (local) | Gateway de nuvem</br>(remoto) | 500  | UDP | Troca de chave da Internet (ISAKMP) para o túnel bidirecional | IPSEC |

## Links relacionados
{: #hcx-archi-port-req-related}

* [Instalando e configurando o HCX na origem](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
