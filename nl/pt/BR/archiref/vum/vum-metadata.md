---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

#	Coletando os metadados

O VUM faz download de metadados sobre os upgrades, correções ou extensões por meio de um processo automático predefinido que pode ser modificado. Em intervalos configuráveis regulares, o VUM entra em contato com o VMware, ou origens de terceiros, para reunir os metadados mais recentes sobre upgrades, correções ou extensões disponíveis. No entanto, as configurações padrão do VMware são aceitáveis para uso na instância do VMware vCenter Server on {{site.data.keyword.cloud}}. É possível mudá-las, conforme necessário, para seus requisitos corporativos.

O VUM exibe as linhas de base gerenciadas pelo sistema que são geradas pelo vSAN. As linhas de base gerenciadas pelo sistema atualizam automaticamente seu conteúdo periodicamente, o que requer que o VUM tenha acesso constante à Internet. As linhas de base do sistema vSAN são geralmente atualizadas a cada 24 horas.

É possível usar as linhas de base gerenciadas pelo sistema para fazer upgrade de seus clusters vSAN para correções críticas recomendadas, drivers, atualizações ou versão mais recente do host ESXi suportada para vSAN.

Para a maioria das empresas, as configurações padrão do VMware para o VUM são consideradas como adequadas. A seguir é fornecido como mudar essas configurações se sua empresa gostaria de usar configurações diferentes.

##	Fazer Download do Planejamento
As atualizações são upgrades de dispositivo virtual, correções de host e extensões e, por padrão, o VUM faz download de atualizações diariamente. Isso pode ser mudado acessando o vSphere Web Client, navegando para **Página inicial** > **Update Manager** > **Gerenciar** > **Configurações** e selecionando **Planejamento de download** e, em seguida, clicando em **Editar**.

##	Planejamento de verificação de notificação
As notificações são informações sobre rechamadas de correção, novas correções e alertas e, por padrão, o VUM faz download de notificações em uma base por hora. Isso pode ser mudado acessando o vSphere Web Client, navegando para **Página inicial** > **Update Manager** > **Gerenciar** > **Configurações** e selecionando **Planejamento de verificação de notificação** e, em seguida, clicando em **Editar**.

##	Configurações da máquina virtual
Para mudar as configurações da máquina virtual (VM), acesse o vSphere Web Client, navegue para **Página inicial** > **Gerenciador de atualização** > **Gerenciar** > **Configurações** e **Configurações da VM** e, em seguida, clique em **Editar**.

##	Configurações do Host / Cluster
Para mudar as Configurações do host/cluster, acesse o vSphere Web Client, navegue para **Página inicial** > **Update Manager** > **Gerenciar** > **Configurações** e **Configurações do host/cluster** e, em seguida, clicando em **Editar**.

### Links relacionados

* [VMware HCX no {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Soluções de VMware no	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
