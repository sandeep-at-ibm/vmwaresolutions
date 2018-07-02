---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-16"

---

# Excluindo instâncias do Cloud Foundation em uma configuração de vários sites

Há considerações especiais que deve-se ter em mente antes de planejar excluir instâncias do Cloud Foundation que fazem parte de uma configuração de vários sites.

Quando você excluir uma instância do Cloud Foundation, os componentes a seguir serão liberados sequencialmente:
1. Todos os serviços implementados
2. Taxa de suporte e serviços
3. Licenças do produto VMware
4. Servidores ESXi
5. Subnets
6. VLANs

Devido a dependências de recursos, os componentes em sua instância não são liberados imediatamente quando você exclui a instância. Por exemplo, as sub-redes e as VLANs não poderão ser excluídas até que os servidores ESXi sejam totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud}}, que acontece no término do ciclo de faturamento do {{site.data.keyword.cloud_notm}}. No término do ciclo de faturamento do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias, as sub-redes e as VLANs são excluídas e a exclusão da instância é concluída.

**Atenção:** você será cobrado até o fim do ciclo de faturamento do {{site.data.keyword.cloud_notm}} pela instância excluída.

## Procedimento

1. Remova todos os serviços da instância secundária do Cloud Foundation.
2. Assegure-se de que não haja objetos NSX expandidos na instância secundária que deseja excluir.
3. Exclua o vCenter e o PSC (Platform Services Controller) secundário do domínio SSO (Conexão única) primário. Para obter mais informações, veja [Cancelar o registro do vCenter Server da conexão única](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}.
4. Rebaixar a VSI (Virtual Service Instance) do controlador de domínio local. Para obter mais informações, veja [Rebaixando os controladores de domínio e os domínios](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Exclua a instância secundária do Cloud Foundation do console do {{site.data.keyword.vmwaresolutions_short}}.
6. Repita as etapas de 1 a 5 para todas as instâncias secundárias do Cloud Foundation em sua configuração de vários sites.
7. Depois de excluir todas as instâncias secundárias, também será possível excluir a instância primária do console do {{site.data.keyword.vmwaresolutions_short}}.

## Links relacionados

* [Excluindo instâncias do Cloud Foundation](sd_deletinginstance.html)
* [Pedindo, visualizando e removendo serviços de instâncias do Cloud Foundation](sd_addingremovingservices.html)
