---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

subcollection: vmware-solutions


---

# Extensión de red y migración de máquina virtual
{: #vcshcx-stretching}

## Extensión de red
{: #vcshcx-network-stretching}

### Conceptos y mejores prácticas para la extensión de red
{: #vcshcx-stretching-best-practices-network}

El pegamento que une la red del lado del cliente con la VXLAN del lado de la nube es una red privada virtual (VPN) sofisticada de varios túneles basada en tecnología HCX patentada. No se basa en NSX, pero sí funciona con NSX y amplía su capacidad. Este proceso está controlado por la interfaz de usuario web de vCenter del lado del cliente y automatiza el despliegue y activa ambos puntos finales en el lado del cliente y de la nube. La selección de la red que se va a extender se realiza de forma individual o por lotes.

Además, como parte del flujo de trabajo de extensión de red, NSX en el lado de la nube tiene autorización para crear una VXLAN que luego se conecta a una interfaz creada en el dispositivo L3 del lado de la nube especificado (DLR o ESG dejado en un estado no conectado) y el dispositivo L2C del lado de la nube.

Normalmente, al migrar una aplicación concreta, todas las redes que utilizan las máquinas virtuales (VM) aplicables deben extenderse en la instancia de {{site.data.keyword.cloud}}.

¿Por qué normalmente y no siempre? Puede ser beneficioso desconectar determinado tráfico desde el lado del cliente después de migrar la máquina virtual. Por ejemplo, los clientes de copia de seguridad de invitado de máquina virtual, que pueden provocar un alto uso de ancho de banda cuando se mueven a la nube. El cliente de copia de seguridad en el invitado no es necesario cuando se migra la máquina virtual, ya que se recoge automáticamente mediante una copia de seguridad de nivel de bloque más moderna en el lado de la nube.

El adaptador de red de copia de seguridad del cliente, debido a que esto implicaría acceder a cada máquina virtual para concluir la planificación de copia de seguridad del cliente en el invitado. Por lo tanto, si se utiliza una red de copia de seguridad, es posible que falle la copia de seguridad. Se trata de una situación temporal hasta que se puedan alcanzar todas las máquinas virtuales después de la migración para inhabilitar el cliente de copia de seguridad en el invitado.

El ancho de banda de una sola L2C es teóricamente de 4 Gbps, sin embargo, este puede ser el límite para todas las redes extendidas dentro de un solo par de L2C y no es alcanzable por una sola red extendida. Una sola red extendida puede alcanzar un máximo de ~1 Gbps, dado que hay suficiente ancho de banda subyacente asignado y la latencia es baja (< ~ 10 ms).

### Proceso para extender una red
{: #vcshcx-stretching-process-stretch}

Para extender una red (VLAN o VXLAN) con HCX, complete los siguientes pasos desde la interfaz de usuario web de vCenter del lado del cliente.

1. Para la selección individual de grupos de puertos, vaya al separador **Redes** en la interfaz de usuario web de vCenter, pulse con el botón derecho del ratón en la red que se va a extender y seleccione **Acciones de Hybridity -> Extender redes a la nube**.
2. Seleccione el dispositivo L3 del lado de la nube con el que conectar y el dispositivo L2C que se utilizará. Escriba la pasarela y la máscara de subred predeterminadas en formato CIDR.
3. Pulse **Extender** en la parte inferior de la pantalla para comenzar el flujo de trabajo de extensión de red.

El progreso de red se supervisa en el panel de tareas del cliente de vCenter.

### Opción de direccionamiento de proximidad
{: #vcshcx-stretching-prox-routing}

Sin ningún tipo de optimización de direccionamiento, las redes extendidas se direccionan de nuevo al lado del cliente para cualquier acceso de L3. Este proceso de bumerán introduce un patrón de tráfico ineficiente, ya que los paquetes tienen que desplazarse continuamente entre el cliente (origen) y la nube, incluso cuando las máquinas virtuales de origen y de destino están dentro de la nube. La característica de direccionamiento de proximidad de HCX se ha diseñado para solucionar este problema y la salida del tráfico local.

## vMotion
{: #vcshcx-stretching-vmotion}

La función vMotion dentro de HCX amplía la función de vSphere vMotion para que funcione en distintas versiones de vSphere, dominios de SSO independientes y varios tipos de conectividad de red a través de Internet. HCX presupone que la red que utiliza para la conexión no es segura y siempre mueve el tráfico entre túneles cifrados, independientemente del tipo de conectividad.

### Conceptos y mejores prácticas para vMotion
{: #vcshcx-stretching-best-practices-vmotion}

HCX es básicamente un proxy bidireccional de vMotion. Cada instancia de HCX emula un único host ESXi dentro del centro de datos de vSphere, fuera de cualquier clúster que sea en sí mismo un "frontal" para el componente de flota de pasarela de nube (CGW). Aparece un host de proxy para cada sitio de HCX enlazado con el sitio visualizado actualmente. Cuando se inicia un vMotion a un host remoto, el host ESXi local aplica vMotion para la máquina virtual al host ESXi de proxy local frontal al CGW, que también está manteniendo un túnel cifrado con el CGW en el lado remoto.

Al mismo tiempo, se inicia una migración de vMotion desde el host de proxy ESXi remoto al host ESXi físico de vSphere de destino, mientras recibe datos del CGW de origen a través del túnel. Cuando se utiliza vMotion, a diferencia de la opción de migración masiva, solo se ejecuta una operación de migración de máquina virtual a la vez. Debido a esto, para migrar grandes cantidades de máquinas virtuales, se recomienda que solo se utilice cuando el tiempo de inactividad no sea una opción o hay riesgo de rearranque de la máquina virtual. Sin embargo, como vMotion estándar, la máquina virtual puede estar en directo durante el proceso.

Se ha observado que un solo vMotion se desplazará a alrededor de 1,7 Gbps en la LAN y entre 300 y 400 Mbps en la WAN a través del optimizador de WAN. Esto no implica que 1,7 Gbps en la LAN sean equivalentes a 400 Mbps en la WAN a través del optimizador de WAN, sino más bien que estos valores máximos se han observado en entornos específicos. Un entorno de este tipo constaba de una red vMotion LAN de 10 GB y un enlace ascendente de Internet de 1 GB, compartido con el tráfico web de producción.

Utilice vMotion cuando:
- Puede causar problemas apagar o iniciar la máquina virtual o si el tiempo de funcionamiento puede extenderse demasiado, con riesgo de que se apague.
- Cualquier aplicación de tipo de clúster requiera UUID de disco, como los clústeres de Oracle RAC. Tenga en cuenta que vMotion no cambia los UUID de disco en el destino.
- Quiera mover una sola máquina virtual lo más rápido posible.
- No se necesite una migración planificado.

### Operación
{: #vcshcx-stretching-operation}

Utilice el portal de complementos de la interfaz de usuario web de HCX o los menús de extensión contextual del cliente web de vSphere para iniciar una vMotion de nube cruzada. En cualquier caso, aparece el mismo asistente de migración. Para los menús contextuales, solo se selecciona una sola máquina virtual para las operaciones de migración. Para el portal, se pueden seleccionar varias máquinas virtuales.

Revertir la migración de máquinas virtuales solo es posible desde el portal de la interfaz de usuario web que utiliza el recuadro de selección **Revertir migración** en el asistente de migración de HCX.

## Migración masiva
{: #vcshcx-stretching-bulk-mig}

### Conceptos y mejores prácticas para la migración masiva
{: #vcshcx-stretching-best-practices-bulk-mig}

La función de migración masiva de HCX utiliza la réplica de vSphere para migrar los datos de disco mientras vuelve a crear la máquina virtual en la instancia de HCX de vSphere de destino. La migración de una máquina virtual conlleva el siguiente flujo de trabajo:
- Creación de una nueva máquina virtual en el lado de destino y sus correspondientes discos virtuales.
- Réplica de los datos de la máquina virtual en la nueva máquina virtual. La réplica se inicia cuando se complete el asistente, independientemente de la planificación de la conmutación.
- Apagar la máquina virtual original.
- Durante el periodo de apagado, se produce la réplica final de cualquier cambio de datos.
- Encender la nueva máquina virtual en el lado de destino.
- Renombrar y mover la máquina virtual original a la carpeta en la nube a la que se haya movido.

A continuación se exponen las ventajas de la migración masiva sobre vMotion:
- Migración de varias máquinas virtuales simultáneamente.
- Uso de ancho de banda más coherente. vMotion puede generar fluctuaciones en el uso del ancho de banda que serían visibles como picos y valles dentro de las herramientas de supervisión de red o la interfaz de usuario del optimizador de WAN.
- Utilice la migración masiva para obtener un uso superior de una capacidad de ancho de banda de red, en comparación con el de un solo vMotion.
- Planifique la migración masiva para cambiar a las máquinas virtuales recién migradas durante una ventana de parada planificada.
- Permita la migración de máquinas virtuales que estén utilizando actualmente características de CPU que difieren del lado de la nube. La migración de vMotion puede fallar en estos casos.

A continuación se exponen los inconvenientes de la migración masiva sobre vMotion:
- Las máquinas virtuales a nivel individual se migran de forma mucho más lenta que con vMotion.
- La máquina virtual genera un breve tiempo de inactividad cuando la nueva máquina virtual de clon se lleva al lado de destino.
- Las máquinas virtuales que dependen del orden de los discos y de los UUID de disco (Oracle RAC) pueden generar problemas y tener discos que se muestren de forma diferente ya que se cambian los UUID, lo que puede cambiar las vías de acceso del sistema operativo a los dispositivos de disco virtual.

## Prácticas recomendadas del tipo de migración
{: #vcshcx-stretching-mig-type-best-practices}

### Clústeres de disco compartido
{: #vcshcx-stretching-shared-disk-clusters}

Los clústeres de Oracle RAC, MS Exchange y MS-SQL son ejemplos de aplicaciones en las cuales participan dos o más máquinas virtuales en un clúster que requiere un disco compartido en todas las máquinas virtuales o nodos de clúster. El distintivo de varios escritores de VMware debe habilitarse en todos los nodos de máquina virtual para los discos que forman parte del clúster de aplicaciones (discos virtuales no del sistema operativo). No se admiten las máquinas virtuales con el distintivo de varios escritores habilitado para cualquier disco virtual.

Migración de un clúster habilitado para discos virtuales de varios escritores:
- Utiliza vMotion ya que se mantienen las correlaciones de UUID y disco de máquina virtual originales.
- El clúster permanece activo en un estado degradado (nodo único) durante la migración.
- El clúster genera tiempo de inactividad antes de iniciar la migración y una vez completada la migración para volver a ensamblar la configuración de varios escritores entre las máquinas virtuales del clúster.

Complete los pasos siguientes para migrar un clúster habilitado para discos de varios escritores:
1. Apague el clúster y todos los nodos para la práctica recomendada de la aplicación.
2. Tome nota del orden de discos, si la aplicación lo requiere, en cada máquina virtual de nodo para los discos virtuales configurados de varios escritores.
3. Para Oracle y cualquier otra aplicación que utilice la característica de UUID de disco virtual, inicie sesión en un host ESXi determinado y ejecute el mandato `vmkfstools -J getuuid /vmfs/volumes/datastore/VM/vm.vmdk` para obtener el UUID de cada archivo de disco virtual que requiera establecer el distintivo de varios escritores para el clúster.
  Esta acción es necesaria si la práctica recomendada alinea los órdenes de disco con el modo en que se visualiza la vía de acceso en el sistema operativo. vMotion puede reordenar los discos (disk1, disk2, disk3), pero los UUID siguen siendo los mismos.
  Cuando finalice la migración, utilice el UUID anotado para correlacionar la información de disco, para volver a crear el orden de denominación de discos, y el ID SCSI, si fuera necesario. La aplicación debería funcionar de cualquier forma. Se utiliza cuando una instancia de Oracle tiene muchos discos virtuales que se correlacionan para la resolución de problemas de la aplicación.
4. Elimine los discos virtuales de todas las máquinas virtuales del clúster, excepto el que se considera primario.
5. Elimine el distintivo de varios escritores de la máquina virtual de clúster primaria que debe ser la única propietaria de los discos de clúster.
6. Encienda el clúster primario, si es necesario para que el tiempo de inactividad sea mínimo.
7. Migre todos los nodos de clúster con vMotion. Migre el clúster primario en primer lugar. Migre los demás nodos después de que se hayan apagado.
8. Cuando el nodo propietario del disco primario complete la migración, apáguelo.
9. Si es necesario, vuelva a correlacionar el orden de disco con el UUID de disco y el ID de SCSI adecuados. No es necesario realizar ningún reajuste para que la aplicación funcione.
10. Vuelva a habilitar el distintivo de varios escritores en el nodo primario.
11. Inicie el nodo primario y verifique su funcionamiento.
12. Correlacione el disco / habilite el distintivo de varios escritores en el resto de las máquinas virtuales del clúster y enciéndalas.
13. Verifique otras funciones del clúster.

### Máquinas virtuales generales
{: #vcshcx-stretching-general-vms}

Una vez que se ha generado confianza alrededor de la función de HCX, se debe utilizar la migración masiva. La migración masiva es necesaria cuando hay aplicaciones redundantes. Por ejemplo, los servidores web y cuando se van a migrar muchas máquinas virtuales de 100s o 1000s.

### Máquinas virtuales que utilizan NAS de conexión directa
{: #vcshcx-stretching-vms-direct-nas}

NFS se utiliza normalmente para compartir datos en muchos servidores, como contenido del servidor web. Se puede utilizar iSCSI en varios nodos de máquina virtual que constituyen un clúster de aplicación, como el correo electrónico o RDBMS, y suelen ser más sensibles a la latencia que NFS.

En cualquier caso, si la latencia se puede mantener baja para el {{site.data.keyword.CloudDataCent_notm}} (< ~7 ms para iSCSI y lo que tolere la aplicación para NFS) y permitir que la aplicación pueda funcionar con un ancho de banda de ~ 1 Gbps o menos, la red NAS se puede extender con HCX en una ubicación de {{site.data.keyword.cloud_notm}}. Después de realizar esta acción, las máquinas virtuales se pueden migrar/aplicar vMotion con HCX como normal.

Después de la migración, los volúmenes de iSCSI se pueden duplicar con el sistema operativo en otra solución de almacenamiento en nube local y los datos de NFS se pueden replicar en cualquier solución de nube. Las consideraciones son las siguientes:
- Latencia (iSCSI o tolerancia de aplicaciones para NFS)
- Ancho de banda (~ 1 Gbps por red extendida)
- Ancho de banda de enlace subyacente

Después del ciclo de vida de la migración, pruebe las aplicaciones de desarrollo o transferencia antes de intentarlo en producción. Se puede utilizar la calidad de servicio para el tráfico de túnel subyacente (udp 500/4500) entre los dispositivos L2C HCX que admitan redes L2 extendidas sensibles a la latencia.

## Oscilación de red
{: #vcshcx-stretching-network-swing}

Si el objetivo es la evacuación del centro de datos a {{site.data.keyword.cloud_notm}}, el siguiente paso antes de eliminar HCX es la oscilación de red. La oscilación de red consigue la migración de la subred de red que aloja las máquinas virtuales migradas desde el centro de datos de origen a una red subyacente NSX dentro de {{site.data.keyword.cloud_notm}}.

La oscilación de red implica los pasos siguientes:
- Verificar que la red ha evacuado todas las cargas de trabajo y que los dispositivos en red que no sean de máquina virtual se hayan movido a otra red, que se hayan migrado funcionalmente a la nube o que hayan quedado en desuso.
- Verificar que cualquier topología de NSX o topología de red con soporte de {{site.data.keyword.cloud_notm}} se haya completado para dar soporte a la oscilación de red. Por ejemplo, los cortafuegos y los protocolos de direccionamiento dinámico.
- Ejecutar un flujo de trabajo de red para eliminar la extensión de HCX en la interfaz de usuario y seleccionar el dispositivo NSX de direccionamiento adecuado para tomar el control de la pasarela predeterminada de las redes no extendidas.
- Ejecutar cualquier cambio de direccionamiento externo, que puede incluir: insertar el direccionamiento cambiado para redes que se han migrado, eliminar rutas a sitios de origen de la red migrada y garantizar que el direccionamiento a dicha subred migrada en la WAN todavía funciona para las aplicaciones que no se hayan migrado.
- Pruebas del propietario de la aplicación de las aplicaciones migradas desde todos los puntos de acceso posibles: Internet, intranet y VPN.

Supongamos que desea realizar la oscilación de red para una aplicación concreta cuyas máquinas virtuales se han migrado completamente a la nube. Por ejemplo:
- Utiliza Vyatta en el lado de la red privada para insertar rutas en la nube MPLS y para establecer un túnel a los dispositivos de direccionamiento de extremo en MPLS para evitar el espacio de IP de {{site.data.keyword.cloud_notm}}.
- Tiene la cuenta establecida con un VRF de {{site.data.keyword.cloud_notm}}.
- Algunas aplicaciones están detrás de una IP virtual (vIP) de carga equilibrada de red. Estas vIP se encuentran en su subred que reside en un F5 virtual detrás de vyatta.

Aunque la adición de un direccionamiento más específico al MPLS para las redes que se han intercambiado a {{site.data.keyword.cloud_notm}} a través de HCX funciona correctamente para otras redes, no funciona para las vIP individuales, ya que se añade una ruta /32.

Solución: es frecuente que los proveedores de WAN filtren las rutas /32 que se añaden. Trátelo con el proveedor de WAN para permitirlo.

A continuación se indican algunas consideraciones e implicaciones:
- Las aplicaciones que comparten subred, vLAN y VXLAN tienen que moverse juntas.
- Las aplicaciones detrás de un equilibrador de carga que utiliza una IP direccionable interna pueden requerir cambios de direccionamiento si no se pueden mover juntas o no es deseable hacerlo. Por ejemplo, si se percibe demasiado implicando demasiadas aplicaciones en una sola oscilación.
- Los administradores de VMware, los administradores de red (incluidos los clientes y proveedores de WAN) y los propietarios de las aplicaciones deben estar implicados, incluso aunque no se haya planificado que haya un impacto en un sistema o equipamiento de red concreto.

## Enlaces relacionados
{: #vcshcx-stretching-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
