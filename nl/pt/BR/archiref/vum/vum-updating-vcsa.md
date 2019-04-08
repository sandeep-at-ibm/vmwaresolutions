---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# Atualização do VCSA e vCenters vinculados à SSO
{: #vum-updating-vcsa}

## Atualização de PSC e VCSA
{: #vum-updating-vcsa-psc-vcsa-update}

Essa seção se relaciona com o vCenter Server Appliance (VCSA) e o Platform Services Controller (PSC). Ambos os
dispositivos são dispositivos VCSA, mas com funções diferentes. Ao fazer upgrade do vSphere com um PSC externo, faça
upgrade do PSC primeiro, depois do VCSA, dos hosts ESXi e, por fim, das versões de hardware e das ferramentas VMware nas
máquinas virtuais.

O VUM não atualiza o PSC/VCSA. As informações a seguir descrevem o processo de atualização desses dispositivos. O
PSC/VCSA implementado em uma instância do VMware vCenter Server on {{site.data.keyword.cloud}} não tem acesso
à Internet, portanto, o pacote configurável de atualização deve ser transferido por download para um servidor de salto
primeiro.

O PSC/VCSA é atualizado por meio do console de gerenciamento de dispositivo, não do vSphere Web Client. O console de
gerenciamento de dispositivo do PSC/VCSA é acessado usando um navegador, o endereço IP do PSC/VCSA e a porta 5480.

Deve-se iniciar uma captura instantânea do dispositivo ou um backup do PSC/VCSA antes de atualizar. Assegure-se de que tudo funcione conforme o esperado e, em seguida, remova a captura instantânea em alguns dias para evitar a degradação de desempenho. Além
disso, revise as notas sobre a liberação do VMware antes de tentar qualquer upgrade para entender qualquer
instrução específica para a liberação especificada.

Para atualizar o PSC/VCSA, siga estas etapas:
1. É possível fazer download de atualizações acessando o [Centro de Download](https://my.vmware.com/group/vmware/patch#search) de Correções do VMware, efetuando login e escolhendo VC no menu **Procurar por produto**. Selecione a correção apropriada e clique em **Download**.
2. Usando o vSphere Web Client, faça upload do arquivo ISO para o repositório de armazenamento de dados do vCenter.
3. Monte o arquivo ISO de atualização para o servidor vCenter.
4. Tome uma captura instantânea de seu servidor vCenter.
5. Efetue login no console de gerenciamento de dispositivo do vCenter em: `https://pscip:5480` (para o
PSC) ou `https://vcenterip:5480` (para o VCSA)
6. Acesse a seção **Atualização** e selecione **Verificar atualizações** e, em seguida, **Verificar CDROM**. A atualização está listada.
7. Selecione **Instalar atualizações** e **Aceitar** o EULA. A atualização é instalada.
8. Após a atualização ser concluída, deve-se voltar para o console de gerenciamento de dispositivo e selecionar para reiniciar o console.
9. Efetue login de volta no Web client do vSphere e verifique qualquer erro. Conclua uma varredura manual de VUM, **Página inicial** > **Hosts e cluster**, em seguida, selecione um data center ou cluster e selecione **guia Update Manager** e, em seguida, clique em **Varrer para atualizações**. Se a varredura manual resultar em um erro, veja [Reconfigurando o banco de dados do VMware Update Manager em um dispositivo vCenter Server 6.5 (2147284)](https://kb.vmware.com/s/article/2147284).
10. Após o teste, se precisar voltar, reverta para captura instantânea ou restaure o vCenter com um backup anterior.

## Instâncias do vCenter Server vinculadas por SSO
{: #vum-updating-vcsa-sso-vcenter}

Se você tiver instâncias primárias e secundárias do vCenter Server, os VCSAs serão configurados para estarem em um único domínio de Conexão única (SSO) do vCenter. Cada VCSA tem uma instância do VUM implementada. As propriedades de configuração que você modifica são aplicadas somente à instância do VUM especificada e que não são propagadas para as outras instâncias no grupo.

É possível especificar uma instância do VUM selecionando o nome do VCSA com o qual a instância do VUM é registrada na barra de navegação. Também é possível gerenciar linhas de base, grupos de linhas de base, varrer e corrigir somente os objetos de inventário que são gerenciados pelo VCSA com o qual a instância do VUM está registrada.

## Links relacionados
{: #vum-updating-vcsa-related}

* [Arquitetura de solução do VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrações)
