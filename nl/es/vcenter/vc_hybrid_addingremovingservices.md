---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-21"

---

# Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)

Puede solicitar servicios para instancias de VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity), como una solución de recuperación tras desastre. Cuando ya no necesite estos servicios, puede eliminarlos de su instancia.

## Servicios disponibles para instancias de vCenter Server con el paquete híbrido (Hybridity)

Están disponibles los siguientes servicios para las instancias de vCenter Server con el paquete híbrido (Hybridity).

Tabla 1. Servicios disponibles para instancias de vCenter Server con el paquete híbrido (Hybridity)

| Nombre de servicio | Disponibilidad | Soporte instancia |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on IBM Cloud](../services/f5_considerations.html)                                 | Sí | V1.9 y posterior |
| [FortiGate Security Appliance on IBM Cloud](../services/fsa_considerations.html)       | Sí | V1.8 y posterior |
| [FortiGate Virtual Appliance on IBM Cloud](../services/fortinetvm_considerations.html) | Sí | V2.0 y posterior |
| [HyTrust CloudControl on IBM Cloud](../services/htcc_considerations.html)              | Sí | V2.3 y posterior |
| [HyTrust DataControl on IBM Cloud](../services/htdc_considerations.html)              | Sí | V2.3 y posterior |
| [IBM Spectrum Protect Plus on IBM Cloud](../services/spp_considerations.html)         | Sí | V2.2 y posterior |
| [KMIP for VMware on IBM Cloud](../services/kmip_considerations.html)                  | Sí | V2.2 y posterior |
| [Veeam on IBM Cloud](../services/veeam_considerations.html)                           | Sí | V1.8 y posterior |
| [VMware HCX on IBM Cloud](../services/hcx_considerations.html)                        | Sí | V2.3 y posterior |
| [Zerto on IBM Cloud](../services/addingzertodr.html)                                  | Sí | V1.2 y posterior |

## Adición de servicios a instancias de vCenter Server con el paquete híbrido (Hybridity)

Para aplicar un servicio a la instancia de vCenter Server con el paquete híbrido (Hybridity), pulse los enlaces en la tabla para revisar las consideraciones para el servicio, comprobar los componentes que se despliegan y seguir las instrucciones de los temas de pedido para solicitar su pedido.

### Resultados de la instalación de un servicio

Cuando la instalación del servicio finalice correctamente, recibirá una notificación por correo electrónico y el servicio se mostrará en el separador **Servicios** de los detalles de la instancia con el estado **Instalado**.

## Visualización de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea ver los servicios.
3. Pulse **Servicios** en el panel de navegación izquierdo.
4. En la página **Servicios**, pulse un servicio para revisar información sobre el mismo, como por ejemplo el estado del servicio y otros detalles.
5. Dependiendo del servicio visualizado, puede acceder a las consolas de servicio utilizando las credenciales proporcionadas en los detalles del servicio y puede gestionar el servicio desde ahí.

## Eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea eliminar servicios.
3. Pulse **Servicios** en el panel de navegación izquierdo.
4. En la página **Servicios**, localice la instancia de servicio que desea suprimir y pulse el icono **Suprimir**.
5. En la ventana **Suprimir servicio**, revise las consideraciones o los avisos, si los hay. Seleccione **Lo entiendo** y pulse **Suprimir**.

### Resultados de la eliminación de un servicio

Una vez aceptada su solicitud de eliminación del servicio, el estado del servicio pasa a ser **Eliminando**.

Cuando la eliminación del servicio finalice correctamente, recibirá una notificación por correo electrónico y el servicio se eliminará de la página **Servicios** de la instancia.

**Atención**: se le facturará por los servicios eliminados hasta el final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}.

## Enlaces relacionados

* [Preguntas frecuentes](../vmonic/faq.html)
