---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Tipos de atualizações de software do VMware

O VMware usa os termos a seguir para descrever atualizações de software.

Tabela 1. Termos e definições de atualização de software do VMware

| Termo | Definição |
|:------- |:----------- |
| Boletim |	Um agrupamento de um ou mais VIBs. Os marcadores são definidos dentro dos metadados. |
| Depósito |	Um agrupamento lógico de VIBs e metadados associados que são publicados on-line |
| Imagem de upgrade do |	Uma imagem ESXi pode ser importada no repositório do Update Manager e usada para fazer upgrade de hosts ESXi 5.5 ou ESXi 6.0 para o ESXi 6.5. |
| Extensão | 	Um boletim que define um grupo de VIBs para incluir um componente opcional em um host ESXi. Uma extensão é geralmente fornecida por um terceiro que também é responsável por correções ou atualizações para a extensão. |
| Metadados |	Dados extras que definem informações de dependência, descrições textuais, requisitos do sistema e boletins. |
| Arquivo .zip do pacote configurável off-line |	Um archive que encapsula VIBs e metadados correspondentes em um pacote autocontido que é útil para correção off-line. Não é possível usar pacotes configuráveis off-line de terceiros ou pacotes configuráveis off-line que você gerou por meio de conjuntos VIB customizados para upgrade do host do ESXi 5.5 ou do ESXi 6.0 para o ESXi 6.5. |
| Patch |	Um boletim que agrupa um ou mais VIBs para resolver um problema ou aprimoramento específico. |
| Roll-up |	Uma coleção de correções que são agrupadas para facilidade de download e implementação. |
| Upgrade de VA |	Atualizações para um dispositivo virtual, que o fornecedor considera um upgrade. |
| VIB |	Um VIB é um único pacote de software. |

### Links relacionados

* [VMware HCX no {{site.data.keyword.cloud}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Soluções de VMware no {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
