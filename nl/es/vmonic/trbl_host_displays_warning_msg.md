---

copyright:

  years:  2016, 2018

lastupdated: "2017-06-29"

---

# El servidor ESXi muestra un problema de configuración

## Problema
Se muestra un problema de configuración en el separador **Problemas** del separador **Monitor** del servidor VMware ESXi en el cliente de vSphere.

Se muestra el siguiente mensaje en el separador **Problemas** para el servidor ESXi:

`This host currently has no management network redundancy (Este servidor actualmente no tiene redundancia de red de gestión)`

El mensaje se muestra aunque haya dos enlaces ascendentes disponibles para el conmutador distribuido privado, que proporciona una redundancia.

## Solución
Este es un problema conocido de VMware. Para resolver el problema, siga las instrucciones de [El host ESX/ESXi muestra un mensaje de aviso cuando la condición de prueba es false (2008602)](https://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2008602){:new_window}.
