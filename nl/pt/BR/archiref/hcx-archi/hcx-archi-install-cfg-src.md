---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---
# Instalando e configurando o HCX na origem
{: #hcx-archi-install-cfg-src}

A instalação no local acarreta a implementação do dispositivo de gerenciamento HCX e no registro dele com o vCenter e um ou mais terminais em nuvem ativados para VCS HCX.

## Instalando o HCX Manager Appliance
{: #hcx-archi-install-cfg-src-install-hma}

Instale o dispositivo HCX Manager no vCenter no local.

1. Efetue login no **Meu VMware** e faça download do arquivo OVA do Hybrid Cloud Services na página de download do produto.
2. Abra um navegador e efetue login no vSphere Web Client. Não é possível executar essa tarefa por meio do vSphere Client. Visualize a guia  ** Página inicial ** .
3. Na lista **Árvores de inventários**, clique em **Host e clusters**.
4. Expanda a hierarquia para mostrar os data centers.
5. Clique com o botão direito no data center de destino e selecione **Implementar modelo OVF** no menu. Pode levar alguns segundos para que o item de menu **Implementar modelo OVF** apareça.
6. Escolha  ** Implementar modelo OVF **.
  1. Selecione **Arquivo local** e clique em **Procurar** para localizar o arquivo OVA transferido por download para o computador. Clique em **Avançar**.
  2. Na página **Revisar detalhes**, marque a caixa ** Aceitar opções de configuração extras** e clique em **Avançar**.
  3. Na página **Aceitar EULAs**, role para baixo para revisar o contrato de licença do usuário do VMware. Clique em  ** Aceitar **  e em  ** Avançar **.
  4. Na página **Selecionar nome e pasta**, edite o nome, se necessário, e selecione o local para o Hybrid Cloud Services. Clique em **Avançar**.
  5. Na página **Selecionar um recurso**, selecione o local de instalação.
  6. Na página **Selecionar armazenamento**, selecione o armazenamento para o Hybrid Cloud Services e clique em **Avançar**. Na lista **Selecionar formato de disco virtual**, é possível selecionar **thin provisioning** ou **thick provisioning**.
  7. Na página **Configurar redes**, mapeie o adaptador Hybrid Cloud Services para uma rede de host escolhida na lista **Destino**.
7. Na página **Modelo customizado**, insira os valores específicos para o ambiente:
  * Para as senhas, o nome do usuário padrão para a interface da linha de comandos (CLI) e a interface com o usuário da web é **admin**. O usuário e a senha **admin** para efetuar login na interface com o usuário da web são necessários, assim como uma conta do usuário **raiz** que tenha uma senha que possa ser configurada.
  * Insira e insira novamente a senha de usuário **admin** da CLI.
  * Insira e insira novamente a senha de usuário **raiz**. No futuro, se a ajuda for necessária do VMware Global Support Services (GSS), essa senha poderá ter que ser compartilhada para que eles possam solucionar problemas do sistema.
  * Para as propriedades de rede, insira o nome do host para a MV do HCX Manager. Insira o endereço IPv4 da rede, o prefixo IPv4 (o CIDR) e o gateway padrão. A tabela a seguir mostra os valores de amostra:

Tabela 1. Valores de amostra para propriedades de rede

| Campo                    | Valor           |
|--------------------------|-----------------|
| Hostname                 | HCM_1           |
| Endereço IPv4 da Rede 1   | 192.168.200.101 |
| Prefixo IPv4 da Rede 1    | 24              |
| Gateway IPv4 padrão     | 192.168.200.1   |
| Endereço IPv6 da Rede 1   |                 |
| Prefixo de 1 IPv6 de Rede    |                 |

8. Revise a página de ligações do vService. Clique em  ** Avançar **  para continuar.
9. Na página **Pronto para concluir**, siga estas etapas:
  * Marque a caixa **Ligar após a implementação**.
  * Revise as configurações do Hybrid Cloud Services e clique em **Concluir**. Pode levar vários minutos para que o dispositivo do Hybrid Cloud Services seja ligado.
  * Para verificar o status, acesse a página inicial do vSphere Web Client e, na guia **Página inicial**, acesse **Inventários** e clique em **Hosts e clusters**. Expanda a hierarquia do data center e clique na máquina virtual do serviço Hybrid Cloud Services para exibir um resumo na área de janela central.
  * Visualize a guia **Resumo**, o console lê **Ligado** e o botão **Reproduzir** é verde.
10. O HCX Manager está ligado e pronto para ser registrado com o vCenter.

## Links relacionados
{: #hcx-archi-install-cfg-src-related}

* [Preparando o ambiente de instalação](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-prep-install)
