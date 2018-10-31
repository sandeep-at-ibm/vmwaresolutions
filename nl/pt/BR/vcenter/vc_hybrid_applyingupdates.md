---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

{:tip: .tip}

# Aplicando atualizações a instâncias do vCenter Server with Hybridity Bundle

O processo de aplicação de correções e atualizações a instâncias do vCenter Server with Hybridity Bundle é automatizado somente para os componentes de gerenciamento. As atualizações do VMware devem ser aplicadas manualmente.

## Antes de iniciar

Antes de tentar aplicar uma atualização, expanda a entrada de atualização clicando na seta para baixo e verifique as informações a seguir:
* A versão da atualização. Deve-se aplicar as atualizações em sequência cronológica que é da mais antiga para a mais recente. Assegure-se de que tenha aplicado todas as atualizações anteriores antes de aplicar a mais recente. Por exemplo, deve-se aplicar a atualização V2.3 antes de tentar aplicar a atualização V2.4.
* Se o tempo de inatividade é necessário.
* O tempo estimado total para concluir a atualização.
* O impacto da atualização no ambiente virtual do VMware.
* Os detalhes da atualização.

A tabela a seguir mostra como os diferentes níveis de impacto afetam o sistema.

Tabela 1. Atualize os níveis e o impacto

| Nível de atualização  | Impacto        |  
|:------------- |:------------- |
| Baixo    | Esta atualização não afeta nenhum sistema. Não é necessário aplicá-lo durante o tempo de inatividade planejado. |  
| Médio | Esta atualização pode afetar alguns sistemas. Recomenda-se aplicar durante o tempo de inatividade planejado. |  
| Grave  | Esta atualização afeta alguns ou todos os sistemas. Deve-se aplicá-lo durante o tempo de inatividade planejado. |  

## Procedimento para aplicar atualizações a instâncias do vCenter Server with Hybridity Bundle

1. No console do {{site.data.keyword.vmwaresolutions_full}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância a ser atualizada.
3. Na página **Resumo**, verifique se todos os detalhes da instância são exibidos corretamente. Em seguida, clique em **Infraestrutura** na área de janela de navegação esquerda para verificar os detalhes na página **Infraestrutura**.
   Se os detalhes não forem exibidos, isso poderá indicar um problema de conectividade com a Virtual Server Instance (VSI) do IBM CloudDriver, como resultado de uma regra de firewall ou outro problema de rede. Resolva o problema antes de continuar com a próxima etapa, caso contrário, a atualização poderá falhar.
4. Clique em **Atualização e correção** na área de janela de navegação esquerda.

   **Nota:** a página **Atualização e correção** contém somente os pacotes para atualizar os componentes de gerenciamento da IBM, não as atualizações do VMware. O {{site.data.keyword.vmwaresolutions_short}} aplica atualizações do VMware às operações a seguir:
   * Quando uma nova instância do vCenter Server é implementada.
   * Quando novos servidores ESXi são incluídos.
   * Quando novos clusters são incluídos.

5. Para upgrades de licença, clique em  ** Atualizar **. Selecione a edição para a qual você deseja fazer upgrade na lista e clique em **Fazer upgrade**. Downgrades da edição da licença não estão disponíveis.

   **Nota:** o upgrade de licença substitui todas as licenças NSX existentes na instância. Encargos adicionais poderão incorrer de uma sobreposição de licenças antigas e novas, se você fizer upgrade no meio de um ciclo de faturamento. Para evitar encargos adicionais, recomenda-se fazer upgrade da licença no final do ciclo de faturamento.

6. Para atualizações de software, clique na seta para baixo para expandir a atualização que você deseja aplicar e, em seguida, conclua uma das etapas a seguir:
   *  Para iniciar a atualização imediatamente, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Atualizar agora**.
   *  Para planejar uma atualização futura, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Planejar atualização**. Selecione a data, o horário e o fuso horário quando desejar que a atualização seja iniciada. Clique em **OK**.
7. Se você estiver aplicando atualizações a instâncias do vCenter Server na configuração de implementação multissite, uma seção intitulada **Etapas necessárias para atualização** será exibida. Esta seção lista as operações de atualização necessárias para todas as instâncias na implementação de vários sites. Deve-se concluir as etapas em sequência clicando em **Aplicar atualização** para cada etapa. Deve-se aguardar a conclusão da etapa anterior antes de iniciar a próxima etapa.   

## Resultados

2. Depois que uma atualização for aplicada, aparecerá um registro na lista de status de atualização de software, no qual é possível visualizar o progresso detalhado e o status da atualização. Quando a atualização for concluída com êxito, um registro aparecerá na lista de atualizações de softwares instalados.

  Para recuperar o status mais recente para uma tarefa de atualização, clique no ícone de atualização no canto superior direito da página.
  {:tip}

3. Para obter detalhes sobre os status de atualização, veja a lista a seguir:
<dl class="dl">
<dt class="dt dlterm">Disponível</dt>
<dd class="dd">A atualização está disponível para ser aplicada. Não é possível selecionar uma atualização disponível até que todas as suas atualizações anteriores sejam aplicadas.
</dd>
<dt class="dt dlterm">Em andamento</dt>
<dd class="dd">A tarefa de atualização foi iniciada, mas não foi concluída ainda. Não será possível aplicar nenhuma outra atualização até que a tarefa de atualização atual esteja concluída.</dd>
<dt class="dt dlterm">Instalado</dt>
<dd class="dd">A tarefa de atualização está concluída. O componente correspondente da plataforma VMware foi atualizado.</dd>
<dt class="dt dlterm">Com falha</dt>
<dd class="dd">A tarefa de atualização falha. O console relata um erro para a falha de atualização. Revise o erro e corrija o problema relatado antes de reaplicar a atualização.</dd>
<dt class="dt dlterm">Planejado</dt>
<dd class="dd">A tarefa de atualização está planejada para um momento posterior. A tarefa de atualização é iniciada automaticamente no momento planejado.</dd>
<dt class="dt dlterm">Desconhecido</dt>
<dd class="dd">O status da tarefa de atualização não pode ser obtido. Entre em contato com o Suporte IBM para obter assistência.</dd>
</dl>

4. Se o processo de atualização falhar em uma etapa específica, [entre em contato com o Suporte IBM](../vmonic/trbl_support.html) para obter assistência. Você será avisado sobre como resolver o problema e orientado a tentar o upgrade novamente a partir da etapa que falhou.

### Links relacionados

* [vCenter Server com visão Hybridity Bundle](../vcenter/vc_hybrid_overview.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas Mais Frequentes](../vmonic/faq.html)
