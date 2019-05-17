---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# Fazendo upgrade de componentes do HCX
{: #vcshcx-upgrade}

O upgrade do HCX é um processo simples que usa a interface com o usuário (IU) da web do cliente na atualização
do gerenciador do HCX do lado do cliente e na IU da web em nuvem na atualização do gerenciador do HCX do lado
da nuvem. Deve-se fazer upgrade de ambos os lados, pois qualquer atualização de componente
da frota faz com que ambos reimplementem os componentes da frota com o
nível de código instalado pelo gerenciador. Se o suporte do VMware solicitar o
ID do sistema, forneça tanto o lado do cliente quanto o da nuvem. Use SSH para o gerenciador do HCX (cliente ou nuvem) e execute
`cat/common/location` para localizar o ID do sistema.

## Links relacionados
{: #vcshcx-upgrade-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
