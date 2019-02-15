---

copyright:

  years:  2016, 2019

lastupdated: "2017-08-28"

---

# Notas sobre a liberação para V1.8

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Serviço Fortinet on IBM Cloud

O serviço Fortinet on {{site.data.keyword.cloud_notm}} está agora disponível para as instâncias do Cloud Foundation e do vCenter Server. Este serviço implementa um par de dispositivos FortiGate Security Appliance (FSA) série 300 em um modo altamente disponível para fornecer serviços de firewall, roteamento, NAT e VPN para proteger todos os servidores e máquinas virtuais na VLAN pública de suas instâncias. É possível pedir instâncias com o serviço Fortinet incluído quando você pede sua instância ou incluir esse serviço em suas instâncias existentes posteriormente na página de detalhes da instância.

Depois que o serviço Fortinet for instalado com êxito, será possível gerenciar e configurar regras de firewall para o FSA do console do FortiGate. Deve-se assegurar que as regras de firewall do FSA sejam definidas para permitir comunicações HTTPS de saída que são iniciadas por componentes de gerenciamento como a máquina virtual do IBM CloudDriver ou o Zerto Virtual Manager para se comunicar com o banco de dados de gerenciamento externo no IBM Bluemix® pela Internet. As comunicações HTTPS de saída se originam do endereço IP público dos serviços de gerenciamento do VMware NSX Edge Services Gateway (ESG) em sua instância.

Para obter mais informações, veja os tópicos a seguir:
* [Visão geral do Fortinet on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fsa_considerations.html)
* [ Gerenciando o Fortinet no  {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/services/managingfsa.html)

## Serviço Veeam on IBM Cloud

Esta liberação apresenta o serviço Veeam on {{site.data.keyword.cloud_notm}}, que pode fazer backup dos componentes de gerenciamento e das cargas de trabalho. O novo serviço suplanta o VSI Veeam anterior que foi integrado em liberações anteriores à V1.8 para backup apenas dos componentes de gerenciamento.

Por causa dessa mudança, embora o VSI Veeam nas instâncias pré-V1.8 continue funcionando, os pontos de backup para as instâncias não estão mais disponíveis no console do {{site.data.keyword.vmwaresolutions_short}} e deve-se criar um chamado de suporte para obter assistência com uma restauração.

Além disso, a licença do VSI Veeam em instâncias anteriores à V1.8 expira em 14 de outubro de 2017. Portanto, deve-se substituir o VSI Veeam anterior pelo novo serviço Veeam em sua primeira conveniência.

Para obter mais informações, veja os tópicos a seguir:
* [Veeam no {{site.data.keyword.cloud_notm}} visão geral](/docs/services/vmwaresolutions/services/veeam_considerations.html)
* [Gerenciando o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/managingveeam.html)

## Atualizações para instâncias do VMware Cloud Foundation

### Traga suas próprias licenças do VMware (BYOL) ao pedir instâncias do Cloud Foundation

Começando com a liberação V1.8, quando você está pedindo uma instância do Cloud Foundation, são fornecidas a você duas opções para licenciamento dos componentes do VMware da instância, incluindo vSphere, vCenter Server, NSX e vSAN. É possível selecionar para usar novas licenças que devem ser compradas em seu nome.

É possível também escolher usar sua própria licença do VMware para um componente, neste caso é solicitado que você forneça as chaves de licença. Nesse caso, o suporte para os componentes do VMware para os quais você fornece licenças será fornecido pelo VMware, não pelo Suporte IBM.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)
* [Pergunta mais frequente sobre BYOL](/docs/services/vmwaresolutions/vmonic/faq_byol.html)

## Atualizações para instâncias do VMware vCenter Server

### Customizar a CPU e a memória da instância

Uma opção do servidor customizável está disponível junto com as opções Pequeno, Médio e Grande pré-construídas e testadas. É possível selecionar em uma lista de servidores do VMware compatíveis com HCL com base em CPUs duais e no número total de núcleos, além da quantidade de RAM. O armazenamento local não é customizável.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [Incluindo e visualizando clusters para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)

### Suporte para incluir mais de 7 compartilhamentos de arquivos do NFS

 É possível anexar até um máximo de 32 compartilhamentos de arquivos em todos os servidores ESXi em um cluster.

 Para obter mais informações, veja os tópicos a seguir:
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [Incluindo e visualizando clusters para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)

### Atualizações para data centers

Os novos data centers a seguir estão disponíveis para implementação: **DAL-09, DAL-12, DAL-13 - Dallas**; **LON-04, LON-06 - Londres**; **SJC-04 - San Jose**; **WDC-06, WDC-07 - Washington, DC**

Para obter mais informações, veja [Requisitos e planejamento para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_planning.html)

## Aprimoramentos de usabilidade

São feitas melhorias em toda a interface com o usuário:
* É possível aprender sobre serviços e pedir uma instância na página **Introdução** na área de janela de navegação esquerda.
* Use o menu overflow na página de detalhes da instância para excluir uma instância no estado **Pronto para Usar**.
* A opção para fazer upgrade em sua edição de licença do NSX está disponível na guia **Atualização e Correção**. O upgrade de licença substitui todas as licenças existentes do NSX em sua conta IBM SoftLayer pela nova licença.
* A guia **Backup e Restauração** na página de detalhes da instância não está mais disponível.
* É possível selecionar vários serviços para implementar no início de um pedido. Além do serviço Zerto on {{site.data.keyword.cloud_notm}}, as opções para selecionar o serviço Veeam on {{site.data.keyword.cloud_notm}} e o serviço Fortinet on {{site.data.keyword.cloud_notm}} também estão disponíveis.
* A guia **Serviços Disponíveis** na guia **Serviços** na página de detalhes da instância é renomeada para **Incluir Serviços**.
