---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Fazendo upgrade de componentes do HCX
{: #hcxclient-vcs-upgrade}

O upgrade do HCX é um processo simples que usa a interface com o usuário (IU) da web do cliente na atualização
do gerenciador do HCX do lado do cliente e na IU da web em nuvem na atualização do gerenciador do HCX do lado
da nuvem.

Deve-se fazer upgrade de ambos os lados pois quaisquer atualizações de componentes da frota fazem com que ambos reimplementem os componentes da frota com o nível de código que está instalado no HCX Manager.

Se o Suporte ao VMware solicitar o ID do sistema, forneça tanto o lado do cliente quanto o lado da nuvem. Use SSH para o HCX Manager (cliente ou nuvem) e execute `cat /common/location` para localizar o ID do sistema.

## Links relacionados
{: #hcxclient-vcs-upgrade-related}

* [Glossário de componentes e termos do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparando o ambiente de instalação](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Implementação do cliente HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Entrelaçamento de serviços HCX no local](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrações de nuvem híbrida do VMware](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Monitorando parâmetros e componentes](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Resolução de problemas do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
