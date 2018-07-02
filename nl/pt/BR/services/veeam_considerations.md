---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Veeam on IBM Cloud Visão Geral

O serviço Veeam no {{site.data.keyword.cloud}} se integra continuamente diretamente com os hypervisors do VMware para ajudar sua empresa a alcançar alta disponibilidade. Este serviço pode fornecer pontos de recuperação e objetivos de tempo para seus aplicativos e dados. Os pontos de recuperação e os objetivos de tempo podem ser fornecidos em menos de 15 minutos após a conclusão da configuração. Ao usar esse serviço, é possível controlar diretamente o backup e a restauração de todas as máquinas virtuais para sua infraestrutura do console do Veeam.

**Disponibilidade**: esse serviço está disponível somente para instâncias implementadas na V1.8 ou liberações mais recentes.

## Componentes do Veeam no IBM Cloud

Os componentes a seguir são pedidos e incluídos no serviço Veeam no {{site.data.keyword.cloud_notm}}:
* Um VSI do Windows Server 2016 com um endereço IP privado primário e 1 GbE de interface
* {{site.data.keyword.cloud_notm}} O armazenamento de bloco de resistência do tamanho e desempenho que você seleciona quando pede o serviço

## Considerações ao instalar o Veeam no IBM Cloud

* O serviço faz backup dos componentes de gerenciamento a seguir:
  - VMware vCenter Server
  - Platform Services Controller (PSC)
  - IBM CloudDriver
  - **Somente instâncias do Cloud Foundation**: VMware SDDC Manager
  - **Instâncias do vCenter Server somente com HA AD/DNS**: par de alta disponibilidade de servidores AD/DNS

* As configurações dos servidores ESXi não têm backup feito pelo serviço Veeam no {{site.data.keyword.cloud_notm}}.

* Por padrão, as configurações do NSX Controller e do NSX Edge têm backup feito diariamente usando o NSX Manager com até 14 pontos de restauração. Para uma restauração completa das configurações NSX, deve-se criar um chamado de suporte do {{site.data.keyword.cloud_notm}}, pois os backups das configurações NSX são salvos no armazenamento que é interno ao {{site.data.keyword.vmwaresolutions_full}}. Para obter mais informações sobre como gerenciar os backups de configuração NSX usando o NSX Manager, veja as [Instruções técnicas do VMware](https://pubs.vmware.com/NSX-6/index.jsp#com.vmware.nsx.admin.doc/GUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html).
* O repositório para o armazenamento e o servidor Veeam estão no pod original e no data center. Por causa disso, o desempenho das operações de backup para clusters remotos pode se deteriorar.

## Considerações ao remover o Veeam no IBM Cloud

Antes de remover o serviço Veeam no {{site.data.keyword.cloud_notm}}, observe que a remoção desse serviço parará todos os backups (incluindo o backup das VMs de gerenciamento) e excluirá todos os backups anteriores (a exclusão é irreversível). Se as VMs de gerenciamento forem corrompidas subsequentemente, elas não poderão ser restauradas.

## Links relacionados

* [Pedindo o Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [Gerenciando o Veeam no {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [Solicitando serviços gerenciados para o Veeam no {{site.data.keyword.cloud_notm}}](managing_veeam_services.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [Website do Veeam](https://www.veeam.com/){:new_window}
* [Centro de Ajuda do Veeam](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
