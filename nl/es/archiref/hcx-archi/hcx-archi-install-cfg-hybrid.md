---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# Instalación y configuración de servicios híbridos
{: #hcx-archi-install-cfg-hybrid}

El instalador suministra y configura una máquina virtual para cada dispositivo virtual de servicio. Las máquinas virtuales de servicio se despliegan tanto en el entorno local como en la nube.

## Requisitos previos
{: #hcx-archi-install-cfg-hybrid-prereq}

* HCX Manager debe estar instalado de forma local y registrado con un punto final de nube habilitado para HCX de VCF/VCS.
* El centro de datos virtual de destino debe tener recursos suficientes.

## Visión general de la configuración
{: #hcx-archi-install-cfg-hybrid-config-ovw}

En el procedimiento de configuración se supone que se configurarán todos los dispositivos virtuales de servicio. Sin embargo, no todos son necesarios.
* El dispositivo Hybrid Cloud Gateway es necesario.
* La instalación de la optimización de WAN se realiza mediante la comprobación del recuadro de servicio de optimización de WAN durante la instalación. No es necesario llevar a cabo ninguna configuración
adicional.
* Para configurar el servicio de extensión de red, consulte la sección _Configuración del servicio de extensión de red_. El despliegue del dispositivo opcional se puede diferir volviendo a la página Servicios híbridos e instalando el dispositivo más adelante.

## Inicio de la instalación y configuración del dispositivo virtual de servicio híbrido
{: #hcx-archi-install-cfg-hybrid-start-hsva}

Se utiliza la interfaz web sencilla para instalar los dispositivos virtuales de servicio y para configurar más concentradores de capa 2.

HCX Manager debe estar instalado y registrado con el punto final de nube habilitado para HCX de VCF/VCS.

### Procedimiento para instalar y configurar el dispositivo virtual de servicio híbrido
{: #hcx-archi-install-cfg-hybrid-proc-install}

1. Inicie una sesión en el cliente web de vSphere.
2. En el separador **Inicio**, pulse el icono **Hybrid Cloud Services**.
3. Pulse el separador **Servicios híbridos**.
4. Pulse **Instalar servicio**.
5. En la página **Elegir servicios híbridos**, seleccione los servicios que se van a instalar y pulse **Siguiente**.

### Qué hacer a continuación
{: #hcx-archi-install-cfg-hybrid-start-hsva-next}

1. El siguiente paso consiste en configurar el dispositivo Hybrid Cloud Gateway, si es necesario.
2. Se puede añadir un concentrador de capa 2 a una instalación existente en cualquier momento si hay suficientes recursos disponibles para dar soporte a la extensión.

## Configuración de Hybrid Cloud Gateway
{: #hcx-archi-install-cfg-hybrid-config-hcg}

Configure el dispositivo virtual de servicio Hybrid Cloud Gateway. Antes de empezar, siga los pasos del apartado _Inicio de la instalación y configuración del dispositivo virtual de servicio híbrido_ y marque Hybrid Cloud Gateway.

### Procedimiento para configurar Hybrid Cloud Gateway
{: #hcx-archi-install-cfg-hybrid-proc-config-hcg}

En la página **Hybrid Cloud Gateway**, especifique los siguientes valores y pulse **Siguiente**:
* **Red**: el conmutador que conecta la interfaz de gestión de Hybrid Cloud Gateway. En los casos de uso 1 y 2, puede ser un conmutador virtual estándar o un conmutador distribuido virtual. Para cualquier configuración que utilice la extensión de capa 2, debe ser un conmutador distribuido virtual.
* **Clúster/Host**: seleccione el clúster o el host en el que se va a desplegar la pasarela de nube.
* **Almacén de datos**: seleccione el almacén de datos en el que se va a desplegar la pasarela de nube.
* **VM/Nombre de host**: este valor es opcional.
* Especifique la dirección IP/CIDR, la pasarela predeterminada y el servidor DNS que se va a utilizar para la interfaz de gestión de la pasarela de nube.
* Para especificar varias direcciones para el servidor DNS, sepárelas con comas.
* En **Ampliado (opcional)**, elija la red vMotion, si procede, y defina las contraseñas de **admin** y de **root**. Estas contraseñas son específicas del dispositivo Hybrid Cloud Gateway. El nombre de usuario y la contraseña no tienen que coincidir con los configurados para el dispositivo Hybrid Cloud Services.

## Configuración del servicio de extensión de red
{: #hcx-archi-install-cfg-hybrid-config-nes}

Configure un servicio de extensión de red para el despliegue de una sola vía de acceso o para una extensión de red autónoma en una vía de acceso alternativa. Antes de empezar, seleccione el servicio de extensión de red. Si se ha instalado la configuración de una sola vía de acceso, **Extensión de red** es la única opción.

### Procedimiento para configurar el servicio de extensión de red
{: #hcx-archi-install-cfg-hybrid-proc-config-nes}

1. En la página **Servicio de extensión de red**, seleccione un conmutador distribuido virtual en el menú **Conmutador distribuido**. Cuando instale un concentrador de capa 2 estándar, estará disponible el recuadro de selección **Direccionar redes extendidas a través de Hybrid Cloud Gateway**. No aparecerá para L2C de alto rendimiento.
2. Si se selecciona **Direccionar redes extendidas a través de Hybrid Cloud Gateway**, el instalador determina una ubicación razonable para el concentrador de capa 2 (en función en el conmutador) y rellena la información de ubicación. De lo contrario, la información de ubicación se debe especificar manualmente en el paso siguiente.
3. Establezca la ruta para la ubicación del concentrador L2. Si se ha seleccionado **Direccionar redes extendidas a través de Hybrid Cloud Gateway**, estos valores no se pueden editar.
  * **Red**: la red de despliegue de la interfaz de gestión del concentrador de capa 2.
  * **Cálculo**: el clúster de despliegue o el host para el concentrador de capa 2.
  * **Almacén de datos**: almacén de datos de despliegue para el concentrador de capa 2.
  * **VM/Nombre de host**: este valor es opcional.
4. Especifique los parámetros de red para el concentrador de capa 2 local.
  * Si esta opción está inhabilitada, utilice los parámetros predeterminados que proporciona el instalador.
  * Si el grupo de puertos seleccionado en el menú **Red** de la página Hybrid Cloud Gateway no forma parte del conmutador distribuido, marque **Especificar parámetros de red para el concentrador de capa 2 local** y edite los recuadros de texto **Configuraciones ampliadas**.
5. (Opcional) **Configuraciones ampliadas**: establezca las contraseñas de **admin** y **root** para este concentrador de capa 2 específico.
6. Pulse **Siguiente**. En la página **Preparado para completar**, revise la información y pulse **Finalizar**.

## Supervisión del despliegue del dispositivo de servicio
{: #hcx-archi-install-cfg-hybrid-monitor}

Se puede utilizar la a consola de tareas para supervisar el progreso del despliegue de una máquina virtual de servicio.

### Procedimiento para supervisar el despliegue del dispositivo de servicio
{: #hcx-archi-install-cfg-hybrid-monitor-proc}

1. Inicie una sesión en el cliente web de vSphere. En el separador **Inicio**, pulse el icono **Hybrid Cloud Services**.
2. En el panel **Hybrid Cloud Services**, pulse el separador **Servicios híbridos**. El despliegue del dispositivo virtual se puede supervisar desde la consola de tareas.
3. Vaya al panel **Tareas recientes** y visualice las **Tareas de todos los usuarios**.
4. Pulse **Más tareas** para abrir la consola de tareas.
5. En la consola de tareas, examine las tareas de despliegue.
6. Cuando se hayan completado todas las tareas, vaya a la lista de inventario y pulse **Hybrid Cloud Services**.
7. En el panel central, pulse el separador **Servicios híbridos**.
8. Revise el resumen de configuración correspondiente a los dispositivos virtuales de servicio híbrido.

## Visualización del estado del túnel
{: #hcx-archi-install-cfg-hybrid-view-tunnel}

Consulte el estado del túnel de la pasarela de nube. El servicio de extensión de red debe estar activo para poder ampliar una red.

### Procedimiento para ver el estado del túnel
{: #hcx-archi-install-cfg-hybrid-proc-view-tunnel}

1. Para comprobar el estado del túnel desde el cliente web, seleccione **Hybrid Cloud Services** en el inventario y pulse el separador **Servicios híbridos**.
2. Para confirmar un túnel de Hybrid Cloud Gateway correcto, compruebe que el estado de CGW (acrónimo de Hybrid Cloud Gateway) sea **Activo** y que, en la parte derecha, el túnel esté codificado en verde.

## Extensión de una red de capa 2 a IBM Cloud

Amplíe una red de capa 2 desde el centro de datos local a la nube habilitada para VCF/VCS HCX.
{: #hcx-archi-install-cfg-hybrid-stretch-layer-2}

### Requisitos previos para extender una red de capa 2 a IBM Cloud
{: #hcx-archi-install-cfg-hybrid-prereq-stretch-layer-2}

* Solo se pueden extender los grupos de puertos etiquetados como VLAN (que no sean el tipo de VLAN Ninguno ni el ID de VLAN 0). Las VXLAN se consideran VLAN.
* En este procedimiento se utiliza el asistente para **Ampliar red**. Este asistente se debe ejecutar desde la vista de inventario de red del cliente web de vSphere®. Aunque el asistente se puede ver desde otras vistas, se debe ejecutar desde el contexto de inventario para obtener la información correcta.

### Procedimiento para extender una red de capa 2 a IBM Cloud
{: #hcx-archi-install-cfg-hybrid-proc-stretch-layer-2}

1. Inicie una sesión en el cliente web de vSphere. En el separador **Inicio** del panel central, pulse el icono **Redes** en la lista **Inventarios**.
2. En la jerarquía de **Redes**, identifique el grupo de puertos correspondiente a la red que se va a ampliar.
3. Pulse con el botón derecho del ratón en el grupo de puertos, y en el menú, seleccione **Acciones de Hybridity** y seleccione **Ampliar red**.
4. En la página **Seleccionar grupos de puertos de origen**, confirme la información de grupo de puertos y especifique la **Dirección IP de pasarela** y el prefijo de la red. Pulse **Siguiente**.
5. En la página **Seleccionar pasarela de destino**, siga estos pasos:
  1. Seleccione VCF/VCS Hybrid Cloud Services Cloud Organization en el menú **Organización**.
  2. Seleccione el centro de datos virtual de VCF/VCS Hybrid Cloud Services Cloud en el menú.
  3. Deje inhabilitado **Direccionamiento de proximidad** para imponer que una VM de la nube habilitada para VCF/VCS Hybrid Cloud Services siempre utilice la pasarela local para acceder a internet. De forma predeterminada, el tráfico que se origina en una máquina virtual en una nube habilitada para VCF/VCS Hybrid Cloud Services atraviesa la vía de acceso de datos de capa 2 para volver al centro de datos local y para dirigirse a la pasarela predeterminada. Si **Direccionamiento de proximidad** está seleccionado, una máquina virtual de una nube habilitada para VCF/VCS Hybrid Cloud Services puede acceder a internet sin atravesar la vía de acceso de datos de capa 2 a vSphere.
  4. Seleccione la pasarela de destino remota en la lista de pasarelas pulsando en la fila. Pulse **Siguiente**.
6. En la página **Preparado para completar**, revise los valores especificados. Pulse **Finalizar**.
7. Para realizar un seguimiento del progreso de la extensión de red, vaya a la ventana **Tareas recientes**, pulse el separador **Todas** y visualice **Todas las tareas de usuario**.
8. Para abrir la consola de tareas, pulse **Más tareas**. La extensión de red se realiza cuando el estado de la tarea **Ampliar red** es **Completado**.

## Enlaces relacionados
{: #hcx-archi-install-cfg-hybrid-related}

* [Modificación o desinstalación de HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
