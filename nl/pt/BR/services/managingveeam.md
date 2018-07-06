---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Gerenciando o Veeam no IBM Cloud

Depois que o serviço for implementado em sua instância, será possível acessar o console do Veeam usando RDP para gerenciar o backup e a restauração de todas as máquinas virtuais em seu ambiente, incluindo o backup e a restauração dos componentes de gerenciamento. É possível também fazer upgrade do serviço fazendo download e instalando as atualizações do Veeam do website do Veeam.

Para instâncias que foram implementadas em liberações anteriores à V1.8, se você quiser usar o serviço Veeam no {{site.data.keyword.cloud}}, deve-se substituir a VSI do Veeam existente nas instâncias. 
Para obter mais informações, consulte a seção _Substituindo a VSI do Veeam de instâncias pré-V1.8 pelo Veeam on IBM
Cloud_ neste tópico.

## Acessando o console do Veeam usando RDP

Para gerenciar o serviço Veeam on {{site.data.keyword.cloud_notm}}, acesse o console do Veeam concluindo as etapas
a seguir:
1. Use o Remote Desktop Protocol (RDP) para se conectar ao endereço IP do Windows.
2. Efetue login no console do Windows usando as credenciais do administrador.
3. Acesse o console do Veeam no console do Windows usando as credenciais do administrador.

É possível localizar o endereço IP do Windows e as credenciais do administrador na página de detalhes do serviço Veeam on {{site.data.keyword.cloud_notm}}.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](../vcenter/vc_addingremovingservices.html)

## Fazendo backup e restaurando componentes de gerenciamento para instâncias que possuem o Veeam no IBM Cloud instalado

O serviço Veeam on {{site.data.keyword.cloud_notm}} é pré-configurado com uma tarefa de backup que é executada
automaticamente. Essa tarefa faz backup dos componentes de gerenciamento diariamente com até 14 pontos de restauração.

É possível também fazer backup dos componentes de gerenciamento manualmente usando o console do Veeam.

Para instâncias implementadas na V1.8 ou em liberações mais recentes (ou que passaram por upgrade para elas), as mudanças de configuração
para o seu ambiente não são automaticamente submetidas a backup. Portanto, antes de mudar a configuração do seu ambiente, é
recomendado que você faça backup dos componentes de gerenciamento manualmente executando a tarefa de backup de
gerenciamento pré-configurada no console do Veeam. Para obter mais informações sobre como fazer backup manualmente, consulte
as [Instruções técnicas do Veeam](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}.

Quando ocorrem falhas nos componentes de gerenciamento, é possível restaurar os componentes de gerenciamento para um backup anterior usando o console do Veeam. 
Para obter mais informações sobre como restaurar manualmente, consulte as
[Instruções
técnicas do Veeam]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}.

## Aplicando atualizações ao Veeam on IBM Cloud

Você é responsável pela manutenção do Veeam para mantê-lo atualizado com a versão mais recente. Para fazer upgrade do Veeam para a versão
mais recente, faça download das atualizações do Veeam no website do Veeam, copie as atualizações para a VSI do Veeam e, em seguida,
instale-as.

## Substituindo a VSI do Veeam de instâncias anteriores à V1.8 por Veeam no IBM Cloud

O serviço Veeam no {{site.data.keyword.cloud_notm}}, que pode fazer backup dos componentes de gerenciamento e das cargas de trabalho, suplanta a VSI do Veeam anterior que foi integrado ao VMware Cloud Foundation e ao VMware vCenter Server em liberações anteriores à V1.8 apenas para o backup de componentes de gerenciamento.

Por causa dessa mudança, a guia **Backup e restauração** anterior na página de detalhes da instância
foi removida e os pontos de backup para as instâncias não estão mais disponíveis no
console do {{site.data.keyword.vmwaresolutions_short}}, embora a VSI do Veeam nas instâncias pré-V1.8 continuem
funcionando.

Deve-se criar um chamado de suporte do {{site.data.keyword.cloud_notm}} para obter assistência com uma restauração. Além disso, a licença da VSI do Veeam em instâncias anteriores à V1.8 expirou em 14 de outubro de 2017. Portanto, deve-se substituir a VSI do Veeam anterior pelo novo serviço Veeam no {{site.data.keyword.cloud_notm}}.

Conclua as etapas a seguir:
1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda e, em seguida, clique na instância de destino.
2. Na página de detalhes da instância, clique na guia **Atualização e Correção**. Assegure-se de ter feito upgrade da instância para a liberação V1.8.
3. Clique na guia **Serviços**.
4. Na guia **Incluir serviços**, instale o serviço Veeam no {{site.data.keyword.cloud_notm}}.

Depois que o novo serviço Veeam no {{site.data.keyword.cloud_notm}} é implementado e um backup bem-sucedido dos componentes de gerenciamento é concluído, é possível remover a VSI do Veeam existente de sua conta criando um chamado de suporte do {{site.data.keyword.cloud_notm}}. O Suporte IBM identificará e excluirá a VSI do Veeam existente e o armazenamento.

## Links relacionados

* [Veeam no {{site.data.keyword.cloud_notm}} visão geral](veeam_considerations.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [Website Veeam.com](https://www.veeam.com/)
* [Documentação técnica do Veeam](https://www.veeam.com/documentation-guides-datasheets.html)
