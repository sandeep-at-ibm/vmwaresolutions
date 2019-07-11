---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, configuration issue, ESXi server issue

subcollection: vmware-solutions


---

# Servidor ESXi exibe problema de configuração
{: #trbl_host_displays_warning_msg}

## Problema
{: #trbl_host_displays_warning_msg-problem}

Um problema de configuração é exibido na guia **Problemas** da guia **Monitorar** do servidor VMware ESXi no cliente vSphere.

A mensagem a seguir é exibida na guia **Problemas** para o servidor ESXi:

`Esse host atualmente não tem nenhuma redundância de rede de gerenciamento`

A mensagem será exibida mesmo que haja dois uplinks disponíveis para o comutador distribuído privado, que fornece uma redundância.

## Resolução
{: #trbl_host_displays_warning_msg-resolution}

Esse é um problema conhecido do VMware. Para resolver o problema, siga as instruções em [O host ESX/ESXi exibe uma mensagem de aviso quando a condição de teste é falsa (2008602)](https://kb.vmware.com/s/article/2008602){:new_window}.
