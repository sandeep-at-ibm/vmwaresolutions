---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Visión general de FortiGate Security Appliance on IBM Cloud

El servicio de FortiGate Security Appliance on {{site.data.keyword.cloud}} despliega un par de dispositivos de seguridad FortiGate (FSA) serie 300 en modalidad altamente disponible para ofrecer servicios de cortafuegos, direccionamiento, NAT y VPN para proteger todos los servidores y máquinas virtuales de la VLAN pública de sus instancias.

Puede gestionar este servicio mediante el cliente web FortiOS o la interfaz de línea de mandatos a través de SSH.

**Disponibilidad**: Este servicio solo está disponible para instancias desplegadas en V1.8 o releases posteriores.

## Componentes de FortiGate Security Appliance on IBM Cloud

Cuando solicite el servicio de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} para la instancia, se desplegará un par de HA de dispositivos de seguridad FortiGate serie 300 en la VLAN pública predeterminada de la instancia o del clúster original. Todo el tráfico a la VLAN pública de su instancia se direcciona mediante el dispositivo de seguridad de FortiGate.

**Nota:** Si solicita clústeres adicionales, las VLAN públicas para estos clústeres recién añadidos no tendrán el par de HA de dispositivos de seguridad.

## Consideraciones al instalar FortiGate Security Appliance on IBM Cloud

Revise las siguientes consideraciones antes de instalar el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:
* Asegúrese de que la cuenta de {{site.data.keyword.cloud_notm}} que utiliza tiene el permiso **Hardware Firewall**. Este permiso se necesita para editar o ver registros y valores del cortafuegos correspondientes al servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} en su instancia.
* Si desea añadir el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} a una instancia desplegada, asegúrese de que no hay otro cortafuego desde la infraestructura {{site.data.keyword.cloud_notm}} ya instalado en la VLAN pública de la instancia.
* La instalación del servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} añadirá una nueva VLAN pública.
* Durante el despliegue del servicio, es posible que la instancia no pueda acceder a Internet temporalmente.
* Después de que se instale correctamente el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, podrá gestionar y configurar reglas de cortafuegos para FSA desde la consola de FortiGate. Debe asegurarse de que las reglas de cortafuegos de FSA estén definidas de modo que permitan comunicaciones HTTPS salientes (puerto TCP 443) iniciadas por componentes de gestión, como la máquina virtual IBM CloudDriver o la máquina virtual Zerto, para establecer comunicación con la base de datos de gestión externa de {{site.data.keyword.cloud_notm}} a través de Internet. Las comunicaciones HTTPS salientes (puerto TCP 443) se originan en la dirección IP pública de los servicios de gestión de VMware NSX Edge Services Gateway (ESG) de su instancia.
* Si despliega un par de dispositivos de seguridad FortiGate como parte de una nueva instancia, los dispositivos de seguridad FortiGate se configuran de modo que solo permiten las comunicaciones de salida necesarias entre su instancia y la red pública y deniegan todas las demás comunicaciones.
* Si despliega un par de dispositivos de seguridad FortiGate como parte de una instancia existente, los dispositivos de seguridad FortiGate se configuran con una regla explícita que permite todas las comunicaciones de gestión de salida necesarias entre su instancia y la red pública. Además, los dispositivos de seguridad FortiGate se configuran con una regla adicional que permite todas las demás comunicaciones para que el tráfico de la aplicación existente no se vea interrumpido. Debe gestionar la configuración del dispositivo de seguridad FortiGate cuidadosamente para que se permitan solo las comunicaciones necesarias y se denieguen todas las demás comunicaciones.

## Consideraciones al eliminar FortiGate Security Appliance on IBM Cloud

Revise las siguientes consideraciones antes de eliminar el servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}:
* La eliminación del servicio FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} eliminará la VLAN pública que se ha añadido.
* Durante la eliminación del servicio, es posible que la instancia no pueda acceder a Internet temporalmente.
* Todas las reglas de FortiGate para permitir, inspeccionar, bloquear o direccionar el tráfico NAT se eliminan junto con el servicio Fortinet. Si tiene alguna regla NAT, deberá volverla a configurar.

## Enlaces relacionados

* [Solicitud de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](fsa_ordering.html)
* [Gestión de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](managingfsa.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de Fortinet](https://www.fortinet.com/){:new_window}
* [Biblioteca de documentos de Fortinet](http://docs.fortinet.com/fortigate/admin-guides){:new_window}
