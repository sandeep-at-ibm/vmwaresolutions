---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

subcollection: vmware-solutions


---

# Remoção do HCX
{: #vcshcx-removal}

A remoção do HCX supõe que as redes estendidas não estejam mais em uso. Use o procedimento a seguir para remover o HCX.

1. Desenque todas as redes estendidas.
2. Na interface com o usuário (IU) do cliente, exclua quaisquer dispositivos L2C. Aguarde até que os dispositivos L2C desapareçam da IU da web.
3. Exclua o CGW. Isso também remove o WAN Opt. Aguarde até que os dispositivos CGW e WAN Opt sejam removidos.
4. Encerre e exclua as máquinas virtuais (MVs) do HCX Manager Appliance do lado do cliente e
da nuvem.
5. Remova o HCX ESG do lado da nuvem do NSX.
6. Use o navegador vCenter Mob para remover o snap-in do HCX.

## Links relacionados
{: #vcshcx-removal-related}

* [Visão geral do vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
