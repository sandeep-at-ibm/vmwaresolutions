---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: Caveonix view license, Caveonix manage license, delete Caveonix license

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gerenciando licenças do Caveonix RiskForesight
{: #caveonix_license_managing}

É possível visualizar, editar notas ou excluir as licenças do Caveonix RiskForesight que você solicitou para uso independente.

## Procedimento para visualizar licenças do Caveonix RiskForesight
{: #caveonix_license_managing_procedure-view}

1. Clique em **Recursos** na área de janela de navegação esquerda e role para baixo para a tabela **Licenças do Caveonix RiskForesight**.

   | Item | Descrição |
   |:-----|:------------|
   | Nome | O nome da licença. |
   | Horário de criação | A data e hora em que a licença foi criada. |
   | Barra de Status | O status da licença: <br>Modificando: a licença está sendo criada.<br>Instalada: a licença está pronta para uso.<br>Removendo: A licença está sendo excluída. |
   {: caption="Tabela 1. Descrição dos itens de licença do Caveonix RiskForesight" caption-side="top"}

2. Para visualizar os detalhes de uma licença específica, clique na licença.

## Procedimento para editar notas para licenças do Caveonix RiskForesight
{: #caveonix_license_managing_procedure-edit}

1. Clique em **Recursos** na área de janela de navegação esquerda.
2. Role para baixo até a tabela **Licenças do Caveonix RiskForesight** e clique na licença para a qual você deseja editar as notas.
3. Na página de detalhes da licença, edite as notas da licença e, em seguida, clique em **Confirmar**.

## Problemas conhecidos sobre exibição de data da licença
{: #caveonix_license_considerations-date}

Se você estiver usando o Mozilla Firefox como seu navegador, as datas de início e de encerramento da licença poderão ser exibidas sem valores no console do Caveonix RiskForesight. Para resolver o problema, visualize as informações sobre licença em outro navegador, como o Google Chrome.

Se você estiver tendo esse problema e o único navegador que puder ser usado for o Firefox, entre em contato com o [Suporte do Caveonix](https://www.caveonix.com/support/){:external} para obter assistência.
{:note}

## Procedimento para excluir licenças do Caveonix RiskForesight
{: #caveonix_license_managing_procedure-delete}

A exclusão de uma licença do Caveonix RiskForesight não remove o serviço Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} que está instalado em uma instância do vCenter Server. Para remover o serviço, deve-se fazer isso no console do {{site.data.keyword.vmwaresolutions_short}}. Para obter mais informações, consulte [Procedimento para remover serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-removing-procedure).
{:note:}

1. Clique em **Recursos** na área de janela de navegação esquerda.
2. Role para baixo até a tabela **Licenças do Caveonix RiskForesight** e localize a licença a ser excluída.
3. Na coluna **Ações**, clique no ícone de exclusão.
4. Na janela **Excluir licença**, clique em **OK**.
   O status da licença é mudado para **Removendo**. Quando a exclusão da licença for concluída, a licença não estará mais disponível na tabela **Licenças do Caveonix RiskForesight**.

## Links relacionados
{: #caveonix_license_managing-related}

* [Visão geral do Caveonix RiskForesight]()
* [ Ordenando licenças do Caveonix RiskForesight ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)
