---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations}

El servicio de FortiGate Security Appliance on {{site.data.keyword.cloud}} despliega un par de dispositivos de seguridad FortiGate (FSA) serie 300 en modalidad altamente disponible para ofrecer servicios de cortafuegos, direccionamiento, NAT y VPN para proteger todos los servidores y máquinas virtuales de la VLAN pública de sus instancias.

Puede gestionar este servicio mediante el cliente web FortiOS o la interfaz de línea de mandatos a través de SSH.

Este servicio solo está disponible para las instancias desplegadas en la versión V1.8 o posteriores.
{:note}

## Especificaciones técnicas para FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-specs}

Los siguientes componentes se solicitan y se incluyen en el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:

### Hardware
{: #fsa_considerations-hardware}

FortiGate 300 series Security Appliance.

### Alta disponibilidad
{: #fsa_considerations-ha}

Se despliegan dos dispositivos en una configuración activa-pasiva.

### Redes
{: #fsa_considerations-networking}

* Dual 1 GbE vinculado en redes ascendentes y descendentes
* Una nueva VLAN pública de {{site.data.keyword.cloud_notm}} ascendente
* Una VLAN pública de {{site.data.keyword.cloud_notm}} descendente existente

## Consideraciones al instalar FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-install}

Revise las siguientes consideraciones antes de instalar el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:
* Asegúrese de que la cuenta de {{site.data.keyword.cloud_notm}} que está utilizando tiene el permiso **Hardware Firewall**. Este permiso se necesita para editar o ver registros y valores del cortafuegos correspondientes al servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} en su instancia.
* Si desea añadir el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} a una instancia desplegada, asegúrese de que no haya ya otro cortafuegos de la infraestructura de {{site.data.keyword.cloud_notm}} en marcha en la VLAN pública de la instancia.
* La instalación del servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} añade una nueva VLAN pública.
* Durante el despliegue del servicio, es posible que la instancia no pueda acceder a Internet temporalmente.
* Después de que se instale correctamente el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, podrá gestionar y configurar reglas de cortafuegos para FSA desde la consola de FortiGate. Debe asegurarse de que las reglas de cortafuegos de FSA estén definidas de modo que permitan comunicaciones HTTPS (TCP puerto 443) salientes que inician los componentes de gestión como el Zerto Virtual Manager para comunicarse con la base de datos de gestión externa en {{site.data.keyword.cloud_notm}} a través de Internet. Las comunicaciones HTTPS salientes (puerto TCP 443) se originan en la dirección IP pública de los servicios de gestión de VMware NSX Edge Services Gateway (ESG) de su instancia.
* Debe gestionar la configuración del dispositivo de seguridad FortiGate cuidadosamente para que se permitan solo las comunicaciones necesarias y se denieguen todas las demás comunicaciones.
* Si solicita clústeres adicionales, las VLAN públicas para estos clústeres recién añadidos no tienen el par HA de dispositivos de seguridad.

## Consideraciones sobre la eliminación de FortiGate Security Appliance on IBM Cloud
{: #fsa_considerations-remove}

Revise las siguientes consideraciones antes de eliminar el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:
* La eliminación del servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} elimina la VLAN pública que se ha añadido.
* Durante la eliminación del servicio, es posible que la instancia no pueda acceder a Internet temporalmente.
* Todas las reglas de FortiGate para permitir, inspeccionar, bloquear o direccionar el tráfico NAT se eliminan junto con el servicio Fortinet. Si tiene alguna regla NAT, deberá volverla a configurar.

## Enlaces relacionados
{: #fsa_considerations-related}

* [Solicitud de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [Gestión de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfsa)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sitio web de Fortinet](https://www.fortinet.com/){:new_window}
* [Biblioteca de documentos de Fortinet](https://docs.fortinet.com/product/fortigate/6.2){:new_window}
