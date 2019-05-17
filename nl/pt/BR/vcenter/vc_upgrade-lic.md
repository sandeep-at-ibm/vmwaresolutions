---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Fazendo upgrade de licenças para instâncias do vCenter Server
{: #vc_upgrade-lic}

Será possível fazer upgrade de suas instâncias do VMware vCenter Server para o vCenter Server with Hybridity Bundle somente se sua instância estiver na V2.3 ou mais recente.

Os usuários do Parceiro de Negócios IBM não têm a opção de fazer upgrade para o Hybridity Bundle.
{:note}

## Antes de fazer upgrade de sua licença para o Hybridity Bundle
{: #vc_upgrade-lic-upgrade-prereq}

Revise as ações a seguir que são tomadas ao fazer upgrade para o Hybridity Bundle:

* Se a sua instância do vCenter Server tiver a edição VMware NSX Base instalada, sua licença do NSX será submetida a upgrade automaticamente para a edição NSX Advanced.
* Se sua instância do vCenter Server tiver armazenamento NFS, você não será cobrado pelo armazenamento do VMware vSAN. No entanto, você será cobrado pela licença do vSAN que está incluída com o Hybridity Bundle.

## Procedimento para fazer upgrade para o Hybridity Bundle (instâncias da V2.3 ou mais recente)
{: #vc_upgrade-lic-procedure-upgrade-to-hybridity}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para fazer upgrade para o Hybridity Bundle.
3. Na página **Resumo**, verifique se todos os detalhes da instância são exibidos corretamente. Em seguida, clique em **Infraestrutura** na área de janela de navegação esquerda para verificar os detalhes na página **Infraestrutura**.

   Se os detalhes não forem exibidos, isso poderá indicar um problema de conectividade com o IBM CloudDriver VSI, como resultado de uma regra de firewall ou de outro problema de rede. Resolva o problema antes de continuar com a próxima etapa, caso contrário, o upgrade poderá falhar.

4. Clique em **Atualização e correção** na área de janela de navegação esquerda.
5. Para aplicar o upgrade de licença do Hybridity Bundle, na tabela **Upgrades de licença**, clique em **Fazer upgrade** na coluna **Ação**. Revise o custo estimado e clique em **Fazer upgrade**.
6. Opcionalmente, é possível implementar o serviço VMware HCX on {{site.data.keyword.cloud_notm}}. Quando o Hybridity Bundle estiver ativado na tabela **Upgrades de licença**, conclua as etapas a seguir:
  1. Na tabela **Upgrades de licença**, clique em **Implementar o HCX on {{site.data.keyword.cloud_notm}}** na coluna **Ação**.
  2. Role para o cartão **HCX on {{site.data.keyword.cloud_notm}}** e clique em **Selecionar serviço**.
  3. Role para baixo e especifique as configurações necessárias para o serviço e clique em **Avançar**.
  4. Revise os termos que se aplicam ao serviço, revise o custo estimado e clique em **Fazer pedido**.

## Procedimento para fazer upgrade de sua licença do NSX (instâncias da V2.1 ou mais recente)
{: #vc_upgrade-lic-nsx}

Este procedimento se aplica a instâncias que são implementadas na V2.1 ou mais recente. Para instâncias que são implementadas na V2.0 e anterior, deve-se fazer upgrade da licença do NSX manualmente.

É possível fazer upgrade da licença do NSX para sua instância para uma edição mais recente. Os downgrades de edição da licença não são suportados.

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância para a qual fazer upgrade da licença do NSX.
3. Na página **Resumo**, verifique se todos os detalhes da instância são exibidos corretamente. Em seguida, clique em **Infraestrutura** na área de janela de navegação esquerda para verificar os detalhes na página **Infraestrutura**.

   Se os detalhes não forem exibidos, isso poderá indicar um problema de conectividade com o IBM CloudDriver Virtual Server Instance (VSI), como resultado de uma regra de firewall ou de um problema de rede. Resolva o problema antes de continuar com a próxima etapa, caso contrário, o upgrade poderá falhar.

4. Clique em **Atualizar e corrigir** na área de janela de navegação esquerda e clique em **Fazer upgrade**. Na janela **Atualizar NSX License Edition**, selecione a edição para a qual deseja fazer upgrade e clique em **Atualizar**.

   O upgrade de licença substitui todas as licenças NSX existentes na instância. Poderão incorrer encargos adicionais de uma sobreposição de licenças antigas e novas se você fizer upgrade no meio de um ciclo de faturamento. Para evitar encargos adicionais, recomenda-se fazer upgrade da licença no final do ciclo de faturamento.
   {:note}

## Links relacionados
{: #vc_upgrade-lic-related}

* [VCenter Server with Hybridity Bundle Visão Geral](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas Mais Frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
