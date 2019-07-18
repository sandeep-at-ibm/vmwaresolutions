---

copyright:

  years:  2019, 2019

lastupdated: "2019-06-28"

subcollection: vmware-solutions


---

# HCX on-premises Service Mesh
{: #hcxclient-vcs-mesh-deployment}

Revise as seguintes etapas para configurar a instância do HCX Client.

## Ambiente de soluções de emparelhamento de sites do IBM Cloud for VMware
{: #hcxclient-vcs-mesh-deployment-sitepair}

1. Faça login no VMware vSphere Web Client.
2. No menu **Página inicial**, selecione a opção **HCX**.
3. Em **Infraestrutura**, **InterConnect**, clique em **Incluir pareamento de site**.
  1. Configure a URL do site para a URL do HCX Cloud Manager, por exemplo, `https://x.x.x.x.x`.
  2. Configure o nome de usuário e a senha nos detalhes do HCX Manager Admin: admin / password.

    Os detalhes anteriores podem ser obtidos no console do IBM Cloud for VMware Solutions, em **Serviços**, **HCX on IBM Cloud** para a instância do vCenter Server.
    
4. Clique em  ** Conectar **.

### Resultados
{: #hcxclient-vcs-mesh-deployment-sitepair-results}

O Emparelhamento de sites foi registrado com êxito e exibido na IU.

## Criando perfis locais do HCX
{: #hcxclient-vcs-mesh-deployment-profiles}

## Perfis de rede do On-Premise Service Mesh
{: #hcxclient-vcs-mesh-deployment-profiles-network}

1. Efetue login no vSphere Web Client.
2. No menu **Página inicial**, selecione a opção **HCX**.
3. Em **Infraestrutura**, clique em **InterConnect**.
4. Em **Malha de serviços multissite**, clique em **Perfis de rede**.
5. Em **Criar perfil de rede**:
   1. Selecione Grupo de portas distribuídas, por exemplo, Externo.
   2. Forneça o intervalo de endereço IP de IPs externos, o comprimento do prefixo de sub-rede externa, o gateway externo e os detalhes do DNS.
   3. Configure a MTU como 1500.
   4. Clique em
**Criar**.
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

1. Efetue login no vSphere Web Client.
2. No menu **Página inicial**, selecione a opção **HCX**.
3. Em **Infraestrutura**, clique em **InterConnect**.
4. Em **Malha de serviços multissite**, clique em **Perfis de cálculo**.
5. Em **Criar perfil de cálculo**:
   1. Forneça o nome do perfil de cálculo.
   2. Selecione Todos os serviços a serem ativados e clique em **Continuar**.
   3. Selecione o Cluster e clique em **Continuar**.
   4. Selecione o Armazenamento de dados e clique em **Continuar**.
   5. Selecione o Perfil de rede para gerenciamento e clique em **Continuar**.
   6. Selecione Perfil de rede para externo/uplink e clique em **Continuar**.
   7. Selecione Perfil de rede para o vMotion e clique em **Continuar**.
   8. Selecione Perfil de rede para a replicação do vSphere (gerenciamento) e clique em **Continuar**.
   9. Selecione Distribuir comutador para extensão, por exemplo, Comutador privado, e clique em **Concluir**.

## Resultados
{: #hcxclient-vcs-mesh-deployment-profiles-compute-results}

Um perfil de cálculo para a combinação de cluster/armazenamento foi criado e está disponível com a criação de Service Mesh.

## HCX On-Premise Service Mesh
{: #hcxclient-vcs-mesh-deployment-servicemesh}

## Criação do On-Premise Service Mesh
{: #hcxclient-vcs-mesh-deployment-servicemesh-creation}

1. Efetue login no vSphere Web Client.
2. No menu **Página inicial**, selecione a opção **HCX**.
3. Em **Infraestrutura**, clique em **InterConnect**.
4. Em **Malha de serviços multissite**, clique em **Malha de serviços**.
5. Em **Criar malha de serviços**:
   1. Selecione sites: no local e na organização do vCloud e clique em **Continuar**.
   2. Selecione o perfil de cálculo de origem.
   3. Selecione Perfil de cálculo remoto. Por exemplo, CloudCompute.
   4. Selecione Todos os serviços e clique em **Continuar**.
   5. Clique em **Continuar**, na página Configuração avançada - Substituir perfis de rede de uplink (opcional)
   6. Clique em **Continuar**.
   7. Clique em **Continuar**, mantenha o padrão na página Configuração avançada - Configurar limite de largura de banda do serviço de otimização de WAN.
   8. Forneça o nome do serviço e clique em **Concluir**.
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

1. Efetue login no vSphere Web Client.
2. No menu **Página inicial**, selecione a opção **HCX**.
3. No menu à esquerda, em **Serviços**, clique em **Extensão de rede**.
4. Clique em **Ampliar rede**:
   1. Selecione a rede a ser ampliada.
   2. Digite o gateway padrão atual e a máscara de sub-rede no formato CIDR.
   3. Clique em **Esticar** na parte inferior da tela para iniciar o fluxo de trabalho de esticamento da rede.

O progresso da rede é monitorado na área de janela de tarefas do cliente do vCenter.

## Conceitos e melhores práticas para o esticamento de rede
{: #hcxclient-vcs-mesh-deployment-stretching-best-practices-network}

A cola que liga a rede do lado do cliente ao VXLAN do lado da nuvem é uma VPN sofisticada com vários túneis que consiste em tecnologia HCX proprietária. Ela não se baseia no NSX, mas funciona com o NSX e amplia sua capacidade. Esse processo é controlado pela interface com o usuário da web do vCenter do lado do cliente e automatiza a implementação e a inicialização de ambos os terminais no cliente e no lado da nuvem. A seleção da rede para estendida é feita individualmente ou em lote.

Além disso, como parte do fluxo de trabalho de esticamento da rede, o NSX no lado da nuvem está autorizado a construir uma VXLAN que será, então, conectada a uma interface criada no dispositivo L3 especificado no lado da nuvem (DLR ou ESG deixado em um estado desconectado) e o dispositivo de Extensão de rede do lado da nuvem.

Geralmente, quando você migra um aplicativo específico, todas as redes em uso pelas máquinas virtuais aplicáveis (VMs) devem ser estendidas na instância do {{site.data.keyword.cloud}}.

Por que geralmente e não sempre? Pode ser vantajoso desconectar um determinado tráfego do lado do cliente após a migração da MV. Por exemplo, clientes de backup guest da MV, que podem causar alto uso da largura de banda quando movidos para a nuvem. O cliente de backup dentro do guest não é necessário quando a MV é migrada, uma vez que é selecionado automaticamente por um backup de nível de bloco mais moderno no lado da nuvem.

O adaptador de rede de backup do cliente não está sendo acessado porque isso significaria acessar cada VM para desligar o planejamento de backup do cliente no guest. Portanto, se uma rede de backup for usada, o backup poderá falhar. Essa é uma situação provisória até que todas as MVs possam ser acessadas após a migração para desativar o cliente de backup dentro do guest.

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
