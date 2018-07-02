---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-13"

---

# Solicitud de IBM Spectrum Protect Plus on IBM Cloud

Puede solicitar el servicio de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} al pedir una instancia nueva incluida con el servicio o añadiendo el servicio a la instancia existente.

## Solicitud de IBM Spectrum Protect Plus on IBM Cloud para una instancia nueva

Puede solicitar una instancia nueva con IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_full}}, al solicitar una instancia nueva, seleccione **IBM Spectrum Protect Plus on IBM Cloud** en la sección **Servicios**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **Servicio de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}**, especifique los valores de servicio y seleccione **Añadir a instancia nueva**.

## Solicitud de IBM Spectrum Protect Plus on IBM Cloud para una instancia existente

Puede añadir el servicio de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} en una instancia existente utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, visualice la instancia para la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir servicio**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **Servicio de IBM Spectrum Protect Plus on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia existente**.

## Configuración del servicio de IBM Spectrum Protect Plus on IBM Cloud

Al solicitar el servicio, proporcione los valores siguientes:

### Número de volúmenes de almacenamiento

El número de volúmenes que satisfagan sus necesidades de almacenamiento.

### Tamaño de almacenamiento por volumen

La capacidad de almacenamiento por volumen. Se necesita un mínimo de 500 GB por volumen para la gestión.

### Rendimiento de almacenamiento

El valor de IOPS (operaciones de entrada/salida por segundo) por GB en función de los requisitos de carga de trabajo.
* Si desea solicitar licencias para IBM Spectrum Protect Plus, especifique **Número de máquinas virtuales para licencia** en el separador **Pedido de licencias**. Se necesitan como mínimo 10 máquinas virtuales para la gestión de licencias.
* Si desea traer su propia licencia (BYOL), pulse el separador **Licencias de IBM Spectrum Protect Plus** y luego pulse **Añadir archivos de licencia** para cargar sus propios archivos de licencia de IBM Spectrum Protect Plus.

## Proceso de despliegue de IBM Spectrum Protect Plus on IBM Cloud

El despliegue de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} es automático. Tanto si solicita una instancia con este servicio incluido como si despliega el servicio posteriormente en la instancia, se llevan a cabo los siguientes pasos mediante el proceso de automatización de {{site.data.keyword.vmwaresolutions_short}}:

1. Se solicita almacenamiento NFS de resistencia de la infraestructura de {{site.data.keyword.cloud_notm}} para el repositorio de copia de seguridad de IBM Spectrum Protect Plus en función de las entradas de los usuarios.
2. Se solicita un número específico de licencias para IBM Spectrum Protect Plus de la infraestructura {{site.data.keyword.cloud_notm}} en función de las entradas de los usuarios. Las licencias se solicitan en incrementos de paquetes de 10 licencias de VM, en función del número de licencias de máquinas virtuales que especifica el usuario al solicitar el servicio IBM Spectrum Protect Plus {{site.data.keyword.cloud_notm}}. Si el usuario opta por traer una licencia existente de IBM Spectrum Protect Plus, no se realiza ningún pedido de la infraestructura de {{site.data.keyword.cloud_notm}}.
3. Se monta todo el almacenamiento de NFS solicitado para este servicio en todos los servidores ESXi en el clúster predeterminado de la instancia, incluida la adición de las rutas estáticas correctas en cada servidor ESXi a la subred privada de almacenamiento.
4. Se crean almacenes de datos NFS en vCenter Server para todos los volúmenes de almacenamiento NFS montados en los servidores ESXi.
5. Se despliega, activa y configura la máquina virtual de IBM Spectrum Protect Plus en el clúster predeterminado de la instancia.
6. Se conecta el almacenamiento NFS solicitado para este servicio a la máquina virtual de IBM Spectrum Protect Plus y se configura el repositorio de copias de seguridad.
7. Se registra el nombre de host y la dirección IP de la máquina virtual de IBM Spectrum Protect Plus con el servidor DNS de la instancia.
8. (Para instancias de V2.3 y posterior) Cree un trabajo de copia de seguridad de gestión predeterminada en IBM Spectrum Protect Plus. Para obtener más información, consulte [Gestión de IBM Spectrum Protect Plus on IBM Cloud](managingspp.html).

## Enlaces relacionados

* [Visión general de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_considerations.html)
* [Planificación del servicio preventivo de IBM Spectrum Protect Plus on IBM Cloud](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestión de IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_addingremovingservices.html)
* [Documentación de IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
