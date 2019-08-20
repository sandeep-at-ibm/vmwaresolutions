---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-24"

keywords: NSX license upgrade, upgrade license hybridity, hybridity license

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Fazendo upgrade de licenças para instâncias do vCenter Server
{: #vc_upgrade-lic}

É possível fazer upgrade de sua licença do NSX para as instâncias V2.1 ou mais recente.

## Procedimento para fazer upgrade de sua licença do NSX
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

* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas Mais Frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
