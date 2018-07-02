---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Visión general de IBM Spectrum Protect Plus on IBM Cloud

El servicio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} proporciona una solución eficiente y escalable para la protección de datos, la reutilización de datos y la recuperación de datos para entornos virtuales. Puede implementar el servicio como una solución autónoma o integrarlo con su entorno IBM Spectrum Protect Plus para descargar copias para su almacenamiento y gestión de datos a largo plazo.

**Disponibilidad**: Este servicio solo está disponible para las instancias que se despliegan en (o se actualizan a) V2.2 o releases posteriores.

**Notas:**
* Si acepta la selección predeterminada de servicios para instancias que se despliegan en V2.4 o releases posteriores, se instala IBM Spectrum Protect Plus V10.1.1 Patch 1. El servicio proporciona soporte de recuperación para las máquinas virtuales (VM) de gestión automáticamente.
* Si acepta la selección de servicio predeterminada para instancias desplegadas en V2.3, se instalará IBM Spectrum Protect Plus V10.1.1. El servicio proporciona copias de seguridad automáticas para VM de gestión.
* Si instala el servicio para instancias que se despliegan en V2.2, se instalará IBM Spectrum Protect Plus V10.1.0. El servicio proporciona protección de datos solo para las VM de carga de trabajo.


## Componentes de IBM Spectrum Protect Plus on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}:

### Recursos de vCenter

* Una sola máquina virtual (VM) que se ejecuta en el servidor IBM Spectrum Protect Plus
* 4 núcleos x 2,0 GHz
* 32 GB de RAM
* Disco de 370 GB

### Almacenamiento para copias de seguridad

Almacenamiento personalizable para copias de seguridad con las opciones siguientes:
* Número de almacenamiento de archivos: 1, 2, 3 o 4
* Cada almacenamiento de archivo de resistencia: 500, 1000, 2000, 4000, 8000 o 12000 GB
* Rendimiento de almacenamiento: 0,25, 2 o 4 IOPS/GB

### Almacenamiento para gestión

Un almacén de archivos de resistencia (500 GB, 2 IOPS/GB) que aloje la máquina virtual IBM Spectrum Protect Plus y se ejecute en la misma subred que el almacenamiento de copia de seguridad solicitado para el servicio.

### Redes

Una dirección IP privada portátil.

### Licencias y tarifas

Se puede obtener una licencia de IBM Spectrum Protect Plus en la consola de {{site.data.keyword.vmwaresolutions_short}} para entre 10 y un máximo de 1000 VM en incrementos de 10. También puede traer su propia licencia (BYOL) y cargar el archivo de licencia durante el proceso de instalación.

## Consideraciones al instalar IBM Spectrum Protect Plus on IBM Cloud

Revise las siguientes consideraciones antes de instalar el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

* Asegúrese de que la CPU y la memoria del clúster predeterminado de la instancia sean suficientes para la máquina virtual de IBM Spectrum Protect Plus.
* Asegúrese de que los montajes de NFS disponibles en los servidores ESXi sean suficientes en función de la versión de los servidores ESXi.

  Las instancias de Cloud Foundation y las instancias de vCenter Server que se despliegan en la V2.2 o posteriores que se actualizan a la misma tienen el valor del parámetro `NFS.MaxVolumes` en VMware. Este parámetro define el número máximo de montajes de NFS de un servidor ESXi y se puede establecer en un máximo de 256, dependiendo de la versión del servidor ESXi. Para obtener más información, consulte [Cómo aumentar el valor predeterminado que define el número máximo de montajes de NFS en un host ESXi/ESX](https://kb.vmware.com/s/article/2239).

  El servicio de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} puede consumir hasta cinco de los volúmenes NFS de cada servidor de ESXi del clúster predeterminado de la instancia. Además, el servicio creará montajes de NFS transitorios para realizar copias de seguridad y restauraciones. Por lo tanto, debe establecer el número de montajes de NFS en un mínimo de 64 para asegurarse de que el servicio pueda instalarse y funcionar correctamente.

## Consideraciones al eliminar IBM Spectrum Protect Plus on IBM Cloud

Revise las siguientes consideraciones antes de eliminar el servicio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}:
* Asegúrese de que todas las configuraciones de los trabajos de copia de seguridad se eliminen y de que no haya ninguna operación activa de copia de seguridad o de restauración.
* Cuando elimine el servicio, el almacenamiento del repositorio de copia seguridad se elimina de la VM de IBM Spectrum Protect Plus y el pedido de almacenamiento se cancela, lo cual suprime de forma permanente los datos del repositorio de copia de seguridad.
* Cuando se elimina el servicio, también se elimina el almacenamiento de copia de seguridad del servicio. Por lo tanto, todas las copias de seguridad pasan a estar inaccesibles durante la eliminación en el servicio.

## Enlaces relacionados

* [Planificación del servicio preventivo de IBM Spectrum Protect Plus on IBM Cloud](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestión de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Solicitud de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_ordering.html)
* [Documentación de IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
