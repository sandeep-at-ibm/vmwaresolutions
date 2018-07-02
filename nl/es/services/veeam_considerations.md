---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Visión general de Veeam on IBM Cloud

El servicio Veeam on {{site.data.keyword.cloud}} se puede integrar de forma fácil y directa con sus hipervisores VMware para ayudar a la empresa a alcanzar un alto grado de disponibilidad. Este servicio puede proporcionar objetivos de puntos de recuperación y de tiempo para sus datos y aplicaciones. Los objetivos de puntos de recuperación y de tiempo se pueden proporcionar menos de 15 minutos después de finalizar la configuración. Con este servicio, puede controlar directamente las copias de seguridad y las operaciones de restauración de todas las máquinas virtuales de la infraestructura desde la consola de Veeam.

**Disponibilidad**: Este servicio solo está disponible para instancias desplegadas en V1.8 o releases posteriores.

## Componentes de Veeam on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio Veeam on {{site.data.keyword.cloud_notm}}:
* Una VSI de Windows Server 2016 con una dirección IP privada primaria y una interfaz de 1 GbE
* Almacenamiento en bloque {{site.data.keyword.cloud_notm}} Endurance con el tamaño y el rendimiento que haya seleccionado al solicitar el servicio.

## Consideraciones al instalar Veeam on IBM Cloud

* El servicio realiza copia de seguridad de los siguientes componentes de gestión:
  - VMware vCenter Server
  - Platform Services Controller (PSC)
  - IBM CloudDriver
  - **Solo instancias de Cloud Foundation**: VMware SDDC Manager
  - **Solo instancias de vCenter Server con HA AD/DNS**: Par de alta disponibilidad de servidores AD/DNS

* El servicio Veeam on {{site.data.keyword.cloud_notm}} no hace copia de seguridad de las configuraciones de los servidores ESXi.

* De forma predeterminada, se hace una copia de seguridad diaria de las configuraciones del controlador NSX y de NSX Edge mediante NSX Manager con un máximo de 14 puntos de restauración. Para realizar una restauración completa de las configuraciones de NSX, debe crear una incidencia de soporte de {{site.data.keyword.cloud_notm}}, porque las copias de seguridad de las configuraciones de NSX se guardan en el almacenamiento interno de {{site.data.keyword.vmwaresolutions_full}}. Para obtener más información sobre la gestión de las copias de seguridad de configuración de NSX mediante NSX Manager, consulte las [instrucciones técnicas de VMware](https://pubs.vmware.com/NSX-6/index.jsp#com.vmware.nsx.admin.doc/GUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html).
* El repositorio del almacenamiento y del servidor Veeam están en el pod y en el centro de datos originales. Por este motivo, el rendimiento de las operaciones de copia de seguridad de clústeres remotos puede verse deteriorada.

## Consideraciones al eliminar Veeam on IBM Cloud

Antes de eliminar el servicio Veeam on {{site.data.keyword.cloud_notm}}, tenga en cuenta que la eliminación de este servicio detendrá todas las copias de seguridad (incluida la copia de seguridad de las VM de gestión) y suprimirá todas las copias de seguridad anteriores (la supresión es irreversible). Si las VM de gestión resultan dañadas, no se podrán restaurar.

## Enlaces relacionados

* [Solicitud de Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [Gestión de Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [Solicitud de servicios gestionados para Veeam on {{site.data.keyword.cloud_notm}}](managing_veeam_services.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de Veeam](https://www.veeam.com/){:new_window}
* [Centro de ayuda de Veeam](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}
