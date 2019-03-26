---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gerenciando o Caveonix RiskForesight no IBM Cloud
{: #managingcaveonix}

## Acessando o console do Caveonix RiskForesight
{: #managingcaveonix-access-console}

Para gerenciar o serviço Caveonix RiskForesight on {{site.data.keyword.cloud}}, deve-se acessar o console do Caveonix RiskForesight concluindo as etapas a seguir:

1. Use a VPN de infraestrutura do IBM Cloud ou um servidor de salto para permitir acesso ao endereço IP da máquina virtual (VM) do Caveonix RiskForesight. É possível localizar o endereço IP na página de detalhes do serviço para o Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} no console do {{site.data.keyword.vmwaresolutions_short}}. Para ser específico:
   1. Crie uma senha de VPN por meio do portal do cliente de infraestrutura do {{site.data.keyword.cloud_notm}}.
   2. Efetue login no portal de VPN do data center usando as credenciais de VPN de infraestrutura do {{site.data.keyword.cloud_notm}}.
   3. Inclua o endereço IP e o mapeamento de nome do host em seu arquivo de hosts locais usando o formato a seguir:

      ```javascript
      IPAddress              HostName
      ```
2. Para acessar o console do Caveonix RiskForesight, clique em **Visualizar console do RiskForesight** na página de detalhes do serviço para o Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} e, em seguida, efetue login usando as credenciais listadas na mesma página de detalhes do serviço.

## Aplicando atualizações ao Caveonix RiskForesight no IBM Cloud
{: #managingcaveonix-update}

Você é responsável pela manutenção do Caveonix RiskForesight para mantê-lo atualizado para a versão mais recente. É possível fazer download das atualizações necessárias por meio do [Portal do provedor de serviços do Caveonix](https://support.caveonix.com).

## Atualizando licenças do Caveonix RiskForesight

A licença do Caveonix RiskForesight é válida por um ano. É possível atualizar a licença do Caveonix RiskForesight quando ela expira usando o procedimento a seguir:
1. Peça uma nova licença do Caveonix RiskForesight e copie-a para o console do Caveonix RiskForesight. Para obter mais informações, consulte [Procedimento para pedir licenças do Caveonix RiskForesight](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_ordering#caveonix_license_ordering-procedure).
2. Exclua a licença expirada da tabela **Licenças do Caveonix RiskForesight** no console do {{site.data.keyword.vmwaresolutions_short}}. Para obter mais informações, consulte [Procedimento para excluir licenças do Caveonix RiskForesight](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_managing#caveonix_license_managing_procedure-delete).

## Links relacionados
{: #managingcaveonix-related}

* [ RiskForesight do Caveonix RiskForesight em  {{site.data.keyword.cloud_notm}}  visão geral ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [ Pedindo o Caveonix RiskForesight no  {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
