---

copyright:

  years:  2019, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX on-premises Service Mesh
{: #hcxclient-vcs-mesh-deployment}

A seção a seguir detalha as etapas que configuram a instância do HCX Client.
  1. Ambiente de soluções de emparelhamento de sites do IBM Cloud for VMware
  2. Criar perfis de rede locais do HCX
  3. Criar perfis de cálculo locais do HCX
  4. Criar o HCX Service Mesh
  5. Redes estendidas

## Ambiente de soluções de emparelhamento de sites do IBM Cloud for VMware
{: #hcxclient-vcs-mesh-deployment-sitepair}

1. Efetue login no vSphere Web Client
2. No menu **Página inicial**, selecione a opção **HCX**.
3. Em **Infraestrutura** -> **InterConnect**, clique em **Incluir emparelhamento de sites**
   1. URL do site: URL do HCX Cloud Manager
     * por exemplo, `https://x.x.x.x.x`
   2. Nome do usuário e senha: detalhes do administrador do HCX Manager
     * administrador/senha
   3. Os detalhes anteriores podem ser obtidos do IBM Cloud Portal, em **Serviços**, HCX on IBM Cloud** para a instância de solução do IBM Cloud for VMware.
4. Clique em **Conectar**

### Resultados
{: #hcxclient-vcs-mesh-deployment-sitepair-results}

O Emparelhamento de sites foi registrado com êxito e exibido na IU.

## Criando perfis locais do HCX
{: #hcxclient-vcs-mesh-deployment-profiles}

## Perfis de rede do On-Premise Service Mesh
{: #hcxclient-vcs-mesh-deployment-profiles-network}

1. Efetue login no vSphere Web Client
2. No menu **Página inicial**, selecione a opção **HCX**.
3. Em **Infraestrutura** -> **InterConnect**
4. Em Multi-Site Service Mesh, clique em **Perfis de rede**
5. De: **Criar perfil de rede**
   1. Selecione o grupo de portas distribuídas: por exemplo, Externo
   2. Forneça o intervalo de endereço IP de IPs externos
   3. Forneça o comprimento do prefixo da sub-rede externa
   4. Forneça o gateway externo
   5. Forneça os detalhes do DNS
   6. Configure a MTU como 1500.
   7. Clique em Criar.
6. Repita as etapas anteriores para Gerenciamento e Redes vMotion.
   Nota: a MTU deve ser configurada como 9000.

## Resultados
{: #hcxclient-vcs-mesh-deployment-profiles-network-results}

| Nome da rede | MTU |
| -----| ----|
| Externo | 1500|
| Gerenciamento | 9000|
| vMotion | 9000|

## Perfis de cálculo do On-Premise Service Mesh
{: #hcxclient-vcs-mesh-deployment-profiles-compute}

1. Efetue login no vSphere Web Client
2. No menu **Página inicial**, selecione a opção **HCX**.
3. Em **Infraestrutura** -> **InterConnect**
4. Em Multi-Site Service Mesh, clique em **Calcular perfis**
5. De: **Criar perfil de cálculo**
   1. Forneça o nome do perfil de cálculo
   2. Selecione Todos os serviços a serem ativados, clique em **continuar**
   3. Selecione o Cluster, clique em **continuar**
   4. Selecione o Armazenamento de dados, clique em **continuar**
   5. Selecione Perfil de rede para gerenciamento, clique em **continuar**
   6. Selecione Perfil de rede para Externo/Uplink, clique em **continuar**
   7. Selecione Perfil de rede para vMotion, clique em **continuar**
   8. Selecione Perfil de rede para replicação do vSphere (Gerenciamento), clique em **continuar**
   9. Selecione Distribuir comutador para extensão, por exemplo, Comutador privado
   10. Clique em Concluir

## Resultados
{: #hcxclient-vcs-mesh-deployment-profiles-compute-results}

Um perfil de cálculo para a combinação de cluster/armazenamento foi criado e está disponível com a criação de Service Mesh.

## HCX On-Premise Service Mesh
{: #hcxclient-vcs-mesh-deployment-servicemesh}

## Criação do On-Premise Service Mesh
{: #hcxclient-vcs-mesh-deployment-servicemesh-creation}

1. Efetue login no vSphere Web Client
2. No menu **Página inicial**, selecione a opção **HCX**.
3. Em **Infraestrutura** -> **InterConnect**
4. Em Multi-Site Service Mesh, clique em **Service Mesh**
5. De: **Criar Service Mesh**
   1. Selecione sites; Organização no local e no vCloud, clique em continuar
   2. Selecione Perfil de cálculo de origem
   3. Selecione Perfil de cálculo remoto. Por exemplo, CloudCompute.
   4. Selecione Todos os serviços, clique em continuar
   5. Clique em continuar na página Configuração avançada - Substituir perfis de rede de uplink (Opcional)
   6. Clique em continuar
   7. Clique em continuar, deixe o padrão na página Configuração avançada - configure o Limite de largura de banda de serviço do WAN Optimization
   8. Forneça o Nome do serviço, clique em **Concluir**
6. Veja a lista de tarefas para criação de malhas de serviços; no final, deve haver três dispositivos HCX no local e três no local da nuvem.

## Resultados
{: #hcxclient-vcs-mesh-deployment-servicemesh-results}

Uma HCX Service Mesh é a configuração efetiva de serviços do HCX para um site de origem e de destino. Um Service Mesh pode ser incluído em um Par de sites conectados que tenha um Perfil de cálculo válido criado em ambos os sites.

A inclusão de um Service Mesh inicia a implementação de dispositivos virtuais de HCX Interconnect em ambos os sites. Um Service Mesh de interconexão é sempre criado no site de origem.

## Rede esticada
{: #hcxclient-vcs-mesh-deployment-network-stretching}

## Processo para estender uma rede
{: #hcxclient-vcs-mesh-deployment-stretching-process-stretch}

Para estender uma rede (VLAN ou VXLAN) com o HCX, conclua as etapas a seguir por meio da IU da web do vCenter do lado do cliente.

1. Efetue login no vSphere Web Client
2. No menu **Página inicial**, selecione a opção **HCX**.
3. No menu do lado esquerdo, em **Serviços** -> **Extensão de rede**
4. clique em **Ampliar rede**
   1. Selecione a rede a ser estendida
   2. Digite o gateway padrão atual e a máscara de sub-rede no formato CIDR.
   3. Clique em **Esticar** na parte inferior da tela para iniciar o fluxo de trabalho de esticamento da rede.

O progresso da rede é monitorado na área de janela de tarefas do cliente do vCenter.

## Conceitos e melhores práticas para o esticamento de rede
{: #hcxclient-vcs-mesh-deployment-stretching-best-practices-network}

A cola que liga a rede do lado do cliente ao VXLAN do lado da nuvem é uma VPN sofisticada com vários túneis que consiste em tecnologia HCX proprietária. Ela não se baseia no NSX, mas funciona com o NSX e amplia sua capacidade. Esse processo é controlado pela interface com o usuário (IU) da web do vCenter do lado do cliente e automatiza a implementação e a ativação de ambos os terminais no lado do cliente e da nuvem. A seleção da rede para estendida é feita individualmente ou em lote.

Além disso, como parte do fluxo de trabalho de esticamento da rede, o NSX no lado da nuvem está autorizado a construir uma VXLAN que será, então, conectada a uma interface criada no dispositivo L3 especificado no lado da nuvem (DLR ou ESG deixado em um estado desconectado) e o dispositivo de Extensão de rede do lado da nuvem.

Geralmente, quando você migra um aplicativo específico, todas as redes em uso pelas máquinas virtuais aplicáveis (VMs) devem ser estendidas na instância do {{site.data.keyword.cloud}}.

Por que geralmente e não sempre? Pode ser vantajoso desconectar um determinado tráfego do lado do cliente após a migração da MV. Por exemplo, clientes de backup guest da MV, que podem causar alto uso da largura de banda quando movidos para a nuvem. O cliente de backup dentro do guest não é necessário quando a MV é migrada, uma vez que é selecionado automaticamente por um backup de nível de bloco mais moderno no lado da nuvem.

O adaptador de rede de backup do cliente não está sendo acessado, porque isso significaria acessar cada VM para desligar o planejamento de backup do cliente no guest. Portanto, se uma rede de backup for usada, o backup poderá falhar. Essa é uma situação provisória até que todas as MVs possam ser acessadas após a migração para desativar o cliente de backup dentro do guest.

A largura de banda de uma única extensão de rede é teoricamente de 4 Gbps, no entanto, esse pode ser o limite para todas as redes estendidas dentro de um único par de extensão de rede e não pode ser alcançado por uma única rede estendida. Uma única rede estendida pode alcançar ~1 Gbps, pois há largura de banda de subjacência suficiente atribuída e a latência é baixa (< ~10 ms).

### Opção de Roteamento de Proximidade
{: #hcxclient-vcs-mesh-deployment-stretching-prox-routing}

Sem qualquer tipo de otimização de rota, as redes estendidas são roteadas de volta para o lado do cliente para qualquer acesso da L3. Esse tipo de retorno introduz um padrão de tráfego ineficiente, pois os pacotes precisam viajar entre o cliente (origem) e a nuvem mesmo para casos em que as MVs de origem e de destino estejam dentro da nuvem. O recurso de Roteamento de proximidade do HCX foi projetado para tratar disso e o egresso local de tráfego.

## Links relacionados
{: #hcxclient-vcs-mesh-deployment-deployment-related}

* [Glossário de componentes e termos do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparando o ambiente de instalação](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Implementação do cliente HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Migrações de nuvem híbrida do VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitorando parâmetros e componentes](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Resolução de problemas do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
