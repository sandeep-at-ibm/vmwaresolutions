---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Lidando com as vulnerabilidades Spectre e Meltdown

Para lidar com as vulnerabilidades Spectre e Meltdown, deve-se aplicar várias correções em uma ordem específica.

## Atualizando o firmware

Para obter as informações mais recentes sobre como atualizar o firmware, veja [Proteção contra vulnerabilidades de segurança recentes](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/).

## Atualizando instâncias que foram implementadas na V2.0 ou mais recente

Instâncias da V2.0 ou mais recente foram implementadas com o VMware vSphere 6.5 e o VMware vCenter Server 6.5. Ambos os componentes de software requerem correção.

### Instâncias do vCenter Server que foram implementadas na V2.0 ou mais recente

#### Para VMware vSphere 6.5

* Para todas as novas instâncias da V2.3, o vSphere será implementado com as correções a seguir aplicadas: ESXi650-201712101-SG, ESXi650-201803401-BG e ESXi650-201803402-BG.  
* Para todas as instâncias existentes implementadas antes da V2.3, todos os novos clusters e servidores ESXi serão atualizados com as correções a seguir: ESXi650-201712101-SG, ESXi650-201803401-BG e ESXi650-201803402-BG.
* Para todos os servidores ESXi existentes, e para quaisquer clusters ou servidores ESXi que você continua implementando antes de fazer upgrade para a V2.3, deve-se aplicar as correções a seguir: ESXi650-201712101-SG, ESXi650-201803401-BG e ESXi650-201803402-BG do [Site de correções do produto VMware](https://my.vmware.com/group/vmware/patch).

#### Para o VMware vCenter Server 6.5

* Para todas as novas instâncias da V2.3, o vCenter Server será implementado com a correção do vCenter 6.5 U1g aplicada.
* Para todas as instâncias existentes implementadas antes da V2.3, deve-se aplicar a correção do vCenter 6.5 U1g por meio do [Site de Correções de produtos VMware](https://my.vmware.com/group/vmware/patch).

### Instâncias do Cloud Foundation que foram implementadas na V2.0 ou mais recente

Para aplicar as correções necessárias para o VMware vSphere 6.5 e o VMware vCenter Server 6.5, deve-se fazer upgrade das instâncias do Cloud Foundation para a versão atual V2.3.

Para todas as instâncias existentes e servidores ESXi, você será solicitado a aplicar as correções (ESXi650-201712101-SG, ESXi650-201803401-BG e ESXi650-201803402-BG para vSphere e vCenter 6.5 U1g para vCenter Server) na página **Atualização e correção** do console do {{site.data.keyword.vmwaresolutions_full}}. Para obter mais informações, veja [Aplicando atualizações a instâncias do Cloud Foundation](../sddc/sd_applyingupdates.html).

### Clusters do VMware vSphere que foram implementados na V2.0 ou mais recente

Para o VMware vSphere 6.5, deve-se aplicar as correções a seguir: ESXi650-201712101-SG, ESXi650-201803401-BG e ESXi650-201803402-BG, por meio do [Site de Correções de produtos VMware](https://my.vmware.com/group/vmware/patch) para todos os seus clusters do vSphere e servidores ESXi, recém-implementados ou existentes.

Para o VMware vCenter Server 6.5, deve-se aplicar a correção do vCenter 6.5 U1g por meio do [Site de Correções de produtos VMware](https://my.vmware.com/group/vmware/patch) para todos os seus servidores vCenter, recém-implementados ou existentes.

## Instâncias que foram implementadas na V1.9 ou anterior

Instâncias do Cloud Foundation, instâncias do vCenter Server e clusters do VMware vSphere da V1.9 ou anterior foram implementados com o VMware vSphere 6.0 e o VMware vCenter Server 6.0.

### Instâncias do vCenter Server que foram implementadas na V1.9 ou anterior

Para o VMware vSphere 6.0 e o VMware vCenter Server 6.0, deve-se aplicar as correções (ESXi600-201711101-SG, ESXi600-201803401-BG e ESXi600-201803402-BG para o vSphere e vCenter 6.0 U3e para o vCenter Server) por meio do [Site de Correções de produtos VMware](https://my.vmware.com/group/vmware/patch) a todas as instâncias e servidores ESXi, recém-implementados ou existentes.

### Instâncias do Cloud Foundation que foram implementadas na V1.9 ou anterior

Atualizações para essas instâncias estarão disponíveis quando as atualizações necessárias do fornecedor das quais essas instâncias dependem forem liberadas.

### Clusters do VMware vSphere que foram implementados na V1.9 ou anterior

Para o VMware vSphere 6.0 e o VMware vCenter Server 6.0, deve-se aplicar as correções (ESXi600-201711101-SG, ESXi600-201803401-BG e ESXi600-201803402-BG para vSphere e vCenter 6.0 U3e para vCenter Server) por meio do [Site de Correções de produtos VMware](https://my.vmware.com/group/vmware/patch) para todos os seus clusters vSphere e servidores ESXi, recém-implementados ou existentes.

### Links relacionados

* [Aplicando atualizações a instâncias do Cloud Foundation](../sddc/sd_applyingupdates.html)
* [Proteger contra vulnerabilidades de segurança recentes](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [Site de Correções de Produtos VMware](https://my.vmware.com/group/vmware/patch)
