---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

# Resolución de problemas de HCX
{: #vcshcx-troubleshooting}

Revise la siguiente información sobre los problemas y arreglos de HCX más frecuentes.

## Problemas de la interfaz de usuario del cliente de HCX
{: #vcshcx-troubleshooting-hcx-client-issues}

### Tiempo de espera de la señal de interfaz de usuario de HCX agotado
{: #vcshcx-troubleshooting-hcx-ui-issues}

Normalmente, si la interfaz de usuario de vCenter (IU) se ha dejado abierta durante algún tiempo, es posible que encuentre que se ha excedido el tiempo de espera en la interfaz de usuario de HCX. Esto se debe a que la señal de inicio de sesión en el servidor de HCX Manager ha excedido el tiempo de espera. Cierre sesión de la interfaz de usuario web de vSphere y vuelva a iniciar sesión para renovar la señal.

### La interfaz de usuario de cliente de HCX muestra "NaN" para todas las métricas en la pantalla del panel de control
{: #vcshcx-troubleshooting-nan-display}

Este problema está relacionado con los permisos de la cuenta de vCenter en la que se ha iniciado sesión. Asegúrese de que el grupo del administrador de empresa esté establecido en la interfaz de usuario del gestor de dispositivos del lado de la nube de HCX.

## Problemas de migración
{: #vcshcx-troubleshooting-mig-issues}

Los problemas de migración en las versiones actuales de HCX suelen estar en tres categorías: licencias, conectividad de red de pasarela de nube y compatibilidad de hardware de destino.

### Licencias
{: #vcshcx-troubleshooting-licensing}

Si una migración falla debido a un problema de licencias, las versiones actuales de HCX lo muestran claramente en el mensaje de error con la interfaz de usuario web del cliente dentro de la interfaz de usuario de vCenter.

### Conectividad de red (WAN)
{: #vcshcx-troubleshooting-wan-connect}

Si hay un problema con la conectividad de WAN, compruebe siempre la pantalla **Interconexión -> Componentes de HCX** dentro de la interfaz de usuario de HCX para el estado del túnel. Normalmente, no es necesario restablecer ni rearrancar los componentes de flota. Si se restaura la conectividad de WAN, se reconectan automáticamente.

Si hay arreglos y actualizaciones que se han aplicado a los gestores de HCX (cliente y nube) y estas actualizaciones también corrigen problemas con los componentes de flota, deberá volver a desplegar Cloud Gateway y cualquier L2C desplegada. Es posible realizar una depuración adicional del estado del túnel, conectándose a HCX Manager a través de un cliente SSH como ccli  

1. Ejecute SSH en HCX Manager utilizando la cuenta de administrador y la contraseña proporcionada.
2. Ejecute el mandato `su –` y especifique la contraseña del usuario `root` (la misma que la contraseña de admin) para cambiar a root.
3. Cambie el directorio a `/opt/vmware/bin` y ejecute el mandato `./ccli`. Si esto no funciona porque el entorno no está configurado para raíz, ejecute el mandato `./ccliSetup.pl`.
4. Ejecute el mandato `list` dentro del shell de `ccli` para mostrar una lista de los componentes de flota registrados con HCX Manager.
5. Especifique el ID de flota para la `ccli` escribiendo el ID listado para el componente de flota. Por ejemplo, `go 8`.
6. Ejecute el mandato `debug remoteaccess enable` para establecer la conexión mediante SSH con el componente de flota deseado.
7. Salga de la `ccli` y establezca la conexión mediante SSH con la dirección IP del componente de flota habilitado para SSH.
9. Continúe para resolver el problema.
10. Vuelva a la `ccli` e inhabilite el servicio `ssh` para el componente.
11. Si es necesario, utilice el mandato de ccli `hc` para ejecutar una comprobación de estado en los componentes.

## Problemas de compatibilidad del hardware de destino
{: #vcshcx-troubleshooting-hw-compatibility}

La migración de vMotion puede ser un problema cuando el lado de origen del cliente es de una versión de hardware y un release de vSphere más recientes que la nube. Como la migración basada en réplica copia datos a una máquina virtual creada recientemente en el lado de destino, cambiar el tipo de migración a "Migración masiva" debería facilitar el éxito de la migración en la mayoría de los casos.

## Problemas del concentrador L2 extendido
{: #vcshcx-troubleshooting-stretched-l2}

Se han experimentado muy pocos problemas con el funcionamiento del concentrador L2 (L2C). De forma similar a CGW, si L2C pierde la conectividad, se vuelve a conectar automáticamente después de restaurar la conectividad de red. Utilice el shell de ccli para comprobar el estado y el funcionamiento. Después de habilitar SSH y conectar L2C, ejecute los mandatos `ip tunnel` e `ip link |grep t_` para visualizar el estado de los túneles.

## Enlaces relacionados
{: #vcshcx-troubleshooting-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
