---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---
# Resolución de problemas de HCX on IBM Cloud
{: #hcx-archi-trbl}

## El registro de nube falla
{: #hcx-archi-trbl-cloud-reg}

* Hybrid Cloud Services no realiza un reintento si las credenciales son incorrectas. Las credenciales deben autenticarse antes de que Hybrid Cloud Services intente iniciar la sesión e iniciar el registro de la nube.
* El registro de nube puede fallar si las credenciales están mal escritas o si las credenciales de VCS Hybrid Cloud Services Cloud se modifican después de que Hybrid Cloud Services se registre con VCS Hybrid Cloud Services Cloud, lo que ocasiona una discrepancia.
* Para actualizar las credenciales en el cliente web, vaya al separador Iniciación a Hybrid Cloud Services y, en **Tareas básicas**, seleccione **Registrar nueva nube**.

## Dirección MAC duplicada
{: #hcx-archi-trbl-dupl-mac-addr}

Después de la migración, es posible que haya problemas de comunicación entre las máquinas virtuales. Cuando se conserva la dirección MAC durante una migración, es posible que se cree una dirección MAC duplicada.

La dirección MAC de la máquina virtual migrada se puede cambiar para resolver este problema.

1. En el cliente de vSphere, apague la máquina virtual.
2. En el inventario, pulse con el botón derecho del ratón en la máquina virtual y elija **Editar valores** en el menú.
3. En el separador **Hardware virtual**, expanda el adaptador de red.
4. Junto al recuadro de texto Dirección MAC, seleccione **Manual** en el menú.
5. Especifique una dirección MAC exclusiva y pulse **Aceptar**.
6. Compruebe que la dirección MAC exclusiva solucione el problema de comunicación.

## Alto consumo de recursos de host
{: #hcx-archi-trbl-high-host-resource}

En casos excepcionales, si todos los dispositivos virtuales de servicio residen en el mismo host, las máquinas virtuales del servicio Hybrid Cloud Services pueden agotar los recursos de CPU y de disco de un host.

Algunos usuarios han experimentado este problema cuando todos los dispositivos virtuales estaban instalados en un host físico. Dada esta configuración, el rendimiento se degrada cuando sucede lo siguiente simultáneamente:
* La red tiene alta latencia, o pérdida de paquete, o ambas. La migración o el transporte de datos es lento cuando se utiliza Internet público o una red ocupada.
* El optimizador de WAN está consumiendo ancho de banda para cifrar y comprimir (o descifrar y descomprimir) cargas de trabajo de gran tamaño.
* El tráfico de aplicaciones es intenso entre las máquinas virtuales locales y las VM migradas.

Para resolver el problema, siga estos pasos:

1. Antes de cambiar la configuración del centro de datos, revise los requisitos para mantener el soporte de estado estable.
2. Póngase en contacto con el soporte de estado estable si se están agotando los recursos. Pueden aconsejarle sobre cómo volver a configurar el entorno con una cantidad mínima de tiempo de inactividad.

## Enlaces relacionados
{: #hcx-archi-trbl-related}

* [Registro de HCX Manager con vCenter](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-reg-vcenter)
* [Modificación o desinstalación de HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
