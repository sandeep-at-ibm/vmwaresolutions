---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Gerenciando o FortiGate Security Appliance no IBM Cloud

Depois que o serviço FortiGate Security Appliance no {{site.data.keyword.cloud}} for instalado com êxito, será possível gerenciar e configurar regras de firewall para o FSA no console do FortiGate.

**Importante**: deve-se assegurar que as regras de firewall do FSA sejam definidas para permitir que as comunicações HTTPS (porta TCP 443) de saída que são iniciadas por componentes de gerenciamento, como o Zerto Virtual Manager, se comuniquem com o banco de dados de gerenciamento externo na infraestrutura da {{site.data.keyword.cloud_notm}} pela Internet. As comunicações HTTPS de saída (porta TCP 443) se originam do endereço IP público do VMware NSX Edge Services Gateway (ESG) dos serviços de gerenciamento em sua instância.

## Acessando o console série 300 do FortiGate

Para gerenciar o serviço FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, deve-se acessar o console do FortiGate® série 300 de uma das maneiras a seguir:
* Efetue login no FortiOS Web Client usando as credenciais que podem ser localizadas no FortiGate Security Appliance na página de detalhes do serviço {{site.data.keyword.cloud_notm}}.
* Acesse o console por meio da conexão SSH usando as credenciais que podem ser localizadas no FortiGate Security Appliance na página de detalhes do serviço {{site.data.keyword.cloud_notm}}.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](../vcenter/vc_addingremovingservices.html)

### Links relacionados

* [FortiGate Security Appliance no {{site.data.keyword.cloud_notm}} visão geral](fsa_considerations.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [Website fortinet.com](https://www.fortinet.com/)
* [Documentação técnica do Fortinet](http://docs.fortinet.com/fortigate/admin-guides)
