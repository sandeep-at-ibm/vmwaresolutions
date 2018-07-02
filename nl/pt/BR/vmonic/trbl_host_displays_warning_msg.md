---

copyright:

  years:  2016, 2018

lastupdated: "2017-06-29"

---

# Servidor ESXi exibe problema de configuração

## Problema
Um problema de configuração é exibido na guia **Problemas** da guia **Monitorar** do servidor VMware ESXi no cliente vSphere.

A mensagem a seguir é exibida na guia **Problemas** para o servidor ESXi:

`Esse host atualmente não tem nenhuma redundância de rede de gerenciamento`

A mensagem será exibida mesmo que haja dois uplinks disponíveis para o comutador distribuído privado, que fornece uma redundância.

## Resolução
Esse é um problema conhecido do VMware. Para resolver o problema, siga as instruções em [O host ESX/ESXi exibe uma mensagem de aviso quando a condição de teste é falsa (2008602)](https://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2008602){:new_window}.
