---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Visão geral do FortiGate Virtual Appliance on IBM Cloud

O serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud}} implementa um par de FortiGate Virtual Appliances em seu ambiente, o que pode ajudá-lo a reduzir o risco ao implementar controles de segurança crítica em sua infraestrutura virtual.

É possível instalar múltiplas instâncias desse serviço, conforme necessário. É possível gerenciar esse serviço usando o Web client FortiOS ou a interface da linha de comandos por meio de SSH.

**Disponibilidade**: esse serviço está disponível somente para instâncias que são implementadas na V2.0 ou liberações mais recentes.

## Componentes do FortiGate Virtual Appliance on IBM Cloud

Quando você pede o serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, um par de FortiGate Virtual Appliances é implementado com uma interface de rede configurada para a rede de gerenciamento e nove interfaces de rede que podem ser configuradas para proteger o tráfego de dados conforme necessário.

Os FortiGate Virtual Appliances não são pré-configurados como um par altamente disponível. Após a implementação, é possível configurar as definições de HA, que incluem o Virtual Router Redundancy Protocol (VRRP) e o FortiGate Cluster Protocol (FGCP), de acordo com suas necessidades.

## Considerações ao instalar o FortiGate Virtual Appliance no IBM Cloud

Revise as considerações a seguir antes de instalar o serviço FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}:
* As máquinas virtuais (VMs) do FortiGate serão implementadas somente no cluster padrão.
* Com base no tamanho de implementação e no modelo de licença selecionado, as duas VMs do FortiGate são implementadas com uma das configurações a seguir:
    * Pequeno (2 vCPUs / 4 GB de RAM)
    * Médio (4 vCPUs / 6 GB de RAM)
    * Grande (8 vCPUs / 12 GB de RAM)

  Além disso, 100% de CPU e de RAM para as duas VMs do FortiGate também são reservados porque essas VMs estão no plano de dados das comunicações de
rede e é fundamental que os recursos ainda estejam disponíveis para elas.

  Para calcular a reserva de CPU e de RAM para uma única VM do FortiGate, use a seguinte fórmula:
   * `Reserva de CPU = velocidade da CPU do servidor ESXi * número de vCPUs`
   * `Reserva de RAM = tamanho de RAM`
* Ao implementar um par de HA do FortiGate Virtual Appliances em sua instância, as regras de firewall e SNAT são definidas no Management NSX Edge Services Gateway (ESG) juntamente com rotas estáticas no FortiGate Virtual Appliances para permitir comunicações HTTPS de saída de sua instância para a rede pública para ativação da licença e para aquisição do conteúdo e das políticas de segurança mais recentes.
* Não é possível mudar o nível de licença após a instalação do serviço. Para mudar o nível de licença, deve-se remover o serviço existente e, em seguida, reinstalá-lo selecionando uma opção de licença diferente.
* Deve-se atender aos seguintes requisitos para evitar falhar com o FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}:
   * Pelo menos dois servidores ESXi ativos estão disponíveis para as duas VMs do FortiGate a serem implementadas com a regra de antiafinidade de manter as VMs em servidores separados.
   * Os dois servidores ESXi ativos têm recursos suficientes disponíveis para que uma VM do FortiGate possa ser hospedada em cada servidor ESXi com 100% de reserva de CPU e de RAM.
   * O VMware vSphere HA tem recursos suficientes para hospedar duas VMs do FortiGate com 100% de CPU e de RAM.

  Devido a esses requisitos, deve-se planejar o espaço necessário para o FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}. Se necessário, antes de pedir o FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}, inclua de 1 a 2 servidores ESXi em sua instância ou reduza a reserva de CPU do vSphere HA para failover,
  ou ambas as opções.

## Exemplo de pedido do FortiGate Virtual Appliance on IBM Cloud

Você pede uma instância **Pequena** do VMware vCenter Server com 2 servidores ESXi com a seguinte configuração: 16 núcleos em 2,10 GHz cada um com 128 GB de RAM. Para o FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}, você seleciona **Grande** (8 vCPUs / 12 GB de RAM) para o tamanho de implementação e qualquer modelo de licença de assinatura.

Nesse caso, uma única VM do FortiGate requer, em cada servidor:
* 2,1 GHz * 8 vCPU = 16,8 GHz de CPU e
* 12 GB de RAM

No total, são 33,6 GHz de CPU e 24 GB de RAM para duas VMs do FortiGate.

Cada servidor ESXi tem uma capacidade de 16 núcleos * 2,1 GHz = 33,6 GHz, então, nós atenderemos aos dois primeiros requisitos se ambos os servidores estiverem ativos e houver pelo menos 16,8 GHz de CPU e 12 GB de RAM disponível em cada servidor.

Por padrão, no entanto, o vSphere HA reserva 50% de CPU e de RAM para failover em instâncias do vCenter Server que foram inicialmente implementadas com 2 servidores ESXi; portanto, só temos:

`50% de 2 * 16 núcleos * 2,1 GHz = 33,6 GHz disponível`

Como haverá outras cargas de trabalho presentes nos servidores ESXi, por exemplo, o IBM CloudDriver, VMware NSX Controller, VMware NSX Edge, usando esses recursos nós não podemos atender ao terceiro requisito, pois precisamos de 33,6 GHz de CPU e 24 GB de RAM para as duas VMs do FortiGate.

Nesse caso, o FortiGate Virtual Appliance na instalação do {{site.data.keyword.cloud_notm}} pode falhar, a menos que no mínimo um servidor ESXi seja incluído no ambiente e as reservas de failover do vShpere HA sejam corretamente atualizadas para assegurar que haja recursos suficientes para duas VMs do FortiGate. Se recursos adicionais forem necessários para executar o serviço FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}, será possível incluir mais servidores ESXi antes de instalar o serviço.

## Considerações ao remover o FortiGate Virtual Appliance no IBM Cloud

Antes de remover o serviço FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}, assegure-se de que a configuração do FortiGate Virtual Appliances existente seja removida corretamente. Especificamente, o tráfego de rede deve ser roteado ao redor do FortiGate Virtual Appliances em vez de através do FortiGate Virtual Appliances. Caso contrário, o tráfego de dados existente em seu ambiente pode ser afetado.

## Links relacionados

* [Solicitando FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}](fortinetvm_ordering.html)
* [Gerenciando o FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [Website do Fortinet](https://www.fortinet.com/){:new_window}
* [Biblioteca de documentos do Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
