---

copyright:

  years:  2016, 2018

lastupdated: "2017-05-22"

---

# Notas sobre a liberação para V1.6

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em liberações diferentes, problemas conhecidos com o produto e dicas adicionais para usar o {{site.data.keyword.vmwaresolutions_full}}, veja o [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Atualizações para instâncias do VMware Cloud Foundation

Os componentes a seguir são novos ou atualizados:

*  SDDC Manager 2.2.1
*  Componentes de gerenciamento IBM V1.6
*  Novas especificações de hardware: **Pequeno** ou **Padrão**, dependendo de seus requisitos.
*  Novos data centers disponíveis para implementação: **HKG02 - Hong Kong**, **OSL01 - Oslo**, **SEO01 - Seul**, **SNG01 - Singapura** e **SYD04 - Sydney**.

Para obter uma lista completa de componentes, veja [Visão geral do VMware Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

## Atualizações para instâncias do VMware vCenter Server

### Aprimoramentos de hardware para instâncias do vCenter Server

Começando com a liberação V1.6, vários aprimoramentos estão disponíveis para suas instâncias do vCenter Server.

*  Implementação integral da especificação da V2.0 para a oferta do vCenter Server. Para obter mais informações, veja a [arquitetura de solução do VMware vCenter Server on IBM Cloud](https://www.ibm.com/devops/method/content/architecture/virtualizationArchitecture#2_0).
*  Novas especificações de hardware: **Pequeno**, **Médio** ou **Grande**, dependendo de seus requisitos.
*  Novos data centers disponíveis para implementação: **HKG02 - Hong Kong**, **OSL01 - Oslo**, **SEO01 - Seul**, **SNG01 - Singapura** e **SYD04 - Sydney**.
*  Pelo menos dois servidores ESXi em seu pedido de instância, com VMware vSphere DRS (Distributed Resource Scheduler) e VMware HA (Alta Disponibilidade) ativados por padrão.
*  Até sete compartilhamentos de arquivos NFS poderão ser incluídos quando você pedir instâncias. Agora, os componentes de gerenciamento (vCenter, PSC, NSX Manager e Controllers, CloudDriver) estão em execução em um compartilhamento de arquivo NFS para alta disponibilidade.
*  Implementação automática e configuração do VMware NSX Edge Services Gateway gerenciado pelo cliente.

Por causa dessas mudanças, não é possível usar no estado em que se encontra (ou fazer upgrade) suas instâncias existentes do vCenter Server na liberação atual. As instâncias do vCenter Server de liberações pré-V1.6 ainda são visíveis no console do {{site.data.keyword.vmwaresolutions_short}} em modo somente de visualização. Estas instâncias são marcadas na interface com o usuário como **Descontinuadas** com um ícone de símbolo de aviso.

As ações a seguir estão disponíveis nas instâncias do vCenter Server pré-V1.6:

*  Visualize as informações na página de detalhes da instância. As informações que são exibidas nas propriedades da instância refletem os dados a partir da data de liberação da V1.6 e não são mais atualizadas.
*  Abra o VMware vSphere Web Client e use a instância no vCenter.
*  Excluir instância.

Todas as outras ações em instâncias pré-V1.6 não estão mais disponíveis.

### Aprimoramentos de rede para instâncias do vCenter Server

*  Uma sub-rede pública com 16 endereços IP na VLAN pública é pedida em seu nome para permitir que suas VMs (máquinas virtuais) acessem a Internet.
*  Uma sub-rede privada com 64 endereços IP na VLAN privada é pedida em seu nome para permitir que suas VMs acessem a rede interna do SoftLayer®.
*  Controladores NSX são implementados com regras antiafinidade e executados em servidores ESXi separados em uma configuração de implementação de 3 nós.
*  Novo VMware NSX Edge Services Gateway para uso do cliente.

   Agora, um NSX Edge Services Gateway (ESG) adicional é implementado como parte das novas instâncias do vCenter Server que você está pedindo.

   Esse ESG é fornecido para ser usado com as suas próprias VMs para comunicações entre as sub-redes privadas e públicas que são pedidas em seu
   nome e ele inclui duas interfaces: uma interface é conectada às VXLANs virtualizadas associadas às suas VMs e a
   outra é conectada à VLAN pública. Além disso, as configurações a seguir são definidas:
   *  Regra de firewall para permitir todo o tráfego de saída do intervalo de sub-rede privada de endereços IP.
   *  Regra SNAT (Source Network Address Translation) (desativada por padrão) para converter todos os endereços IP da sub-rede privada em um
   único endereço IP na sub-rede pública.
   * VMware HA (Alta Disponibilidade) está configurado para usar um novo grupo da porta que é compartilhado entre o ESG de gerenciamento e o ESG
   gerenciado pelo cliente.

   Esse ESG é implementado para todos os tipos de hardware da instância e os clientes podem modificar a configuração. Para obter mais informações, veja os tópicos a seguir:
   *  [Configurando sua rede para usar o NSX Edge Services Gateway gerenciado pelo cliente com suas VMs](../vcenter/vc_esg_config.html)
   *  [Documentação do VMware NSX](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Aprimoramentos de usabilidade

São feitas melhorias em toda a interface com o usuário:

*  A navegação principal no console é muito melhorada por meio da introdução da área de janela de navegação esquerda com acesso a todas as áreas da interface com o usuário. É possível pedir rapidamente uma nova instância, visualizar as instâncias implementadas, revisar notificações do sistema, mudar configurações e acessar a documentação on-line.
*  A nova página **Introdução** acessível na área de janela de navegação esquerda fornece detalhes suficientes diretamente no console para ajudá-lo a tomar uma decisão informada sobre os componentes da instância que você está pedindo. Na página **Introdução**, você também é guiado passo a passo pelo processo de pedido de uma instância, começando com atender a todos os pré-requisitos para pedir uma instância, como contas de usuário necessárias e terminando com fazer um pedido.
*  Os detalhes do resumo para as instâncias do Cloud Foundation e do vCenter Server são consolidados em uma única página, que é acessível no menu **Instâncias Implementadas** na área de janela de navegação esquerda. Nessa página, é possível selecionar a guia apropriada para filtrar as instâncias do Cloud Foundation ou do vCenter Server.
* Se você tiver a recuperação de desastre do Zerto instalada em sua instância, será possível acessar o console do Zerto na página de detalhes do serviço diretamente com um único clique. Para obter mais informações, veja [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](../sddc/sd_addingremovingservices.html) e [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](../vcenter/vc_addingremovingservices.html).
