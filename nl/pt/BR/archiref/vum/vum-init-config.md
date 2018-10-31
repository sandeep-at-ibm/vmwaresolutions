---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-05"

---

# Configuração inicial

A automação IC4VS configura o VCSA com um gateway padrão configurado para o IBM Cloud Backend Customer Router (BCR). No entanto, não há nenhuma rota para a Internet por meio do BCR. A rota padrão para a Internet da instância do VCS é por meio do ESG de Gerenciamento. Como não é aconselhável mudar a configuração do VCSA ou do ESG de Gerenciamento, uma implementação do servidor proxy na sub-rede do cliente é recomendada para ativar o VUM.

Essa abordagem significa que o VCSA ou o ESG de Gerenciamento não precisam ser reconfigurados, no entanto, uma pequena VM ou um dispositivo precisa ser instalado. Um servidor proxy é um sistema que fica entre dois dispositivos de terminal e age como um dispositivo intermediário. Neste caso, ele fica entre o VUM e os servidores de atualização no VMware.

Quando um VUM solicita um recurso do servidor de atualização no VMware, a solicitação é enviada para o servidor proxy primeiro e o servidor proxy, em seguida, envia a solicitação para o servidor de atualização. Depois que o recurso é obtido pelo servidor proxy, ele envia o recurso para VUM. Um servidor proxy pode ser usado para facilitar a segurança, os controles administrativos e os serviços de armazenamento em cache.

Este documento descreve o uso de um servidor proxy com base no CentOS e no Squid. O Proxy do Squid é um proxy de armazenamento em cache de software livre para a web e suporta muitos protocolos, incluindo HTTP e HTTPS. Há vários proxies baseados em VM e dispositivo que estão disponíveis e é necessário selecionar aquele apropriado com base nos requisitos de sua empresa e instalar e configurar seguindo a orientação do fornecedor. Os clientes que optam por usar uma implementação do CentOS/Squid devem continuar com o processo abaixo.

*	Fazer download do ISO do CentOS em um servidor de salto
*	Criar uma Biblioteca do vCenter
*	Fazer upload do ISO para a Biblioteca vCenter
*	Criar uma VM, instalar e configurar o CentOS e instalar o Squid

Antes de poder iniciar essa tarefa, é necessário coletar informações para preencher a Tabela 1. Revise os valores sugeridos e assegure-se de que eles sejam apropriados para sua empresa. Essa configuração é baseada em um pequeno proxy apenas para o VUM que usa o CentOS-Minimal e o Squid.

Tabela 1. Valores de implementação

| Parâmetro | Valores sugeridos | Notas |
|:--------- |:-------------- |:------ |
| CPU do proxy | 1 vCPU | O Squid não tem requisitos mínimos |
| RAM de proxy | 2 GB | O Squid não tem requisitos mínimos |
| Disco de proxy |	25 | O GB Squid não possui requisitos mínimos |
| Hostname | Proxy01 | |
| Endereço |	IP de proxy |	Um endereço IP sobressalente deve ser usado por meio da sub-rede móvel privada do Cliente, designada durante o processo de fornecimento. Somente dois endereços IP teriam sido reservados nessa sub-rede; um para o BCR e o outro para o customer-esg
| Máscara de |	255.255.255.192 | |
| Gateway| 	customer-nsx-ip private uplink ip |	Essa é a configuração de gateway padrão para o servidor proxy, que é o endereço de uplink privado customer-nsx -edge. O IP pode ser localizado revisando a guia Configurações para o customer-nsx-edge |
| Servidor DNS |	IP do AD/DNS | Esse endereço IP pode ser localizado na página Instância no [Console em nuvem do IC4VS](https://console.bluemix.net/infrastructure/vmware-solutions/console/vcenters/), Instâncias implementadas; |
| IP do BCR |	bcr ip | Esse é o endereço IP do IBM Cloud Backend Customer Router e é o gateway para 10.0.0.0/8 e 161.26.0.0/16. Este endereço é usado em uma rota estática no servidor proxy para que ele possa atingir o VCSA e o servidor AD/DNS |

## Configurando o NSX

As configurações de firewall do ESG do Cliente NSX e da NAT são necessárias para ativar o tráfego do servidor proxy.

### Firewall

1. Acesse  ** Home **  >  ** Networking & Security **.
2. Selecione **NSX Edges**, customer-nsx-edge e, em seguida, **Firewall**.
3. Clique no símbolo **+** e inclua uma regra de firewall.
4. Forneça os parâmetros necessários conforme observado na tabela a seguir. A nova regra de firewall deve vir antes da última regra, a regra de Negação padrão.

Tabela 2. Regra de firewall

| Parâmetro | Valores sugeridos |
|:--------- |:-------------- |
| Nome | Proxy01 de saída |
| Tipo | User |
| Origem | IP do servidor proxy |
| Destino | qualquer |
| Serviço | Eco do HTTP/HTTPS/ICMP |
| Ação | Aceitar |

Após os parâmetros serem fornecidos, clique em **Publicar mudanças**.

### Instalando e configurando um servidor proxy

O processo a seguir implementa uma VM para hospedar o CentOS e o Squid da Biblioteca de Conteúdo e consiste nas etapas a seguir. Presume-se que você tenha uma VSI do Windows provisionada para uso como um jumpbox e que esteja usando o Remote Desktop Protocol para se conectar à interface pública da VSI:

* Fazer download do arquivo CentOS-Minimal ISO
* Configurar uma Biblioteca de Conteúdo do vCenter e preencher com o arquivo ISO do CentOS
* Configurar a VM do Proxy, instalar o CentOS e o Squid

### Fazendo download do arquivo CentOS-Minimal ISO

Usando um navegador em seu servidor de salto, faça download do arquivo ISO do CentOS-Minimal por meio do [CentOS](https://www.centos.org/download/). Observe que o IBM Cloud mantém um espelho de muitas distribuições Linux populares. Esse espelho está disponível somente na rede privada e os ISOs do CentOS estão disponíveis no endereço a seguir: http://mirrors.service.softlayer.com/centos/7/isos/x86_64/.

### Configurando uma biblioteca de conteúdo e preenchendo-a com o arquivo ISO do CentOS

Crie uma biblioteca de conteúdo do vCenter local. A biblioteca é acessível somente na instância do vCenter Server na qual ela é criada. Preencha a biblioteca com modelos e ISOs necessários para implementar máquinas virtuais.

1. Por meio do vSphere Web Client, navegue para **Página inicial** > **Biblioteca de conteúdo** > **Objetos** > **Criar uma nova biblioteca de conteúdo** > **Criar biblioteca inscrita no vCenter**.
2. Insira um nome para a biblioteca de conteúdo, por exemplo, ISO, e, na caixa de texto Notas, insira uma descrição para a biblioteca e clique em **Avançar**.
3. Selecione **Biblioteca de conteúdo local** e clique em **Avançar**.
4. Selecione um armazenamento de dados e, em seguida, clique em um armazenamento de dados adequado, por exemplo, vsanDatastore.
5. Revise as informações na página Pronto para concluir e clique em **Concluir**.

### Configurando a VM do proxy, instalar o CentOS e o Squid

Esta atividade tem as tarefas a seguir:

*	Criar uma nova VM
*	Instalar o CentOS
*	Instalar o Squid

#### Criar uma nova VM

Esta tarefa cria uma nova VM pronta para uso como o servidor proxy. As configurações da Tabela 1 Valores de implementação devem ser usadas para preencher a configuração.

1.	Por meio do vSphere Web Client, navegue para **Página inicial** > **VMs e modelos**.
2.	Na área de janela do Navegador, clique em **datacenter1** e, em seguida, clique com o botão direito e selecione **Nova máquina virtual** > **Nova máquina virtual**.
3.	Selecione **Criar uma nova máquina virtual** e, em seguida, clique em **Avançar**.
4.	Insira um Nome para a VM, por exemplo, Proxy01, e selecione **datacenter1**, em seguida, clique em **Avançar**.
5.	Selecione  ** cluster1 **  e, em seguida, clique em  ** Avançar **.
6.	Selecione um armazenamento de dados apropriado, por exemplo, vsanDatastore, e clique em **Avançar** e em **Avançar** novamente.
7.	Em **Família de S.O. guest**, selecione **Linux** e, em **Versão do S.O. guest**, selecione **CentOS 7 (64 bits)** e clique em **Avançar**.
8.	Configure **CPU como 1**, **Memória como 2048 MB** e **Novo disco rígido como 25 GB**. Selecione **Arquivo ISO de Biblioteca de Conteúdo** e, em seguida, **CentOS-7-x86_64-Minimal**, clique em **OK** e marque a caixa **Conectado**.
9.	Na caixa Novo dispositivo, selecione **Rede** e, em seguida, clique em **Incluir**.
10.	Selecione a rede **SDDC-DPortGroup-Mgmt** e assegure-se de que a caixa de seleção Conectar esteja marcada, clique em **Avançar**.
11.	Revise e clique em  ** Concluir **

#### Instalar o CentOS

Esta tarefa instala e configura a VM recém-criada pronta para a instalação do Squid

1.	Na área de janela do Navegador do vSphere Web Client, selecione a **VM** recém-criada, Proxy01, em seguida, selecione a **Guia Resumo**.
2.	Pressione o botão **"Executar"** para ligar a VM.
3.	A VM agora será ligada e inicializada por meio do ISO do CentOS 7. Inicie um **Console remoto ou console da web** para a VM. Observe que o Console Remoto deve estar instalado e o sistema que está executando o navegador da web deve resolver os hosts vSphere ESXi por nome.
4.	Na tela Bem-vindo ao CentOS 7, selecione seu idioma necessário e clique em **Continuar**.
5.	Na tela **LOCALIZAÇÃO**, clique em **DATA E HORA** e selecione seu fuso horário e, em seguida, clique em **Pronto**.
6.	Na tela **LOCALIZAÇÃO**, clique em **TECLADO** para mudar do padrão, se necessário, em seguida, pressione **Pronto**.
7.	Na tela **LOCALIZAÇÃO**, clique em **DESTINO DA INSTALAÇÃO**, clique no **Ícone do disco virtual do VMware** e, em seguida, clique em **Pronto**.
8.	Na tela **LOCALIZAÇÃO**, clique em **REDE e NOME DO HOST**, mude o Nome do host para o seu nome do host escolhido, por exemplo, Proxy01.
9.	Clique no botão **Configurar**, em seguida, em **Configurações de IPv4** e, na caixa **Método**, selecione **Manual**.
10.	Usando o botão **Incluir**, insira _Máscara de rede de endereço_ e _Gateway_ da _Tabela 1 - Valores de implementação_
11.	Insira o _Endereço IP do servidor DNS_ da Tabela 1 – Valores de implementação
12.	Clique no botão **Rotas** e inclua as rotas estáticas a seguir, _10.0.0.0/8 e 161.26.0.0/16_ com um endereço IP de gateway do _Endereço IP do BCR_ da Tabela 1 Valores de implementação, como o gateway. Essa rota estática permite que o servidor proxy atinja o servidor DNS
13.	Clique em **Salvar** e, em seguida, assegure-se de que a interface Ethernet esteja Ligada e mostrada como conectada. Clique em  ** Pronto **  e em  ** Iniciar Instalação **
14.	Conforme a instalação continua, configure uma senha raiz e configure um usuário.
15.	Quando a instalação estiver concluída, efetue login como o usuário e, em seguida, insira o comando _ping vmware.com_. O nome deve ser resolvido para um endereço IP e você deverá obter resposta. Se você não obtiver respostas, verifique os endereços IP, as regras de firewall e as configurações de NAT.

#### Instalar e configurar o Squid

O Squid não tem nenhum requisito mínimo de hardware, mas a quantia de RAM pode variar de acordo com os usuários que acessam a Internet por meio de seu proxy e os objetos que estão armazenados no cache. Como o servidor proxy é acessado somente pelo VUM e o cache não está ativado, somente uma VM pequena foi configurada.

1. Usando o Console da Web ou o Console Remoto por meio do vSphere Web Client, efetue login no servidor proxy como o usuário e, em seguida, `su` para raiz.
2. Antes de instalar quaisquer pacotes, é recomendável atualizar o sistema e os pacotes usando o comando a seguir:
  `yum -y update`

3. Para instalar o Squid, é necessário instalar o repositório EPEL para o sistema, pois o Squid não está disponível no repositório yum padrão. Execute o comando a seguir para instalar o repositório EPEL:
  `yum -y install epel-release`

4. Atualize e limpe usando os comandos a seguir:

  `yum -y update`
  `yum clean all`

5. O Squid é instalado usando o comando a seguir: `yum -y install squid`
6. Depois de instalado, inicie o Squid imediatamente usando o comando a seguir: `systemctl start squid`
7. Para iniciar automaticamente o Squid no tempo de inicialização, execute o comando a seguir: `systemctl enable squid`
8. Assegure-se de que o Squid esteja em execução, executando o comando a seguir: `systemctl status squid`
9. O firewall do CentOS precisa permitir acesso à porta do Squid, TCP 3128, usando o comando a seguir: `firewall-cmd –add-port=3128/tcp –permanent`
10.	Para salvar a regra e reiniciar o serviço, use o comando a seguir: `firewall-cmd –reload`

## A configuração inicial do VUM

Configure o VUM para usar o servidor proxy para acessar os repositórios na Internet.
1.	Usando o vSphere Web Client, navegue para **Página inicial** > **Update Manager**. Clique em seu vCenter Server.
2.	Selecione a **guia Gerenciar** e clique no botão **Configurações**.
3.	Selecione **Configurações de download** e, em seguida, em _Configurações de proxy_, clique no botão **Editar**.
4.	Marque a caixa **Usar proxy** e insira o _Endereço IP do servidor proxy_ e a _porta 3128_, clique em **OK**
5.	O Status de conectividade deverá mudar para _Validando_ e, em seguida, para _Conectado_.
6.	Clique no botão **Fazer download agora** e, na área de janela _Tarefas recentes_, você deverá ver essa atividade concluída.

### Links relacionados

* [ VMware HCX on IBM Cloud Solution ](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Soluções VMware no IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
