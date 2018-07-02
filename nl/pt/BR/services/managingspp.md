---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Gerenciando o IBM Spectrum Protect Plus no IBM Cloud

## Acessando o console de gerenciamento do IBM Spectrum Protect Plus

Para gerenciar o serviço IBM Spectrum Protect&trade; Plus no {{site.data.keyword.cloud}}, deve-se acessar o console de gerenciamento do IBM Spectrum Protect Plus concluindo as etapas a seguir:
1. Use a VPN de infraestrutura do {{site.data.keyword.cloud_notm}} ou um servidor jump para permitir o acesso ao endereço IP da máquina virtual do IBM Spectrum Protect Plus. É possível localizar o endereço IP na página de detalhes do serviço para o IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} no console do {{site.data.keyword.vmwaresolutions_short}}.
2. Para acessar o console de gerenciamento do IBM Spectrum Protect Plus, clique em **Visualizar o console do IBM Spectrum Protect Plus** na página de detalhes do serviço para o IBM Spectrum Protect Plus on {{site.data.keyword.cloud}} e, em seguida, efetue login usando as credenciais listadas na mesma página de detalhes do serviço.

## Aplicando correções para o IBM Spectrum Protect Plus no IBM Cloud

Você é responsável por manter o serviço IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}} na versão mais recente. É possível fazer download das atualizações necessárias do [IBM Spectrum Protect Plus na página {{site.data.keyword.cloud_notm}} Suporte](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus).

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](../vcenter/vc_addingremovingservices.html)

## Atualizando o sistema operacional da máquina virtual do IBM Spectrum Protect Plus

Para atualizar o sistema operacional da máquina virtual do IBM Spectrum Protect Plus, deve-se efetuar login como usuário **raiz**. A senha de usuário **raiz** é a mesma que a senha que pode ser localizada na página de detalhes do serviço para o IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

## Fazendo backup e restaurando componentes de gerenciamento para instâncias que possuem o IBM Spectrum Protect Plus on IBM Cloud instalado

 **Nota**: as informações a seguir se aplicam a instalações do IBM Spectrum Protect Plus em instâncias implementadas na (ou submetidas a upgrade para a) V2.3 ou mais recente. Para instâncias da V2.2, esse serviço fornece proteção de dados somente para as máquinas virtuais de carga de trabalho.

O serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} é pré-configurado com uma tarefa de backup de gerenciamento que é executada automaticamente para fazer backup dos componentes de gerenciamento a seguir diariamente com até sete pontos de restauração:
* VMware vCenter Server
* Platform Services Controller (PSC)
* IBM CloudDriver
* **Somente instâncias do Cloud Foundation**: VMware SDDC Manager
* **Instâncias do vCenter Server somente com HA AD/DNS**: par de alta disponibilidade de AD/DNS

Se ocorrem falhas nos componentes de gerenciamento, é possível abrir um chamado [entrando em contato com o Suporte IBM](../vmonic/trbl_support.html) para solicitar que os componentes de gerenciamento sejam restaurados para um backup anterior.

## Links relacionados

* [IBM Spectrum Protect Plus no {{site.data.keyword.cloud_notm}} visão geral](spp_considerations.html)
* [Como aumentar o armazenamento vsnap para a pós-implementação do IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)
* [Documentação do IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
