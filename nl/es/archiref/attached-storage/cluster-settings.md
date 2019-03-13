---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-13"

---

# Valores de clúster
{: #cluster-settings}

Antes de la adición del almacenamiento adjunto, la solución vCenter Server no habilitó características avanzadas, como por ejemplo el planificador de recursos distribuidos (DRS) y alta disponibilidad (HA) de vSphere. Con la adición del dispositivo de almacenamiento adjunto NFS, estas características se habilitan en el clúster con los valores que se muestran en las secciones siguientes.

## Planificador de recursos distribuidos de vSphere
{: #cluster-settings-vsphere-drs}

Cuando activa DRS de vSphere en un clúster se habilitan características principales: el equilibrio de carga y la gestión de alimentación.

### Equilibrio de carga
{: #cluster-settings-load-balance}

Con el equilibrio de carga, la distribución y el uso de los recursos de CPU y memoria para todos los hosts y máquinas virtuales (VM) del clúster se supervisan continuamente. DRS compara estas métricas con una utilización de recursos ideal dados los atributos de las agrupaciones de recursos y máquinas virtuales del clúster y la demanda actual. A continuación, realiza o recomienda las migraciones de VM necesarias.

Cuando una VM se enciende por primera vez en el clúster, DRS intenta mantener el equilibrio de carga adecuado colocando la máquina virtual en un host apropiado o realizando una recomendación. Los valores de ubicación o de recomendación se establecen en la sección de automatización de DRS de los valores del clúster.

En este diseño, el nivel de automatización de DRS se establece en totalmente automatizado, por lo que, cuando se encienden las máquinas virtuales, se colocan automáticamente en hosts con suficiente capacidad. Las máquinas virtuales también se migran automáticamente de un host a otro para equilibrar la carga del clúster. Además, el umbral de migración del clúster DRS se establece en un punto medio entre un enfoque conservador y uno agresivo, de modo que se aplican recomendaciones de prioridad 1, prioridad 2 y prioridad 3. vCenter Server proporciona al menos buenas mejoras en el equilibrio de la carga del clúster.

En la tabla siguiente se muestran los valores para el clúster DRS de vSphere en el cliente web de VMware vSphere.

Tabla 1. Valores de automatización de DRS para el clúster DRS de vSphere

| Parámetro             | Valor  |
|:------------------- |:------ |
| Activar DRS de vSphere | Seleccionado |
| Nivel de automatización | Totalmente automatizado |
| Umbral de migración | Aplicar recomendaciones de prioridad 1, prioridad 2 y prioridad 3 |
| Habilitar niveles de automatización de máquina individuales | Seleccionado, establecido en 15 ms |

Para obtener más información sobre la configuración de estos valores en el cliente web de vSphere, consulte [Establecimiento de un nivel de automatización personalizado para una máquina virtual en el cliente web de vSphere](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-C21C0609-923B-46FB-920C-887F00DBCAB9.html).

Junto con el nivel de automatización y el umbral de migración del clúster, este diseño habilita la automatización de las máquinas virtuales para que pueda modificar valores en las VM individuales. Un control más granular de las VM le permite priorizar el equilibrio de la carga de las VM.

### Gestión de alimentación
{: #cluster-settings-power-mgmt}

Cuando la función de gestión de alimentación distribuida de VMware está habilitada, DRS compara la capacidad a nivel de clúster y de host con las demandas de las máquinas virtuales del clúster, incluida la demanda histórica reciente. La característica de gestión de alimentación coloca o recomiendan colocar hosts en modalidad de alimentación en espera si encuentra exceso de capacidad o encender hosts si falta capacidad. En función de las recomendaciones de estado de alimentación de host resultantes, es posible que también haya que migrar máquinas virtuales a hosts o desde hosts.
En este diseño, la gestión de alimentación está inhabilitada ya que apagar o encender hosts en el clúster no reporta ningún beneficio operativo o financiero.

## Alta disponibilidad de vSphere
{: #cluster-settings-vsphere-ha}

vSphere proporciona alta disponibilidad para las máquinas virtuales mediante la agrupación de las mismas y de los host en los que residen en un clúster. Los hosts de un clúster se supervisa y, si se produce un error, las máquinas virtuales de un host anómalo se reinician en hosts alternativos.
En este diseño, la alta disponibilidad de vSphere está habilitada con supervisión de host y supervisión de VM en el clúster.

### Supervisión de host
{: #cluster-settings-host-monitor}

La supervisión de host permite que los hosts del clúster intercambien pulsaciones de red y habilita HA de vSphere cuando detecta anomalías. Esta característica está habilitada en este diseño.

### Supervisión de máquina virtual
{: #cluster-settings-machine-monitor}

La función de supervisión de VM utiliza la información de pulsaciones que capturan las herramientas de VMware como un proxy para la disponibilidad del sistema operativo invitado. La supervisión de VM permite que HA de vSphere restablezca o reinicie automáticamente máquinas virtuales individuales que han perdido su capacidad de pulsación. Este diseño habilita la supervisión de las VM y de las aplicaciones.

#### Condiciones de error y respuesta de VM
{: #cluster-settings-failure-conditions}

Las condiciones de error definen el modo en que pueden fallar las VM y la respuesta que se asigna a cada error. En este diseño, la prioridad de reinicio de VM se establece en media. Revise este valor y ajuste la configuración de modo que la prioridad de reinicio se ajuste a la importancia de la carga de trabajo. Además, la respuesta para el aislamiento de host se establece en "Apagar y reiniciar VM" para que las VM no se vean afectadas por un host aislado en el clúster. El resto de los valores conservan el valor predeterminado.

En la tabla siguiente se muestran los valores correspondientes a alta disponibilidad de clúster de vSphere en el cliente web de VMware vSphere.

Tabla 2. Condiciones de error y valores de respuesta de máquina virtual para HA de clúster de vSphere

| Parámetro             | Valor  |
|:------------------- |:------ |
| Prioridad reinicio VM | Medio |
| Respuesta para aislamiento de host | Apagar y reiniciar VM |
| Respuesta para almacén de datos con pérdida de dispositivo permanente (PDL) | Inhabilitado |
| Respuesta para almacén de datos con todas las vías de acceso apagadas (APD) | Inhabilitado |
| Respuesta para recuperación de APD después del tiempo de espera de APD | Inhabilitado |
| Sensibilidad de supervisión de VM | Personalizada |
| Intervalo de error | 50 s |
| Tiempo de actividad mínimo | 90 s |
| Número máximo restablecimientos por VM | 10 |
| Ventaja de tiempo máximo restablecimientos | Dentro de 1 hr |

Para obtener más información sobre la configuración de estos valores en el cliente web de vSphere, consulte [Configuración de respuestas de máquina virtual](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.avail.doc/GUID-3DAED2B1-55B8-4877-BD0F-BC57C10A516C.html).

#### Control de admisiones
{: #cluster-settings-admission-control}

vCenter Server utiliza el control de admisiones para garantizar que hay suficientes recursos disponibles en un clúster para ofrecer protección de migración tras error y para asegurar que se respetan las reservas de recursos de VM. En este diseño, la capacidad de migración tras error se reserva mediante la especificación de un porcentaje de los recursos del clúster. La capacidad de migración tras error definida se establece en 25% de CPU y 25% de memoria.

#### Pulsaciones del almacén de datos
{: #cluster-settings-datastore}

HA de vSphere utiliza pulsaciones del almacén de datos para identificar los hosts que han fallado y los hosts que residen en una partición de red. Las pulsaciones del almacén de datos permiten a HA de vSphere supervisar los hosts cuando se produce una partición de red de gestión y para continuar respondiendo ante los errores que se producen. En este diseño, la política de selección del almacén de datos de pulsaciones está establecida en "Selección automática de almacenes de datos accesibles desde el host".

## Enlaces relacionados
{: #cluster-settings-related}

* [Visión general de la solución](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
