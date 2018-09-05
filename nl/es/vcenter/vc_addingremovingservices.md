---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-09"

---

# Solicitud, visualización y eliminación de servicios para instancias de vCenter Server

Puede solicitar servicios para instancias de VMware vCenter Server, como una solución de recuperación tras desastre. Cuando ya no necesite estos servicios, puede eliminarlos de sus instancias.

## Servicios disponibles para instancias de vCenter Server

La tabla siguiente muestra los servicios que están disponibles para instancias de vCenter Server.

Tabla 1. Servicios disponibles para las instancias de vCenter Server

| Nombre de servicio | Disponibilidad | Soporte instancia |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud}}](../services/f5_considerations.html)                                 | Sí | V1.9 y posterior |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html) | Sí | V2.0 y posterior |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html)              | Sí | V2.3 y posterior |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)              | Sí | V2.3 y posterior |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](../services/spp_considerations.html)         | Sí | V2.2 y posterior |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_considerations.html)                  | Sí | V2.2 y posterior |
| [Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html)                          | Sí | V1.8 y posterior |
| [VMware HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html)                         | No | No es aplicable |
| [Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html)                                 | Sí | V1.2 y posterior |


## Adición de servicios a instancias de vCenter Server

Para añadir un servicio a la instancia de vCenter Server, pulse el enlace de servicio adecuado en la tabla anterior para revisar las consideraciones para el servicio y comprobar los componentes que se despliegan. A continuación, siga las instrucciones del tema de ordenación del servicio para añadir el servicio a su instancia.

### Resultados de la instalación de un servicio

Cuando la instalación del servicio finalice correctamente, recibirá una notificación por correo electrónico y el servicio se mostrará en la página **Servicios** de la instancia con el estado **Instalado**.

## Visualización de servicios para instancias de vCenter Server

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea ver los servicios.
3. Pulse **Servicios** en el panel de navegación izquierdo.
4. En la página **Servicios**, pulse un servicio para revisar información sobre el mismo, como por ejemplo el estado del servicio y otros detalles.
5. Dependiendo del servicio visualizado, puede acceder a las consolas de servicio utilizando las credenciales proporcionadas en los detalles del servicio y puede gestionar el servicio desde ahí.

## Eliminación de servicios para instancias de vCenter Server

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea eliminar servicios.
3. Pulse **Servicios** en el panel de navegación izquierdo.
4. En la página **Servicios**, localice la instancia de servicio que desea suprimir y pulse el icono **Suprimir**.
5. En la ventana **Suprimir servicio**, revise las consideraciones o los avisos, si los hay. Seleccione **Lo entiendo** y pulse **Suprimir**.

### Resultados de la eliminación de un servicio

Una vez aceptada su solicitud de eliminación del servicio, el estado del servicio pasa a ser **Eliminando**.

Cuando la eliminación del servicio finalice correctamente, recibirá una notificación por correo electrónico y el servicio se eliminará de la página **Servicios** de la instancia.

**Atención**: se le facturará por los servicios eliminados hasta el final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}.

### Enlaces relacionados

* [Preguntas frecuentes](../vmonic/faq.html)
