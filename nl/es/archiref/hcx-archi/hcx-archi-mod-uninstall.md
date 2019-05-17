---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Modificación o desinstalación de HCX
{: #hcx-archi-mod-uninstall}

Las instalaciones existentes se pueden actualizar, y es posible eliminar todo o parte de un despliegue de Hybrid Cloud Services.

##  Eliminación de la extensión de una red de capa 2
{: #hcx-archi-mod-uninstall-unstretch-layer2}

Es necesario eliminar la extensión de una red de capa 2 antes de eliminar el dispositivo virtual asociado del servicio concentrador de capa 2 o antes de desinstalar Hybrid Cloud Services.

1. Marque las redes extendidas.
2. En la página del plugin Hybrid Cloud Services, visualice el separador Servicios híbridos y marque la sección Servicio de extensión de red. Si hay trabajos activos o planificados en curso, espere hasta que se hayan completado o deténgalos antes de continuar.
3. Para eliminar la red, pulse el icono Suprimir (X roja) de la derecha.
4. Pulse **Aceptar** para confirmar.

## Desinstalación de dispositivos virtuales HCX
{: #hcx-archi-mod-uninstall-uninst-hva}

Un dispositivo de servicio se puede desinstalar para preparar la desinstalación de Hybrid Cloud Services o debido a un cambio en la arquitectura de la instalación. Utilice Hybrid Cloud Services para administrar dispositivos, tal como se describe en el siguiente procedimiento.

### Requisitos previos para desinstalar dispositivos virtuales HCX
{: #hcx-archi-mod-uninstall-prereq-uninst-hva}

* Cancele o restablezca el tiempo de ejecución de las migraciones que se puedan producir durante la tarea de desinstalación.
* Compruebe en la consola de tareas del cliente web de vSphere si hay migraciones en ejecución y espere hasta que se hayan completado.
* Asegúrese de que no haya tareas activas de Hybrid Cloud Services de ningún tipo.

Nunca suprima dispositivos virtuales desde el inventario de vSphere. Utilice siempre el portal de gestión para interactuar con los dispositivos virtuales de servicio.
{:note}

### Procedimiento para desinstalar dispositivos virtuales HCX
{: #hcx-archi-mod-uninstall-proc-uninst-hva}

1. En la interfaz del cliente web de vSphere, seleccione el plugin Hybrid Cloud Services en el panel de la izquierda.
2. En el panel central, pulse el separador **Servicios híbridos**.
3. Localice el dispositivo Hybrid Cloud Gateway y pulse la entrada para visualizar los detalles.
4. En la parte inferior derecha, pulse el icono Suprimir para eliminar el dispositivo.
5. Si una red extendida no comparte una dirección IP con el dispositivo Hybrid Cloud Gateway, debe eliminarla por separado. Amplíe los detalles del servicio de extensiones de red y pulse el icono Suprimir para eliminar el concentrador de capa 2.

Hybrid Cloud Gateway y cualquier dispositivo virtual de servicio híbrido que utilice Hybrid Cloud Gateway se eliminan tanto de vCenter como de VCS Hybrid Cloud Services Cloud.

## Desinstalación de HCX Manager
{: #hcx-archi-mod-uninstall-unist-hcxm}

El dispositivo HCX Manager se debe desinstalar antes de eliminar la solución HCX desde el centro de datos local. Siga estos pasos para desinstalar la máquina virtual de Hybrid Cloud Services.

1. Elimine la extensión de todas las redes de capa 2.
2. Elimine los dispositivos virtuales de servicio híbrido.
3. En el vCenter local, apague la máquina virtual de Hybrid Cloud Services.
4. Suprima la máquina virtual de Hybrid Cloud Services.

Se eliminan todos los dispositivos de servicio virtual. Es posible que se conserven los siguientes elementos:
* Registros
* MV migradas

### Qué hacer a continuación
{: #hcx-archi-mod-uninstall-what-next}

Se puede hacer copia de seguridad o se pueden suprimir manualmente las VM y los registros migrados.

## Inicio de sesión en el portal de gestión de HCX
{: #hcx-archi-mod-uninstall-log-hcxmp}

El despliegue de Hybrid Cloud Services se puede administrar desde el portal de gestión mediante una interfaz de usuario basada en navegador.

1. En un navegador web, escriba la dirección IP asignada a Hybrid Cloud Services y especifique el número de puerto 9443. Por ejemplo, `https://HCXip:9443`.
2. La interfaz de usuario de Hybrid Cloud Services se abre en una ventana de navegador web utilizando SSL. Si es necesario, acepte el certificado de seguridad. Se abre la pantalla de inicio de sesión de VMware Hybridity and Networking.
3. Escriba el nombre de usuario y la contraseña. De forma predeterminada, el nombre de usuario es Admin. La contraseña es el valor que se ha proporcionado al instalar el dispositivo virtual de Hybrid Cloud Services.

## Enlaces relacionados
{: #hcx-archi-mod-uninstall-related}

* [Resolución de problemas de HCX on IBM Cloud](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-trbl)
