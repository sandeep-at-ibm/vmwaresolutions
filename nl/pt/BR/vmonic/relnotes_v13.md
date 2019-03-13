---

copyright:

  years:  2016, 2017

lastupdated: "2017-01-23"

---

# Notas sobre a liberação para V1.3
{: #relnotes_v13}

Esta liberação inclui novos recursos, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Armazenamento de nível de arquivo compartilhado para instâncias do vCenter Server

Agora, é possível incluir o NAS (Network Attached Storage) compartilhado para instâncias do vCenter Server. A inclusão desse recurso permite executar cargas de trabalho de produção no vCenter Server e evitar a perda de dados se ocorrerem falhas do nó. O File Storage NFS (Network File System) é fornecido como uma opção no processo de pedido para instâncias do vCenter Server. Para obter mais informações, veja [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Remoção da recuperação de desastre Zerto

Se você pediu a recuperação de desastre Zerto como parte de sua instância ou a incluiu como uma instância existente, agora poderá remover esse serviço quando não precisar mais dele. Depois de solicitar a remoção do serviço do console, você será guiado pelo Suporte IBM para concluir o processo de remoção.

Para obter mais informações, veja os tópicos a seguir:

* [Remoção da recuperação de desastre](/docs/services/vmwaresolutions/services/removingzertodr.html)
* [Visualizando instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_viewinginstances)
* [Visualizando instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)

## VMware NSX Edge para instâncias do Cloud Foundation

Agora, o NSX Edge é incluído como parte das novas instâncias do Cloud Foundation que você está pedindo. O NSX Edge fornece serviços de segurança e de gateway de rede de ponta para isolar uma rede virtualizada.

Durante a implementação da instância, um Management NSX Edge Services Gateway (ESG) é implementado pela IBM. Este ESG é usado pelas máquinas virtuais de gerenciamento da IBM para se comunicar com componentes de gerenciamento externo específicos da IBM relacionados à automação. Esse ESG é implementado para incluir duas interfaces: uma interface é conectada à VLAN privada do {{site.data.keyword.cloud_notm}} e a outra é conectada à VLAN pública do {{site.data.keyword.cloud_notm}}.

Para garantir a segurança, as regras de firewall estão em vigor para permitir apenas comunicações HTTPS de saída iniciadas pelas máquinas virtuais de gerenciamento. Este ESG é implementado em uma configuração Grande e somente o Suporte IBM pode modificar a configuração.

Para obter mais informações, veja os tópicos a seguir:

* [ Especificações técnicas para instâncias do Cloud Foundation ](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview#technical-specifications-for-cloud-foundation-instances)
* [O NSX Edge de serviços de gerenciamento representa um risco de segurança?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [Documentação do VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Processo de pedido da instância

O processo de pedido da instância é melhorado para as instâncias do Cloud Foundation e do vCenter Server:

* A página de resumo exibe todos os termos e condições aplicáveis para todos os componentes e serviços que são pedidos, para acesso fácil para revisar e concordar com esses termos antes de você fazer o pedido.
* É possível salvar e imprimir o resumo do pedido para sua instância antes de fazer o pedido. Com essa nova função, é possível revisar as configurações e o custo da instância, modificar os componentes que são pedidos se necessário, obter aprovação, e, em seguida, voltar para o seu pedido.

Para obter mais informações, veja os tópicos a seguir:

* [Pedindo instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)

## Gerenciamento de Instância

Novos recursos e aprimoramentos são feitos no processo de gerenciamento da instância:

* Para instâncias do Cloud Foundation e do vCenter Server, é possível ver e revisar o custo estimado de seus servidores ESXi antes de decidir incluí-los em sua instância. Depois de especificar quantos servidores você deseja incluir, o custo estimado por servidor, por mês, é exibido no console. Para obter mais informações, veja [Expandindo e contraindo a capacidade para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers) e [Expandindo e contraindo a capacidade para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers).
* Para as instâncias do Cloud Foundation e do vCenter Server, o número total de instâncias é exibido na parte superior da página de resumo. É possível também pedir uma instância com um clique das páginas de resumo da instância. Além disso, na página de resumo é possível visualizar o status do pedido detalhado durante o fornecimento. Ao passar o mouse sobre o status que é exibido, é possível ver mais detalhes sobre a etapa atual ou o erro, se houver.
* Para instâncias do Cloud Foundation, a página de detalhes da instância exibe o histórico de implementação da instância, com informações sobre o status de implementação passo a passo. Para obter mais informações, veja [Visualizando instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_viewinginstances).
* Para instâncias do Cloud Foundation, a usabilidade do processo de atualizações e correções é melhorada fornecendo mais detalhes sobre a atualização na página **Atualização e Correção**, como: o tempo de inatividade que é necessário para uma correção, o tempo para o qual a atualização foi planejada e a indicação visual quando uma correção necessária precisa ser aplicada antes da atual. Para obter mais informações, veja [Aplicando atualizações e correções a instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_applyingupdates).

## Notificações por e-mail

Agora, você recebe uma notificação por e-mail quando um novo pedido foi feito para implementação da instância e quando um serviço foi incluído, implementado ou removido da instância. As configurações de notificação são ativadas por padrão. Com base em suas preferências, é possível configurar quais notificações você deseja receber na página **Configurações**. Para obter mais informações, veja [Configuração e contas do usuário](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
