---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-17"

---

# vRealize Network Insight
{: #opsmgmt-vrni}

O ambiente do vRealize Network Insight (vRNI) consiste em duas máquinas virtuais (VMs), uma Plataforma (IU) e um Nó do Controlador.

![Diagrama do Network Insights](../../images/opsmgmt-vrninw.svg "Diagrama do Network Insights")

O dispositivo vRNI Platform fornece análise, interface com o usuário e gerenciamento de dados e conecta-se ao Dispositivo do Controlador que realiza a coleta de diversas origens de dados, como o NSX Edges, o vCenter e assim por diante. Todos os componentes do vRNI utilizam endereços IP móveis do {{site.data.keyword.cloud}} Private. O vRLI é configurado como o servidor syslog para o vRNI.

![Componentes do Network Insights](../../images/opsmgmt-vrnicomponents.svg "Componentes do Network Insights")

## Requisitos do sistema
{: #opsmgmt-vrni-requirements}

Essa arquitetura suporta 3.000 VMs com o uso de um tamanho de tijolo Médio.

Tabela 1. Requisitos do sistema para o Network Insight Platform

| Atributo | Especificação |
|---|---|
| vCPU | 8 |
| Memória | 32 GB |
| Disco (thin provisioned) | 1 TB |

Tabela 2. Requisitos do sistema para o Network Insight Collector

| Atributo | Especificação |
|---|---|
| vCPU | 4 |
| Memória | 12 GB |
| Disco (thin provisioned) | 200 GB |

## Rede
{: #opsmgmt-vrni-network}

A implementação do dispositivo vRNI requer dois endereços IP da sub-rede móvel privada do Conjunto de ferramentas. Conectividade de rede à qual o vRNI solicita o acesso:
* Dispositivo do vCenter
* Dispositivo vRealize Log Insight
* Dispositivos NSX-V/T
* VXLAN de expansão de conjunto de ferramentas
* Redes do cliente
* Servidor NTP (time.services.softlayer.com)
* Active Directory/DNS do {{site.data.keyword.vmwaresolutions_short}}

## Portas
{: #opsmgmt-vrni-ports}

Tabela 3. Portas do Network Insight

| Descrição |Port | Protocolo |
|---|---|---|
| Comunicação entre as VMs do vRealize Network Insight | 443 | HTTPS |
| Serviços que requerem acesso à Internet<br>svc.ni.vmware.com<br>support2.ni.vmware.com<br>reg.ni.vmware.com|443|HTTPS
| API de ingestão de insight de log | 9000 | TCP |
| API de ingestão de insight de log sobre SSL | 9543 | TCP |
| Interface com o usuário | 80,443 | TCP |
| NTP |123 | UDP |
| SMTP | 25 | TCP |
| DNS| 53 | UDP |
| LDAP/LDAPS | 389, 636 | TCP |
| ESXi | 2055 | TCP |
| VMware vSphere / NSX | 443 | TCP |

## Autenticação
{: #opsmgmt-vrni-auth}

A autenticação do usuário do vRNI é diretamente com um Servidor do Active Directory.

## Links relacionados
{: #opsmgmt-vrni-links}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
* [vRealize Network Insights](https://docs.vmware.com/en/VMware-vRealize-Network-Insight/index.html){:new_window}
