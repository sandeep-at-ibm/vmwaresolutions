---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Migração de rede e de máquina virtual
{: #vcshcx-stretching}

## Rede esticada
{: #vcshcx-network-stretching}

### Conceitos e melhores práticas para o esticamento de rede
{: #vcshcx-stretching-best-practices-network}

A cola que liga a rede do lado do cliente ao VXLAN do lado da nuvem é uma VPN sofisticada com vários túneis que consiste em tecnologia HCX proprietária. Ela não se baseia no NSX, mas funciona com o NSX e amplia sua capacidade. Esse processo é controlado pela interface com o usuário (IU) da web do vCenter do lado do cliente e automatiza a implementação e a ativação de ambos os terminais no lado do cliente e da nuvem. A seleção da rede para estendida é feita individualmente ou em lote.

Além disso, como parte do fluxo de trabalho de esticamento da rede, o NSX no lado da nuvem é comandado para construir uma VXLAN que é, então, conectada a uma interface criada no dispositivo L3 especificado do lado da nuvem (DLR ou ESG deixado em um estado desconectado) e no dispositivo L2C do lado da nuvem.

Quando um aplicativo específico é migrado, todas as redes em uso pelas máquinas virtuais (MVs) aplicáveis geralmente devem ser estendidas para a instância do {{site.data.keyword.cloud}}.

Por que geralmente e não sempre? Pode ser vantajoso desconectar um determinado tráfego do lado do cliente após a migração da MV. Por exemplo, clientes de backup guest da MV, que podem causar alto uso da largura de banda quando movidos para a nuvem. O cliente de backup dentro do guest não é necessário quando a MV é migrada, uma vez que é selecionado automaticamente por um backup de nível de bloco mais moderno no lado da nuvem.

Em vez de acessar cada MV para encerrar o planejamento de backup do cliente dentro do guest, não conectar o adaptador de rede de backup do cliente (caso uma rede de backup seja usada) faz com que o backup falhe. Essa é uma situação provisória até que todas as MVs possam ser acessadas após a migração para desativar o cliente de backup dentro do guest.

A largura de banda de um único L2C é teoricamente 4 Gbps, no entanto, isso pode ser o limite para todas as redes estendidas dentro de um único par de L2C e não é acessível por uma única rede estendida. Uma única rede estendida pode alcançar ~1 Gbps, pois há largura de banda de subjacência suficiente atribuída e a latência é baixa (< ~10 ms).

### Processo para estender uma rede
{: #vcshcx-stretching-process-stretch}

Para estender uma rede (VLAN ou VXLAN) com o HCX, conclua as etapas a seguir por meio da IU da web do vCenter do lado do cliente.

1. Para a seleção individual de grupos de portas, navegue para a guia **Redes** dentro da IU da web do vCenter, clique com o botão direito na rede a ser estendida e selecione **Ações de hibridismo -> Ampliar redes para a nuvem**.
2. Selecione o dispositivo L3 do lado da nuvem ao qual se conectar e o dispositivo L2C que será usado. Digite o gateway padrão atual e a máscara de sub-rede no formato CIDR.
3. Clique em **Esticar** na parte inferior da tela para iniciar o fluxo de trabalho de esticamento da rede.

O progresso da rede é monitorado na área de janela de tarefas do cliente do vCenter.

### Opção de Roteamento de Proximidade
{: #vcshcx-stretching-prox-routing}

Sem qualquer tipo de otimização de rota, as redes estendidas são roteadas de volta para o lado do cliente para qualquer acesso da L3. Esse tipo de retorno introduz um padrão de tráfego ineficiente, pois os pacotes precisam viajar entre o cliente (origem) e a nuvem mesmo para casos em que as MVs de origem e de destino estejam dentro da nuvem. O recurso de Roteamento de proximidade do HCX foi projetado para tratar disso e o egresso local de tráfego.

## vMotion
{: #vcshcx-stretching-vmotion}

O recurso vMotion dentro do HCX amplia a capacidade do vSphere vMotion para trabalhar em diferentes versões do vSphere, domínios SSO separados e vários tipos de conectividade de rede na Internet. O HCX supõe que a rede usada para se conectar não é segura e sempre move o tráfego por meio de túneis criptografados independentemente do tipo de conectividade.

### Conceitos e melhores práticas para o vMotion
{: #vcshcx-stretching-best-practices-vmotion}

O HCX é essencialmente um proxy de duas vias do vMotion. Cada instância do HCX emula um único host ESXi dentro do data center do vSphere, fora de quaisquer clusters que são em si uma "frente" para o componente cloud gateway fleet (CGW). Aparece um host do proxy para cada site do HCX vinculado ao site visualizado atualmente. Quando um vMotion for iniciado para um host remoto, o host ESXi local moverá essa MV por meio do vMotion para o host ESXi do proxy local que está à frente do CGW que também está mantendo um túnel criptografado com o CGW no lado remoto.

Ao mesmo tempo, um vMotion é iniciado por meio do host do proxy ESXi remoto para o host ESXi físico do vSphere de destino, pois ele recebe dados do CGW de origem através do túnel. Quando o vMotion é empregado, ao contrário da opção de migração em massa, apenas uma única operação de migração da MV é executada de cada vez. Por causa disso, para que grandes quantias de MVs sejam migradas, recomenda-se que ele seja usado apenas quando o tempo de inatividade não for uma opção ou houver risco de reinicialização da MV. No entanto, como o vMotion padrão, a MV pode ficar ativa durante o processo.

Foi observado que um único vMotion atingirá cerca de ~1,7 Gbps na LAN e 300 a 400 Mbps na WAN por meio do WAN Optimizer. Isso não significa que 1,7 Gbps na LAN seja igual a 400 Mbps na LAN, mas os máximos observados de acordo com o ambiente observado. O ambiente em que isso foi observado consistia em 10 GB de Rede LAN vMotion, 1 GB de uplink de Internet, que é compartilhada com o tráfego da web de produção.

Use vMotion em que:
- A MV é problemática para encerrar, iniciar ou o tempo de atividade pode ser longo, o que apresentaria risco no encerramento.
- Qualquer aplicativo de tipo de cluster que requer UUIDs de disco, tais como clusters Oracle Rac. O vMotion não mudou os UUIDs do disco no destino.
- Você deseja mover uma única MV o mais rápido possível.
- A migração planejada não é necessária.

### Operation
{: #vcshcx-stretching-operation}

Use o portal de snap-in da IU da web do HCX ou os menus de extensão contextual do vSphere Web Client para iniciar um vMotion de nuvem cruzada. Em ambos os casos, aparece o mesmo assistente de migração. Para os menus contextuais, apenas uma única MV é selecionada para operações de migração. Para o portal, múltiplas MVs podem ser selecionadas.

Reverter as MVs de migração só é possível por meio do portal da IU da web que usa a caixa de seleção **Reverter migração** no assistente de Migração do HCX.

## Migração em massa
{: #vcshcx-stretching-bulk-mig}

### Conceitos e melhores práticas para migração em massa
{: #vcshcx-stretching-best-practices-bulk-mig}

O recurso de migração em massa do HCX usa a replicação do vSphere para migrar dados do disco ao recriar a MV na instância do vSphere HCX de destino. Uma migração de uma MV incorre no fluxo de trabalho a seguir:
- Criação de uma nova MV no lado de destino e seus discos virtuais correspondentes.
- Replicação de dados da MV para a nova MV. A replicação é iniciada assim que o assistente é concluído, independentemente de alternar o planejamento.
- Desligue a MV original.
- Durante o período desligado, ocorre a replicação final de quaisquer dados de mudança.
- Ligação da nova MV no lado de destino.
- Renomeação e movimento da MV original para a pasta de nuvem movida.

A seguir estão as vantagens da migração em massa sobre o vMotion:
- Migração de muitas MVs simultaneamente.
- Mais uso de largura da banda consistente. O vMotion pode gerar flutuações no uso da largura de banda que seriam visíveis como picos e vales dentro das ferramentas de monitoramento de rede ou na IU do WAN Opt.
- Use a migração em massa para obter um uso geral maior de um recurso de largura de banda de rede do que um único vMotion seria capaz de fazer.
- Planeje a migração em massa para alternar para as MVs recém-migradas durante uma janela de indisponibilidade planejada.
- Pode permitir a migração de MVs que estão atualmente usando recursos de CPU virtual que são diferentes do lado da nuvem, em que o vMotion falha.

A seguir estão as desvantagens da migração em massa no vMotion:
- As MVs individuais migram muito mais lentamente do que com o vMotion.
- A MV incorre em um rápido tempo de inatividade conforme a nova MV clone é ativada no lado de destino.
- As MVs que dependem de pedidos de disco e UUIDs de disco (Oracle RAC) podem ter problemas e ter discos exibidos de forma diferente à medida que os UUIDs mudam, podendo mudar os caminhos do S.O. para os dispositivos de disco virtual.

## Melhores práticas do tipo de migração
{: #vcshcx-stretching-mig-type-best-practices}

### Clusters de disco compartilhados
{: #vcshcx-stretching-shared-disk-clusters}

Clusters do Oracle RAC, do MS Exchange e do MS-SQL são exemplos de aplicativos em que duas ou mais MVs participam de um cluster que requer disco compartilhado em todas as MVs ou nós do cluster. A sinalização de vários gravadores do VMware precisa ser ativada em todos os nós da MV para discos que fazem parte do cluster de aplicativo (discos virtuais que não são do S.O.). As MVs com a sinalização de vários gravadores ativada para qualquer disco virtual não são suportadas.

Migrando um cluster ativado para disco virtual de vários gravadores:
- Usa o vMotion conforme o disco original da MV e os mapeamentos de UUID são mantidos.
- O cluster permanece ativo em um estado comprometido (nó único) durante a migração.
- O cluster incorre em tempo de inatividade antes do início da migração e após a conclusão da migração para remontar a configuração de vários gravadores entre os nós da MV do cluster.

Conclua as etapas a seguir para migrar um cluster ativado para disco de vários gravadores:
1. Desative o cluster e todos os nós de acordo com a melhor prática do aplicativo.
2. Anote a ordem do disco, caso o aplicativo requeira, em cada MV do nó para os discos virtuais configurados com vários gravadores.
3. Para o Oracle e qualquer outro aplicativo que use o recurso UUID do disco virtual, efetue login em um host ESXi específico e execute o comando `vmkfstools -J getuuid /vmfs/volumes/datastore/VM/vm.vmdk` para obter o UUID de cada arquivo de disco virtual que requeira a sinalização de vários gravadores configurada para
o cluster.
  Isso será necessário se a melhor prática alinhar os pedidos de disco com a maneira com a qual o caminho é exibido no sistema operacional. O vMotion pode reordenar os discos (disk1, disk2, disk3), mas os UUIDs permanecem os mesmos.
  Use o UUID anotado para as informações de mapeamento de disco para recriar a ordem de nomenclatura do disco. ID do Scsi quando a migração for concluída, se necessário. O aplicativo deve funcionar de qualquer maneira. Isso é usado em locais em que uma instância do Oracle tem muitos discos virtuais que são mapeados para resolução de problemas do aplicativo.
4. Remova os discos virtuais de todos os nós da MV do cluster, exceto aquele considerado primário.
5. Remova a sinalização de vários gravadores do nó do cluster da MV primária que deve ser a única proprietária dos discos de cluster atualmente.
6. Ative o nó do cluster primário novamente, se necessário, para tempo de inatividade mínimo.
7. Migrar todos os nós do cluster com vMotion. Migre o cluster principal primeiro e todos os outros nós serão migrados quando desligados.
8. Quando o nó proprietário do disco primário concluir a migração, desligue-o.
9. Se necessário, remapeie o pedido de disco com o UUID de disco apropriado e o ID de scsi. O remapeamento não é necessário para que o aplicativo funcione.
10. Reative a sinalização de vários gravadores no nó primário.
11. Inicie o nó primário e verifique a operação.
12. Mapeie o disco/ative a sinalização de vários gravadores em todas as outras MVs de nó do cluster e ligue-as.
13. Verifique outra operação de nós do cluster.

### VMs Gerais
{: #vcshcx-stretching-general-vms}

Após a construção de confiança em torno da função do HCX, a migração em massa deve ser empregada. A migração em massa é necessária quando os aplicativos redundantes são uma preocupação. Por exemplo, servidores da web e locais em que muitas centenas ou milhares de MVs devem ser migradas.

### MVs usando NAS conectadas diretamente
{: #vcshcx-stretching-vms-direct-nas}

O NFS geralmente é empregado para uso para compartilhar dados entre muitos servidores, como o conteúdo do servidor da web. A iSCSI pode ser empregada em nós da MV compostas por um cluster de aplicativo como e-mail ou RDBMS e é geralmente mais sensível à latência do que o NFS.

Em ambos os casos, se a latência puder ser mantida baixa para o {{site.data.keyword.CloudDataCent_notm}} (< ~7 ms para a iSCSI e qualquer que seja a tolerância do aplicativo para NFS) e for permitido que o aplicativo possa operar com a largura de banda de ~1 Gbps ou menos, a rede NAS poderá ser estendida com o HCX em um local do {{site.data.keyword.cloud_notm}}. Depois de isso ser feito, as MVs poderão ser migradas/colocadas em vMotion com o HCX normalmente.

Após a migração, os volumes iSCSI podem ser espelhados com o S.O. em outra solução de armazenamento em nuvem local e os dados do NFS podem ser replicados para qualquer uma na solução em nuvem. As considerações são:
- Latência (iSCSI ou tolerância do aplicativo para NFS)
- Largura da Banda (~ 1 Gbps por rede estendida)
- Entendendo a largura da banda do link

Seguindo o ciclo de vida de migração, assegure-se de testar com aplicativos de Desenvolvimento ou de preparação antes de tentar com a produção. O QoS pode ser empregado para o tráfego do túnel de subjacência (udp 500/4500) entre os dispositivos L2C HCX que transportam redes L2 estendidas sensíveis à latência.

## Network swing
{: #vcshcx-stretching-network-swing}

Se o objetivo for a evacuação do data center para o {{site.data.keyword.cloud_notm}}, a próxima etapa até a última antes da remoção do HCX será a troca de rede. A troca de rede atinge uma migração da sub-rede de rede que hospeda as MVs migradas do data center de origem em uma rede de sobreposição do NSX dentro do {{site.data.keyword.cloud_notm}}.

Swinging the network, envolve o seguinte:
- Verifique se todas as cargas de trabalho foram evacuadas da rede e se todos os dispositivos de rede não MV foram movidos para outra rede, migrados funcionalmente para a nuvem ou descontinuados.
- Verifique se qualquer topologia do NSX ou a topologia de rede de suporte do {{site.data.keyword.cloud_notm}} está concluída para suportar a troca de rede. Por exemplo, protocolos de roteamento dinâmico e firewalls.
- Execute um fluxo de trabalho de rede não estendido do HCX na IU e selecione o dispositivo NSX de roteamento apropriado para assumir o controle do gateway padrão de redes não estendidas.
- Execute qualquer mudança externa de roteamento, que pode incluir: a inserção de roteamento mudado para redes que foram migradas, a remoção de rotas para o site de origem para a rede migrada e assegurar o roteamento para essa sub-rede migrada na WAN para aplicativos não migrados, se necessário.
- Teste do proprietário do aplicativo de aplicativos migrados de todos os pontos de acesso possíveis: Internet, intranet e VPN.

Considerações para a troca de rede de um aplicativo específico com todas as MVs completamente migradas para a nuvem:
se você estiver usando um Vyatta no lado de rede privada para inserir rotas em sua nuvem e túnel MPLS para os dispositivos de roteamento de borda no MPLS para evitar o espaço de IP do {{site.data.keyword.cloud_notm}}. Sua conta é configurada com um VRF do {{site.data.keyword.cloud_notm}}. Alguns dos aplicativos estão protegidos por um IP virtual (vIP) com carga balanceada de rede. Esses vIPs estão em sua sub-rede própria que reside em um F5 virtual atrás do vyatta. Embora o anúncio de roteamento mais específico para o MPLS para redes comutadas para o {{site.data.keyword.cloud_notm}} por meio do HCX funcione bem para outras redes, ele não funciona para os vIPs individuais, pois uma rota /32 está sendo inserida.

Solução: é comum os provedores da WAN filtrarem as rotas /32 anunciadas. Trabalhe com o fornecedor da WAN para permitir.

A seguir estão as considerações e implicações:
- Os aplicativos que compartilham a sub-rede, a vLAN e a VXLAN precisam se mover juntos.
- Os aplicativos protegidos por um balanceador de carga que usa um IP roteável interno poderão requerer mudanças de roteamento se não puderem ser movidos juntos ou se não for desejável fazer isso. Por exemplo, se houver um risco muito percebido que envolva muitos aplicativos em uma troca.
- Os administradores do VMware, os administradores de rede (incluindo fornecedores do cliente/WAN), os proprietários do aplicativo precisam estar envolvidos. Mesmo que não seja planejado que as mudanças afetem um sistema específico ou um equipamento de rede.

## Links relacionados
{: #vcshcx-stretching-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)   
