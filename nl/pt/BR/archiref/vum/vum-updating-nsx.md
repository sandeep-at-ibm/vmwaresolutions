---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-15"

subcollection: vmware-solutions


---

# Atualizando o NSX
{: #vum-updating-nsx}

As informações a seguir são um exemplo do processo de atualização para NSX. Consulte o guia do VMware para obter o processo de atualização para a versão do NSX para a qual você está fazendo upgrade.

Caso seja necessário fazer upgrade do NSX e do vSphere, o VMware recomenda concluir o upgrade do NSX primeiro e, em seguida, concluir o upgrade do vSphere, pois os VIBs do NSX são específicos para a versão do ESXi que está instalada no host. No entanto, é recomendado usar o VUM, conforme especificado neste documento; se feito manualmente, use o fluxo de trabalho a seguir, um host por vez:

1. **Fazer upgrade do ESXi** - depois que o upgrade do ESXi for concluído, o host sairá do modo de manutenção, no entanto, não será possível mover MVs conectadas a comutadores lógicos para o host até que a próxima etapa seja concluída.
2. **Fazer upgrade de VIBs NSX** - depois que os VIBs forem submetidos a upgrade e o host for removido do modo de manutenção, será possível mover MVs conectadas a comutadores lógicos para o host.

O NSX é atualizado por meio da atualização do NSX Manager usando um download em _my.vmware.com_. Portanto, você precisa de uma conta para o download da atualização. Se você estiver consumindo o licenciamento de assinatura do {{site.data.keyword.cloud}} com sua instância do VMware vCenter Server on {{site.data.keyword.cloud_notm}}, não será possível fazer download das atualizações com sua conta **my.vmware.com**. Portanto, será necessário [entrar em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).

Antes de iniciar o upgrade, verifique as notas do NSX para problemas de upgrade e soluções alternativas. Usando as notas sobre a liberação, verifique se o vCenter atende aos novos requisitos do sistema para NSX.

Se você instalou qualquer software adicional de parceiros de negócios do VMware, consulte a documentação do parceiro de negócios para obter detalhes de compatibilidade e upgrade. Se você implementou instâncias primárias e secundárias do Servidor vCenter Server e tiver um ambiente do cross-vCenter NSX, consulte as notas sobre a liberação para obter o processo de upgrade correto.

Em um ambiente do cross-vCenter NSX, o dispositivo NSX Manager primário é atualizado primeiro, seguido por todos os dispositivos NSX Manager secundários.
**Downgrades não são suportados**, portanto, faça um backup do NSX Manager antes de continuar com um upgrade. Todas as configurações do NSX Edge, todos os roteadores lógicos e todos os gateways de serviços de borda são submetidos a backup como parte do backup do NSX Manager.

Depois que o NSX Manager for submetido a upgrade com êxito, não será possível fazer downgrade do NSX. É aconselhável que qualquer atividade de manutenção seja executada em uma janela de manutenção acordada, portanto, siga sua orientação corporativa. Recomenda-se que seja feito upgrade de todos os componentes do NSX em uma única janela de indisponibilidade para minimizar o tempo de inatividade e reduzir problemas de funcionalidade. O processo de upgrade do NSX pode levar algum tempo, portanto, é importante entender a ordem de upgrade de implementação do NSX:
* Gerenciador NSX
* Cluster do Controlador NSX
* Clusters de Host NSX
* É possível fazer upgrade do Edge Services Gateways a qualquer momento após o upgrade do NSX Manager
* Introspecção de guest; se usado, siga as instruções nas notas sobre a liberação

O fluxo de trabalho é o seguinte:
1. Efetue login em seu servidor de salto e, em seguida, abra um navegador.
2. Usando suas credenciais _my.vmware.com_, navegue para a seção de download e procure por _NSX for vSphere_.
3. Selecione a versão que você precisa.
4. Na página de download, selecione **Fazer upgrade do pacote configurável, fazer download agora**.
5. Faça download para uma pasta adequada.
6. ** Fazer upgrade do NSX Manager **:
  - Efetue login no NSX Manager Virtual Appliance usando o endereço IP e as credenciais que estão documentados no console do IBM Cloud for VMware Solutions e clique no botão Upgrade na página inicial.
  - Efetue login no NSX Manager.
  - Em  ** Gerenciamento de Dispositivos **, clique em  ** Backups & Restauração **.
  - Clique em Backup e insira um nome de arquivo apropriado. O VMware recomenda que você reinstale o dispositivo NSX Manager antes de restaurar dados do NSX Manager. Embora uma operação de restauração em um dispositivo NSX Manager existente possa funcionar, ela não é oficialmente suportada. A melhor prática é tomar nota das configurações de IP para o dispositivo NSX Manager para que elas possam ser usadas para especificar informações de IP e informações de localização de backup para o dispositivo NSX Manager recém-implementado.
  - Na parte superior direita, clique em **Fazer upload do pacote configurável** e faça upload do arquivo que você transferiu por download de _my.vmware.com_.
  - Leia as informações de upgrade e selecione se você deseja ativar o SSH e participar do Customer Experience Improvement Program do VMware.
  - Clique em  ** Fazer upgrade **.
  - Quando o upload for concluído, você será redirecionado para a página de login do NSX Manager. Efetue login novamente e verifique se a versão de software atual exibida está correta.
7. ** Fazer upgrade do NSX Controller Cluster **:
  - Abra o vSphere Web Client e efetue login no VCSA.
  - Navegue para **Página inicial** > **Rede e segurança** > **Instalação**, selecione a guia **Gerenciamento** e clique em **Upgrade disponível** na coluna Status do cluster do controlador.
  - Os controladores em seu ambiente são submetidos a upgrade e reinicializados um de cada vez. Depois de iniciar o upgrade, o sistema faz download do arquivo de upgrade, faz upgrade de cada controlador, reinicia cada controlador e atualiza o status de upgrade de cada controlador.
8. ** Fazer Upgrade de Clusters de Host NSX **:
  - Após o upgrade do NSX Manager e dos NSX Controllers, os clusters do host são atualizados nos VIBs do NSX nos hosts vSphere ESXi.
  - No vSphere Web Client, navegue para **Página inicial** > **Rede e segurança** > **Instalação**, selecione a guia **Preparação do host**. Para cada cluster do qual você deseja fazer upgrade, clique em **Upgrade disponível**. O Status de Instalação exibe Instalando.
  - O Status da instalação do cluster exibe _Não pronto_. Clique em **Não pronto** para exibir mais informações e clique em **Resolver todos** para tentar concluir a instalação do VIB. O host é colocado no modo de manutenção e reinicializado, se necessário, para concluir o upgrade. A coluna Status da instalação exibe Instalando. Depois que o upgrade for concluído, a coluna Status da instalação exibirá uma marca de seleção verde e a versão do NSX submetida a upgrade.
9. ** Gateways de Serviços de Edge Services **:
  - Durante o processo de upgrade, um novo dispositivo virtual do Edge é implementado ao lado do existente. Quando o novo Edge estiver pronto, os vNICs do Edge antigo serão desconectados e os vNICs do novo Edge serão conectados. O novo Edge, então, envia pacotes de ARP gratuito (GARP) para atualizar o cache do ARP de comutadores conectados. Quando o HA é implementado, o processo de upgrade é executado duas vezes. Esse processo pode afetar temporariamente o encaminhamento de pacotes.
  - No vSphere Web Client, selecione **Rede e segurança** > **NSX Edges**. Para cada instância do NSX Edge, selecione **Fazer upgrade da versão** no menu **Ações**.
  - Após o upgrade do NSX Edge ser feito com êxito, o Status será Implementado e a coluna Versão exibirá a nova versão do NSX. Se um Edge falhar ao fazer upgrade e não retroceder para a versão antiga, clique no ícone **Reimplementar o NSX Edge** e, em seguida, tente novamente o upgrade.

## Links relacionados
{: #vum-updating-nsx-related}

* [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (demonstrações)
