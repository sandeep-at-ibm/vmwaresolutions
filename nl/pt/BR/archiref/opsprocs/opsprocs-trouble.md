---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

---

# Solução de Problemas
{: #opsprocs-trouble}

Para solucionar problemas de instâncias do vCenter Server, os administradores de sistema devem identificar os sintomas do problema, determinar quais dos componentes da solução foram afetados, pesquisar e propor uma correção ou uma solução alternativa, além de testar a correção.

* Identificando sintomas - Uma variedade de possíveis causas pode levar ao baixo desempenho ou à falta de desempenho de sua instância. A primeira etapa na resolução de problemas eficiente é identificar exatamente o que está acontecendo. Esses sintomas podem ser relatados por meio de: eventos e alarmes do vSphere, Operations Management in {{site.data.keyword.cloud}} ou relatado por meio da Central de serviço de um de seus usuários.
* Isolando os componentes afetados - Depois de identificar os sintomas do problema, deve-se identificar os componentes de software ou hardware afetados e que possam estar causando o problema e os componentes que não estão envolvidos. Ferramentas como o vCenter Operations Management in {{site.data.keyword.cloud_notm}} ajudam com essa etapa.
* Propondo uma correção ou solução alternativa - Depois de entender os sintomas e isolar os componentes, será possível pesquisar correções e soluções alternativas possíveis. Os administradores de sistema também usam o Portal do {{site.data.keyword.cloud_notm}}, incluindo os cenários de resolução de problemas neste documento, o IBM ServiceNow e o VMware Knowledgebase. Além disso, há muitos wikis e blogs que podem ajudar. Para resoluções ainda mais rápidas, o Operations Management in {{site.data.keyword.cloud_notm}} inclui uma série de correções para problemas identificados.
* Testando soluções possíveis - Quando você sabe quais são os sintomas do problema, quais componentes estão envolvidos e tem uma proposta de correção/solução alternativa, os administradores do seu sistema testam as soluções sistematicamente até que o problema seja resolvido.

O vSphere inclui eventos configuráveis pelo usuário e o subsistema de alarmes, que rastreia eventos que ocorrem em todo o ambiente do vSphere e armazena os dados em arquivos de log e no banco de dados do vCenter. Esse subsistema também permite que os administradores do sistema especifiquem as condições sob as quais os alarmes são acionados. Os alarmes mudam de estado, de avisos a alertas mais sérios, conforme as condições do sistema mudam e podem acionar ações de alarme automáticas, como o envio de e-mail à equipe do administrador do sistema. Essa funcionalidade é útil quando você deseja ser informado ou tomar uma ação imediata quando determinados eventos ou condições ocorrem para um objeto de inventário específico ou um grupo de objetos.

Mais ferramentas, como aquelas incorporadas na arquitetura do Operations Management on {{site.data.keyword.cloud_notm}}, fornecem maior assistência com a identificação de sintomas, o isolamento de componentes afetados e a proposta de uma correção ou uma solução alternativa.

## Diretrizes
{: #opsprocs-trouble-guidelines}

As diretrizes a seguir são consideradas melhores práticas para solucionar problemas do {{site.data.keyword.vmwaresolutions_short}}:
* Aborde a resolução de problemas sistematicamente.
* Os sintomas estão relacionados à disponibilidade, à utilização ou à configuração:
 *  Disponibilidade - Esses sintomas estão relacionados à disponibilidade de componentes de hardware e software e são tipificados por uma ausência de resposta. Geralmente, o design de alta disponibilidade mascara esses problemas para que não afetem as cargas de trabalho e os usuários diretamente.
 * Utilização - Esses sintomas estão relacionados à capacidade e ao desempenho e são tipificados por uma execução lenta ou uma falta de capacidade de carregamento. O gerenciamento proativo da capacidade reduz drasticamente esses problemas.
 * Configuração - Esses problemas são geralmente descobertos na provisão de novos serviços ou como um resultado da aplicação de uma mudança. Configurações incorretas podem surgir como sintomas de disponibilidade ou utilização. Por exemplo, um endereço IP incorreto é exibido como um problema de disponibilidade, enquanto as configurações de RAM da máquina virtual (VM) muito baixas causam sintomas de utilização.
* Tente isolar o problema para um componente no ambiente.
* Tome notas para que seja possível rastrear as etapas realizadas.
* Entenda e documente suas versões de software.
* Documente o uso de suas sub-redes e endereço IP, incluindo os endereços VIP e NAT.
* Tenha diagramas de sua rede. Serão necessários diversos diagramas que mostrem as camadas físicas (de base) e lógicas (sobreposição).
* Entenda quaisquer mudanças recentes no ambiente.
* Pesquise o impacto da correção e não se bloqueie de nenhuma interface de gerenciamento.
* Assegure-se de que tenha backups de todos os principais componentes no caso de precisarem ser recarregados ou reconfigurados.
* Não mude mais de uma coisa por vez.
* Documente cada mudança e seu resultado.
* Ao abrir uma solicitação de suporte, assegure-se de documentar cuidadosamente e fornecer informações pertinentes. Seja claro nos sintomas que você está vendo e identifique os componentes que acredita estar com defeito. Assegure-se de usar a terminologia correta. Tente minimizar qualquer confusão ou ambiguidade em sua escolha de palavras.
* Entenda onde estão os arquivos de configuração do vSphere ESXi e do vCenter Server, pois eles controlam o comportamento do sistema. A maioria das configurações do arquivo de configuração é definida durante a instalação, mas pode ser modificada posteriormente.
* Os arquivos de log capturam mensagens geradas pelo kernel e diferentes subsistemas e serviços. Os serviços vSphere ESXi e vCenter mantêm arquivos de log separados. Entender onde eles estão localizados e como podem ser acessados.
* Entenda como usar as ferramentas populares de administração de sistema para obter ajuda nos diagnósticos.

Para obter mais informações, consulte [Diretrizes de resolução de problemas KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}.

## Resolução de problemas com arquivos de log
{: #opsprocs-trouble-logs}

Os arquivos de log são uma excelente fonte de informações para solucionar problemas. No entanto, o número de arquivos de log e a grande quantia de entradas em cada log dificultam o diagnóstico. [Resolução de problemas com arquivos de log KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window} detalha o local desses arquivos de log no ambiente do VMware. Devido ao número de arquivos de log e ao grande número de entradas em cada log, é necessário considerar o conjunto de ferramentas no Operations Management on {{site.data.keyword.cloud_notm}} para ajudar a capturar e analisar os logs de eventos.

## Cenários comuns de resolução de problemas
{: #opsprocs-trouble-common}

Para ajudar a isolar os componentes afetados, essa documentação sobre cenários comuns de resolução de problemas foi classificada da seguinte forma:

* Máquinas virtuais - esses tópicos de resolução de problemas fornecem orientação sobre possíveis problemas em VMs.
* Hosts - esses tópicos de resolução de problemas fornecem orientação sobre problemas de host do vSphere ESXi.
* Cluster - esses tópicos de resolução de problemas fornecem orientação sobre o gerenciamento de disponibilidade e recursos.
* Armazenamento - esses tópicos de resolução de problemas fornecem orientação sobre como resolver problemas de armazenamento do vSAN e do NFS.
* Rede - esses tópicos de resolução de problemas fornecem orientação sobre como resolver problemas de rede.
* vCenter - esses tópicos de resolução de problemas fornecem orientação sobre como resolver problemas do vCenter.
* Licenças - esses tópicos de resolução de problemas fornecem orientação sobre como resolver problemas de licença. Geralmente, esses problemas se relacionam a clientes que trouxeram suas próprias licenças para o {{site.data.keyword.cloud_notm}}.

### Máquinas virtuais
{: #opsprocs-trouble-common-vm}

Tabela 1. Resolução de problemas de máquina virtual

| Título | Descrição |
|---|---|
| Resolução de problemas genéricos da VM | Para obter mais informações, consulte [Resolução de problemas de máquinas virtuais](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window}. |
| Problemas de desempenho da VM | Para obter informações sobre como solucionar os sintomas de problemas de desempenho da VM, incluindo inicializações lentas do S.O. guest, execução insatisfatória dos aplicativos, tempo muito longo de ativação dos aplicativos ou não resposta dos aplicativos, consulte [Resolução de problemas de desempenho da máquina virtual ESX/ESXi (2001003)](https://kb.vmware.com/s/article/2001003){:new_window}. |
| Recuperar VM órfã | Para obter informações sobre a recuperação de VMs órfãs que existem no banco de dados do vCenter, mas que não são reconhecidas pelo host do vSphere ESXi, consulte [Conhecimento - KB0012862 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=57c90b74dbdd7300c4fa302f9d96199e){:new_window}. |
| A VM não liga | Para obter mais informações, consulte [Resolução de problemas de uma máquina virtual que não inicializa (2001005)](https://kb.vmware.com/s/article/2001005){:new_window}. |
| A VM não liga após a clonagem ou implementação por meio de um modelo | O [artigo do VMware](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2742CE14-20FD-416F-B89C-A156053A973F.html){:new_window} verifica os problemas que afetam uma VM após ela ter sido clonada ou implementada por meio de um modelo. |
| O VMware Tools está desatualizado ou não está instalado - O VMware Tools deve ser instalado nas VMs e mantido atualizado. | O [IBM Cloud KB0012161](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=797afaf0dbb477486001327e9d9619e6){:new_window} fornece orientação sobre essas tarefas. |
| Dispositivos de rede da VM antigos | Se os dispositivos de rede da VM não forem mantidos atualizados, os desempenhos da rede e do aplicativo poderão ser afetados. Para obter mais informações sobre a implementação de novos dispositivo de rede virtual e driver, consulte [Escolhendo um adaptador de rede para sua máquina virtual (1001805)](https://kb.vmware.com/s/article/1001805){:new_window}. |
| Limite de memória da máquina virtual | Os limites de memória são frequentemente usados. No entanto, se um S.O. guest não puder acessar a memória necessária, a execução dos aplicativos dentro do S.O. guest poderá ser insatisfatória. Para obter mais informações sobre como resolver o problema, consulte [Definindo as configurações de alocação de recursos](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-14102AB7-2CF9-42E3-9642-3EB6629EF530.html){:new_window}. |
| Capturas instantâneas da VM | Embora as capturas instantâneas sejam úteis, a quantidade e a duração das capturas instantâneas de uma VM afetam diretamente seu desempenho. Para obter informações sobre como resolver o problema, consulte [Consolidar capturas instantâneas](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2F4A6D8B-33FF-4C6B-9B02-C984D151F0D5.html){:new_window}. |
| Criação de log da VM | Se a criação de log não tiver sido configurada corretamente, a capacidade do armazenamento de dados poderá ter um impacto adverso. Para obter informações sobre como resolver o problema, consulte [Configurando níveis de criação de log para o sistema operacional guest](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-F465D340-6556-49E8-B137-C0B4A060E83B.html){:new_window}. |
| Resolução de problemas de conexão de rede | Os sintomas podem incluir a falha na conexão da VM com a rede ou a falta de conectividade de rede com ou de uma única VM. Para obter informações sobre como resolver o problema, consulte [Resolução de problemas de conexão de rede da máquina virtual (1003893)](https://kb.vmware.com/s/article/1003893?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}.  |
| Determinando se diversas CPUs virtuais estão causando problemas de desempenho  | Para obter informações sobre a resolução dos problemas de desempenho de VMs configuradas com diversas CPUs, consulte [Determinando se diversas CPUs virtuais estão causando problemas de desempenho (1005362)](https://kb.vmware.com/s/article/1005362?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}. Esses problemas podem incluir velocidades de transferência insatisfatórias ao copiar dados para ou de uma VM, tempo limite ou lentidão das tarefas de backup, ou a execução insatisfatória de uma VM.  |
| Uma VM foi desligada ou reiniciada  | Para obter informações sobre como resolver o problema, consulte [Determinando o motivo do desligamento ou da reinicialização de uma máquina virtual (1019064)](https://kb.vmware.com/s/article/1019064?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}. |
| Uma ou mais de suas VMs tem um tempo de resposta ruim |  Para obter informações sobre o isolamento de um problema de desempenho em um host do vSphere ESXi, consulte [Resolução de problemas de desempenho da máquina virtual do ESX/ESXi (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}. Os problemas de desempenho podem ser causados por restrições de CPU, memória sobre comprometimento, latência de armazenamento ou latência de rede. |

### Hosts do vSphere ESXi
{: #opsprocs-trouble-common-host}

Tabela 2. Resolução de problemas típicos de hosts do vSphere ESXi

| Título | Descrição |
|---|---|
| Comandos do ESXI | Para obter uma visão geral das interfaces de linha de comandos no vSphere, dos comandos shell do ESXi e dos comandos da vCLI (VMware® vSphere Command-Line Interface), consulte [Introdução ao vSphere Command-Line Interfaces](https://vdc-download.vmware.com/vmwb-repository/dcr-public/bc4fa31a-40ac-4aa9-a6a1-7171d1fff7f4/740990ee-4d65-4627-a9d4-0f046cb78aec/vsphere-esxi-vcenter-server-67-command-line-interface-getting-started-guide.pdf){:new_window}. |
| Estados do host do vSphere HA | Se o vCenter relatar um estado do host HA do vSphere que indique uma condição de erro no host, isso precisará ser corrigido, pois esse problema poderá evitar que o vSphere HA reinicie VMs após uma falha. Para obter mais informações, consulte [Resolução de problemas de estado no host do vSphere HA](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window}. |
| O host do vSphere ESXi está em um estado sem resposta | Para obter informações sobre a resolução de problemas de um host do vSphere ESXi mostrado como Não respondendo, Desconectado ou para as VMs no host mostradas como indisponíveis no vCenter, consulte [Hosts ESX/ESXi não respondem e ficam esmaecidos (1019082)](https://kb.vmware.com/s/article/1019082){:new_window}. |
| Ao ligar uma VM, você vê um erro `File not found` | Para obter informações sobre como recriar um arquivo descritor de disco virtual perdido (VMDK), consulte [Recriando um arquivo descritor de disco da máquina virtual ausente (1002511)](https://kb.vmware.com/s/article/1002511){:new_window}. |
| Problemas de desempenho da VM | Para obter informações sobre o isolamento de um problema de desempenho em um host do vSphere ESXi, consulte [Resolução de problemas de desempenho da máquina virtual do ESX/ESXi (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}. Os problemas de desempenho podem ser causados por restrições de CPU, memória sobre comprometimento, latência de armazenamento ou latência de rede. |
| O Servidor Bare Metal está inativo | Se o Servidor Bare Metal que está executando o vSphere ESXi não estiver respondendo ou estiver inativo, efetue logon na IU de gerenciamento ou no console do {{site.data.keyword.cloud_notm}} e verifique o status. Se necessário, abra um caso para obter assistência com o seu Servidor Bare Metal. Para obter mais informações, veja [Trabalhando com casos de suporte](/docs/get-support?topic=get-support-open-case#open-case){:new_window}. |
| O host do vSphere ESXi está em estado desconectado ou sem resposta  | Para obter mais informações, consulte [Resolução de problemas de um host ESXi/ESX em um estado sem resposta (1003409)](https://kb.vmware.com/s/article/1003409?lang=en_US){:new_window}. |
| Tela roxa de morte  | O Purple Screen of Death (PSOD) é um pânico kernel e o vSphere ESXi kernel (vmkernel) aciona essa medida de segurança em resposta a um evento ou erro irrecuperável e significaria que continuar a execução representaria um alto risco para os serviços e as VMs. Quando o pânico ocorre e o host do vSphere ESXi trava, ele termina todos os serviços em execução nele, juntamente com todas as VMs hospedadas. As VMs não são encerradas normalmente, mas desligadas abruptamente. Se o host for parte de um cluster e você tiver configurado a alta disponibilidade, essas VMs serão reiniciadas nos outros hosts no cluster. Para obter mais informações, consulte [Conhecimento - KB0012864 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=dd5d2330db11f300c4fa302f9d96198d){:new_window}. |

### Armazenamento
{: #opsprocs-trouble-common-storage}

Tabela 3. Resolução de problemas típicos de armazenamento

| Título | Descrição |
|---|---|
| Resolução de problemas de armazenamento | Para obter mais informações sobre desempenho lento, falhas imprevisíveis, distorção de disco ou de VM, consulte [Resolução de problemas de armazenamento ao usar os produtos VMware (2013160)](https://kb.vmware.com/s/article/2013160?lang=en_US){:new_window}. |
| Resolução de problemas da vSAN | Para obter mais informações, consulte [Manipulação de falhas no vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-35A4B700-6640-4519-A885-440A1AE8D3BD.html){:new_window}.  |
| Falha de disco do vSAN | Para obter mais informações sobre como identificar um disco com falha e como solicitar substituição, consulte [Um disco rígido/disco magnético em um grupo de discos do VMware vSAN falha (2077185)](https://kb.vmware.com/s/article/2077185){:new_window}. |
| Lidando com os problemas do vSAN Health | Na página Monitorar do VMware vSphere Web Client, é possível ver alertas e avisos relacionados a problemas do vSAN Health. Para obter informações sobre como lidar com esses problemas, consulte [Alertas e avisos do Virtual SAN Health](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_vsan_alerts#trbl_vsan_alerts){:new_window}.|
| Rebalanceamento do vSAN | Se os discos relatarem erros na verificação de funcionamento, indicando que o cluster está desbalanceado e há discos com alto uso de espaço, enquanto outros estão baixos, e você tiver que executar um rebalanceamento proativo. Isso inicia manualmente um rebalanceamento dos objetos em um cluster vSAN. Para obter mais informações sobre o rebalanceamento proativo do vSAN e quando ele pode ser aplicável, consulte [Rebalanceamento proativo do vSAN (2149809)](https://kb.vmware.com/s/article/2149809){:new_window}. |
| Iniciar teste de funcionamento do vSAN | Se suspeitar de algum problema com o vSAN, será possível iniciar um teste de funcionamento para verificar se os componentes do cluster estão funcionando conforme o esperado. A execução do teste de criação de VM cria uma VM em cada host no cluster e, em seguida, realiza sua exclusão. Se essas tarefas forem bem-sucedidas, os componentes do cluster estarão funcionando conforme o esperado e o cluster estará funcional. Em seguida, o teste de desempenho de rede é usado para detectar e diagnosticar problemas de conectividade e para assegurar que a largura de banda da rede entre os hosts seja adequada. Para obter mais informações, consulte [Testes proativos](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-B88B5900-33A4-4821-9659-59861EF70FB8.html){:new_window}. |
| Monitorando o desempenho do vSAN | Para obter mais informações, consulte [Monitorando o desempenho do vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-3D2D1382-9DDC-44D4-AF3B-ACA4F1DDBDCC.html){:new_window}. Os gráficos de desempenho estão disponíveis para clusters, hosts, discos físicos, VMs e discos virtuais. |
| Resolução de problemas da vSAN | Para obter mais informações, consulte [Lidando com falhas e solucionando problemas do vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-0F3C4D3F-9B86-4879-9C60-D6A977523112.html){:new_window}. |


### Rede
{: #opsprocs-trouble-common-network}

Tabela 4. Resolução de problemas de rede típica

| Título | Descrição |
|---|---|
|  NSX Edge /var/log está ficando cheio no Edge ativo | Para obter informações sobre uma solução alternativa se você foi alertado sobre o disco do Edge estar enchendo e descobriu que a partição /var/log também está ficando cheia, consulte [O NSX Edge /var/log está ficando cheio no Edge ativo (50108355)](https://kb.vmware.com/s/article/50108355){:new_window}.  |
| Testando a largura da banda do HCX  | Para obter informações sobre como usar `perftest` para localizar largura de banda disponível nos túneis HCX, caso você ache que há um problema de largura de banda de rede com o HCX, consulte [Etapas para executar perftest no HCX (56211)](https://kb.vmware.com/s/article/56211?lang=en_US){:new_window}. São executados testes bidirecionais para cada `perftest`. Para o par de gateways, um está dentro do data center de origem, chamado OnPrem, e o outro está no {{site.data.keyword.cloud_notm}}. A maneira com que o rendimento do `perftest` funciona é fazer com que o emissor tente enviar o mais rápido que o link possa sustentar. Portanto, para cada teste, você vê uma taxa de "remetente" mais alta do que a taxa de "destinatário". É possível considerar o valor da taxa de "destinatário" como um resultado de rendimento unidirecional. |
| Resolução de problemas do HCX | Para obter mais informações, consulte [Resolução de problemas do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting). |
| Estado de sincronização do HCX com 0% de progresso e 0 bytes com Erro de status | Para obter mais informações, consulte [A replicação do HCX está no estado de Sincronização com 0% de progresso e 0 bytes com Erro de status (56710)](https://kb.vmware.com/s/article/56710?lang=en_US#q=HCX){:new_window}. |
| Desempenho ruim da rede da VM | Revise as configurações de NIC virtual da VM. O VMware recomenda 3 NICs virtuais VMXNET para VMs, uma vez que é a geração mais recente de NICs paravirtualizadas projetadas para desempenho. Verifique a compatibilidade do VMXNET 3 usando a lista de compatibilidade do VMware e, se suportado, mude o NIC virtual para obter desempenho de rede adicional. Para obter mais informações, consulte [Resolução de problemas de rede](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}. |

### vCenter
{: #opsprocs-trouble-common-vcenter}

Tabela 5. Resolução de problemas típicos do vCenter

| Título | Descrição |
|---|---|
| Acesso ao console da máquina virtual | Para obter mais informações, consulte [Conhecimento - KB0012863 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=5446a73cdb1db300c4fa302f9d961934){:new_window}. |
| O novo certificado do vCenter Server não parece estar carregando | Após a substituição dos certificados padrão do vCenter Server, pode parecer que os novos certificados não estão carregando. Para obter mais informações, consulte [O novo certificado do vCenter Server não parece estar carregando](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-415CF843-42E8-4AD7-98EC-7265227337B6.html){:new_window}. |
| O vCenter Server não consegue se conectar a hosts gerenciados | Após a substituição dos certificados padrão do vCenter Server e a reinicialização do sistema, o vCenter Server não consegue se conectar a hosts gerenciados. Para obter mais informações, consulte [O vCenter Server não consegue se conectar a hosts gerenciados](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-8D3DCEC4-50B6-4523-BF24-0DE6C65600E9.html){:new_window}. |
| Não é possível configurar o vSphere HA usando certificados SSL customizados | Após a instalação de certificados SSL customizados, as tentativas de ativação do vSphere High Availability (HA) falham. Para obter mais informações, consulte [Não é possível configurar o vSphere HA usando certificados SSL customizados](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3FC16DC8-7157-4340-AB8A-B8DC87D7DC0F.html){:new_window}. |

### Licenças
{: #opsprocs-trouble-common-licenses}

Tabela 6. Resolução de problemas típicos de licença

| Título | Descrição |
|---|---|
|  Configuração de licença incompatível ou incorreta | Para obter mais informações, consulte [Resolução de problemas de licenciamento de host](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window}. |
|  A VM não liga | Poderá haver um problema de licença se você não puder ligar uma VM em um host do vSphere ESXi e receber a mensagem ``The 60-day evaluation period of the host is expired or the license of the host is expired``. Para obter mais informações, consulte [Não é possível ligar uma máquina virtual](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-D4770546-9F9A-4F1E-AC1C-CF313E6130F4.html){:new_window}. |
| Um recurso está indisponível ou não foi possível mudar uma configuração  | Para obter mais informações, consulte [Não é possível configurar ou usar um recurso](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-26C0E2F0-A581-4A5A-B1F7-2BA4F151E27A.html){:new_window}.  |


## Links relacionados
{: #opsprocs-trouble-links}

* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-trbl_support#trbl_support)
* [Visão geral da resolução de problemas do vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-C70D5A5E-7D84-446C-B8CE-0766AA7351A4.html){:new_window}
* [Resolução de problemas do vSphere com logs](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-552CC9E8-441C-434A-88FC-3F50881245D7.html){:new_window}
* [Operations management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
* [Reunião do log de suporte](https://kb.vmware.com/s/article/1010705){:new_window}
* [Monitorando eventos, alarmes e ações automatizadas](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}
* [Arquivos de log do sistema do vSphere](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-DABCB024-E083-4A4D-8AE0-D1AF4CB3800C.html){:new_window}
* [Considerações sobre como alterar os artefatos do vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
