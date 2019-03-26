---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Perguntas mais frequentes sobre servidores ESXi
{: #faq_esxi}

Encontre respostas às perguntas mais frequentes sobre os servidores ESXi gerenciados no console do {{site.data.keyword.vmwaresolutions_full}}.

## Quantos servidores ESXi posso incluir em minha instância?
{: #faq_esxi-instance}
{: faq}

* Para instâncias do vCenter Server, é possível expandir o cluster padrão para ter até 51 servidores ESXi. Cada um dos clusters não padrão pode ser expandido para ter até 59 servidores ESXi. Como é possível incluir até 10 clusters em uma instância, cada instância implementada pode ter um máximo de 51 + 9x59 = 582 servidores ESXi em todos os clusters.
* Para instâncias do Cloud Foundation, a configuração padrão tem quatro servidores ESXi. É possível incluir um máximo de 28 servidores (para um total de 32 servidores). Para instâncias do Cloud Foundation em uma configuração de vários sites, é possível ter um máximo de 128 servidores ESXi em todas as instâncias.

  Se a configuração do Cloud Foundation requerer uma implementação multisite com mais de 128 servidores ESXi, [entre em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) para obter assistência.
  {:note}

## Quantos servidores ESXi posso incluir em um cluster?
{: #faq_esxi-cluster}
{: faq}

Para instâncias implementadas na V2.2 e mais recente, é possível incluir um máximo de 51 servidores ESXi em um cluster inicial e um máximo de 59 servidores ESXi nos clusters incluídos.

Para instâncias implementadas na V2.1 ou anterior, deve-se ativar o suporte vSAN necessário para aumentar o tamanho do cluster além de 32. Conclua as etapas a seguir para ativar o suporte vSAN necessário:

1. Em cada servidor ESXi implementado, execute os comandos a seguir:

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. Reinicie cada servidor ESXi. Para obter mais informações, veja [Criando um cluster vSAN 6.x com até 64 hosts](https://kb.vmware.com/s/article/2110081).
3. Talvez seja necessário aumentar o tamanho do vCenter Server para acomodar as máquinas virtuais incluídas e os servidores ESXi.
4. Abra um chamado de suporte IBM para indicar que você aplicou as mudanças no vSAN manualmente, concluindo as etapas de 1 a 3. No chamado, solicite que sua instância atualizada esteja ativada para servidores ESXi além de 32.

## Posso mudar os nomes dos servidores ESXi e endereços IP?
{: #faq_esxi-change-name-ip}
{: faq}

Os nomes do servidor ESXi e os endereços IP não podem ser mudados porque estão registrados para a resolução DNS do Windows. As mudanças podem resultar em falha durante a implementação ou falha de funções do vCenter Server.

Não use o recurso **Renomear dispositivo** na interface com o usuário do {{site.data.keyword.cloud_notm}} para mudar nomes de servidores ESXi. Essa função muda o FQDN do servidor ESXi, mas o vCenter Server configurado e os registros de host do VSI do Windows estarão incorretos e poderão causar falhas.
{:note}

## Posso desativar o acesso raiz nos meus servidores ESXi?
{: #faq_esxi-disable-root}
{: faq}

Recomenda-se manter o acesso raiz ativado em servidores ESXi, caso contrário, poderão ocorrer falhas nas funções do {{site.data.keyword.vmwaresolutions_short}}.

Se necessário, é possível desativar o acesso raiz após os servidores ESXi terem um status **Pronto para uso** no console do {{site.data.keyword.vmwaresolutions_short}}.

Deve-se reativar o acesso raiz para operações de automação subsequentes, por exemplo, ao incluir ou remover compartilhamentos de arquivos ou ao instalar serviços de complemento, como Zerto on {{site.data.keyword.cloud_notm}}.

## Posso incluir rotas estáticas nos meus servidores ESXi para montar o armazenamento de outros locais?
{: #faq_esxi-static-routes}
{: faq}

É possível incluir rotas estáticas para armazenamento, mas deve-se fazer isso com extremo cuidado. Caso contrário, os compartilhamentos existentes poderão se tornar desmontados.

A inclusão de rotas estáticas para o vMotion não é suportada. As mudanças na configuração de sub-rede vMotion podem resultar em falha nas funções do {{site.data.keyword.vmwaresolutions_short}}.
{:note}

## Links relacionados
{: #faq_esxi-related}

* [Expandindo e contraindo a capacidade para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
