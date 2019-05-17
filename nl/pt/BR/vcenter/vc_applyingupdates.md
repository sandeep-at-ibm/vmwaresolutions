---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Aplicando atualizações de componente de gerenciamento da IBM às instâncias do vCenter Server
{: #vc_applyingupdates}

O procedimento nesta seção se aplica à atualização de componentes de gerenciamento da IBM para instâncias que são implementadas nas liberações da V2.1 a V2.4.

Para instâncias implementadas em (ou submetidas a upgrade para) V2.5 ou mais recente, as atualizações e correções para os componentes de gerenciamento da IBM são aplicadas automaticamente, conforme necessário.

Para instâncias que são implementadas na V2.0 e anterior, deve-se aplicar as atualizações manualmente.

Além disso, observe o comportamento a seguir quando concluir determinadas operações em sua instância:
* Quando você pede novos serviços, a instância é atualizada para a versão mais recente.
* Quando você inclui novos clusters, esses clusters são provisionados com os componentes mais recentes do VMware, mas os clusters existentes não são.
* Ao incluir novos servidores ESXi, esses servidores ESXi são provisionados com os componentes mais recentes do VMware, mas os servidores ESXi existentes não são.

O {{site.data.keyword.vmwaresolutions_short}} não oferece suporte para aplicar atualizações e correções aos componentes do VMware. Deve-se monitorar e aplicar essas atualizações sozinho.
{:important}

## Antes de aplicar as atualizações de componente de gerenciamento da IBM
{: #vc_applyingupdates-prereq}

Expanda a entrada de atualização clicando na seta para baixo e verifique as informações a seguir:
* A versão da atualização. Deve-se aplicar as atualizações em sequência cronológica que é da mais antiga para a mais recente. Assegure-se de que tenha aplicado todas as atualizações anteriores antes de aplicar a mais recente. Por exemplo, deve-se aplicar a atualização V2.3 antes de tentar aplicar a atualização V2.4.
* Se o tempo de inatividade é necessário.
* O tempo estimado total para concluir a atualização.
* O impacto da atualização no ambiente virtual do VMware. A Tabela 1 mostra como os diferentes níveis de atualizações afetam o sistema.
* Os detalhes da atualização.

Tabela 1. Atualize os níveis e o impacto

<table>
  <tr>
    <th>Atualizar nível</th>
    <th>Impacto</th>
  </tr>
  <tr>
    <td>Baixo</td>
    <td>Esta atualização não afeta nenhum sistema. Não é necessário aplicá-lo durante o tempo de inatividade planejado.</td>
  </tr>
  <tr>
    <td>Médio</td>
  <td>Esta atualização pode afetar alguns sistemas. Recomenda-se aplicar durante o tempo de inatividade planejado.</td>
  </tr>
    <tr>
    <td>Grave</td>
  <td>Esta atualização afeta alguns ou todos os sistemas. Deve-se aplicá-lo durante o tempo de inatividade planejado.</td>
  </tr>
</table>

## Procedimento para aplicar as atualizações de componente de gerenciamento da IBM (instâncias V2.1 a V2.4)
{: #vc_applyingupdates-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância a ser atualizada.
3. Na página **Resumo**, verifique se todos os detalhes da instância são exibidos corretamente. Em seguida, clique em **Infraestrutura** na área de janela de navegação esquerda para verificar os detalhes na página **Infraestrutura**.

   Se os detalhes não forem exibidos, isso poderá indicar um problema de conectividade com o IBM CloudDriver Virtual Server Instance (VSI), como resultado de uma regra de firewall ou de um problema de rede. Resolva o problema antes de continuar com a próxima etapa, caso contrário, a atualização poderá falhar.

4. Clique em **Atualizar e corrigir** na área de janela de navegação esquerda e clique na seta para baixo para expandir a atualização de gerenciamento da IBM que você deseja aplicar e, em seguida, conclua uma das etapas a seguir:
   * Para iniciar a atualização imediatamente, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Atualizar agora**.
   * Para planejar uma atualização futura, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Planejar atualização**. Selecione a data, o horário e o fuso horário quando desejar que a atualização seja iniciada. Clique em **OK**.
5. Se você estiver aplicando atualizações a instâncias na configuração de implementação multissite, uma seção intitulada **Etapas necessárias para atualizar** será exibida. Esta seção lista as operações de atualização necessárias para todas as instâncias na implementação de vários sites. Deve-se concluir as etapas em sequência clicando em **Aplicar atualização** para cada etapa. Deve-se aguardar a conclusão da etapa anterior antes de iniciar a próxima etapa.

## Resultados após a aplicação de atualizações de componente de gerenciamento da IBM
{: #vc_applyingupdates-results}

1. Depois que uma atualização for aplicada, aparecerá um registro na lista de status de atualização de software, no qual é possível visualizar o progresso detalhado e o status da atualização. Quando a atualização for concluída com êxito, um registro aparecerá na lista de atualizações de softwares instalados.

  Para recuperar o status mais recente para uma tarefa de atualização, clique no ícone de atualização no canto superior direito da página.
  {:tip}

2. Para obter detalhes sobre os status de atualização, veja a tabela a seguir.

   Tabela 2. Detalhes de status de atualização

    <table>
      <tr>
        <th>Status</th>
        <th>Detalhes</th>
      </tr>
      <tr>
        <td>Disponível</td>
        <td>A atualização está disponível para ser aplicada. Não é possível selecionar uma atualização disponível até que todas as suas atualizações anteriores sejam aplicadas.</td>
      </tr>
      <tr>
        <td>Em andamento</td>
      <td>A tarefa de atualização foi iniciada, mas não foi concluída ainda. Não será possível aplicar nenhuma outra atualização até que a tarefa de atualização atual esteja concluída. </td>
      </tr>
        <tr>
        <td>Instalado</td>
      <td>A tarefa de atualização está concluída. O componente correspondente da plataforma VMware foi atualizado.</td>
      </tr>
        <tr>
        <td>Com falha</td>
      <td>A tarefa de atualização falha. O console relata um erro para a falha de atualização. Revise o erro e corrija o problema relatado antes de reaplicar a atualização.</td>
      </tr>
          <tr>
        <td>Planejado</td>
      <td>A tarefa de atualização está planejada para um momento posterior. A tarefa de atualização é iniciada automaticamente no momento planejado.</td>
      </tr>
          <tr>
        <td>Desconhecido</td>
      <td>O status da tarefa de atualização não pode ser obtido. Entre em contato com o Suporte IBM para obter assistência.</td>
      </tr>
    </table>

3. Se o processo de atualização falhar em uma etapa específica, [entre em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) para obter assistência. Você será avisado sobre como resolver o problema e orientado a aplicar as atualizações e correções da etapa que falhou.

## Links relacionados
{: #vc_applyingupdates-related}

* [Visão geral do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Fazendo upgrade de licenças para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_upgrade-lic)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas Mais Frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
