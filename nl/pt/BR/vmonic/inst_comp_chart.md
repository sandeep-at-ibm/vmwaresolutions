---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: vmware offering, vmware solutions functions, function support

subcollection: vmware-solutions


---

# Gráfico de comparação Oferta
{: #inst_comp_chart}

Revise o gráfico a seguir para entender as diferenças no suporte de funções para instâncias do VMware vCenter Server e clusters do VMware vSphere.

| Função | vCenter Server | VMware vSphere |
|:--- |:--- |:--- |:--- |
| Desenvolvido por automação avançada {{site.data.keyword.IBM}} <sup>1</sup> | Sim | Não. Autoconstruído e configurado |
| Opções de armazenamento | vSAN ou NFS (armazenamento de nível de arquivo compartilhado) | vSAN ou NFS |
| Número de servidores ESXi no cluster inicial | 4 para vSAN e um mínimo de 2 (3 recomendados) para NFS | 1 para escalar um cluster existente, 4 para novo cluster vSAN e um mínimo de 3 para o novo cluster com NFS |
| Número máximo de servidores ESXi <sup>2</sup> | 59 por cluster | 60 por cluster |
| Implementação de vários sites automatizada em nuvem |Suportado para novas instâncias que são implementadas na V2.0 ou mais recente | Suportado. Configuração automatizada não incluída |
| Incluir servidores ESXi | Suportado | Suportado. Configuração automatizada não incluída |
| Remover servidores ESXi | Suportado | Suportado. Configuração automatizada não incluída |
| Suporte multi-cluster | O número máximo depende das diretrizes de dimensionamento do VMware | Suportado. Configuração automatizada não incluída |
| Atualização e correção gerenciadas pelo cliente da pilha do VMware | Atualizações gerenciadas pelo cliente:<br/>Ferramentas nativas do VMware (VMware Update Manager) | Atualizações gerenciadas pelo cliente:<br/>Ferramentas nativas do VMware (VMware Update Manager) |
| Backup e restauração | Usando manualmente o IBM Spectrum Protect Plus ou o Veeam | Solução de backup e restauração não incluída |
| Rede definida por software | NSX Base, Advanced ou Enterprise | NSX Standard, Base ou Enterprise. Configuração automatizada não incluída |
| BYOL para vSphere e vSAN | Totalmente suportado por cluster | Suportado |
| BYOL para vCenter e NSX | Totalmente suportado por instância | Suportado |
| Opções de upgrade de licença NSX | Upgrade disponível do NSX Base para Advanced ou Enterprise e do NSX Advanced para Enterprise. | Nenhum |
| Edições de licença do vSAN | vSAN Advanced ou Enterprise | vSAN Advanced ou Enterprise  |
| Serviços de complemento | Suportado | Não suportado pela automação dessa solução, mas é possível trazer e instalar o seu próprio software. |
{: caption="Tabela 1. Funções suportadas para o vCenter Server e clusters do vSphere" caption-side="top"}

## Notas
{: #inst_comp_chart-notes}

<sup>1</sup> Segundo um design validado e com a verificação durante a implementação.

<sup>2</sup> É possível aumentar o número de servidores ESXi em um cluster vSAN para um máximo de 64. Para obter mais informações, consulte _Quantos servidores ESXi posso incluir em um cluster?_ em [Perguntas mais frequentes sobre servidores ESXi](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi).

## Links relacionados
{: #inst_comp_chart-related}

* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Visão geral do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Visão geral do VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)
* [BOM do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [ BOM do VMware vSphere ](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
