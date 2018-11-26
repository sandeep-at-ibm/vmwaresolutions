---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-07"

---

# Atualização do VCSA e vCenters vinculados à SSO

## Atualização do VCSA

O VUM não atualiza o VCSA, portanto, esta seção descreve o processo de atualização desse dispositivo. O VCSA implementado em uma instância do VMware vCenter Server on {{site.data.keyword.cloud}} não tem acesso à Internet, portanto, o pacote configurável de atualização deve ser transferido por download para um servidor de salto primeiro.

O VCSA é atualizado por meio do console de gerenciamento de dispositivo, não do vSphere Web Client. O console de gerenciamento de dispositivo VCSA é acessado usando um navegador, o endereço IP do VCSA e a porta 5480.

É necessário iniciar uma captura instantânea do dispositivo ou um backup do VCSA antes de atualizar. Certifique-se de que tudo funcione conforme o esperado e, em seguida, remova a captura instantânea dentro de alguns dias para evitar a degradação de desempenho. Adicionalmente, revise as notas sobre a liberação antes de tentar qualquer upgrade.

Para atualizar o VCSA, siga estas etapas:
1. É possível fazer download de atualizações acessando o [Centro de Download](https://my.vmware.com/group/vmware/patch#search) de Correções do VMware, efetuando login e escolhendo VC no menu **Procurar por produto**. Selecione a correção apropriada e clique em **Download**.
2. Usando o vSphere Web Client, faça upload do arquivo ISO para o repositório de armazenamento de dados do vCenter.
3. Monte o arquivo ISO de atualização para o servidor vCenter.
4. Tome uma captura instantânea de seu servidor vCenter.
5. Efetue login no console de gerenciamento de dispositivo do vCenter em: `https://vcenterip:5480`
6. Acesse a seção **Atualização** e selecione **Verificar atualizações** e, em seguida, **Verificar CDROM**. A atualização deve ser listada.
7. Selecione **Instalar atualizações** e **Aceitar** o EULA. A atualização é instalada.
8. Após a atualização ser concluída, deve-se voltar para o console de gerenciamento de dispositivo e selecionar para reiniciar o console.
9. Efetue login de volta no Web client do vSphere e verifique qualquer erro. Execute uma varredura manual do VUM, **Página inicial** > **Hosts e clusters**, em seguida, selecione um data center ou cluster e selecione **guia Update Manager** e, em seguida, clique em **Varrer atualizações**. Se isso resultar em um erro, veja [Reconfigurando o banco de dados do VMware Update Manager em um dispositivo vCenter Server 6.5 (2147284)](https://kb.vmware.com/s/article/2147284).
10. Após o teste, se precisar voltar, reverta para captura instantânea ou restaure o vCenter com um backup anterior.

## vCenters vinculados à SSO

Se você tiver instâncias primárias e secundárias do vCenter Server, os VCSAs serão configurados para estarem em um único domínio de Conexão única (SSO) do vCenter. Cada VCSA terá uma instância do VUM implementada. As propriedades de configuração que você modifica são aplicadas somente à instância do VUM especificada e que não são propagadas para as outras instâncias no grupo.

É possível especificar uma instância do VUM selecionando o nome do VCSA com o qual a instância do VUM é registrada na barra de navegação. Também é possível gerenciar linhas de base e grupos de linhas de base, bem como varrer e corrigir somente os objetos de inventário que são gerenciados pelo VCSA com o qual a instância do VUM é registrada.

### Links relacionados

* [VMware HCX no {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Soluções de VMware no {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
