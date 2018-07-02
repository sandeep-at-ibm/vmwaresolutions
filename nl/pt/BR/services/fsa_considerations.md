---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Visão geral do FortiGate Security Appliance on IBM Cloud

O serviço FortiGate Security Appliance on {{site.data.keyword.cloud}} implementa um par de dispositivos FortiGate Security Appliance (FSA) série 300 em um modo altamente disponível para fornecer serviços de firewall, roteamento, NAT e VPN para proteger todos os servidores e máquinas virtuais na VLAN pública de suas instâncias.

É possível gerenciar esse serviço usando o FortiOS Web Client ou a interface da linha de comandos por meio de SSH.

**Disponibilidade**: esse serviço está disponível somente para instâncias que são implementadas na V1.8 ou liberações mais recentes.

## Componentes do FortiGate Security Appliance on IBM Cloud

Quando você pede o serviço FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} para sua instância, um par de HA de FortiGate Security Appliances série 300 é implementado na VLAN pública padrão da instância ou do cluster original. Todo o tráfego para a VLAN pública de sua instância é roteado por meio do FortiGate Security Appliance.

**Nota:** se você pedir clusters adicionais, as VLANs públicas para esses clusters recém-incluídos não terão o par de HA de Security Appliances.

## Considerações ao instalar o FortiGate Security Appliance no IBM Cloud

Revise as considerações a seguir antes de instalar o serviço FortiGate Security Appliance no {{site.data.keyword.cloud_notm}}:
* Assegure-se de que a conta do {{site.data.keyword.cloud_notm}} que você está usando tenha a permissão **Hardware Firewall**. Essa permissão é necessária para editar ou visualizar logs e configurações de firewall para o serviço FortiGate Security Appliance no {{site.data.keyword.cloud_notm}} de sua instância.
* Se você quiser incluir o serviço FortiGate Security Appliance no {{site.data.keyword.cloud_notm}} em uma instância implementada, assegure-se de que não haja nenhum outro firewall da infraestrutura do {{site.data.keyword.cloud_notm}} já em vigor na VLAN pública da instância.
* Instalar o serviço FortiGate Security Appliance no {{site.data.keyword.cloud_notm}} incluirá uma nova VLAN pública.
* Durante a implementação do serviço, sua instância pode não ser capaz de acessar a internet temporariamente.
* Depois que o serviço FortiGate Security Appliance no {{site.data.keyword.cloud_notm}} for instalado com êxito, será possível gerenciar e configurar regras de firewall para o FSA no console do FortiGate. Deve-se assegurar que as regras de firewall do FSA sejam definidas para permitir que as comunicações HTTPS de saída (TCP porta 443) iniciadas por componentes de gerenciamento, como a máquina virtual do IBM CloudDriver ou o Zerto Virtual Manager, comuniquem-se com o banco de dados de gerenciamento externo no {{site.data.keyword.cloud_notm}} pela Internet. As comunicações HTTPS de saída (porta TCP 443) se originam do endereço IP público do VMware NSX Edge Services Gateway (ESG) dos serviços de gerenciamento em sua instância.
* Se você implementar um par de dispositivos do FortiGate Security Appliance como parte de uma nova instância, os dispositivos do FortiGate Security Appliance serão configurados para permitir apenas as comunicações de saída requeridas de sua instância para a rede pública e negar todas as outras comunicações.
* Se você implementar um par de dispositivos do FortiGate Security Appliance como parte de uma instância existente, os dispositivos do FortiGate Security Appliance serão configurados com uma regra explícita para permitir todas as comunicações de gerenciamento de saída requeridas de sua instância para a rede pública. Além disso, os dispositivos do FortiGate Security Appliance serão configurados com uma regra adicional para permitir todas as outras comunicações de modo que o tráfego de aplicativo existente não seja interrompido. Deve-se gerenciar a configuração do FortiGate Security Appliance cuidadosamente para permitir apenas as comunicações necessárias e negar todas as outras comunicações.

## Considerações ao remover o FortiGate Security Appliance no IBM Cloud

Revise as considerações a seguir antes de remover o serviço FortiGate Security Appliance no {{site.data.keyword.cloud_notm}}:
* Remover o serviço FortiGate Security Appliance no {{site.data.keyword.cloud_notm}} removerá a VLAN pública que foi incluída.
* Durante a remoção do serviço, sua instância pode não ser capaz de acessar a Internet temporariamente.
* Todas as regras do FortiGate para permitir, inspecionar, bloquear e rotear o tráfego do NAT são removidas junto com o serviço Fortinet. Se você tiver quaisquer regras NAT, deverá reconfigurá-las.

## Links relacionados

* [Solicitando FortiGate Security Appliance no {{site.data.keyword.cloud_notm}}](fsa_ordering.html)
* [Gerenciando o FortiGate Security Appliance no {{site.data.keyword.cloud_notm}}](managingfsa.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [Website do Fortinet](https://www.fortinet.com/){:new_window}
* [Biblioteca de documentos do Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
