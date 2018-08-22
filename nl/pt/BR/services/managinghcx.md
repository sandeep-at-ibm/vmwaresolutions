---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Gerenciando VMware HCX on IBM Cloud

## Acessando os consoles de gerenciamento do HCX on IBM Cloud

Para gerenciar o serviço HCX no {{site.data.keyword.cloud}}, deve-se acessar o Console em Nuvem do HCX ou o Console do Administrador do HCX Manager:
1. Use a VPN da infraestrutura do {{site.data.keyword.cloud_notm}} ou um servidor jump para permitir o acesso ao endereço IP do dispositivo virtual HCX Manager (HCX Manager). É possível localizar o endereço IP no HCX na página de detalhes do serviço {{site.data.keyword.cloud_notm}} no console do {{site.data.keyword.vmwaresolutions_short}}.
2. Para acessar o Console em Nuvem do HCX, clique em **Visualizar o Console em Nuvem do HCX** no HCX na página de detalhes do serviço {{site.data.keyword.cloud_notm}} e, em seguida, efetue login usando as credenciais do vCenter Server.
3. Para acessar o Console do Administrador do HCX Manager, clique em **Visualizar o Console do Administrador do HCX Manager** no HCX na página de detalhes do serviço {{site.data.keyword.cloud_notm}} e, em seguida, efetue login usando as credenciais do HCX Manager listadas na mesma página de detalhes do serviço.

Para obter mais informações, veja [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html).

## Aplicando atualizações ao HCX on IBM Cloud

O HCX on {{site.data.keyword.cloud_notm}} é implementado com a construção mais recente testada da tecnologia VMware Hybrid Cloud Extension. O VMware envia atualizações para essas construções regularmente, que incluem correções importantes e novos recursos. Essas construções são enviadas para instalações do HCX on {{site.data.keyword.cloud}} automaticamente, incluindo instalações do HCX no local.

Para aplicar quaisquer correções de manutenção enviadas por push para seu ambiente, deve-se usar o Console do Administrador do HCX Manager em seu data center no local e sua instância do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle.

Se você não vir uma atualização de construção que está esperando, se tiver problemas com o HCX ou se desejar ter a construção mais recente do HCX enviada por push para seu sistema imediatamente, abra um chamado de suporte seguindo as etapas em [Contatando o suporte IBM](../vmonic/trbl_support.html).

### Links relacionados

* [HCX no {{site.data.keyword.cloud_notm}} visão geral](hcx_considerations.html)
* [Glossário de termos do HCX](hcx_glossary.html)
* [Visão geral do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentação do VMware Hybrid Cloud Extension](https://hcx.vmware.com/#vm-documentation)
