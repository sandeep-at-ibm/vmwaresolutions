---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gerenciando o FortiGate Security Appliance no IBM Cloud
{: #managingfsa}

Depois que o serviço FortiGate Security Appliance no {{site.data.keyword.cloud}} for instalado com êxito, será possível gerenciar e configurar regras de firewall para o FSA no console do FortiGate.

Deve-se assegurar que as regras de firewall do FSA sejam definidas para permitir que comunicações HTTPS (Porta TCP 443) de saída iniciadas pelos componentes de gerenciamento, como o Zerto Virtual Manager, se comuniquem com o banco de dados de gerenciamento externo na infraestrutura do {{site.data.keyword.cloud_notm}} na Internet. As comunicações HTTPS de saída (porta TCP 443) se originam do endereço IP público do VMware NSX Edge Services Gateway (ESG) dos serviços de gerenciamento em sua instância.
{:important}

## Acessando o console série 300 do FortiGate
{: #managingfsa-access-console}

Para gerenciar o serviço FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, deve-se acessar o console do FortiGate® série 300 de uma das maneiras a seguir:
* Efetue login no FortiOS Web Client usando as credenciais que podem ser localizadas no FortiGate Security Appliance na página de detalhes do serviço {{site.data.keyword.cloud_notm}}.
* Acesse o console por meio da conexão SSH usando as credenciais que podem ser localizadas no FortiGate Security Appliance na página de detalhes do serviço {{site.data.keyword.cloud_notm}}.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)

## Links relacionados
{: #managingfsa-related}

* [FortiGate Security Appliance no {{site.data.keyword.cloud_notm}} visão geral](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Website fortinet.com](https://www.fortinet.com/)
* [Documentação técnica do Fortinet](http://docs.fortinet.com/fortigate/admin-guides)
