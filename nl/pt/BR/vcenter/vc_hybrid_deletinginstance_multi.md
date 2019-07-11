---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: vCenter Server Hybridity delete instance, delete vCenter Server Hybridity, delete multi-site

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Excluindo instâncias do vCenter Server with Hybridity Bundle em uma configuração multissite
{: #vc_hybrid_deletinginstance_multi}

Há considerações especiais a serem conhecidas antes de você planejar excluir instâncias do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle que fazem parte de uma configuração de vários sites.

Quando você excluir uma instância do vCenter Server with Hybridity Bundle, os componentes a seguir serão liberados sequencialmente:
1. Todos os serviços implementados
2. Taxa de suporte e serviços
3. Licenças do produto VMware
4. Servidores ESXi
5. Subnets
6. VLANs

Devido a dependências de recursos, os componentes em sua instância não são liberados imediatamente quando você exclui a instância. Por exemplo, as sub-redes e VLANs não podem ser excluídas até que os servidores ESXi sejam totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud_notm}}, o que acontece no final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}. No final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias, as sub-redes e VLANs são excluídas e a exclusão da instância é concluída.

Você é faturado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para a instância excluída.
{:note}

## Procedimento para excluir instâncias do vCenter Server with Hybridity Bundle em uma configuração multisite
{: #vc_hybrid_deletinginstance_multi-procedure}

1. Remova todos os serviços da instância secundária do vCenter Server with Hybridity Bundle.
2. Assegure-se de que não tenha objetos NSX expandidos na instância secundária que deseja excluir.
3. Exclua o vCenter Server secundário do domínio SSO (Conexão única) primário. Para obter mais informações, veja [Cancelar o registro do vCenter Server da conexão única](https://kb.vmware.com/s/article/2106736){:new_window}.
4. Rebaixar a VSI (Virtual Service Instance) do controlador de domínio local. Para obter mais informações, veja [Rebaixando os controladores de domínio e os domínios](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Exclua a instância secundária do vCenter Server with Hybridity Bundle do console do {{site.data.keyword.vmwaresolutions_short}}.
6. Repita as etapas 1 a 5 para todas as instâncias secundárias do vCenter Server with Hybridity Bundle em sua configuração multisite.
7. Depois de excluir todas as instâncias secundárias, também será possível excluir a instância primária do console do {{site.data.keyword.vmwaresolutions_short}}.

## Links relacionados
{: #vc_hybrid_deletinginstance_multi-related}

* [Excluindo instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance)
* [Pedindo, visualizando e removendo serviços de instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Cancelando servidores virtuais](/docs/vsi?topic=virtual-servers-managing-virtual-servers#cancel)
