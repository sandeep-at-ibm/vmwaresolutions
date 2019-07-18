---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: IBM Cloud Private, ICP, tech specs ICP

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do IBM Cloud Private Hosted
{: #icp_overview}

O serviço {{site.data.keyword.cloud}} Private Hosted implementa automaticamente o {{site.data.keyword.cloud_notm}} Private Hosted e o {{site.data.keyword.cloud_notm}} Automation Manager em suas instâncias do VMware vCenter Server. Esse serviço traz o poder de microsserviços e contêineres para seu ambiente VMware no {{site.data.keyword.cloud_notm}}. Com esse serviço, é possível ampliar o mesmo VMware familiar, o modelo operacional e as ferramentas do {{site.data.keyword.cloud_notm}} Private, do local para o {{site.data.keyword.cloud_notm}}.

Esse serviço está disponível para as instâncias a seguir:
* Instâncias do vCenter Server with Hybridity Bundle que são implementadas em (ou submetidas a upgrade para) V2.7 e mais recente
* Instâncias do vCenter Server que são implementadas em (ou submetidas a upgrade para) V2.5 e mais recente

A versão atual do IBM Cloud Private instalada é a 3.1.2. O {{site.data.keyword.cloud_notm}} Automation Manager também é implementado como parte da ordem de serviço do {{site.data.keyword.cloud}} Private Hosted.
{:note}


## Especificações técnicas para o IBM Cloud Private Hosted
{: #icp_overview-specs}

A tabela a seguir lista os requisitos mínimos para pedir o serviço IBM Cloud Private Hosted para o ambiente **Pronto para produção** e o ambiente **Desenvolvimento/Teste**.

|Ambiente | Núcleos | Memória (GB) | Hosts | Armazenamento (GB) |
|:---------- |:---- |:------ |:---- |:------- |
| Produção-Pronto | 52 | 640 | 3 | 8.000 |
| Desenvolvimento / Teste | 30 | 200 | 3 | 4.000 |
{: caption="Tabela 1. Requisitos mínimos para ambientes Prontos para produção e Desenvolvimento/Teste" caption-side="top"}

### Requisitos de recurso para o IBM Cloud Private Hosted
{: #icp_overview-resource-req}

A tabela a seguir lista os requisitos de recurso do serviço {{site.data.keyword.cloud_notm}} Private Hosted em um ambiente pronto para produção.

| Tipo de nó  | Núcleos   |  Memória (GB) | Disco 1 (GB) | Disco 2 (GB) | Número de MVs |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Inicializar       | 12 | 24 | 100 | 1 | 1 |   
| Gerenciamento | 8 | 64 | 500 | 3 | 3 |
| Mestrado     | 8 | 64 | 200 | 3 | 3 |  
| Proxy      | 2 | 4  | 150 | 3 | 3 |
| Trabalhador     | 4 | 16 | 200 | 300 | 6 |
| Consultor de Vulnerabilidade | 8 | 16 | 500 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| servidor NFS | 8 | 4  | 350 | 1 | 1 |
| Gateway de Serviços de Edge NSX | 2 | 1 | 0,5 | 0,5 | 2 |
| Restrições documentadas | 52 | 640 |  | 8.000 |   |
{: caption="Tabela 2. Ambiente pronto para produção" caption-side="top"}

A tabela a seguir lista os requisitos de recurso do serviço {{site.data.keyword.cloud_notm}} Private Hosted nos ambientes de desenvolvimento e teste.

| Tipo de nó  | Núcleos   |  Memória (GB) | Disco 1 (GB) | Disco 2 (GB) | Número de MVs |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Inicializar       | 12 | 24 | 100 | 1 | 1 |   
| Gerenciamento | 8 | 16 | 150 | 1 | 1 |
| Mestrado     | 8 | 16 | 200 | 1 | 1 |  
| Proxy      | 2 | 4  | 150 | 1 | 1 |
| Trabalhador     | 4 | 16 | 200 | 300 | 3 |
| Consultor de Vulnerabilidade | 8 | 16 | 150 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| servidor NFS | 8 | 4  | 350 | 1 | 1 |
| Gateway de Serviços de Edge NSX | 2 | 1 | 0,5 | 0,5 | 2 |
| Restrições documentadas | 30 | 200 |  | 4.000 |  |
{: caption="Tabela 3. Ambientes de desenvolvimento e teste do {{site.data.keyword.cloud_notm}}" caption-side="top"}

### Fórmulas para calcular os requisitos de espaço do IBM Cloud Private Hosted
{: #icp_overview-formulas}

As fórmulas a seguir são usadas para calcular os requisitos de espaço para o IBM Cloud Private e as sobrecargas de gerenciamento.

#### Fórmula para calcular o número de núcleos disponíveis
{: #icp_overview-formulas-1}

A tabela a seguir lista variáveis na Fórmula 1:

`AvailableCores = [HostCoreCount - HostOverheadCores - (HostVSanOverheadCorePercentage * HostCoreCount)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadCores`

| Variáveis | Descrição | Unidade | Exemplo de vSAN | Exemplo de NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores | O número de núcleos reais disponíveis para cargas de trabalho e serviços no ambiente | Núcleos | 38 | 43 |
| HostCount | O número de hosts no cluster padrão | Hosts | 4 | 4 |
| HostCoreCount | O número de núcleos brutos disponíveis em cada host no cluster padrão | Núcleos | 16 | 16 |
| HostOverheadCores | O número de núcleos que são reservados pelo servidor ESXi como sobrecarga, que é igual a 0,1 núcleos | Núcleos | 0,1 | 0,1 |
| MgmtOverheadCores | O número de núcleos reservados pelos componentes de gerenciamento do vCenter Server (vCenter Server, PSC, AD/DNS, Edges), que é igual a cinco núcleos | Núcleos | 5 | 5 |
| vSphereHAHostTolerance | O número de hosts a serem tolerados na configuração do vSphere HA, que é igual a um host |	Hosts	 | 1 | 1 |
| HostVsanOverheadCorePercentage | A porcentagem de núcleos de um host usada pelo vSAN, que será igual a 10% ou igual a 0% se o host não for vSAN | % | 10% | 0% |
{: caption="Tabela 4. Descrição de variáveis na Fórmula 1" caption-side="top"}

#### Fórmula para calcular a memória disponível
{: #icp_overview-formulas-2}

A tabela a seguir lista variáveis na Fórmula 2:

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

| Variáveis | Descrição | Unidade | Exemplo de vSAN | Exemplo de NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory | O número de GB de memória disponível para cargas de trabalho e serviços no ambiente | GB | 693 | 860 |
| HostCount | O número de hosts no cluster padrão | Hosts  | 6 | 6 |
| HostMemory | O número de GBs brutos de memória disponíveis em cada host no cluster padrão | GB | 192 | 192 |
| HostVsanCapacityDiskSize | O número de GB de uma capacidade de cada disco SSD de capacidade da vSAN nesse host, que é igual a 960, 1.946 ou 3.891 ou igual a 0 GB se o host não for vSAN | GB | 960 | 0 |
| HostOverheadMemory | O número de GB de memória reservada pelo servidor ESXi como sobrecarga, que é igual a 4,6 GB | GB | 4,6 | 4,6 |
| MgmtOverheadMemory | O número de GB de memória reservada pelos componentes de gerenciamento do vCenter Server (vCenter Server, PSC, AD/DNS, Edges), que é igual a 77 GB | GB | 77 | 77 |
| vSphereHAHostTolerance | O número de hosts a serem tolerados na configuração do vSphere HA, que é igual a um host | Hosts	| 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | O número de GB de memória reservada pelo gerenciamento de vSAN (representado como porcentagem de um dos discos vSAN de capacidade), que é igual a 2,75% | % | 2,75% | 2,75% |
| HostVsanOverheadMemory | O número de GB de memória reservada pelo gerenciamento de vSAN independentemente do tamanho do disco, que é igual a 7 GB ou igual a 0 GB se o host não for vSAN | GB |  7 | 0 |
{: caption="Tabela 5. Descrição de variáveis na Fórmula 2" caption-side="top"}

## Considerações ao instalar o IBM Cloud Private Hosted
{: #icp_overview-install}

* Reúna as licenças necessárias antes de instalar o serviço {{site.data.keyword.cloud_notm}} Private Hosted. Isso inclui as licenças do {{site.data.keyword.cloud_notm}} Private e do {{site.data.keyword.cloud_notm}} Automation Manager. Assegure-se de que suas licenças suportem não somente a implementação de serviço inicial, mas também a expansão de tamanho futuro em sua infraestrutura.
* Para implementações do {{site.data.keyword.cloud_notm}} Private Hosted em ambientes Prontos para produção, 64 GB de RAM por host não é suportado. Portanto, deve-se selecionar uma opção que seja maior que 64 GB para **RAM**.
* Antes que o serviço {{site.data.keyword.cloud_notm}} Private Hosted seja instalado em seu ambiente, é executada uma verificação com relação à capacidade disponível do cluster padrão no ambiente para assegurar que os componentes de serviço possam se ajustar. Se a verificação de capacidade falhar, o serviço não será instalado e o estado de serviço será configurado como **Falha na validação de capacidade** no console. Além disso, uma mensagem do console com mais detalhes será exibida e você será notificado por e-mail. Para instalar o serviço, deve-se aumentar a capacidade no cluster padrão, incluindo mais hosts ou liberando RAM, CPU ou espaço em disco e, em seguida, incluir o serviço novamente no console. Depois disso, é possível remover o serviço existente no estado **Falha na validação de capacidade** clicando no ícone **Excluir** próximo a ele.
* Se desejar implementar nós adicionais, consulte [Implementando nós adicionais](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering-deploy-nodes#icp_ordering-deploy-nodes).

## Considerações ao remover o IBM Cloud Private Hosted
{: #icp_overview-remove}

* Somente as máquinas virtuais (VMs) que foram implementadas durante a instalação inicial do serviço {{site.data.keyword.cloud_notm}} Private Hosted são excluídas. Qualquer nó que for implementado após a instalação não será limpo.
* O{{site.data.keyword.cloud_notm}} excluirá o VXLAN, o DLR e o Edge Gateway que foi criado durante a implementação inicial do {{site.data.keyword.cloud_notm}} Private Hosted. As MVs que você implementou na VXLAN perderão a conectividade depois que a remoção do serviço {{site.data.keyword.cloud_notm}} Private Hosted for iniciada.

## Links relacionados
{: #icp_overview-related}

* [ Ordenando  {{site.data.keyword.cloud_notm}}  Privado Hospedado ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)
* [ vCenter Server e  {{site.data.keyword.cloud_notm}}  Guia privado ](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [Abrir um chamado para o {{site.data.keyword.cloud_notm}} Private](https://www.ibm.com/mysupport/s/?language=en_US){:external}
* [Licenciamento do {{site.data.keyword.cloud_notm}} Automation Manager](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/licensing.html){:external}
* [Componentes do {{site.data.keyword.cloud_notm}} Automation Manager](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_managed_components.html){:external}
