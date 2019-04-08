---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-06"

subcollection: vmwaresolutions


---

# Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation
{: #sd_addingremovingservices}

É possível pedir serviços para suas instâncias do VMware Cloud Foundation, como uma solução de recuperação de desastre. Quando você não precisar mais desses serviços, será possível removê-los de suas instâncias.

## Serviços disponíveis para instâncias do Cloud Foundation
{: #sd_addingremovingservices-available-services}

A tabela a seguir mostra os serviços que estão disponíveis para instâncias do Cloud Foundation, junto com as versões de serviço instaladas.

Tabela 1. Serviços disponíveis para instâncias do Cloud Foundation

| Nome do Serviço | Versão do serviço atual | Versão da instância |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | BIG-IP VE v14.1.0.2 | V1.9 e mais recentes |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)       | Série 300 | V1.8 e mais recentes |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | 6.0.3 | V2.0 e mais recentes |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)              | 5.4.2 | V2.3 e mais recentes |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)              | 4.2.1 | V2.3 e mais recentes |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations) | 4.2 | V2.5 e mais recente |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)  | 10.1.2 | V2.2 e mais recentes |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) |  2.0 | N/A |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | 9.5u4 | V1.8 e mais recentes |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | 6,5 de atualização 3 | V1.2 e mais recentes |

## Procedimento para incluir serviços em instâncias do Cloud Foundation
{: #sd_addingremovingservices-adding-procedure}

Para incluir um serviço em sua instância do Cloud Foundation, clique no link de serviço apropriado na tabela anterior para revisar as considerações para o serviço e verifique os componentes que estão implementados. Depois, siga as instruções no tópico apropriado de serviços de solicitação para incluir o serviço em sua instância.

### Resultados da instalação de serviço
{: #sd_addingremovingservices-adding-results}

Quando a instalação do serviço for concluída com êxito, você será notificado por e-mail e o serviço será exibido na página **Serviços** da instância com o status **Instalado**.

## Procedimento para visualizar serviços para instâncias do Cloud Foundation
{: #sd_addingremovingservices-viewing-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do Cloud Foundation**, clique na instância para a qual você deseja visualizar serviços.
3. Clique em **Serviços** na área de janela de navegação esquerda.
4. Na página **Serviços**, clique em um serviço para revisar informações sobre ele, como o status de serviço e outros detalhes.
5. Dependendo do serviço visualizado, é possível acessar os consoles de serviço usando as credenciais fornecidas nos detalhes do serviço e gerenciar o serviço por meio deles.

## Procedimento para remover serviços para instâncias do Cloud Foundation
{: #sd_addingremovingservices-removing-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do Cloud Foundation**, clique na instância para a qual você deseja remover serviços.
3. Clique em **Serviços** na área de janela de navegação esquerda.
4. Na página **Serviços**, localize a instância de serviço que você deseja remover e clique no ícone **Excluir**.
5. Na janela **Excluir serviços**, revise as considerações ou os avisos, se houver algum. Selecione **Eu entendo** e clique em **Excluir**.

### Resultados da remoção de serviço
{: #sd_addingremovingservices-removing-results}

Depois que sua solicitação para remoção do serviço for aceita, o status do serviço mudará para **Removendo**.

Quando a remoção do serviço for concluída com êxito, você será notificado por e-mail e o serviço será removido da página **Serviços** da instância.

Você é faturado até o término do ciclo de faturamento do {{site.data.keyword.cloud_notm}} para os serviços removidos.
{:note}

## Links relacionados
{: #sd_addingremovingservices-related}

* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
