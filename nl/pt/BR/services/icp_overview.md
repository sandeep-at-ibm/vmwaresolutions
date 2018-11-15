---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do IBM Cloud Private Hosted

O serviço {{site.data.keyword.cloud}} Private Hosted implementa automaticamente o {{site.data.keyword.cloud_notm}} Private Hosted em suas instâncias do VMware vCenter Server. Esse serviço traz o poder de microsserviços e contêineres para seu ambiente VMware no {{site.data.keyword.cloud_notm}}. Com esse serviço, é possível ampliar o mesmo VMware familiar, o modelo operacional e as ferramentas do {{site.data.keyword.cloud_notm}} Private, do local para o {{site.data.keyword.cloud_notm}}.

Esse serviço está disponível para:
* Instâncias do vCenter Server que são implementadas ou submetidas a upgrade para a V2.5 e mais recente
* Instâncias do vCenter Server with Hybridity Bundle que são implementadas ou submetidas a upgrade para a V2.7 e mais recente.
{:note}

## Especificações técnicas para o IBM Cloud Private Hosted

A tabela a seguir lista os requisitos mínimos para pedir o serviço IBM Cloud Private Hosted para o ambiente **Pronto para produção** e o ambiente **Desenvolvimento/Teste**.

Tabela 1. Requisitos mínimos para ambientes Prontos para produção e Desenvolvimento/Teste

|Ambiente | Núcleo | Memória | Host | Armazenamento |
|:---------- |:---- |:------ |:---- |:------- |
| Produção-Pronto | 52 | 640 | 3 | 8000 |
| Desenvolvimento / Teste | 30 | 200 | 3 | 4000 |

### Requisitos do recurso do IBM Cloud Privated Hosted

As tabelas a seguir listam os requisitos de recurso do serviço {{site.data.keyword.cloud_notm}} Private Hosted em ambientes Prontos para produção e Desenvolvimento/Teste.

Tabela 2. Requisitos de recursos do {{site.data.keyword.cloud_notm}} Private Hosted no ambiente Pronto para produção

| Tipo de nó  | Núcleos   |  Memória (GB) | Disco 1 (GB) | Disco 2 (GB) | Número de VMs |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Inicializar       | 8 | 16 | 100 | 1 | 1 |   
| Gerenciamento | 8 | 64 | 500 | 3 | 3 |
| Mestrado     | 8 | 64 | 200 | 3 | 3 |  
| Proxy      | 2 | 4  | 150 | 3 | 3 |
| Trabalhador     | 4 | 16 | 200 | 300 | 6 |
| Consultor de Vulnerabilidade | 8 | 16 | 500 | 3 | 3 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| servidor NFS | 8 | 4  | 350 | 1 | 1 |
| Borda | 2 | 1 | 0,5 | 0,5 | 2 |
| Total | 162 | 642 | 6401 | 1951 | 26 |
| Restrições documentadas | 52 | 640 |  | 8000 |   |
|   | Proporção de 1: 3 | 1: 1 proporção |  | 1: 1 proporção |  |

Tabela 3. Requisitos de recursos do {{site.data.keyword.cloud_notm}} Private Hosted no ambiente de Desenvolvimento/Teste

| Tipo de nó  | Núcleos   |  Memória (GB) | Disco 1 (GB) | Disco 2 (GB) | Número de VMs |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Inicializar       | 8 | 16 | 100 | 1 | 1 |   
| Gerenciamento | 8 | 16 | 150 | 1 | 1 |
| Mestrado     | 8 | 16 | 200 | 1 | 1 |  
| Proxy      | 2 | 4  | 150 | 1 | 1 |
| Trabalhador     | 4 | 16 | 200 | 300 | 3 |
| Consultor de Vulnerabilidade | 8 | 16 | 150 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| servidor NFS | 8 | 4  | 350 | 1 | 1 |
| Borda | 1 | 0,5 | 0,5 | 2 | 2 |
| Total | 96 | 201 | 2401 | 1050 | 15 |
| Restrições documentadas | 30 | 200 |  | 4000 |  |
|  | Proporção de 1: 3 | 1: 1 proporção |  | 1: 1 proporção |  |

### Fórmulas para calcular os requisitos de espaço do IBM Cloud Private Hosted

As fórmulas a seguir são usadas para calcular os requisitos de espaço do IBM Cloud Private e as sobrecargas de gerenciamento.

Fórmula 1: `AvailableCores = [ HostCoreCount - HostOverheadCores - ( HostVSanOverheadCorePercentage * HostCoreCount) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadCores`

Tabela 4. Descrição de variáveis na Fórmula 1

| Variáveis	| Descrição |	Unidade |	Exemplo de vSAN | Exemplo de NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |	O número de núcleos reais disponíveis para cargas de trabalho e serviços no ambiente |	núcleos |	38	| 43 |
| HostCount	| O número de hosts no cluster padrão	| hosts | 4	| 4 |
| HostCoreCount	| O número de núcleos brutos disponíveis em cada host no cluster padrão |	núcleos |	16 | 16 |
| HostOverheadCores	| O número de núcleos reservados pelo servidor ESXi como sobrecarga, que é igual a 0,1 núcleos	| núcleos	| 0,1 |	0,1 |
| MgmtOverheadCores | O número de núcleos reservados pelos componentes de gerenciamento do vCenter Server (vCenter Server, PSC, AD/DNS, Edges), que é igual a 5 núcleos	| núcleos	| 5	| 5 |
| vSphereHAHostTolerance |	O número de hosts a serem tolerados na configuração do vSphere HA, que é igual a 1 host |	hosts	 | 1 | 1 |
| HostVsanOverheadCorePercentage | A porcentagem de núcleos de host utilizados pelo vSAN, que é igual a 10% ou igual a 0% se for host não vsan	| % | 10% |	0% |

Fórmula 2: `AvailableMemory = [ HostMemory - HostOverheadMemory - HostVsanOverheadMemory - ( HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadMemory`

Tabela 5. Descrição de variáveis na Fórmula 2

| Variáveis	| Descrição |	Unidade |	Exemplo de vSAN | Exemplo de NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory	| O número de GB de memória disponível para cargas de trabalho e serviços no ambiente | GB | 	693	| 860 |
| HostCount	| O número de hosts no cluster padrão | hosts  | 6	| 6 |
| HostMemory |	O número de GBs brutos de memória disponíveis em cada host no cluster padrão |	GB	| 192 |	192 |
| HostVsanCapacityDiskSize | O número de GB de uma capacidade de cada disco SSD de capacidade vSAN nesse host, que é igual a 960, 1946 ou 3891 ou igual a 0 GB se não VSAN | GB |	960 | 0 |
| HostOverheadMemory |	O número de GB de memória reservada pelo servidor ESXi como sobrecarga, que é igual a 4,6 GB |	GB	| 4,6 |	4,6 |
| MgmtOverheadMemory |	O número de GB de memória reservada pelos componentes de gerenciamento do vCenter Server (vCenter Server, PSC, AD/DNS, Edges), que é igual a 77 GB | GB | 77 | 77 |
| vSphereHAHostTolerance | O número de hosts a serem tolerados na configuração do vSphere HA, que é igual a 1 host | hosts	| 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | O número de GB de memória reservada pelo gerenciamento de vSAN (representado como porcentagem de um dos discos vSAN de capacidade), que é igual a 2,75% |	% | 2,75%	| 2,75% |
| HostVsanOverheadMemory | O número de GB de memória reservada pelo gerenciamento de vSAN independentemente do tamanho de disco, que é igual a 7 GB ou é igual a 0 GB se não VSAN	| GB |  7	| 0 |

## Considerações ao instalar o IBM Cloud Private Hosted

Reúna a licença necessária antes de instalar o serviço {{site.data.keyword.cloud_notm}} Private Hosted. É recomendado assegurar que sua licença possa suportar não somente a implementação inicial do {{site.data.keyword.cloud_notm}} Private Hosted, mas também a futura expansão do tamanho do {{site.data.keyword.cloud_notm}} Private Hosted em sua infraestrutura.

## Considerações ao remover o IBM Cloud Private Hosted

* O {{site.data.keyword.cloud_notm}} exclui somente as máquinas virtuais (VMs) que foram implementadas durante a instalação inicial do serviço {{site.data.keyword.cloud_notm}} Private Hosted. Qualquer nó que for implementado após a instalação não será limpo.
* O {{site.data.keyword.cloud_notm}} excluirá o VXLAN, o DLR e o gateway de borda que foi criado durante a implementação inicial do serviço {{site.data.keyword.cloud_notm}} Private Hosted. As VMs que você implementou na VXLAN perderão a conectividade assim que a remoção do serviço {{site.data.keyword.cloud_notm}} Private Hosted for iniciada.

### Links relacionados

* [ Ordenando o IBM Cloud Privado Hospedado ](../services/icp_ordering.html)
* [ IBM Cloud Privado Hospedado ](https://www.ibm.com/developerworks/community/files/form/anonymous/api/library/eafb752c-55f3-4b07-9b20-b61c8ea980b9/document/af203658-30c0-40ba-81b5-46c393fb723f/media/IBM_Cloud_Private_Hosted-IBM_Cloud.pdf)  (download em PDF)
* [Abra um chamado para o IBM Cloud Private](https://www.ibm.com/mysupport/s/?language=en_US)
