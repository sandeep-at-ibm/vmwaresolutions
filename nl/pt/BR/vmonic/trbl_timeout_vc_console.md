---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-07"

keywords: troubleshooting, vSphere timeout, timeout console

subcollection: vmware-solutions


---

# Tempo limite atingido ao se conectar ao VMware vSphere Web Client
{: #trbl_timeout_vc_console}

## Problema
{: #trbl_timeout_vc_console-problem}

Ao tentar se conectar ao vSphere Web Client, você pode obter o seguinte erro de tempo limite:

`The server at <IP_address> is taking too long to respond.`

## Resolução
{: #trbl_timeout_vc_console-resolution}

Use as etapas a seguir para investigar e corrigir o problema.

1. Assegure-se de ter concluído as etapas da dica de ferramenta que é exibida quando você passa o mouse sobre o botão **Console do vCenter**. Para
   sua conveniência, essas etapas também são listadas da seguinte maneira:   
   1. Instale o plug-in do Adobe Flash Player para o seu navegador.   
   2. Crie uma senha de VPN do {{site.data.keyword.slportal_full}}.    
   3. [Efetue login na VPN do data center](/docs/infrastructure/iaas-vpn?topic=VPN-getting-started#login-to-the-vpn) usando as credenciais da VPN de infraestrutura do {{site.data.keyword.cloud_notm}}.    
   4. Inclua o endereço IP e o mapeamento de nome do host do PSC (Platform Services Controller) no arquivo `hosts` por meio de seu computador local. Use o formato a seguir:

      ```javascript
      IP_Address              Host_Name
      ```

2. Anote o endereço IP que é exibido, porque você precisará dele em uma das próximas etapas.
3. Assegure-se de ter acesso ao VPN de infraestrutura do {{site.data.keyword.cloud_notm}}. Conclua as etapas a seguir no {{site.data.keyword.slportal}}:
   1. Clique em **Conta > Acesso VPN**.
   2. Clique no **Link SSL** na coluna **Acesso VPN**.
   3. Na página **Acesso VPN para nome do usuário**, configure a opção **Acesso à Sub-rede** como **Manual**.
   4. Na mesma página, localize a sub-rede para o par endereço IP/nome do host. Para obter mais informações, consulte a  ** Etapa 2 **.    

      Por exemplo, se o endereço IP para sua instância for `xx.yyy.zz.15` e o endereço IP para vCenter for `xx.yyy.zz.10`, você deverá conceder acesso para a sub-rede `xx.yyy.zz.0/26`.

   5. Marque a caixa de seleção **Conceder Acesso** para essa sub-rede e clique em **Salvar**.
