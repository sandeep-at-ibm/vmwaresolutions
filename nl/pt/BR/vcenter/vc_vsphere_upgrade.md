---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-30"

keywords: vSphere upgrade, NSX upgrade, PSC upgrade

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Fazendo upgrade do software vCenter Server vSphere do VMware vSphere 6.5 para 6.7
{: #vc_vsphere_upgrade}

A oferta vCenter Server on {{site.data.keyword.cloud}} é uma solução de implementação totalmente automatizada para a pilha SDDC do VMware vSphere, incluindo produtos vSphere, NSX e opcionalmente vSAN. Embora o vCenter Server automatize as partes mais desafiadoras da implementação, da expansão e da contração de uma infraestrutura baseada no VMware SDDC, ele não é um serviço gerenciado. Como o vCenter Server tem uma política de suporte à automação de versões do software VMware SDDC dentro do intervalo de N-1, deve-se fazer upgrade de instâncias existentes do vCenter Server se você deseja continuar a se beneficiar da automação do {{site.data.keyword.vmwaresolutions_short}}.

As versões do vCenter Server fora dos níveis necessários para o suporte à automação continuam sendo suportadas, conforme necessário, pela política de suporte do VMware, mas não funcionam mais com a automação do {{site.data.keyword.vmwaresolutions_short}}. Deve-se executar a correção periódica e o upgrade do software VMware durante o ciclo de vida de uma instância do vCenter Server. Isso inclui o upgrade do software VMware SDDC para uma versão que seja suportada pela automação do {{site.data.keyword.vmwaresolutions_short}}, conforme necessário.

O procedimento a seguir fornece as etapas necessárias para converter uma instância baseada no vCenter Server VMware vSphere 6.5 em uma instância baseada no vCenter Server VMware vSphere 6.7. Estas etapas fornecem o upgrade inicial para o nível 6.7 mais recente do vSphere, NSX e vSAN. Após esse upgrade, talvez seja necessário usar a funcionalidade normal do vSphere para fazer upgrade de níveis de hardware da máquina virtual (VM) e ferramentas.

O vCenter Server foi projetado para permitir um upgrade “contínuo”. Ou seja, as cargas de trabalho da VM que estão atualmente em funcionamento continuarão funcionando sem uma indisponibilidade se você concluir o procedimento a seguir. As empresas devem envolver suas políticas de gerenciamento de mudanças para permitir um upgrade estruturado e comunicado e planejar para contingências. No entanto, durante o processo de upgrade de determinadas funções de gerenciamento, como o vCenter e o NSX Manager, indisponibilidades temporárias de funções de gerenciamento, mudanças na configuração, desligamento e ligação de VMs podem ser afetadas.
{:note}

## Antes de iniciar
{: #vc_vsphere_upgrade-prereq}

O tempo estimado para executar o upgrade é desconhecido. O upgrade completo de um ambiente pode exigir várias janelas de manutenção. A execução de versões niveladas para cima e niveladas para baixo do software SDDC é suportada pelo VMware durante o processo de upgrade. No entanto, algumas funções como vMotion talvez sejam limitadas durante esse processo.

Conclua os requisitos a seguir antes de iniciar o upgrade:  
* É sua responsabilidade fazer upgrade de quaisquer extensões ou snap-ins dentro do ambiente do vCenter Server. Revise a documentação a seguir antes de planejar seu upgrade:
  * [Notas sobre a liberação do VMware vCenter Server 6.7 Atualização 1b](https://docs.vmware.com/en/VMware-vSphere/6.7/rn/vsphere-vcenter-server-67u1b-release-notes.html){:external}
  * [Sobre o upgrade do VMware ESXi](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.upgrade.doc/GUID-65B5B313-3DBB-4490-82D2-A225446F4C99.html){:external}
* Configure o vSphere Update Manager (VUM) dentro da instância do vCenter Server para fazer download das atualizações mais recentes do VMware vSphere. Para obter mais informações, consulte [Introdução ao VMware Update Manager](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vum-intro#vum-intro).
* Abra um chamado de suporte com a equipe do {{site.data.keyword.vmwaresolutions_short}} para notificá-los de que um upgrade está sendo executado. O chamado permanece aberto até que a instância seja registrada no nível submetido a upgrade no console do {{site.data.keyword.vmwaresolutions_short}}.
* Confirme se a instância do vCenter Server da qual você está fazendo upgrade está vinculada ou não a outra instância do vCenter Server como primária ou secundária no console do {{site.data.keyword.vmwaresolutions_short}}. Todas as instâncias vinculadas devem ter seus Platform Services Controllers (PSCs) submetidos a upgrade primeiro como parte de um upgrade de site específico.
* Confirme o seguinte para instâncias baseadas no vSAN:
  * Assegure-se de que a ferramenta vSAN Health esteja ativada e não relate erros críticos. Se erros críticos estiverem presentes, entre em contato com a equipe de Suporte da IBM com o ID do chamado de suporte de upgrade.
  * Assegure-se de que haja espaço em cada nó para manipular a reconstrução de redundância de objetos do vSAN caso um host ESXi falhe ao ficar ativo novamente durante o upgrade. Pode ser necessário reduzir o uso de disco ou incluir um host ESXi adicional antes do upgrade.  
  * Verifique se o volume geral do vSAN está ou não acima de 70 por cento utilizado. Pode ser necessário reduzir o uso de disco ou incluir um host ESXi adicional antes do upgrade.
* Se a sua instância do vCenter Server iniciou como um {{site.data.keyword.vmwaresolutions_short}} V2.5 ou mais recente, deve-se entrar em contato com o Suporte IBM para a senha do ID do usuário **raiz** para o PSC e o vCenter, já que somente uma conta de serviços com acesso **customerroot** está visível no portal. Se o ID do usuário **raiz** do PSC e do vCenter estiver visível com sua senha, essa etapa não será necessária.
* Confirme se você tem um ID do usuário do https://my.vmware.com para o qual fazer download dos binários de upgrade necessários. Se você não tiver, entre em contato com o Suporte IBM com o ID do chamado de suporte de upgrade.
* Confirme se o VUM está configurado para acessar https://www.vmware.com para fazer download de correções. Se não for possível configurá-lo por causa de políticas de segurança, será necessário fazer download manualmente dos conjuntos de correções mais recentes e fazer upload deles para o VUM. Para obter mais informações, consulte [Introdução ao VMware Update Manager](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro).

### Preparando seu jumpbox
{: #vc_vsphere_upgrade-prereq-jumpbox}

Como a VPN de acesso do cliente do {{site.data.keyword.cloud_notm}} é limitada a 512 Kbps, recomenda-se provisionar uma Instância de Servidor Virtual (VSI) do servidor Windows 2012-2016 do {{site.data.keyword.cloud_notm}} ou configurar uma VM do Windows semelhante em um ambiente do vSphere vCenter Server separado dentro do mesmo {{site.data.keyword.CloudDataCent_notm}}. Isso é usado como um jumpbox na instância do vCenter Server para fazer upgrade e permite downloads rápidos de https://my.vmware.com para os binários. Embora seja possível colocar essa VM na instância do vCenter Server que está sendo submetida a upgrade, isso não é recomendável.

Conclua as etapas a seguir para pedir um jumpbox de VSI.

Ignore a primeira etapa se você já tiver um jumpbox de VSI em seu ambiente.
{:note}

1. Peça uma VSI por hora ou mensal por meio do portal do cliente de infraestrutura do [{{site.data.keyword.cloud_notm}}](https://control.softlayer.com/){:external}. Peça os atributos a seguir:
  * Windows 2012 ou 2016 Server Standard
  * 2 CPUs
  * 16 GB de memória
  * 100 G de disco
  * Uplinks público e privado de 1 Gbps
2. Quando a VSI for provisionada, configure as Listas de Controle de Acesso (ACLs) do {{site.data.keyword.cloud_notm}} dentro do painel de controle para permitir todo o ingresso e egresso dos links privados e somente o egresso do público. Deve-se usar a VPN de acesso do cliente do {{site.data.keyword.cloud_notm}} para sessões do Remote Desktop Protocol (RDP) para a VSI do Windows.
3. RDP para a VSI do Windows. Modifique suas configurações do Sistema de Nomes de Domínio (DNS) no adaptador de rede privada para apontar somente para o servidor Windows AD dentro da instância do vCenter Server para fazer upgrade.
4. Faça download e instale o navegador Google Chrome. É possível usar o Mozilla Firefox, mas ele tem um problema de cache ao usar as telas do VUM dentro da interface com o usuário do vCenter.
5. Faça download de seu software de terminal preferencial do SSH. Por exemplo, Putty.
6. Use o Google Chrome para acessar a instância do vCenter Server para fazer upgrade. Use **administrator@vsphere.local** e assegure-se de que seja possível visualizar a interface com o usuário.  
7. Verifique o ambiente do vSphere quanto a erros e problemas, conforme discutido na seção anterior.
8. Use seu software de terminal SSH para acessar o PSC e o vCenter com o portal ou as senhas fornecidas pelo suporte para **raiz**.
9. Opcionalmente, use o ID do usuário **raiz** e a senha observados no painel de controle do SL para acessar cada host ESXi para verificar a senha **raiz**.

#### Fazendo download de arquivos binários
{: #vc_vsphere_upgrade-prereq-jumpbox-binary}

Use seu jumpbox VSI do Windows e efetue login em sua conta https://my.vmware.com para fazer download dos arquivos binários a seguir:

* Imagem do VMware vSphere 6.7u1 Hypervisor (ESXi ISO) (inclui ferramentas do VMware)
* ISO do dispositivo vCenter 6.7u1b. Não o pacote configurável de atualização.
* Pacote configurável de upgrade do NSX for vSphere 6.4.4

Para unidades Intel Optane, faça download do arquivo a seguir para usar como parte do processo de correção de pós-upgrade que utiliza o VMware Update Manager.

Localize o arquivo ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` para o driver Intel NVMe para Intel® Optane™ SSD DC P4800X Series SSDPED1K750GA (750 GB, HHHL) em https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX67-INTEL-INTEL-NVME-VMD-1401016&productId=742.

#### Fazendo backup de componentes

Antes de iniciar o upgrade, faça backup de cada componente.

* Para obter informações sobre o backup do vCenter Server e dos PSCs, consulte [Visão geral de opções de backup e restauração no vCenter Server 6.x (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:external}.
* Para obter considerações adicionais e informações sobre o backup do vCenter Server e dos PSCs, consulte [Backup baseado em arquivo do vCenter](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup#solution_backingup-vcenter).
* Para obter informações sobre o backup do NSX, consulte [Fazendo backup de dados do NSX Manager](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:external}.

Recomenda-se usar o backup baseado em arquivo. O backup baseado em imagem (usando o vSphere Data Protection) não é suportado no VMware vSphere 6.7.
{:note}

## Procedimento para fazer upgrade do software IBM vCenter Server vSphere de 6.5 para 6.7
{: #vc_vsphere_upgrade-procedure}

Se você encontrar um problema a qualquer momento durante o processo de upgrade, use o chamado de upgrade do {{site.data.keyword.vmwaresolutions_short}} que foi aberto no início do processo para entrar em contato com o Suporte IBM. O Suporte IBM abre chamados com o suporte do VMware conforme necessário.

**Importante**:

* Deve-se usar esse caminho para assegurar que o {{site.data.keyword.vmwaresolutions_short}} forneça suporte do VMware com todas as informações necessárias sobre o design do vCenter Server, a configuração e as informações do {{site.data.keyword.cloud_notm}}. Seguir esse processo para assegurar que informações precisas sejam compartilhadas com o suporte do VMware reduz a experiência de suporte. Depois que o Suporte IBM fornece as informações necessárias para o suporte do VMware, é possível interagir diretamente com o suporte do VMware conforme necessário.
* Assegure-se de manter registro de todas as novas senhas e credenciais criadas como uma parte desse processo de upgrade. O suporte IBM requer essas credenciais no término do processo de upgrade para atualizar seu banco de dados interno.

### Fazendo upgrade do VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx}

O upgrade do VMware NSX pode levar algum tempo porque o processo de upgrade atualiza os vSphere Installation Bundles nos hosts ESXi e requer uma reinicialização de cada host. Planeje sua janela de manutenção adequadamente.

#### Antes de fazer upgrade do VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-before}

* Se você tiver o Zerto for {{site.data.keyword.cloud_notm}} instalado em seu ambiente, use a interface com o usuário do Zerto para encerrar as VMs zVRA em cada host. Selecione **Permitir que o Zerto insira entre os hosts no modo de manutenção durante a correção** dentro das configurações de site do Zerto, seção de políticas na interface com o usuário do Zerto. Caso contrário, o Zerto inicializará o zVRA e impedirá que o upgrade continue, não permitindo que o host ESXi que está sendo submetido a upgrade entre no modo de manutenção.
* Para VMs que não têm as ferramentas do VMware instaladas, encerre manualmente ou desligue de maneira forçada antes da instalação do módulo do host NSX ESXi. Essas VMs impedem o host ESXi de destino de entrar no modo de manutenção.

#### Procedimento para fazer upgrade do VMware NSX
{: #vc_vsphere_upgrade-procedure-nsx-procedure}

Consulte o [Guia de upgrade do NSX](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:external} para obter detalhes relacionados ao procedimento a seguir.

1. Leia as notas sobre a liberação do NSX 6.4.4 para assegurar a compatibilidade com sua configuração de ambiente específica. Para obter mais informações, consulte [Notas sobre a liberação do VMware NSX Data Center for vSphere 6.4.4](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:external}.
2. Faça upgrade do NSX Manager primeiro. Se você tiver múltiplos ambientes NSX que usam o modo de link de vários vCenters, faça upgrade de todos os gerenciadores NSX antes de fazer upgrade de componentes na interface com o usuário do NSX **Coordenador de upgrade**.
3. Use o **Coordenador de upgrade** na interface com o usuário do NSX dentro da interface com o usuário do vCenter para fazer upgrade de componentes do NSX.
4. Continue revisando e monitorando a interface com o usuário de upgrade do NSX dentro da interface com o usuário do vCenter à medida que os possíveis problemas são resolvidos para assegurar que o upgrade continue até que todos os componentes sejam submetidos a upgrade.

### Fazendo upgrade do Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc}

Se você tem instâncias vinculadas do vCenter Server, deve-se fazer upgrade de todas as instâncias do PSC nos sites primário e secundário do vCenter Server. Como as instâncias vinculadas do vCenter Server criam uma topologia hub-and-spoke de replicação do PSC com a instância primária do vCenter Server sendo o hub, recomenda-se iniciar fazendo upgrade do PSC da instância primária do vCenter Server e, em seguida, fazer upgrade de cada PSC do site secundário.

#### Antes de fazer upgrade do Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc-before}

* Tenha suas senhas raiz do vCenter e do PSC disponíveis para o procedimento a seguir. Use o console do {{site.data.keyword.vmwaresolutions_short}} para observar se sua versão da instância do vCenter Server foi submetida a upgrade ou não da V2.4 ou anterior para a V2.7 ou mais recente.
* No console do {{site.data.keyword.vmwaresolutions_short}}, uma única senha para raiz para o PSC e o vCenter é exibida. No entanto, essa é somente a senha do vCenter. Deve-se [entrar em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) para obter a senha raiz do PSC.
* Para evitar conflitos, use o endereço IP na parte superior da mesma sub-rede que o vCenter e o PSC estão usando atualmente. Deve-se usar um endereço IP temporário para a nova implementação do dispositivo.

#### Procedimento para fazer upgrade do Platform Services Controller
{: #vc_vsphere_upgrade-procedure-psc-procedure}

1. Efetue login nas interfaces com o usuário de gerenciamento de dispositivo do PSC, `https://<psc-fqdn>:5480` e do vCenter para confirmar se a senha raiz expirou ou não. Se a data de expiração de senha é **1970**, então ela expirou e deve-se ativar o SSH e o shell bash na interface com o usuário de gerenciamento de dispositivo do PSC.
    1. Use SSH para o PSC com o ID raiz e a senha. Mesmo que a senha tenha expirado, ela permite que você efetue login.
    2. Use o comando shell **passwd** para configurar uma nova senha raiz para o PSC e o vCenter.
    3. Salve as senhas que foram exibidas no console do {{site.data.keyword.vmwaresolutions_short}} ou fornecidas a você pelo Suporte IBM. Essas senhas são reutilizadas posteriormente ao fazer upgrade dos dispositivos.
2. Use a função de montagem ISO do Windows integrada para montar o vCenter 6.7u1b ISO dentro de seu jumpbox.
3. Siga as instruções do VMware para fazer upgrade de todos os PSCs primeiro. Para obter mais informações, consulte [Fazer upgrade de um vCenter Server Appliance 6.0 ou 6.5 com uma instância externa do vCenter Single Sign-On ou do Platform Services Controller usando a GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html){:external}.

O requisito declarado **Deve-se executar o upgrade da GUI em uma máquina Windows, Linux ou Mac que esteja na mesma rede que o dispositivo do qual você deseja fazer upgrade** se aplica a qualquer sub-rede dentro de seu {{site.data.keyword.cloud_notm}} em sua conta.
{:note}

É recomendável usar o vCenter como sua origem e destino para o upgrade.

### Fazendo upgrade do vCenter
{: #vc_vsphere_upgrade-procedure-vcenter}

Para instâncias vinculadas do vCenter Server, embora seja recomendável fazer upgrade de todas as instâncias do vCenter nos sites primário e secundário do vCenter Server, isso não é necessário.

#### Antes de fazer upgrade do vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-before}

* Tenha suas senhas raiz do vCenter e do PSC disponíveis para o procedimento a seguir. Use o console do {{site.data.keyword.vmwaresolutions_short}} para observar se sua versão da instância do vCenter Server foi submetida a upgrade ou não da V2.4 ou anterior para a V2.7 ou mais recente.
* Para evitar conflitos, use o endereço IP na parte superior da mesma sub-rede que o vCenter e o PSC estão usando atualmente. Deve-se usar um endereço IP temporário para a nova implementação do dispositivo.

#### Procedimento para fazer upgrade do vCenter
{: #vc_vsphere_upgrade-procedure-vcenter-procedure}

1. Efetue login nas interfaces com o usuário de gerenciamento de dispositivo do PSC, `https://<psc-fqdn>:5480` e do vCenter para confirmar se a senha raiz expirou ou não. Se a data de expiração de senha é **1970**, então ela expirou e deve-se ativar o SSH e o shell bash na interface com o usuário de gerenciamento de dispositivo do PSC.
    1. Use SSH para o PSC com o ID raiz e a senha. Mesmo que a senha tenha expirado, ela permite que você efetue login.
    2. Use o comando shell **passwd** para configurar uma nova senha raiz para o PSC e o vCenter.
    3. Salve as senhas que foram exibidas no console do {{site.data.keyword.vmwaresolutions_short}} ou fornecidas a você pelo Suporte IBM. Essas senhas são reutilizadas posteriormente ao fazer upgrade dos dispositivos.
2. Use a função de montagem ISO do Windows integrada para montar o vCenter 6.7u1b ISO dentro de seu jumpbox.
3. Siga as instruções do VMware para fazer upgrade do vCenter. Para obter mais informações, consulte [Fazer upgrade de um vCenter Server Appliance 6.0 ou 6.5 com uma instância externa do vCenter Single Sign-On ou do Platform Services Controller usando a GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html){:external}. As instruções do VMware são semelhantes ao processo de upgrade do PSC. No entanto, em vez de apontar
para o PSC, aponte para o vCenter FQDN/IP para o processo de upgrade.

**Notas**:
* O requisito declarado **Deve-se executar o upgrade da GUI em uma máquina Windows, Linux ou Mac que esteja na mesma rede que o dispositivo do qual você deseja fazer upgrade** se aplica a qualquer sub-rede dentro de seu {{site.data.keyword.cloud_notm}} em sua conta.
* É recomendável usar o vCenter como sua origem e destino para o upgrade.

#### Consolidando a função PSC no vCenter

1. Depois de concluir com êxito o upgrade do PSC e do vCenter, efetue login na interface com o usuário baseada no vCenter FLEX e verifique o funcionamento de todos os serviços relacionados ao vCenter e ao PSC na seção **Configuração do sistema**.  
2. Faça backup do seu PSC.  Recomenda-se usar o backup baseado em arquivo. Para obter mais informações, consulte [Backup baseado em arquivo no vSphere 6.7](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.install.doc/GUID-8A16C037-F1E0-40C9-B106-05C30625B9CB.html){:external}.
3. Navegue para o diretório ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\converge``.
4. Copie o arquivo ``converge.json`` para uma unidade local em sua VM de salto.
  * Se este é o primeiro PSC que você está consolidando, deve-se remover a seção **replication** do arquivo ``json``.
  * Se este é um PSC vinculado subsequente, deve-se preencher os atributos solicitados na seção **replication** do arquivo ``json``.
5. Navegue para o diretório ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\templates\decommission``.
6. Copie o arquivo ``decommission_psc.json`` para uma unidade local em sua VM de salto.
7. Edite os arquivos ``converge.json`` e ``decommission_psc.json``. As instruções para os campos a serem editados estão nos arquivos ``json``. É recomendável que o host ESXi contendo o PSC seja usado em vez do vCenter na seção **managing_esxi_or_vc**.
8. Navegue para o diretório ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` em uma janela de comando.
9. Execute o ``vcsa-util.exe`` com o comutador **converge** e o caminho para o arquivo ``converge.json`` editado anteriormente. Por exemplo, ``vcsa-util converge --no-ssl-certificate-verification c:\temp\converge.json -v``.
   1. Digite **Y** para confirmar se o PSC foi submetido a backup para continuar.
   2. Quando o processo for concluído, digite **Y** para confirmar a reinicialização do vCenter.

   Se o processo converge falhar com a mensagem ``ERRO converge falhou ao obter usuários vecs e as permissões``, consulte [Falha de converge para integrado](https://virtualtassie.com/2018/vcenter-6-7-update-1-converge-to-embedded-failed/#comment-3713){:external} para obter as etapas de resolução do erro.
   {:note}

10. Após o vCenter ser reinicializado, verifique a operação normal efetuando login na interface com o usuário do vCenter.
11. Navegue para o diretório ``<VCSA 6.7 iso mount>:\vcsa-converge-cli\win32`` em uma janela de comando.
12. Execute o ``vcsa-util.exe`` com o comutador **decommission** e o caminho para o arquivo ``decommission_psc.json`` editado anteriormente. Por exemplo, ``vcsa-util decommission --no-ssl-certificate-verification c:\temp\decommission_psc.json -v``.
13.	Quando o comando for concluído com êxito, efetue login na interface com o usuário do vCenter Flex e verifique se o dispositivo do vCenter é o único listado em ambientes não vinculados e se todos os serviços estão funcionais.
14. Exclua o PSC antigo, o vCenter e as VMs do PSC consolidadas não usadas.
15. Renomeie o vCenter Server dentro da interface com o usuário do vCenter para **<instancename>_vc_separate**. Por exemplo, se o nome da instância do vCenter Server for **production**, o nome da interface com o usuário do vCenter será **production_vc_separate**. Isso é necessário para que a automação possa continuar sua função para essa instância do vCenter Server.  

### Fazendo upgrade de hosts ESXi
{: #vc_vsphere_upgrade-procedure-esxi}

A função VMware Update Manager no vCenter é utilizada para fazer upgrade e corrigir os hosts ESXi para o nível 6.7u1. Semelhante à seção de upgrade do NSX deste documento, qualquer VM que não possa usar vMotion para outro host deve ser encerrada sem problemas, caso contrário, isso poderá causar paralisação no processo de upgrade.
{:note}

#### Fazendo upload do ESXi ISO no VUM
{: #vc_vsphere_upgrade-procedure-esxi-iso}

1. Assegure-se de que você tenha o VUM configurado para fazer download de correções por meio de https://www.vmware.com. Para obter mais informações, consulte [Introdução ao VMware Update Manager](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro#vmware-update-manager-introduction).
2. Use Flex ou HTML para abrir a interface com o usuário do vCenter e navegue para a **Visualização de administrador do VUM**.
3. Na **Visualização de administrador do VUM**, selecione a guia **Imagens do ESXi** e selecione **Importar imagens do ESXi**.
4. Procure a imagem **ESXi 6.7u1iso** que foi transferida por download do VMware e importe-a para o repositório do VUM.

#### Procedimento para fazer upgrade dos hosts ESXi
{: #vc_vsphere_upgrade-procedure-esxi-upgrade}

1. Na interface com o usuário do vCenter, navegue para o cluster que contém os hosts ESXi para fazer upgrade.
2. Clique na guia de **atualizações** no painel de navegação. Acesse as atualizações do host e clique em **Conectar**.
3. Selecione a linha de base (imagem ISO para upgrade do ESXi) transferida por upload para o VUM e clique em **Corrigir**.
4. Aceite o Contrato de Licença do Usuário Final e clique em **OK**.
5. Revise os hosts a serem corrigidos e confirme os resultados da verificação de pré-correção.

   Deve-se remover quaisquer CDs ou DVDs conectados às VMs ou o host que contém essa VM não terá permissão para entrar no modo de manutenção.
   {:note}

6. Depois que a verificação de pré-correção for bem-sucedida, clique em **Corrigir**. Monitore o processo de upgrade com a tarefa de entidade de correção.
7. Após a conclusão do upgrade, revise a seção de resumo do host para confirmar que o ``VMware ESXi, 6.7.0`` está exibido.

Se o processo de upgrade falhar imediatamente e exibir a mensagem de erro **o host não pode entrar no modo de manutenção**, encerre os Zerto ZVAs e tente novamente. As VMs do ZVRA iniciam automaticamente quando cada servidor sai da correção. Para obter informações sobre como continuar a replicação do Zerto durante o processo de upgrade, consulte [Como colocar um host com um VRA associado no modo de manutenção](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/){:external}.
{:note}

#### Incluindo a correção do driver Intel NVME no repositório do VUM
{: #vc_vsphere_upgrade-procedure-esxi-nvme}

Conforme descrito na seção de downloads binários, deve-se importar o conteúdo do arquivo ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` para o repositório. Em seguida, ele será aplicado à seção de continuidade como uma extensão não crítica do host ESXi.

1. Extraia o arquivo ``VMW-ESX-6.7.0-intel-nvme-vmd-vmd-vmd-1.4.0.1016-8733247.zip`` em uma unidade local em sua VM de salto.
2. Use Flex ou HTML para abrir a interface com o usuário do vCenter e navegue para a **Visualização de administrador do VUM**.
3. Na **Visualização de administrador do VUM**, selecione a guia **Repositório de correção** e selecione **Importar correções**.
4. Procure o conteúdo extraído do diretório ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` e selecione o arquivo ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-offline_bundle-8733247.zip``. O arquivo é importado imediatamente para o repositório do VUM.

Localize a imagem no repositório de correção como uma Extensão de host **importante**.

#### Corrigindo os hosts ESXi
{: #vc_vsphere_upgrade-procedure-esxi-patch}

Após o upgrade, é recomendável aplicar todas as correções críticas e não críticas do host ESXi.

1. Na interface com o usuário do vCenter, selecione o cluster que contém os hosts a serem corrigidos.
2. Clique na guia de **atualizações** no painel de navegação e selecione a guia **Atualizações do host**. Selecione **Correções críticas do host (predefinidas)**. Repita o procedimento para fazer upgrade dos hosts ESXi.
3. Clique na guia de **atualizações** no painel de navegação e selecione a guia **Atualizações do host**. Selecione **Correções não críticas do host (predefinidas)**. Repita o procedimento para fazer upgrade dos hosts ESXi.

Talvez seja necessário encerrar as VMs Zerto zVRA novamente como parte deste processo.
{:note}

### Fazendo upgrade de itens adicionais
{: #vc_vsphere_upgrade-procedure-addtl}

#### Fazendo upgrade da versão do vSAN On Disk Format
{: #vc_vsphere_upgrade-procedure-addtl-vsan}

Faça upgrade da versão do vSAN Disk Format para a versão 7.

1. Navegue para o cluster que contém o vSAN para fazer upgrade na interface com o usuário do vCenter.
2. No objeto de cluster, selecione **Configuração > vSAN > Geral**.
3. Clique em **Pré-verificar o upgrade** para verificar a compatibilidade de upgrade e os possíveis problemas. Aguarde até que a verificação retorne **Pronto para fazer upgrade**.
4. Clique em  ** Fazer upgrade **. Como o upgrade processa um grupo de disco de cada vez, isso pode levar algum tempo para ser concluído, dependendo do tamanho do cluster. Opcionalmente, selecione **redundância reduzida** durante o processo. Embora possa reduzir significativamente o tempo que leva para o upgrade, isso poderá resultar em perda de dados se houver uma falha de disco durante o processo de upgrade.

#### Fazendo upgrade do Virtual Distributed Switch
{: #vc_vsphere_upgrade-procedure-addtl-vds}

O upgrade do Virtual Distributed Switch (VDS) para a v6.6.0 também faz upgrade do controle de E/S de Rede e inclui suporte ao Link Aggregation Control Protocol (LACP) aprimorado.

1.	Se você tem o HCX implementado, deve-se remover a implementação da parte do Cloud Gateway do HCX antes de fazer upgrade do VDS no qual ele reside. Assegure-se de que o HCX seja atualizado para a versão mais recente antes da reimplementação do Cloud Gateway.
2.	Na interface com o usuário do vCenter, navegue para a guia **Rede**.
3.	Clique com o botão direito no comutador distribuído para fazer upgrade (**SDDC-Dswitch-Private** ou **SDDC-Dswitch-Public**) e selecione **Fazer upgrade do comutador distribuído**.

#### Fazendo upgrade de extensões e plug-ins da interface com o usuário do vCenter
{: #vc_vsphere_upgrade-procedure-addtl-extension}

É sua responsabilidade fazer upgrade de quaisquer extensões ou snap-ins dentro do ambiente do vCenter Server. Na interface com o usuário do vCenter, clique em **Página inicial > Administração > Soluções** para visualizar o status e ativar ou desativar extensões e plug-ins do vCenter.

#### Fazendo upgrade de ferramentas do VMware
{: #vc_vsphere_upgrade-procedure-addtl-tools}

Use a interface com o usuário do vCenter para executar upgrades de ferramentas guest do VMware. Algumas ferramentas do VMware podem ser necessárias em algumas VMs mais antigas que foram migradas para o ambiente do vCenter Server.  

#### Fazendo upgrade do nível de hardware da máquina virtual
{: #vc_vsphere_upgrade-procedure-addtl-vmhw}

Semelhante a ferramentas guest do VMware, um upgrade de ambiente do vCenter Server pode fazer com que as VMs mais antigas fiquem em um estado não suportado em seu nível de hardware atual. Use a interface com o usuário do vCenter para localizar e atualizar essas VMs conforme necessário.  

#### Configurando o modo Enhanced vMotion Compatibility para o Intel Skylake
{: #vc_vsphere_upgrade-procedure-addtl-evc}

É possível configurar hosts com a geração do Intel Skylake para um cluster no modo Skylake Enhanced vMotion Compatibility (EVC) após o upgrade. Use as etapas a seguir para atualizar o modo EVC:

1. No cluster que contém os hosts, clique em **Configurar**.
2. No **VMware EVC**, clique em **Editar** e mude o modo de EVC para **Geração Intel "Skylake"**.

Para obter mais informações, consulte [Suporte ao processador Enhanced vMotion Compatibility (EVC) (1003212)](https://kb.vmware.com/s/article/1003212){:external}.

#### Reconfigurando o gerenciador NSX e o gerenciador HCX para apontar para o PSC

1. Em um navegador da web, navegue até a interface com o usuário do dispositivo NSX Manager em ``https://<nsx-manager-ip>`` ou ``https://<nsx-manager-hostname>``. Efetue login com as credenciais.
2. Na página inicial, clique em **Gerenciar registro do vCenter**.
3. Edite a **URL de serviço de consulta** para apontar para o IP do vCenter. Use o PSC independente integrado **O PSC não existe mais**.

## Resultados após o upgrade do software vCenter Server vSphere
{: #vc_vsphere_upgrade-results}

A execução da verificação de funcionamento do vSAN após o upgrade ser concluído pode trazer avisos sobre atualizações de firmware para os controladores RAID e de rede fornecidos pelo {{site.data.keyword.cloud_notm}}. Depois de determinar os hosts que precisam de atualizações de firmware, abra um chamado com o Suporte IBM para obter o firmware atualizado para as versões recomendadas.

1. Na interface com o usuário do vCenter, selecione o cluster que contém o vSAN com funcionamento a ser verificado.
2. Selecione a guia **Monitorar** e, em seguida, selecione a guia **vSAN**.
3. Selecione **Funcionamento** e anote quaisquer avisos exibidos.
4. Se um aviso de **Compatibilidade de hardware** for exibido, expanda o aviso e clique na mensagem **O firmware do controlador é certificado pelo VMware**, se estiver em um estado de aviso.
5. Anote os hosts listados com recomendações de atualização de firmware.
6. Abra um chamado com o Suporte IBM para planejar um horário para retirar cada host de serviço para permitir atualizações de firmware.

Quando seu upgrade estiver concluído, atualize o chamado de suporte com o Suporte IBM. Forneça as novas senhas criadas como uma parte desse processo de upgrade. Por exemplo, forneça senhas para implementar os serviços de gerenciamento de dispositivo, PSC e vCenter, no chamado de suporte. O suporte IBM atualiza então o console do {{site.data.keyword.vmwaresolutions_short}} e o banco de dados interno para continuar a automação do {{site.data.keyword.vmwaresolutions_short}} em um nível 6.7. Isso inclui incluir e remover serviços, hosts, cluster e instâncias secundárias do vCenter Server.

## Links relacionados
{: #vc_vsphere_upgrade-related}

* [Notas sobre a liberação do VMware NSX Data Center for vSphere 6.4.4](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:external}
* [Guia de upgrade do NSX](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:external}
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
