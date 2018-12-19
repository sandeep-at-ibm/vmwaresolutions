---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Redundância da máquina virtual vSAN

Ao colocar um host do vSphere ESXi no modo de manutenção em um cluster vSAN, é necessário selecionar um modo de evacuação de dados. A seleção do modo pode ter um impacto sobre as máquinas virtuais (VMs) e os dispositivos que estão consumindo o armazenamento de dados vSAN:
* Uma **migração de dados integral** evita todos os dados do host e os move para os outros hosts vSphere ESXi no cluster vSAN. Esse modo de evacuação resulta na maior quantia de transferência de dados e consome mais tempo e recursos. Todos os componentes no armazenamento local do host selecionado são migrados em outro lugar no cluster. Quando o host entra no modo de manutenção, todas as VMs e os dispositivos têm acesso aos seus componentes de armazenamento e ainda estão em conformidade com suas políticas de armazenamento designadas. A evacuação de dados integral pode levar muito tempo e pode fazer com que a janela de manutenção para um upgrade tenha uma duração longa.
* O modo **Assegurar a evacuação dos dados de acessibilidade** é a opção padrão e quando o host vSphere ESXi é colocado no modo de manutenção, o vSAN assegura que todas as VMs ou todos os dispositivos acessíveis no host permaneçam acessíveis. Como ocorre apenas a evacuação parcial de dados, a VM ou o dispositivo podem não estar mais totalmente em conformidade com uma política de armazenamento da VM durante a evacuação e podem não ter acesso a todas as suas réplicas. Se ocorrer uma falha enquanto o host estiver no modo de manutenção e o nível primário de falhas a ser tolerado estiver configurado como 1, a perda de dados ocorrerá e a VM ou o dispositivo poderão ficar indisponíveis.
* No modo **sem migração de dados**, o vSAN não evacua nenhum dado do host ao entrar no modo de manutenção. Embora isso reduza o tempo para entrar no modo de manutenção e, portanto, reduza a duração da janela de manutenção, algumas VMs ou dispositivos podem se tornar inacessíveis.

Esta seção cria uma nova política de armazenamento da VM que permite que o modo **Assegurar a evacuação dos dados de acessibilidade** seja selecionado para reduzir as janelas de manutenção, mas reduzir o risco de uma falha de um host enquanto outro está no modo de manutenção tornará uma VM ou um dispositivo inacessível. Para qualquer VM ou dispositivo, em que se tornar não redundante quando um host vSAN é colocado no modo de manutenção não é aceitável, realize o processo a seguir antes de realizar quaisquer ações de correção. Um cluster com pelo menos 6 hosts será necessário.

1. Crie um novo perfil vSAN com as configurações de RAID 5/6 e FTT = 2 (RAID 6) e, em seguida, aplique essa política com relação às VMs ou aos dispositivos necessários.

2. Aguarde até que o vSAN tenha concluído a sincronização antes de iniciar quaisquer ações de correção. O status de conclusão pode ser verificado navegando para a **página de monitoramento de Objetos Virtuais de vSAN** para o cluster e revisando o **Status de conclusão**.

### Links relacionados

* [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Soluções de VMware no {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
