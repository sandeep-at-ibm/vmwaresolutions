---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

# Sobre o NSX Edge Services Gateway
{: #nsx_overview}

A solução VMware NSX Edge Services Gateway (ESG) é uma extensão da oferta do vCenter Server on {{site.data.keyword.cloud_notm}} que está atualmente disponível no {{site.data.keyword.cloud_notm}}. A arquitetura da solução para o vCenter Server detalha os componentes da solução e a configuração de alto nível de cada componente no design.

Para obter mais informações sobre o design do vCenter Server, consulte [Visão geral da solução](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

## Visão geral do NSX Edge Services Gateway
{: #nsx_overview-nsx-esg}

O NSX Edge Services Gateway conecta redes de stub isoladas a redes compartilhadas (uplink), fornecendo serviços comuns de gateway, como o Protocolo de Configuração de Host Dinâmico (DHCP), Rede Privada Virtual (VPN), Conversão de Endereço de Rede (NAT), roteamento dinâmico e balanceamento de carga. As implementações comuns do NSX Edge incluem zona desmilitarizada (DMZ), Extranets de VPN e ambientes de nuvem de diversos locatários em que o NSX Edge cria limites virtuais para cada componente de locatário, carga de trabalho ou gerenciamento. Os recursos a seguir estão disponíveis dentro do NSX Edge Service Gateway.

Tabela 1. Recursos disponíveis com o NSX Edge Service Gateway

| Recurso | Descrição |
|:------- |:----------- |
| Roteamento de serviço do NSX Edge | Fornece as informações de encaminhamento necessárias entre os domínios de transmissão da camada 2, permitindo que você reduza os domínios de transmissão da camada 2 e melhore a eficiência e a escala da rede. O NSX estende essa inteligência para onde as cargas de trabalho residem para fazer roteamento Leste-Oeste. Isso permite uma comunicação mais direta de máquina virtual para máquina virtual sem a necessidade cara ou oportuna de ampliar os hops. Ao mesmo tempo, o NSX também fornece conectividade Norte-Sul, permitindo que os locatários acessem as redes públicas. |
| Firewall | As regras suportadas do firewall incluem configuração de IP de 5 tuplas com IP e intervalos de portas para inspeção stateful para todos os protocolos. |
| NAT | Fornece controles separados para endereços IP de Origem e Destino e a conversão de porta. |
| DHCP | Fornece configuração de conjuntos de IPs, gateways, servidores DNS e domínios de procura. |
| VPN de site para site | Usa configurações de protocolo IPSec padronizadas para interoperar com todos os principais fornecedores de VPN. |
| L2VPN | Estende redes L2 em topologias L3. |
| SSL VPN-Plus |  O SSL VPN-Plus permite que os usuários remotos se conectem com segurança a redes privadas atrás de um gateway NSX Edge. |
| Balanceamento de Car | Fornece endereços IP virtuais simples e dinamicamente configuráveis e grupos de servidores. |
| Alta Disponibilidade | Assegura um NSX Edge ativo na rede no caso de a máquina virtual NSX Edge primária estar indisponível. |

## Links relacionados
{: #nsx_overview-related}

* [Visão geral da solução](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
