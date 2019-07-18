---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: FortiGate security, FortiGate Sirtual Appliance, tech specs FortiGate

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations}

O serviço FortiGate Security Appliance on {{site.data.keyword.cloud}} implementa um par de dispositivos FortiGate Security Appliance (FSA) série 300 em um modo altamente disponível para fornecer serviços de firewall, roteamento, NAT e VPN para proteger todos os servidores e máquinas virtuais na VLAN pública de suas instâncias.

É possível gerenciar esse serviço usando o FortiOS Web Client ou a interface da linha de comandos por meio de SSH.

Este serviço está disponível somente para instâncias implementadas na V1.8 ou liberações mais recentes.
{:note}

## Especificações técnicas para o FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-specs}

Os componentes a seguir são pedidos e incluídos no serviço FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:

### Hardware
{: #fsa_considerations-hardware}

O dispositivo de segurança FortiGate série 300.

### Alta disponibilidade
{: #fsa_considerations-ha}

Dois dispositivos são implementados na configuração ativa/passiva.

### Rede
{: #fsa_considerations-networking}

* Dual 1 GbE ligado nas redes de envio de dados e de recebimento de dados
* Uma nova VLAN pública do {{site.data.keyword.cloud_notm}} de envio de dados
* Uma VLAN pública do {{site.data.keyword.cloud_notm}} de recebimento de dados existente

## Considerações ao instalar o FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-install}

Revise as considerações a seguir antes de instalar o serviço FortiGate Security Appliance no {{site.data.keyword.cloud_notm}}:
* Assegure-se de que a conta do {{site.data.keyword.cloud_notm}} que você está usando tenha a permissão **Hardware Firewall**. Essa permissão é necessária para editar ou visualizar logs e configurações de firewall para o serviço FortiGate Security Appliance no {{site.data.keyword.cloud_notm}} de sua instância.
* Se desejar incluir o serviço FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} em uma instância implementada, assegure-se de que nenhum outro firewall de infraestrutura do {{site.data.keyword.cloud_notm}} já esteja em vigor na VLAN pública da instância.
* A instalação do serviço FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} inclui uma nova VLAN pública.
* Durante a implementação do serviço, sua instância pode não ser capaz de acessar a internet temporariamente.
* Depois que o serviço FortiGate Security Appliance no {{site.data.keyword.cloud_notm}} for instalado com êxito, será possível gerenciar e configurar regras de firewall para o FSA no console do FortiGate. Deve-se assegurar que as regras de firewall do FSA sejam definidas para permitir que as comunicações HTTPS (porta TCP 443) de saída que são iniciadas por componentes de gerenciamento, como o Zerto Virtual Manager, se comuniquem com o banco de dados de gerenciamento externo no {{site.data.keyword.cloud_notm}} pela Internet. As comunicações HTTPS de saída (porta TCP 443) se originam do endereço IP público do VMware NSX Edge Services Gateway (ESG) dos serviços de gerenciamento em sua instância.
* Deve-se gerenciar a configuração do FortiGate Security Appliance cuidadosamente para permitir apenas as comunicações necessárias e negar todas as outras comunicações.
* Se você pedir clusters adicionais, as VLANs públicas para esses clusters recém-incluídos não terão o par de HA de dispositivos de segurança.

## Considerações ao remover o FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-remove}

Revise as considerações a seguir antes de remover o serviço FortiGate Security Appliance no {{site.data.keyword.cloud_notm}}:
* A remoção do serviço FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} remove a VLAN pública que foi incluída.
* Durante a remoção do serviço, sua instância pode não ser capaz de acessar a Internet temporariamente.
* Todas as regras do FortiGate para permitir, inspecionar, bloquear e rotear o tráfego do NAT são removidas junto com o serviço Fortinet. Se você tiver quaisquer regras NAT, deverá reconfigurá-las.

## Links relacionados
{: #fsa_considerations-related}

* [Solicitando FortiGate Security Appliance no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [Gerenciando o FortiGate Security Appliance no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfsa)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Website do Fortinet](https://www.fortinet.com/){:external}
* [Biblioteca de documentos do Fortinet](https://docs.fortinet.com/product/fortigate/6.2){:external}
