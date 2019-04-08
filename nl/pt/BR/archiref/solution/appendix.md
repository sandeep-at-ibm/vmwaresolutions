---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# Gráfico de comparação para edições do componente do VMware
{: #solution-appendix}

## Comparação de Edição do VMware NSX
{: #solution-appendix-nsx-editions}

Dentro desse design, há múltiplos componentes que requerem licenças. Essas informações capturam as licenças mínimas que são necessárias para que o ambiente opere corretamente.

Tabela 1. Requisitos de licença

Componente | Propósito | Licença
----------|---------|-------------
**vSphere** | Virtualização de cálculo | vSphere 6.7 Enterprise Plus
**vCenter Server** | Gerenciamento de infraestrutura | vCenter Server 6.7 Standard
**NSX** | Virtualização de rede | NSX Base for Service Providers 6.4
**vSAN** | Virtualização de armazenamento | vSAN 6.6 Advanced  

A edição do NSX Base for Service Providers está disponível somente para provedores de serviço por meio da VMware vCloud Air Network (vCAN). Os recursos nesta edição podem ser localizados na tabela a seguir.
{:note}

Tabela 2. Gráfico de comparação de edição do VMware NSX

| Recurso NSX                                   | Base | Avançado | Corporativo |
|-----------------------------------------------|------|----------|------------|
| Comutação distribuída e roteamento             | •    | •        | •          |
| Firewall do NSX Edge                             | •    | •        | •          |
| NAT                                           | •    | •        | •          |
| Balanceamento de carga do NSX Edge                       | •    | •        | •          |
| VPN (IPsec)                                   | •    | •        | •          |
| VPN (SSL)                                     | •    | •        | •          |
| automação acionada por API                         | •    | •        | •          |
| Integração com vRealize e OpenStack \ *     | •    | •        | •          |
| Automação de políticas de segurança com vRealize |      | •        | •          |
| L2 de ponte do SW L2 para ambiente físico        |      | •        | •          |
| Roteamento dinâmico com ECMP (ativo-ativo)     |      | •        | •          |
| Firewalling Distribuído                       |      | •        | •          |
| Integração com o Active Directory             |      | •        | •          |
| Monitoramento de atividade do                    |      | •        | •          |
| Inserção de serviço (integração de terceiros)     |      | •        | •          |
| Balanceamento de Carga Distribu                    |      |          | •          |
| VCenter Cruzado NSX                             |      |          | •          |
| Otimizações NSX multissite                  |      |          | •          |
| Gateway remoto                                |      |          | •          |
| Integração com VTEPs da HW                     |      |          | •          |
\*Somente integração de L2, L3 e NSX Edge. Nenhum consumo de Grupos de Segurança

## Comparação de edição do VMware vSAN
{: #solution-appendix-vsan-editions}

A tabela a seguir lista os recursos disponíveis para as edições **Advanced** e **Enterprise** do VMware vSAN que a solução suporta.

Tabela 3. Gráfico de comparação de edição do VMware vSAN

| Recurso do vSAN                                    | Avançado | Corporativo |
|-------------------------------------------------|----------|------------|
| Gerenciamento baseado em política de armazenamento                 | •        | •          |
| Atualização do cache de leitura / gravação                        | •        | •          |
| RAID Distribuído                                | •        | •          |
| Comutador Distribuído Virtual                      | •        | •          |
| Reconhecimento do rack                                  | •        | •          |
| replicação do vSphere                             | •        | •          |
| Soma de verificação de                               | •        | •          |
| Hardware All-Flash                              | •        | •          |
| Serviço de Destino iSCSI                            | •        | •          |
| Limite de IOPS                                      | •        | •          |
| Desduplicação e compactação                   | •        | •          |
| RAID-5/6 erasure codificação                         | •        | •          |
| Criptografia de dados em repouso                         |          | •          |
| Cluster estendido com proteção contra falha local |          | •          |

## Links relacionados
{: #solution-appendix-related}

* [Visão geral da solução](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [Visão geral do design](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [Fazendo backup de componentes](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)
