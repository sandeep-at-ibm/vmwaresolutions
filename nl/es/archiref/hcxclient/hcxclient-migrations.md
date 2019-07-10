---

copyright:

  years:  2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Migraciones de VMware Hybrid Cloud
{: #hcxclient-migrations}

Una vez que se han suministrado y ampliado las extensiones de red y la malla de servicio HCX, el paso siguiente es la migración de las máquinas virtuales. 

Hay tres tipos de migración: 
  - vMotion
  - Migración masiva
  - Migración en frío

## Operación
{: #hcxclient-migrations-operation}

Utilice el portal de complementos de la interfaz de usuario web de HCX o los menús de extensión contextual del cliente web de vSphere para iniciar una vMotion de nube cruzada. En cualquier caso, aparece el mismo asistente de migración. Para los menús contextuales, solo se selecciona una sola máquina virtual para las operaciones de migración. Para el portal, se pueden seleccionar varias máquinas virtuales.

Revertir la migración de máquinas virtuales solo es posible desde el portal de la interfaz de usuario web que utiliza el recuadro de selección **Revertir migración** en el asistente de migración de HCX.

## vMotion
{: #hcxclient-migrations-vmotion}

La función vMotion dentro de HCX amplía la función de vSphere vMotion para que funcione en distintas versiones de vSphere, dominios de SSO independientes y varios tipos de conectividad de red a través de Internet. HCX presupone que la red que se utiliza para la conexión no es segura y siempre mueve el tráfico entre túneles cifrados, independientemente del tipo de conectividad. 

### Conceptos y mejores prácticas para vMotion
{: #hcxclient-migrations-best-practices-vmotion}

HCX es básicamente un proxy bidireccional de vMotion. Cada instancia de HCX emula un único host ESXi dentro del centro de datos de vSphere, fuera de cualquier clúster que sea en sí mismo un "frontal" para el componente de flota de pasarela de nube (CGW). Aparece un host de proxy para cada sitio de HCX enlazado con el sitio visualizado actualmente. Cuando se inicia un vMotion a un host remoto, el host ESXi local aplica vMotion para la máquina virtual al host ESXi de proxy local frontal al CGW, que también está manteniendo un túnel cifrado con el CGW en el lado remoto.

Al mismo tiempo, se inicia una migración de vMotion desde el host de proxy ESXi remoto al host ESXi físico de vSphere de destino, mientras recibe datos del CGW de origen a través del túnel. Cuando se utiliza vMotion, a diferencia de la opción de migración masiva, solo se ejecuta una operación de migración de máquina virtual a la vez. Debido a esto, para migrar grandes cantidades de máquinas virtuales, se recomienda que utilice vMotion solo cuando el tiempo de inactividad
no sea una opción o haya riesgo en el rearranque de la máquina virtual. Sin embargo, como vMotion estándar, la máquina virtual puede estar en directo durante el proceso.

Se ha observado que un solo vMotion se desplazará a alrededor de 1,7 Gbps en la LAN y entre 300 y 400 Mbps en la WAN a través del optimizador de WAN. Esto no implica que 1,7 Gbps en la LAN sean equivalentes a 400 Mbps en la WAN a través del optimizador de WAN, sino más bien que estos valores máximos se han observado en entornos específicos. Un entorno de este tipo constaba de una red vMotion LAN de 10 GB y un enlace ascendente de Internet de 1 GB, compartido con el tráfico web de producción. 

Utilice vMotion cuando:
- Puede causar problemas apagar o iniciar la máquina virtual o si el tiempo de funcionamiento puede extenderse demasiado, con riesgo de que se apague.
- Cualquier aplicación de tipo de clúster requiera UUID de disco, como los clústeres de Oracle RAC. Tenga en cuenta que vMotion no cambia los UUID de disco en el destino.
- Quiera mover una sola máquina virtual lo más rápido posible.
- No se necesite una migración planificado.

## Migración masiva
{: #hcxclient-migrations-bulk-mig}

### Conceptos y mejores prácticas para la migración masiva
{: #hcxclient-migrations-best-practices-bulk-mig}

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
- Permita la migración de máquinas virtuales que estén utilizando actualmente características de CPU, que difieren del lado de la nube. La migración de vMotion puede fallar en estos casos. 

A continuación se exponen los inconvenientes de la migración masiva sobre vMotion:
- Las máquinas virtuales a nivel individual se migran de forma mucho más lenta que con vMotion.
- La máquina virtual genera un breve tiempo de inactividad cuando la nueva máquina virtual de clon se lleva al lado de destino.
- Las máquinas virtuales que dependen del orden de los discos y de los UUID de disco (Oracle RAC) pueden generar problemas y tener discos que se muestren de forma diferente ya que se cambian los UUID, lo que puede cambiar las vías de acceso del sistema operativo a los dispositivos de disco virtual.

## Prácticas recomendadas del tipo de migración
{: #hcxclient-migrations-mig-type-best-practices}

### Clústeres de disco compartido
{: #hcxclient-migrations-shared-disk-clusters}

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
{: #hcxclient-migrations-general-vms}

Una vez que se ha generado confianza alrededor de la función de HCX, se debe utilizar la migración masiva. La migración masiva es necesaria para las aplicaciones redundantes. Por ejemplo, los servidores web y cuando se van a migrar varios cientos o miles de máquinas virtuales. 

### Máquinas virtuales que utilizan NAS de conexión directa
{: #hcxclient-migrations-vms-direct-nas}

NFS se utiliza normalmente para compartir datos en muchos servidores, como contenido del servidor web. Se puede utilizar iSCSI en varios nodos de máquina virtual que constituyen un clúster de aplicación, como el correo electrónico o RDBMS, y suelen ser más sensibles a la latencia que NFS. 

En cualquier caso, si la latencia se puede mantener baja para el {{site.data.keyword.CloudDataCent_notm}} (< ~7 ms para iSCSI y lo que tolere la aplicación para NFS) y permitir que la aplicación pueda funcionar con un ancho de banda de ~ 1 Gbps o menos, la red NAS se puede extender con HCX en una ubicación de {{site.data.keyword.cloud_notm}}. Después de realizar esta acción, las máquinas virtuales se pueden migrar o trasladar con vMotion con HCX. 

Después de la migración, los volúmenes de iSCSI se pueden duplicar con el sistema operativo en otra solución de almacenamiento en nube local y los datos de NFS se pueden replicar en cualquier solución de nube. Las consideraciones son las siguientes:
- Latencia (iSCSI o tolerancia de aplicaciones para NFS)
- Ancho de banda (~ 1 Gbps por red extendida)
- Ancho de banda de enlace subyacente

Después del ciclo de vida de la migración, pruebe las aplicaciones de desarrollo o transferencia antes de intentarlo en producción. Se puede utilizar la calidad de servicio para el tráfico de túnel subyacente (udp 500/4500) entre los dispositivos L2C HCX que admitan redes L2 extendidas sensibles a la latencia.

## Oscilación de red
{: #hcxclient-migrations-network-swing}

Si el objetivo es la evacuación del centro de datos a {{site.data.keyword.cloud_notm}}, el siguiente paso antes de eliminar HCX es la oscilación de red. La oscilación de red consigue la migración de la subred de red que aloja las máquinas virtuales migradas desde el centro de datos de origen a una red subyacente NSX dentro de {{site.data.keyword.cloud_notm}}.

La oscilación de red implica los pasos siguientes:
- Verificar que la red ha evacuado todas las cargas de trabajo y que los dispositivos en red que no sean de máquina virtual se hayan movido a otra red, que se hayan migrado funcionalmente a la nube o que hayan quedado en desuso.
- Verificar que cualquier topología de NSX o topología de red con soporte de {{site.data.keyword.cloud_notm}} se haya completado para dar soporte a la oscilación de red. Por ejemplo, los cortafuegos y los protocolos de direccionamiento dinámico.
- Ejecutar un flujo de trabajo de red para eliminar la extensión de HCX en la interfaz de usuario y seleccionar el dispositivo NSX de direccionamiento adecuado para tomar el control de la pasarela predeterminada de las redes no extendidas.
- Ejecutar cualquier cambio de direccionamiento externo, que puede incluir: insertar el direccionamiento cambiado para redes que se han migrado, eliminar rutas a sitios de origen de la red migrada y garantizar que el direccionamiento a dicha subred migrada en la WAN todavía funciona para las aplicaciones que no se hayan migrado.
- Pruebas del propietario de la aplicación de las aplicaciones migradas desde todos los puntos de acceso posibles: Internet, intranet y VPN.

Supongamos que desea realizar la oscilación de red para una aplicación concreta cuyas máquinas virtuales se han migrado a la nube. Por ejemplo:
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
{: #hcxclient-migrations-related}

* [Glosario de componentes y términos de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparación del entorno de instalación](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Despliegue del cliente de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Malla de servicio en instalaciones locales de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Supervisión de parámetros y componentes](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Resolución de problemas de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
