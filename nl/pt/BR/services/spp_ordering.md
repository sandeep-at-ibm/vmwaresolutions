---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-15"

---

# Pedindo o IBM Spectrum Protect Plus on IBM Cloud

É possível pedir o IBM Spectrum Protect Plus no serviço do {{site.data.keyword.cloud}} durante o pedido de
uma nova instância com o serviço incluído ou incluindo o serviço em sua instância existente.

## Pedindo o IBM Spectrum Protect Plus on IBM Cloud para uma nova instância

É possível pedir uma nova instância com o IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_full}}, quando você pedir uma nova instância, selecione **IBM Spectrum Protect Plus on IBM Cloud** na seção **Serviços**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **Serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}**, especifique as configurações de serviço e selecione **Incluir em nova instância**.

## Pedindo o IBM Spectrum Protect Plus on IBM Cloud para uma instância existente

É possível incluir o serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} em uma instância existente usando um dos métodos a seguir:
* No console do {{site.data.keyword.vmwaresolutions_short}}, visualize a instância para a qual você deseja incluir o serviço, clique em **Serviços** na área de janela de navegação esquerda e clique em **Incluir serviço**.
* No catálogo do {{site.data.keyword.cloud_notm}}, selecione **Serviço IBM Spectrum Protect Plus on IBM Cloud**, especifique as configurações de serviço e selecione **Incluir em instância existente**.

## Configuração do serviço IBM Spectrum Protect Plus on IBM Cloud

Quando você pedir o serviço, forneça as configurações a seguir.

### Número de volumes de armazenamento

O número de volumes que atendem as necessidades de armazenamento.

### Tamanho de armazenamento por volume

A capacidade de armazenamento por volume. É necessário um mínimo de 500 GB por volume para gerenciamento.

### Desempenho de Armazenamento

As IOPS (Input/output Operations Per Second) por GB com base em seus requisitos de carga de trabalho.
* Se desejar pedir licenças para o IBM Spectrum Protect Plus, especifique o **Número de VMs a serem licenciadas** na guia **Pedir licenças**. 
Um mínimo de 10 máquinas virtuais (VMs) é necessário para o gerenciamento de licença.
* Se você deseja usar Bring Your Own License (BYOL), clique na guia **Licenças do IBM Spectrum Protect Plus** e, em seguida, clique em **Incluir arquivos de licença** para fazer upload dos arquivos de licença do IBM Spectrum Protect Plus que você possui.

## Processo de implementação para o IBM Spectrum Protect Plus no IBM Cloud

A implementação do IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}} é automatizada. Quer você peça uma instância com esse serviço incluído, quer implemente o serviço posteriormente em sua instância, as etapas a seguir são concluídas pelo processo de automação do {{site.data.keyword.vmwaresolutions_short}}:

1. Com base nas configurações que você especificar, o armazenamento NFS do Endurance é pedido da infraestrutura do
{{site.data.keyword.cloud_notm}} para o repositório de backup do IBM Spectrum Protect Plus.
2. Com base nas configurações que você especificar, um número de licenças para o IBM Spectrum Protect Plus é pedido por meio da
infraestrutura do {{site.data.keyword.cloud_notm}}. As licenças são pedidas em incrementos de 10 pacotes de
licença de VM, com base no número de VMs que você especificou para a licença quando pediu o serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. Se você quiser trazer uma licença existente do IBM Spectrum Proteger Plus, nenhum pedido
de licença será realizado por meio da infraestrutura do {{site.data.keyword.cloud_notm}}.
3. O armazenamento NFS pedido para esse serviço é montado em todos os servidores ESXi no cluster padrão da
instância, incluindo rotas estáticas corretas em cada servidor ESXi para a sub-rede privada de armazenamento.
4. Armazenamentos NFS são criados no vCenter Server para todos os volumes de armazenamento NFS que são montados para os
servidores ESXi.
5. A VM do IBM Spectrum Protect Plus é implementada, ativada e configurada no cluster padrão da instância.
6. O armazenamento NFS que foi pedido para esse serviço é conectado à VM do IBM Spectrum Protect Plus e o repositório
de backup é configurado.
7. O nome do host e o endereço IP da VM do IBM Spectrum Protect Plus são registrados com o servidor DNS da instância.
8. (Para instâncias V2.3 e mais recentes) Uma tarefa de backup de gerenciamento padrão é criada no IBM Spectrum Protect Plus. Para obter mais informações, veja [Gerenciando o IBM Spectrum Protect Plus on IBM Cloud](managingspp.html).

## Links relacionados

* [IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}} visão geral](spp_considerations.html)
* [Planejamento de Serviços Preventivos do IBM Spectrum Protect Plus no IBM Cloud](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gerenciando o IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Documentação do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
