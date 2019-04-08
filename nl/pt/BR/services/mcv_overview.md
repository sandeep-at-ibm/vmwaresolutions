---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

# Visão geral do Mission Critical VMware on IBM Cloud
{: #mcv_overview}

O Mission Critical VMware on {{site.data.keyword.cloud}} entrega uma arquitetura de nuvem multizona para ajudar as empresas a evitar o tempo de inatividade para aplicativos em nuvem e para automatizar failovers dentro de uma região de nuvem.

Com essa arquitetura de nuvem, os clientes podem alcançar uma taxa de sucesso de disponibilidade e de failover mais alta do que a maioria dos clientes do VMware podem alcançar com ambientes no local ou plataformas de nuvem concorrentes.

Essa arquitetura suporta cargas de trabalho anteriores existentes que são essenciais, incluindo aplicativos nativos não em nuvem, em uma disponibilidade agregada prevista de 99,99%. As regiões multizona do IBM Cloud são projetadas para manter as cargas de trabalho essenciais on-line se ocorrer uma indisponibilidade de site. As cargas de trabalho em um site com falha são reiniciadas automaticamente em tempo quase real, enquanto as cargas de trabalho em sites adjacentes permanecem on-line e disponíveis.

A arquitetura abrange vários serviços corporativos, incluindo redes, armazenamento, resiliência e outras ferramentas construídas para monitoramento e resolução de problemas de aplicativos baseados em nuvem. Além disso, essa arquitetura pode ser integrada ao IBM Services Platform with Watson, construído no {{site.data.keyword.cloud_notm}}, para permitir um consumo mais amplo de serviços. Usando os recursos cognitivos da plataforma, os clientes podem minerar dados de forma mais eficiente para novos insights de negócios para ajudar a manter operações contínuas.

## Especificações técnicas para o Mission Critical VMware on IBM Cloud
{: #mcv_overview-specs}

A arquitetura Mission Critical VMware on {{site.data.keyword.cloud_notm}} é uma arquitetura de referência de ponta a ponta que fornece failover automatizado para cargas de trabalho do cliente. Ela usa uma região multizona do {{site.data.keyword.cloud_notm}} com um serviço gerenciado pela IBM que abrange os componentes a seguir:

* Arquitetura de cálculo (VMware vSphere)
* Arquitetura de rede (atualmente NSX-V)
* Arquitetura de armazenamento (VMware vSAN)
* Integração com o IBM Services Platform with Watson para permitir o consumo de serviços
* Ferramentas para monitoramento, resolução de problemas, desempenho e gerenciamento de capacidade:
  * Padrão do vRealize Suite (Operations, Log Insight and Network Insight)
  * Padrão do Active Directory
  * Integração com o Netcool/Bluecare para chamado automático, alerta e enriquecimento de evento
  * Padrões de resiliência (backup e recuperação)

O Mission Critical VMware on {{site.data.keyword.cloud_notm}} está disponível nas regiões a seguir:
* América: Sul AN - todos os Data Centers do IBM Cloud em Dallas e Leste da AN: todos os Data Centers do IBM Cloud em Washington, DC
* Europa: todos os Data Centers do IBM Cloud em Frankfurt e Londres
* Ásia-Pacífico: todos os Data Centers do IBM Cloud em Sydney e Tóquio

### Especificações de arquitetura de infraestrutura de
{: #mcv_overview-base-specs}

A infraestrutura de base tem as especificações a seguir:
* Cada site tem seu próprio cluster de borda e de gerenciamento dedicado
* O cluster de recursos é um cluster estendido do vSphere + vSAN
* O site de testemunha contém um host ESXi de testemunha
* Arquitetura do vCenter único e do NSX Manager
* vCenter Server Appliance com Platform Services Controller (PSC) integrado que usa o vCenter High Availability (HA) sobre uma arquitetura de rede L3
* A recuperação do NSX Manager está usando uma metodologia Espera a Quente que sincroniza os arquivos de backup

### Especificações de arquitetura de conjunto de ferramentas e de tecnologia
{: #mcv_overview-tooling-specs}

A arquitetura de conjunto de ferramentas e de tecnologia tem as especificações a seguir:
* O vRealize Operations, vRealize Log Insight e vRealize Network Insight para fornecer operações e recursos de gerenciamento específicos para os produtos VMware que estão sendo usados, por exemplo, NSX, vSAN e vSphere
* O IBM Software Defined Environment Automation Tool Health Check (SAT HC) para validar implementações com relação às melhores práticas e políticas de segurança
* A Recuperação de Desastre (DR) opcional para um site fora da região do {{site.data.keyword.cloud_notm}}
* O Fortigate Security Appliance ou semelhante para proteger qualquer acesso à Internet e para facilitar a integração de rede ativa/ativa com a rede no local

### Especificações de arquitetura de cluster estendido do vSphere + vSAN
{: #mcv_overview-stretched-cluster-specs}

A arquitetura de cluster estendido do vSphere + vSAN tem as especificações a seguir:
* O cluster fornece recursos de armazenamento e de cálculo que abrangem dois sites para fornecer disponibilidade aprimorada.
* As solicitações de gravação de máquinas virtuais (MVs) são gravadas de forma síncrona em ambos os sites, incorrendo em latência de rede de site para site.
* As solicitações de leitura de MVs são preenchidas localmente para o local físico no qual a MV está localizada, evitando latência extra.
* O site de testemunha e o host de testemunha agem como o split-brain/quorum.
* A Criptografia Nativa do vSAN (para criptografia em repouso) pode ser usada em combinação com essa arquitetura.

### Especificações de arquitetura de
{: #mcv_overview-network-specs}

A arquitetura de rede tem as especificações a seguir:
* Edge/DLR/VXLANs em combinação com o roteamento baseado em métrica do BGP para facilitar um design de site ativo/ativo com failover automatizado.
* Cada site tem o conceito de seu próprio conjunto de Edges/DLRs e VXLANs.
* Em circunstâncias normais, todas as MVs conectadas ao DLR-A, por exemplo VM-A, estarão na zona de disponibilidade nº 1 do {{site.data.keyword.cloud_notm}} e o ingresso e o egresso do tráfego ocorrerá localmente.
* Durante uma atividade de vMotion para o VM-A, ainda ocorrerá o tráfego de ingresso e egresso por meio da zona de disponibilidade nº 1 do {{site.data.keyword.cloud_notm}}.
* Durante uma falha de site ou de borda, o tráfego será roteado para fora do site disponível restante.

## Links relacionados
{: #mcv_overview-related}

* [Solicitando o Mission Critical VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_mcv)
