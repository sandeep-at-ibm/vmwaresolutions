---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

keywords: VMware HCX, HCX, tech specs HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de VMware HCX on IBM Cloud
{: #hcx_considerations}

El servicio HCX on {{site.data.keyword.cloud}} permite ampliar fácilmente las redes de centros de datos locales en {{site.data.keyword.cloud_notm}}, lo que permite migrar las máquinas virtuales (VM) de {{site.data.keyword.cloud_notm}} sin ninguna conversión ni cambio. HCX crea una capa de abstracción que permite la movilidad de aplicaciones y la hibridación de infraestructuras a través de redes estiradas de forma segura. Puede simplemente modernizar el entorno de VMware de vSphere 5.1 a la versión más reciente de vSphere sin necesidad de refractar o modificar la aplicación existente, ya que HCX habilita esta transformación de forma transparente. HCX le permite llevar los rangos de subred IP a {{site.data.keyword.cloud_notm}} garantizando la coherencia de IP a través de un despliegue híbrido, al tiempo que proporciona seguridad de alto nivel con cifrados Suite B de extremo a extremo.

HCX on {{site.data.keyword.cloud_notm}} requiere que utilice NSX Advanced o Enterprise a través de {{site.data.keyword.cloud_notm}} o una versión equivalente utilizando BYOL (Bring Your Own License - Traer su propia licencia). Se exige un compromiso de 12 meses al hacer un pedido del servicio VMware HCX on {{site.data.keyword.cloud_notm}}. El pago es en 12 meses consecutivos después del despliegue inicial de HCX. Los nodos adicionales se incluyen dentro de la fecha de caducidad de suministro inicial. Cuando vence el compromiso de 12 meses, puede instalar y desinstalar el servicio HCX on {{site.data.keyword.cloud_notm}} y puede añadir y eliminar hosts y clústeres sin restricciones. A partir de entonces, se realiza un cargo en su cuenta cada mes y puede cancelarlo en cualquier momento.

La fecha de expiración de 12 meses está disponible en la página de detalles de HCX on {{site.data.keyword.cloud_notm}}. Para obtener más información sobre cómo ver los detalles del servicio, consulte [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure).
{:note}

Una instancia de vCenter Server con HCX on {{site.data.keyword.cloud_notm}} está limitada a tres conexiones simultáneas de sitios locales.

HCX on {{site.data.keyword.cloud_notm}} está soportado en las plataformas siguientes:

* vSphere 5.1 (línea de mandatos sólo para vCenter 5.1 utilizando la API)
* vSphere 5.5 (interfaz de usuario de cliente Web soportada en vCenter 5.5u3 y superior)
* vSphere 6.0
* vSphere 6.5 (vDS debe estar a un nivel de 6.0)
* vSphere 6.7

## Especificaciones técnicas para HCX on IBM Cloud
{: #hcx_considerations-specs}

Los componentes siguientes se solicitan y se incluyen en el servicio HCX on {{site.data.keyword.cloud_notm}}.

Las instancias de HCX locales incluyen solo la licencia y la activación.
{:note}

### Un par activo/pasivo de pasarelas de servicio VMware NSX Edge para la gestión de HCX
{: #hcx_considerations-nsx}

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### Dispositivo de gestión HCX - máquina virtual
{: #hcx_considerations-vm}

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: 60 GB VMDK

Los dispositivos HCX adicionales se despliegan durante la configuración, según sean necesarios para la conectividad de L2, la optimización de WAN y las conexiones de pasarela.

### Redes
{: #hcx_considerations-networking}

* Una subred portátil pública con 16 direcciones IP
* Dos subredes portátiles privadas con 64 direcciones IP
* Ocho direcciones IP desde una subred vMotion portátil privada

## Consideraciones al instalar HCX on IBM Cloud
{: #hcx_considerations-install}

Revise las siguientes consideraciones antes de intentar instalar HCX on {{site.data.keyword.cloud_notm}}.

### Requisitos sobre el número de servidores ESXi
{: #hcx_considerations-esxi-servers}

El servicio HCX on {{site.data.keyword.cloud_notm}} no se puede instalar en una instancia para la cual el clúster predeterminado tenga más de 51 servidores ESXi. Como HCX on {{site.data.keyword.cloud_notm}} necesita ocho direcciones IP en la subred vMotion del clúster predeterminado, si el número de servidores ESXi supera los 51 no habrá ninguna dirección IP disponible en la subred vMotion para HCX on {{site.data.keyword.cloud_notm}}.

### Requisitos sobre las reglas de cortafuegos
{: #hcx_considerations-firewall}

Antes de instalar el servicio HCX on {{site.data.keyword.cloud_notm}}, debe añadir una regla de cortafuegos a cualquier cortafuegos existente para permitir todo el tráfico HTTPS de salida para que el dispositivo virtual HCX Manager (HCX Manager) se pueda registrar a sí mismo. Una vez finalizada la instalación de HCX Manager, puede eliminar la regla de cortafuegos. Además, debe configurar reglas de cortafuegos para permitir que HCX funcione correctamente. Para obtener más información, consulte [Requisitos de acceso a puertos de VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req#hcx-archi-port-req).

## Consideraciones al eliminar HCX on IBM Cloud
{: #hcx_considerations-delete}

Revise las siguientes consideraciones antes de eliminar el servicio HCX on {{site.data.keyword.cloud_notm}}:
* Asegúrese de que se eliminen las interconexiones y las redes ampliadas entre el sitio local de origen y los sitios de destino de {{site.data.keyword.cloud_notm}}. Para eliminar las interconexiones y las redes ampliadas, utilice la interfaz de usuario de HCX del cliente web local de VMware vSphere.
* Asegúrese de que se eliminen los emparejamientos de sitios entre el sitio local de origen y los sitios de destino de {{site.data.keyword.cloud_notm}}. Para eliminar los emparejamientos de sitios, utilice la interfaz de usuario de HCX del cliente web local de VMware vSphere.
* La eliminación de HCX on {{site.data.keyword.cloud_notm}} es automática. Se llevan a cabo los procedimientos siguientes para eliminar correctamente este servicio:
   * La licencia HCX que se solicita para el HCX Manager del lado de la nube está desactivada.
   * Se suprime HCX Manager.
   * Se liberan las direcciones IP de vMotion que se habían reservado para HCX.
   * Si están vacías, se eliminan las agrupaciones de recursos relacionadas con HCX.
   * Si están vacías, se eliminan las carpetas relacionadas con HCX.
   * Se suprimen los dispositivos del extremo de gestión de HCX.

## Enlaces relacionados
{: #hcx_considerations-related}

* [Solicitud de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering)
* [Gestión de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [Demostración guiada de VMware HCX on IBM Cloud: Obtenga información sobre cómo migrar una máquina virtual utilizando HCX](https://www.ibm.com/cloud/garage/dte/producttour/vmware-hcx-ibm-cloud-guided-demo-learn-how-migrate-vm-using-hcx){:external}
* [Glosario de términos de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Visión general de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx){:external}
* [Documentación de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources){:external}
