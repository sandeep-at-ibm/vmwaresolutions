---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Pedindo o IBM Spectrum Protect Plus on IBM Cloud

É possível pedir o serviço {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} ao pedir uma nova instância com o serviço incluído ou incluindo o serviço em sua instância existente.

## Pedindo o IBM Spectrum Protect Plus on IBM Cloud para uma nova instância

É possível pedir uma nova instância com o IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, quando você pedir uma nova instância, selecione **IBM Spectrum Protect Plus on IBM Cloud** na seção **Serviços**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione o **IBM Spectrum Protect Plus on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em nova instância**.

## Pedindo o IBM Spectrum Protect Plus on IBM Cloud para uma instância existente

É possível incluir o serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} em uma instância existente usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **IBM Spectrum Protect Plus on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em instância existente**.

## Configuração do serviço IBM Spectrum Protect Plus on IBM Cloud

Quando você pedir o serviço, forneça as configurações a seguir.

### Número de volumes de armazenamento

O número de volumes que atendem as necessidades de armazenamento.

### Tamanho de armazenamento por volume

A capacidade de armazenamento por volume.

### Desempenho de Armazenamento

As IOPS (Input/output Operations Per Second) por GB com base em seus requisitos de carga de trabalho.
* Se desejar pedir licenças para o IBM Spectrum Protect Plus, especifique o **Número de MVs a serem licenciadas** na guia **Pedir licenças**.
* Se você deseja usar Bring Your Own License (BYOL), clique na guia **Licenças do IBM Spectrum Protect Plus** e, em seguida, clique em **Incluir arquivos de licença** para fazer upload dos arquivos de licença do IBM Spectrum Protect Plus que você possui.

## Processo de implementação para o IBM Spectrum Protect Plus no IBM Cloud

A implementação do IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}} é automatizada. Quer você peça uma instância com esse serviço incluído, quer implemente o serviço posteriormente em sua instância, as etapas a seguir são concluídas pelo processo de automação do {{site.data.keyword.vmwaresolutions_short}}:

1. Com base nas configurações que você especificar, o armazenamento NFS do Endurance é pedido da infraestrutura do
{{site.data.keyword.cloud_notm}} para o repositório de backup do IBM Spectrum Protect Plus.
2. Com base nas configurações que você especificar, um número de licenças para o IBM Spectrum Protect Plus é pedido por meio da
infraestrutura do {{site.data.keyword.cloud_notm}}. As licenças são pedidas em incrementos de 10 pacotes de licença de máquina virtual (MV), com base no número de MVs que você especificou para licenciar ao pedir o serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. Se você quiser trazer uma licença existente do IBM Spectrum Proteger Plus, nenhum pedido
de licença será realizado por meio da infraestrutura do {{site.data.keyword.cloud_notm}}.
3. O armazenamento NFS pedido para esse serviço é montado em todos os servidores ESXi no cluster padrão da
instância, incluindo rotas estáticas corretas em cada servidor ESXi para a sub-rede privada de armazenamento.
4. Armazenamentos NFS são criados no vCenter Server para todos os volumes de armazenamento NFS que são montados para os
servidores ESXi.
5. As MVs do IBM Spectrum Protect Plus são implementadas, ativadas e configuradas no cluster padrão da instância.
6. O armazenamento NFS que foi pedido para esse serviço é conectado à MV do IBM Spectrum Protect Plus e o repositório
de backup é configurado.
7. O nome do host e o endereço IP da MV do IBM Spectrum Protect Plus são registrados com o servidor DNS da instância.

### Links relacionados

* [IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}} visão geral](/docs/services/vmwaresolutions/services/spp_considerations.html)
* [Planejamento de serviço preventivo do IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gerenciando o IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managingspp.html)
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter/vc_hybrid_addingremovingservices.html)
* [Documentação do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
