---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Redundância da máquina virtual vSAN
{: #vum-vsan-redundancy}

Ao colocar um host do vSphere ESXi no modo de manutenção em um cluster vSAN, é necessário selecionar um modo de evacuação de dados. A seleção do modo pode ter um impacto sobre as máquinas virtuais (MVs) e os dispositivos que estão consumindo o armazenamento de dados vSAN:
* Uma **migração de dados integral** evita todos os dados do host e os move para os outros hosts vSphere ESXi no cluster vSAN. Esse modo de evacuação resulta na maior quantia de transferência de dados e consome mais tempo e recursos. Todos os componentes no armazenamento local do host selecionado são migrados em outro lugar no cluster. Quando o host entra no modo de manutenção, todas as MVs e os dispositivos têm acesso aos seus componentes de armazenamento e ainda estão em conformidade com suas políticas de armazenamento designadas. A evacuação de dados integral pode levar muito tempo e pode fazer com que a janela de manutenção para um upgrade tenha uma duração longa.
* O modo **Assegurar a evacuação dos dados de acessibilidade** é a opção padrão e quando o host vSphere ESXi é colocado no modo de manutenção, o vSAN assegura que todas as MVs ou todos os dispositivos acessíveis no host permaneçam acessíveis. Como ocorre apenas a evacuação parcial de dados, a MV ou o dispositivo podem não estar mais totalmente em conformidade com uma política de armazenamento da MV durante a evacuação e podem não ter acesso a todas as suas réplicas. Se ocorrer uma falha enquanto o host estiver no modo de manutenção e o nível primário de falhas a ser tolerado estiver configurado como 1, a perda de dados ocorrerá e a MV ou o dispositivo poderá ficar indisponível.
* No modo **sem migração de dados**, o vSAN não evacua dados do host enquanto entra no modo de manutenção. Embora isso reduza o tempo para entrar no modo de manutenção e, portanto, reduza a duração da janela de manutenção, algumas MVs ou dispositivos podem se tornar inacessíveis.

Esta seção cria uma nova política de armazenamento da MV que permite que o modo **assegurar a evacuação de dados de acessibilidade** seja selecionado para reduzir as janelas de manutenção, mas reduzindo o risco de que uma falha de um host enquanto outro está no modo de manutenção torne uma MV ou um dispositivo inacessível. Para qualquer MV ou dispositivo, em que se tornar não redundante quando um host vSAN é colocado no modo de manutenção não é aceitável, conclua o processo a seguir antes de concluir qualquer ação de correção. Um cluster com pelo menos seis hosts é necessário.

1. Crie um novo perfil vSAN com as configurações de RAID 5/6 e FTT = 2 (RAID 6) e, em seguida, aplique essa política com relação às MVs ou aos dispositivos necessários.

2. Aguarde até que o vSAN tenha concluído a sincronização antes de iniciar qualquer ação de correção. O status de conclusão pode ser verificado navegando para a **página de monitoramento de Objetos Virtuais de vSAN** para o cluster e revisando o **Status de conclusão**.

## Links relacionados
{: #vum-vsan-redundancy-related}

* [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [Demos do {{site.data.keyword.vmwaresolutions_full}}](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (demonstrações)
