---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Resolução de problemas do HCX
{: #vcshcx-troubleshooting}

Revise o seguinte para problemas e correções comuns do HCX.

## Problemas da interface com o usuário do HCX Client
{: #vcshcx-troubleshooting-hcx-client-issues}

### Tempo limite do token da interface com o usuário do HCX
{: #vcshcx-troubleshooting-hcx-ui-issues}

Geralmente, se a interface com o usuário (IU) do vCenter tiver sido deixada aberta por algum tempo, você poderá encontrar um tempo limite na IU do HCX. Isso é porque o token de login para o servidor do gerenciador do HCX atingiu o tempo limite. Efetue logout da IU da web do vSphere e volte para atualizar o token.

### IU do cliente HCX exibindo "NaN" para todas as métricas na tela do painel
{: #vcshcx-troubleshooting-nan-display}

Esse problema está relacionado às permissões da conta atualmente conectada do vCenter. Assegure-se de que o grupo Administrador corporativo esteja configurado na IU do gerenciador de dispositivo do lado da nuvem do HCX.

## Problemas de Migração
{: #vcshcx-troubleshooting-mig-issues}

Os problemas de migração nas versões atuais do HCX são geralmente em três categorias: licenciamento, conectividade de rede do gateway em nuvem e compatibilidade do hardware de destino.

### Licsing
{: #vcshcx-troubleshooting-licensing}

Se uma migração falhar devido a um problema de licenciamento, as versões atuais do HCX claramente exibirão isso na mensagem de erro com a IU da web do cliente dentro da IU do vCenter.

### Conectividade de rede (WAN)
{: #vcshcx-troubleshooting-wan-connect}

Se houver um problema com a conectividade da WAN, sempre verifique a tela **Interconexão -> Componentes do HCX**
dentro da IU do HCX para o status do túnel. Os componentes da frota geralmente não precisam ser reconfigurados nem reinicializados. Se a conectividade da WAN for restaurada, eles se reconectarão automaticamente.

Caso haja correções e atualizações que foram aplicadas aos HCX Managers (Cliente e Nuvem) e essas atualizações também corrigem problemas com os componentes da frota, deve-se reimplementar o Cloud Gateway e quaisquer L2Cs implementados. É possível executar a depuração de status de túnel adicional, conectando-se ao gerenciador do HCX por meio de um cliente SSH, como ccli  

1. SSH para o gerenciador do HCX usando a conta de administrador e a senha fornecida.
2. Execute o comando `su –` e a senha raiz (a mesma senha do administrador) para mudar para a raiz.
3. Mude o diretório para `/opt/vmware/bin` e execute o comando `./ccli`. Se isso não for bem-sucedido, porque o ambiente não está configurado para raiz, execute o comando `./ccliSetup.pl`.
4. Execute o comando `list` dentro do shell do ccli para listar os componentes da frota registrados com o gerenciador do HCX.
5. Selecione o foco do ccli digitando o ID listado para o componente de frota. Por exemplo,  ` go 8 `.
6. Execute o comando `debug remoteaccess enable` para se conectar usando SSH ao componente de frota do SSH desejado.
7. Saia do ccli e conecte-se usando SSH para o endereço IP do componente de frota ativado para SSH.
9. Continuar a solucionar problemas.
10. Retorne para o ccli e desative o serviço ssh do componente.
11. Se necessário, use o comando ccli `hc` para executar uma verificação de funcionamento nos componentes.

## Problemas de compatibilidade de hardware de destino
{: #vcshcx-troubleshooting-hw-compatibility}

A migração do vMotion pode ser um problema quando o lado da origem do cliente é de uma versão de hardware e liberação do vSphere mais recentes do que a nuvem. Como a migração baseada em replicação copia dados para uma máquina virtual (MV) recém-construída no lado do destino, mudar o tipo de migração para "Migração em massa" deve permitir que a migração seja bem-sucedida na maioria dos casos.

## Problemas do L2 estendido
{: #vcshcx-troubleshooting-stretched-l2}

Poucos problemas, se algum, foram enfrentados com a operação do concentrador L2. Semelhante ao CGW, se o L2C perder a conectividade, ele se reconectará automaticamente após a conectividade de rede ser restaurada. Use o shell do ccli para verificar o funcionamento e a operação. Depois que o SSH for ativado e o L2C estiver conectado, execute os comandos `ip tunnel` e `ip link |grep t_` para visualizar o status dos túneis.

## Links relacionados
{: #vcshcx-troubleshooting-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)   
