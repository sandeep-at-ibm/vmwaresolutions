---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Monitorando parâmetros e componentes
{: #vcshcx-monitoring}

## Usando o WAN Optimizer para monitoramento
{: #vcshcx-monitoring-using-wan}

O dispositivo de otimização da WAN Silver Peak implementado como parte do
HCX não obtém sua interface de gerenciamento configurada. A interface com o usuário da web (IU) é uma
ferramenta de uso valiosa quando você baseia o rendimento do tráfego de linha e o uso da largura de banda
de migração de rede de limitação.

Somente o tráfego de túnel da WAN do HCX CGW Gateway flui por meio do
dispositivo WAN Optimizer. Portanto, ele não pode monitorar o tráfego L2 estendido.
{:note}

### Configurando a UI
{: #vcshcx-monitoring-config-ui}

Fora da configuração de um endereço IP para a IU da web, não faça mudanças na
configuração para o dispositivo WAN Optimizer, a menos que orientado pela
equipe de suporte da {{site.data.keyword.IBM}} ou do VMware.   

Para configurar a IU da web do WAN Opt:
1.	Localize o dispositivo de máquina virtual (MV) WAN Opt dentro do cliente vCenter.
2.	Abra um console para a MV que usa o cliente vCenter.
3.	Dentro do console, clique em **F4** para configurar a interface de gerenciamento.
4.	Selecione para configurar um IP estático.
5.	Use um endereço IP no intervalo de IP móvel e no gateway padrão designados pelo
{{site.data.keyword.cloud}} de gerenciamento.
6.	Clique em **Aplicar** na próxima tela para salvar.
7.  Clique em editar configurações para a MV do WAN Opt dentro do console do vCenter.
8.	Selecione **Conectado na inicialização** e **Conectado para o Adaptador de rede 1**.
9.	Clique em  ** OK **  para salvar.
10.	Localize o CGW-<xxx>-WANOPT no vCenter.
11.	Edite as configurações na MV.
12.	Clique na caixa de seleção para conectar o Adaptador de rede 1.
13.	Clique em **OK**.
14.	Acesse  ` https://<configured_WAN_OPT_IP>`.
15.	Efetue login com o usuário padrão `admin` e a senha `admin`.

Agora é possível usar a IU da web do WAN Opt para monitorar taxas de
rendimento, proporções de compactação e configurar restrições de largura de banda.

### throttling da largura da banda da migração
{: #vcshcx-monitoring-mig-bandwidth}

Antes de migrar MVs, execute uma avaliação do link de rede usado. Trabalhe com os engenheiros
de rede da rede que contém a instância de origem do vSphere ou
revise o uso de tráfego semanalmente e mensalmente. Limite a largura de banda disponível para migrações se esse tráfego
atravessar um link que for crítico para seus negócios,
especialmente se esse link tiver menos que 1 Gbps. Use o
lado com a largura de banda mais limitada, que geralmente é o
lado do cliente.

Faça isso quando implementar os componentes da frota na IU do HCX
Client, mas a pós-implementação requer que você acesse a IU do WAN Opt.

As mudanças serão perdidas se você reimplementar o HCX CGW por meio da IU da web do HCX.
Isso configura os limites de largura de banda somente para o tráfego de migração. O tráfego do L2
estendido não é afetado por essa configuração.
{:note}

1.	Efetue login na IU da web do Wan Opt.
2.	Na guia **Configuração**, selecione **Shaper** no menu suspenso.
3.	Na caixa de largura de banda máxima, configure a largura de banda máxima disponível para o
dispositivo Wan Opt em kbps. Não exceda a largura de banda máxima do link da
WAN.     
  - Para configurar para Mbps (base 10) = Mbps x 1000
  - Para configurar para Gbps = 1000^2 = Gbps x 1000^2
  - Padrão = 10 Gbps (10000000)
4.	Clique em **Aplicar**.

Para a limitação da largura de banda do L2 estendido, o QoS pode ser empregado para UDP 500
e 4500 para o tráfego de túnel entre os dispositivos L2C.

## Monitorando componentes do HCX
{: #vcshcx-monitoring-hcx-comp}

Monitore componentes do HCX, como HCX Manager, Cloud Gateway, WAN Opt e as operações
Layer 2 Concentrator das maneiras a seguir:

- Configure o HCX Manager para enviar logs para um servidor de syslog. Use
o utilitário de gerenciamento de dispositivo do gerenciador do HCX para executar o comando `https://<hcxhostname or
IP>:9443`.
- Configure um ping para uma MV que é migrada antes da troca de rede
para cada rede L2 estendida.
- Monitore o funcionamento da MV do componente HCX com o VMware vRealize Operations
Manager ou outras ferramentas de monitoramento da MV do VMware.

## Uso de Largura da B
{: #vcshcx-monitoring-band-use}

Use os métodos a seguir para monitorar o uso de largura da banda e a latência.

- O tráfego do vMotion é melhor alcançado usando a IU da web do WAN Opt. O WAN
Opt reduz significativamente o tráfego que está passando pela WAN e reduz
a perda do pacote enviando pacotes redundantes. Foi observado que a
razão típica de uso da largura de banda LAN para WAN é ~3:1 (350 Mbps LAN =
90-120 Mbps de WAN).

- A migração baseada em replicação (em massa) de MVs dentro do HCX resulta na
movimentação densa de MVs. Embora isso não possa ser desejável, a IU do WAN Opt
revela uma razão alta entre LAN e WAN quando
dados de disco "vazios" são movidos. Por outro lado, observa-se que, quando
dados não compactáveis são migrados, como dados do BD e mídia digital, o uso
da WAN atinge seu máximo, conforme se aproxima do uso de entrada
da LAN.

Observações:
- O vMotion de uma MV dentro do HCX resulta em não mais do que o rendimento
da rede do vMotion para um único host ESX.
- Como a migração em massa pode ter diversas migrações em andamento
simultaneamente, ela atinge maior uso de largura de banda do que uma
migração do vMotion. A razão observada em um lado do cliente com links do vMotion
de 1 Gbps para os hosts ESX era: oito replicações = uso da
largura de banda de 1 vMotion.
- A movimentação de espaço vazio em disco resulta na exibição de um alto uso da LAN com uma
razão alta e, subsequentemente, baixo uso da WAN. Observe que 1 Gbps parece
ser o limite. De fato, nesse caso específico, a rede do vMotion é
capaz apenas de 1 Gbps, que é o gargalo.
- A migração do vMotion de um BD Oracle de múltiplos TB. Com um link da WAN de 1 Gbps,
a limitação é a rede do vMotion de 1 Gbps.

## Tráfego do Stretched Layer 2
{: #vcshcx-monitoring-stretched-layer-2-traffic}

O componente de frota do HCX Layer 2 Concentrator tem uma limitação de largura de banda
de ~4 Gbps agregado para todo o tráfego de rede L2 que o atravessa. As redes
estendidas individuais têm um limite de largura da banda de ~1 Gbps ou menos,
dependendo do tipo de tráfego. É possível ter muitas redes de L2
estendidas em um único par de L2C (máximo teórico permitido de 4096
redes por par de L2C). Embora o L2C seja projetado para detectar e
proteger fluxos de tráfego pequenos para que não sejam superados por grandes fluxos dentro do
mesmo par de L2C, pode ser vantajoso identificar se essa situação está
ocorrendo e trazer mais L2Cs para aumentar a capacidade geral da
largura de banda. A implementação de múltiplos L2Cs também pode ser vantajosa, na qual
existem múltiplos caminhos entre o site do cliente e o {{site.data.keyword.cloud}}, como link direto e Internet, de forma que ambos possam ser usados, considerando que você
tem mais de uma rede para ser difundida entre eles. Uma única rede não pode se tornar redundante ou receber a maior largura de banda em diversos
pares de L2C.

Monitore o tráfego em todas as interfaces que usam a guia Monitoramento
da MV L2C. Se a taxa total de dados estiver se aproximando de 8 Gbps (4 Gbps dentro/fora),
considere a inclusão de outro par de L2 e redistribua as redes estendidas para
rebalancear.


## Links relacionados
{: #vcshcx-monitoring-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)   
