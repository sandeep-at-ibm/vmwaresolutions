---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: shared order resource, order on demand shared, order on demand resources

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo o Shared On-demand
{: #shared_ordering_ondemand}

O {{site.data.keyword.vmwaresolutions_full}} Shared é fornecido como uma oferta experimental.
{:note}

Para o On-demand, a vCPU e a RAM de data center virtual são alocadas conforme necessário e podem variar na quantia de tempo que a alocação demora, dependendo do uso global do consumo de vCPU e de RAM de data center virtual.
* Os limites que são estabelecidos para a quantia de vCPU e RAM são valores máximos que podem ser consumidos a qualquer momento.
* Os recursos de vCPU e RAM podem ser aumentados e diminuídos posteriormente, conforme necessário.
* O custo é calculado de hora em hora e é baseado no uso de recurso no data center virtual.
* Não há limites sobre a quantia de armazenamento que pode ser alocada e usada no data center virtual. Os encargos são de hora em hora com base em GB de armazenamento alocado.
* Não há limites sobre a quantia de rede pública de entrada e de saída. A largura da banda pública é cobrada por GB.

## Requisitos para o IBM Cloud for VMware Solutions Shared
{: #shared_ordering_ondemand-req}

### Conta de infraestrutura do IBM Cloud
{: #shared_ordering_ondemand-account-req}

Para usar o {{site.data.keyword.vmwaresolutions_short}} para pedir o IBM Cloud for VMware Solutions Shared, deve-se ter uma conta de **Pagamento conforme o uso** ou **Assinatura**{{site.data.keyword.cloud_notm}}. O custo dos recursos que são pedidos é faturado para essa conta do {{site.data.keyword.cloud_notm}}.

### Requisitos de nome do data center virtual
{: #shared_ordering_ondemand-vdc-name-req}

O nome do data center virtual *deve* atender aos requisitos a seguir. Os requisitos de nomenclatura serão cumpridos no futuro.
* Somente caracteres alfabéticos minúsculos, numéricos e de traço (-) são permitidos.
* O nome deve começar com um caractere alfabético minúsculo.
* O nome deve terminar com um caractere alfabético minúsculo ou numérico.
* O comprimento máximo do nome do data center virtual é de 10 caracteres.
* O nome do data center virtual deve ser exclusivo dentro de sua conta.

## Procedimento para pedir o Shared On-demand
{: #shared_ordering_ondemand-procedure}

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique no ícone **VMware** na área de janela de navegação esquerda e, em seguida, clique no cartão **IBM Cloud for VMware Solutions Shared** na seção **VMware Virtual Data Centers**.
2. Na página **IBM Cloud for VMware Solutions Shared**, clique no cartão **On-demand** e clique em **Criar**.
3. Na página **IBM Cloud for VMware Solutions Shared - On-demand**, insira o nome do data center virtual. O {{site.data.keyword.CloudDataCent_notm}} no qual a oferta está disponível é pré-selecionado.
4. Selecione os limites de vCPU e RAM de acordo com seus requisitos.
5. Na área de janela **Resumo do pedido**, verifique a configuração e o custo estimado antes de fazer o pedido.
6. Clique em **Provisão**.

## Resultados depois de pedir o Shared On-demand
{: #shared_ordering_ondemand-results}

* A implementação dos recursos é iniciada automaticamente e você recebe a confirmação de que o pedido está sendo processado. É possível verificar o status da implementação, incluindo quaisquer problemas que possam requerer sua atenção, visualizando o **Status do Virtual Data Center**.
* Quando os recursos são implementados com êxito, os componentes que estão descritos em [Especificações técnicas para o {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview#shared_overview-specs) são instalados em sua plataforma virtual VMware.
* Quando os recursos estiverem prontos para uso, o status será mudado para **Pronto para uso**.

## Links relacionados
{: #shared_ordering_ondemand-related}

* [Visão geral do {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Pedindo o Shared Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [Gerenciando o {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_managing)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}
