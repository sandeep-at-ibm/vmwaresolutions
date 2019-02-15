---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Aplicando atualizações a instâncias do Cloud Foundation

O console do {{site.data.keyword.vmwaresolutions_full}} periodicamente detecta e lista as atualizações de software disponíveis que podem ser aplicadas ao seu ambiente virtual do VMware.

Uma atualização disponível é um registro na lista de atualizações de software da instância, que pode ser aplicado imediatamente ou planejado para um horário posterior. A atualização é um pacote configurável que contém um ou mais pacotes para atualizar os componentes de gerenciamento da IBM e os componentes do VMware.

Iniciando com a V2.5, as atualizações do IBM CloudDriver não são mais listadas porque as atualizações automáticas estão ativadas. Ações como a inclusão de um host, a inclusão de um cluster e a solicitação de um serviço atualizam automaticamente a instância para a versão mais recente. Para obter mais informações sobre atualizações automáticas, consulte a seção *Resiliência do IBM CloudDriver* em Notas sobre a liberação do [ para a V2.5](/docs/services/vmwaresolutions/vmonic/relnotes_v25.html).
{:note}

## Antes de iniciar

Antes de tentar aplicar uma atualização, expanda a entrada de atualização clicando na seta para baixo e verifique as informações a seguir:
* A versão da atualização. Deve-se aplicar as atualizações em sequência cronológica que é da mais antiga para a mais recente. Assegure-se de que tenha aplicado todas as atualizações anteriores antes de aplicar a mais recente. Por exemplo, deve-se aplicar a atualização V2.4 antes de tentar aplicar a atualização V2.5.
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

## Procedimento para aplicar atualizações a instâncias do Cloud Foundation

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do Cloud Foundation**, clique na instância a ser atualizada.
3. Na página **Resumo**, verifique se todos os detalhes da instância são exibidos corretamente. Em seguida, clique em **Infraestrutura** na área de janela de navegação esquerda para verificar os detalhes na página **Infraestrutura**.
   Se os detalhes não forem exibidos, isso poderá indicar um problema de conectividade com o IBM CloudDriver Virtual Server Instance (VSI), como resultado de uma regra de firewall ou outro problema de rede. Resolva o problema antes de continuar com a próxima etapa, caso contrário, a atualização poderá falhar.
4. Clique em **Atualização e correção** na área de janela de navegação esquerda.
5. Clique na seta para baixo para expandir a atualização que você deseja aplicar e, em seguida, conclua uma das etapas a seguir:
   *  Para iniciar a atualização imediatamente, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Atualizar agora**.
   *  Para planejar uma atualização futura, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Planejar atualização**. Selecione a data, o horário e o fuso horário quando desejar que a atualização seja iniciada. Clique em **OK**.
6. Se estiver aplicando atualizações em instâncias do Cloud Foundation na configuração de implementação multisite, será exibida uma seção intitulada **Etapas necessárias para atualizar**, que lista as operações de atualização necessárias para todas as instâncias na implementação multisite. Deve-se concluir as etapas em sequência clicando em **Aplicar atualização** para cada etapa. Deve-se aguardar a conclusão da etapa anterior antes de iniciar a próxima etapa.

## Resultados

1. Antes de uma operação de atualização ser iniciada, uma verificação de funcionamento da instância será concluída. Se a verificação de funcionamento falhar, você será notificado para poder corrigir o problema antes de aplicar a atualização.
2. Durante atualizações que incluem atualizações de componentes VMware, as MVs podem precisar ser migradas dos servidores ESXi para entrar no modo de manutenção. A migração da MV poderá ser evitada se uma MV tiver um armazenamento de dados local ou um CD-ROM montado.
3. Durante o fornecimento de um novo ambiente, o {{site.data.keyword.vmwaresolutions_short}} cria o ID **automationuser** que é usado para gerenciamento da instância, incluindo para aplicar atualizações. Não mude a senha para esse ID do usuário. Mudar a senha pode fazer com que a atualização falhe.

4. Depois que uma atualização for aplicada, aparecerá um registro na lista de status de atualização de software, no qual é possível visualizar o progresso detalhado e o status da atualização. Quando a atualização for concluída com êxito, um registro aparecerá na lista de atualizações de softwares instalados.

  Para recuperar o status mais recente para uma tarefa de atualização, clique no ícone de atualização no canto superior direito da página.
  {:tip}

5. Para obter mais informações sobre os status de atualização, consulte a tabela a seguir.

   Tabela 2. Detalhes de status de atualização

    <table>
      <tr>
        <th> Status </th>
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

6. Se o processo de atualização falhar em uma etapa específica, [entre em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html) para obter assistência. Você será avisado sobre como resolver o problema e será orientado a reiniciar o upgrade a partir da etapa que falhou.

### Links relacionados

* [Visão geral do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html)
* [Veeam no {{site.data.keyword.cloud_notm}} visão geral](/docs/services/vmwaresolutions/services/veeam_considerations.html)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [Perguntas Mais Frequentes](/docs/services/vmwaresolutions/vmonic/faq.html)
