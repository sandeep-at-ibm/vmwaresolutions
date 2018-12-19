---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Aplicando drivers NIC nativos

O ESXi 6.5 contém muitos novos drivers nativos que são uma substituição aos drivers vmklinux anteriores. Embora a maioria dos novos drivers nativos seja ativada por padrão após a instalação ou o upgrade, três dos novos drivers nativos são desativados por padrão, porque eles não suportam totalmente as funções dos drivers vmklinux correspondentes.

O ixgben é um driver nativo que substitui o driver vmklinux net-ixgbe, mas não suporta SR-IOV e SW FcOE. A automação do ICVS não teria ativado esse driver quando o host vSphere ESXi estivesse provisionado. É aconselhável ativar esse driver para os benefícios de desempenho que ele traz. O procedimento a seguir descrito neste apêndice mostra como ativar e desativar os drivers nativos usando o vSphere Command-Line (vCLI).

Antes de iniciar esta tarefa, recupere todos os endereços IP, IDs de login e senhas IPMI dos hosts físicos do [portal de infraestrutura do {{site.data.keyword.cloud}}](https://control.softlayer.com/devices). Isso é necessário em uma restauração ou para verificar o progresso de um upgrade, em que não existe acesso direto de rede ao host.

Para cada host, sucessivamente:
1. Use o vSphere Web Client para colocar o host vSphere ESXi no modo de manutenção, selecionando **Página inicial** > **Hosts e clusters**. Na área de janela do Navegador, selecione o host vSphere ESXi e clique com o botão direito no host e selecione **Modo de manutenção** > **Entrar no modo de manutenção**. Como o host faz parte de um cluster DRS automatizado, as máquinas virtuais são migradas para hosts diferentes quando o host entra no modo de manutenção.
2. Use SSH para o host vSphere ESXi, usando os detalhes do Console do IC4VS.
3. Execute o comando vCLI a seguir para ativar os drivers nativos ixgben:
   `esxcli system module set --enabled=true --module=ixgben`
4. Execute o comando vCLI a seguir para reiniciar o host vSphere ESXi:
  `system shutdown reboot --reason “Install ixgben driver”`
5. Após o host vSphere ESXI ser reinicializado, usando SSH, efetue login novamente no host. Emita o comando vCLI a seguir e verifique se o driver ixgben está “carregado” (primeira coluna) e “ativado” (segunda coluna):
  `esxcli system module list |grep ixg`
6. Se os drivers estiverem ativados, usando o vSphere Web Client, selecione o host na área de janela do Navegador, clique com o botão direito e selecione **Modo de manutenção** > **Sair do modo de manutenção**. Selecione o próximo host e ative os drivers até que todos os hosts estejam prontos.
7. Se a mudança não funcionar, para reverter, execute o comando a seguir:
  `esxcli system module set --enabled=false --module=ixgben`

8. Se não for possível se conectar ao host pela rede, execute o comando anterior por meio do console IPMI usando a janela de controle do {{site.data.keyword.cloud_notm}}.
9. Após a reinicialização do host vSphere ESXi, você agora observa o driver ixgbe padrão que está carregado e ativado.

Se for necessário reverter e não for possível aplicar SSH ao host vSphere ESXi, será necessário efetuar login no console do KVM do host que precisa da reversão por meio da janela de controle do {{site.data.keyword.cloud_notm}}.

Use o ID e a senha listados na janela de controle do {{site.data.keyword.cloud_notm}} com o endereço IP IPMI para efetuar login na interface da web do IPMI. É necessário estar conectado ao data center no qual o host está localizado por meio da VPN. Para obter mais informações, veja [Introdução à VPN](../../../../infrastructure/iaas-vpn/getting-started.html).

1. Acesse a página Detalhes do dispositivo, gerenciamento remoto para o host vSphere ESXi e selecione **Ações** > **Console do KVM**. Outra janela será aberta para você inserir o Usuário e a Senha do IPMI.
2. Selecione **Controle remoto** > **iKVM/HTML5** e clique em **iKVM/HTML5** para ativar novamente. Agora você será capaz de acessar o console do host vSphere ESXi.
3. Se o host estiver respondendo a comandos, use **ALT-F1** no console para acessar o console do host ESXi. Use as credenciais do host para efetuar login.
4. Se o host não estiver respondendo, use os menus do IPMI para o ciclo de energia do host.
5. Observe o console do HTML5 cuidadosamente à medida que o host for reiniciado. Você terá somente alguns segundos para entrar no modo de recuperação quando o ESXi começar a ser reiniciado.
6. Pressione as teclas **CMD + R** simultaneamente para entrar no modo de recuperação.
7. Digite **"Y"** para entrar no modo de recuperação e inicialize o servidor ESXi com a versão anterior.
8. Monitore seus progressos por meio do console. Isso pode levar de 10 a 20 minutos.

### Links relacionados

* [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Soluções de VMware no {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
