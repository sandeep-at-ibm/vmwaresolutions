---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# El sistema vCenter Server secundario no aparece en el inventario del cliente web de vSphere
{: #trbl_sec_inst_not_visible}

## Problema
{: #trbl_sec_inst_not_visible-problem}

En una configuración de varios sitios, después de añadir una nueva instancia secundaria, su sistema vCenter Server no resulta visible cuando se inicia una sesión en el cliente web de VMware vSphere de una instancia solicitada anteriormente.

## Solución
{: #trbl_sec_inst_not_visible-resolution}

Este es un problema conocido de VMware 6.5.

Para resolver el problema, debe rearrancar el cliente web de vSphere:

1. Mediante la cuenta **root**, conéctese sobre **ssh** a la máquina virtual (VM) de vCenter de la instancia solicitada anteriormente.
2. Escriba ``shell`` para entrar en el shell bash.
3. Escriba `service-control --stop vsphere-client` para detener el cliente.
4. Escriba `service-control --start vsphere-client` para rearrancar el cliente.
5. Una vez rearrancado el cliente web de vSphere de la instancia solicitada anteriormente, confirme que el sistema vCenter Server de la instancia secundaria recién añadida está visible en el cliente web de vSphere.
