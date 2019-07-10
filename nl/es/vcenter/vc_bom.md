---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-11"

keywords: vCenter Server BOM, bill of materials vCenter Server, BOM

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Lista de materiales de vCenter Server
{: #vc_bom}

Revise la información de la Lista de materiales (BOM) de las instancias de VMware vCenter Server.

## Lista de materiales de VLAN para instancias de vCenter Server
{: #vc_bom-vlans}

En la tabla siguiente se muestra la información de la lista de materiales para las VLAN de vCenter Server.

Tabla 1. Lista de materiales para las VLAN de instancias de vCenter Server

| VLAN       | Tipo       | Detalles       |
|:---------- |:---------- |:------------- |
| VLAN1     | Pública, Primaria | Asignada a servidores ESXi físicos para acceso público de red. Los servidores se asignan a una dirección IP pública pero dicha dirección IP no está configurada en servidores, por lo que no son directamente accesibles en la red pública. En su lugar, la VLAN pública está pensada para proporcionar acceso a
Internet público para otros componentes, como NSX Edge Services Gateways (ESG). |
| VLAN2     | Privada A, Primaria | Asignado por {{site.data.keyword.cloud}} a servidores físicos de ESXi. La utiliza la interfaz de gestión para el tráfico de gestión de VMware vSphere.<br><br>Asignada a VM (máquinas virtuales) que funcionan como componentes de gestión.<br><br>Asignada a VMware NSX VTEP (punto final de túnel VXLAN) |
| VLAN3     | Privada B, Portátil | Asignada a VMware vSAN, si se utiliza.<br><br>Asignada a VMware NFS, si se utiliza.<br><br>Asignada a VMware vSphere vMotion.<br><br>Para NSX-T, asignada a VMware NSX VTEP (punto final de túnel de VXLAN).|

## Lista de materiales de software para instancias de vCenter Server
{: #vc_bom-software}

En la tabla siguiente se muestra la información de la lista de materiales para los componentes de software de vCenter Server.

Tabla 2. Lista de materiales para los componentes de software de instancias de vCenter Server

| Fabricante  | Componente                      | Versión    |
|:------------- |:------------------------------ |:------------- |
| VMware       | vSphere ESXi                    | 6.7 Update 1 (build 6.7.0-13004448) o <br/>6.5 Update 2 (build 6.5.0-13635690) |
| VMware       | vSphere 6.7                     | vSwitch distribuido 6.6.0 |
| VMware       | vSphere 6.5                     | vSwitch distribuido 6.5.0 |
| VMware       | vCenter Server Appliance        | 6.7 Update 1b (build 6.7.0-11727113) o <br/>6.5 Update 2g (build 6.5.0-13638625) |
| VMware       | Platform Services Controller    | 6.7 Update 1b (compilación 6.7.0-11727113) o <br/>6.5 Update 2d (compilación 6.5.0-10964411) |
| VMware       | vSAN                            | 6.7 Update 1 o <br/>6.6.1       |
| VMware       | NSX for vSphere                 | 6.4.4 (build 11197766)    |
| VMware       | NSX-T for vSphere               | 2.4                       |
| Microsoft    | Windows Server Standard Edition | 2016       |

VMware vSAN es un componente opcional.
{:note}

## Valores de configuración avanzada para servidores ESXi
{: #vc_bom-esxi-server-advance-config}

Revise la tabla siguiente para obtener una visión general de los valores de configuración avanzada que se aplican a los servidores ESXi. Estos valores dependen de si la instancia de vCenter Server se ha desplegado en V2.2 o posterior, o se ha actualizado a V2.2 o posterior desde V2.1 o anterior.

Los valores se aplican a instancias nuevas y a clústeres nuevos de instancias nuevas V2.2 o posteriores. Los valores no se aplican a clústeres nuevos de instancias existentes de V2.1 o anteriores ni a instancia existentes actualizadas a V2.2 o posterior.

Tabla 3. Valores de configuración avanzada de servidores ESXi para clústeres e instancias de vCenter Server

| Valor de configuración | Si se ha desplegado en 2.2 o post.  | Si se ha actualizado desde V2.1 o ant. |
|:------------- |:------------- |:------------- |
| Máximo de volúmenes | **MaxVolumes** = 256 | Tanto **/NFS/MaxVolumes** como **/NFS41/MaxVolumes** = 256 |
| Máximo errores latido | **HeartbeatMaxFailures** = 10 | No definido |
| Frecuencia latido | **HeartbeatFrequency** = 12 | No definido |
| Tiempo espera latido | **HeartbeatTimeout** = 5 | No definido |
| Profundidad máx. cola | **MaxQueueDepth** = 64 | No definido |
| Tamaño muestra cola completa | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Umbral cola completa | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |
| Tamaño pila TCP/IP | **TcpipHeapSize** = 32 | No definido |
| Máx. pila TCP/IP | **TcpipHeapMax** = 1536 | No definido |

**Notas:**
* El valor **MaxVolumes** es obligatorio para el servicio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} porque el servicio puede utilizar más del número predeterminado de montajes de NFS en el servidor ESXi.
* Un valor de **No definido** para un valor de configuración indica que el nuevo valor no se aplica automáticamente porque requiere que se rearranquen los servidores ESXi, lo que puede suponer una interrupción.

  Se recomienda cambiar los valores de configuración **No definido** por los nuevos valores para mantener la coherencia entre todas las instancias y permitir un soporte adecuado para la ampliación de almacenamiento. IBM tiene intención de realizar pruebas solo con estos nuevos valores para {{site.data.keyword.vmwaresolutions_short}} V2.2 y releases posteriores.

  Para obtener más información, consulte [Cómo aumentar el valor predeterminado que define el número máximo de montajes NFS en un host ESXi](https://kb.vmware.com/s/article/2239).

## Valores de configuración de grupos de puertos y NSX
{: #vc_bom-nsx-port-group-config}

Revise la tabla siguiente para obtener una visión general de los valores de configuración de grupos de puertos y NSX de VMware para instancias de vCenter Server y las diferencias entre releases.

Los valores se aplican a instancias nuevas y a clústeres nuevos de instancias nuevas V2.2 o posteriores. Los valores no se aplican a clústeres nuevos de instancias existentes de V2.1 o anteriores ni a instancia existentes actualizadas a V2.2 o posterior.

Tabla 4. Valores de configuración de grupos de puertos y NSX para instancias de vCenter Server

| Valor de configuración | V2.1 o anterior  | V2.2 o posterior |   
|:------------- |:------------- |:------------- |
| Política de agrupación de clústeres NSX VXLAN | Migración tras error | Equilibrio carga - SRCID |
| VTEP de clúster NSX VXLAN | 1 | 2 |
| Agrupación ID segmento para instancia primaria | 6000-8000 | 6000-7999 |  
| Agrupación ID segmento para siguientes instancias secundarias | 6000-8000 | Rango final anterior en la configuración de varios sitios + 1 en el rango final anterior en la configuración de varios sitios + 2000 |  
| Grupo puestos SDDC-DPortGroup-VSAN (si procede) | **Enlaces ascendentes activos** establecido en **uplink1** y **Enlaces ascendentes en espera** establecido en **uplink2** | **Enlaces ascendentes activos** establecido en **uplink2** y **Enlaces ascendentes en espera** establecido en **uplink1** |  
| Grupo puertos SDDC-DPortGroup-Gestión | **Enlace de puertos** establecido en **Efímero - sin enlace** y **Equilibrio de carga** establecido en **Ruta basada en el puerto virtual de origen** | **Enlace de puertos** establecido en **Enlace estático** y **Equilibro de carga** establecido en **Redirigir basado en carga de NIC física** |  
| Grupo puertos SDDC-DPortGroup-Externo | **Enlace de puertos** establecido en **Efímero - sin enlace** | **Enlace de puertos** establecido en **Enlace estático** |

## Valores de configuración de MTU de red
{: #vc_bom-network-mtu-config}

El clúster de vSphere utiliza dos conmutadores distribuidos de vSphere (vDS), uno para la conectividad de red pública y el otro para la conectividad de red privada.

Las conexiones de red privada están configuradas para utilizar MTU (unidad de transmisión máxima) de tramas Jumbo con un tamaño de 9000, lo que mejora el rendimiento de las grandes transferencias de datos como almacenamiento y VMware vMotion. Este valor es la MTU máxima permitida en VMware y por {{site.data.keyword.cloud_notm}}.

En V2.1 o posterior, las conexiones de red pública utilizan una MTU estándar de Ethernet de 1500. Este valor de 1500 debe mantenerse; cualquier cambio puede provocar la fragmentación de paquetes a través de Internet.

Revise la tabla siguiente para obtener una visión general de los valores de configuración de MTU de red que se aplican a los conmutadores virtuales distribuidos (DVS) público y privado en función de si la instancia de vCenter Server se ha desplegado en V2.1 o posterior.

Tabla 5. Valores de configuración de MTU para clústeres e instancias de vCenter Server según la versión de la instancia

| vDS | V2.1 o posterior  | V2.0 o anterior (o actualizado desde V2.0 o anterior) |
|:-------------- |:-------------- |:------------- |
| Conmutador público  | 1500 (predeterminado) | 9000 (tramas Jumbo) |
| Conmutador privado | 9000 (tramas Jumbo) | 9000 (tramas Jumbo) |

Los valores se aplican a instancias nuevas y a clústeres nuevos de instancias desplegadas en V2.1 o posterior. Los valores también se aplican a los clústeres nuevos entre {{site.data.keyword.CloudDataCents_notm}} de instancias que se han actualizado a V2.1 o posterior.

Los valores no se aplican a clústeres nuevos en el mismo {{site.data.keyword.CloudDataCent_notm}}, para las instancias existentes de V2.0 o de instancias anteriores o existentes que se han actualizado a V2.1 o posterior.

Para instancias desplegadas en V2.0 o anterior, se recomienda que actualice usted mismo el valor de MTU del conmutador público a 1500.

### Actualización del valor de MTU del conmutador público
{: #vc_bom-procedure-update-public-switch-mtu-setting}

Para actualizar el valor de MTU del conmutador público, siga estos pasos en el cliente web de VMware vSphere:
1. Pulse con el botón derecho del ratón en el vDS y pulse **Editar valores**.
2. En el separador **Propiedades**, seleccione la opción **Avanzado**.
3. Asegúrese de que el valor de **MTU máxima** está establecido en 1500.

   Cuando se cambia el tamaño de MTU en un vDS, los enlaces ascendentes adjuntos (NIC físicos) se detienen y se vuelven a iniciar. Como resultado se produce una breve parada para las máquinas virtuales que están utilizando el enlace ascendente. Por lo tanto se recomienda planear la actualización del valor de la MTU durante una parada planificada.
   {:note}

## Enlaces relacionados
{: #vc_bom-related}

* [Números de compilación y versiones de VMware ESXi y ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Números de compilación y versiones de VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [Habilitación de tramas de gran tamaño en conmutadores distribuidos virtuales](https://kb.vmware.com/s/article/1038827)
* [Hoja de protección de datos de {{site.data.keyword.vmwaresolutions_short}}](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040){:new_window}
* [Visión general de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Planificación de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
