---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)

Puede solicitar servicios para instancias de VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity), como una solución de recuperación tras desastre. Cuando ya no necesite estos servicios, puede eliminarlos de su instancia.

## Servicios disponibles para instancias de vCenter Server con el paquete híbrido (Hybridity)

Los siguientes servicios están disponibles para las instancias de vCenter Server con el paquete híbrido (Hybridity), junto con las versiones de servicio instaladas.

Tabla 1. Servicios disponibles para instancias de vCenter Server con el paquete híbrido (Hybridity)

| Nombre de servicio | Versión de servicio | Versión de instancia |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud_notm}}](../services/f5_considerations.html)                                 | BIG-IP VE v13.1 | V1.9 y posterior |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html)       | serie 300 | V1.8 y posterior |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html) | 6.0.3 | V2.0 y posterior |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html)              | 5.4.0 | V2.3 y posterior |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)              | 4.2.1 | V2.3 y posterior |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](../services/htkc_considerations.html)              | 4.2 | V2.5 y posterior |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](../services/spp_considerations.html)  | 10.1.1 Parche 1 | V2.2 y posterior |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_considerations.html)                  |   | V2.2 y posterior |
| [Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html)                           | 9.5u3 | V1.8 y posterior |
| [VMware HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_considerations.html)                        | 3.5.1 | V2.3 y posterior |
| [Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html)                                  | 6.0 actualización 3 | V1.2 y posterior |

## Procedimiento para añadir servicios a instancias de vCenter Server con el paquete híbrido (Hybridity)

Para aplicar un servicio a la instancia de vCenter Server con el paquete híbrido (Hybridity), pulse los enlaces de la tabla para revisar las consideraciones para el servicio. A continuación, compruebe los componentes que se despliegan y siga las instrucciones de los temas de pedido para solicitar su pedido.

### Resultados de la instalación de un servicio

Cuando la instalación del servicio finalice correctamente, recibirá una notificación por correo electrónico y el servicio se mostrará en el separador **Servicios** de los detalles de la instancia con el estado **Instalado**.

## Procedimiento para visualizar servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea ver los servicios.
3. Pulse **Servicios** en el panel de navegación izquierdo.
4. En la página **Servicios**, pulse un servicio para revisar información sobre el mismo, como por ejemplo el estado del servicio y otros detalles.
5. Dependiendo del servicio visualizado, puede acceder a las consolas de servicio utilizando las credenciales proporcionadas en los detalles del servicio y puede gestionar el servicio desde ahí.

## Procedimiento para eliminar servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Instancias desplegadas** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse la instancia para la que desea eliminar servicios.
3. Pulse **Servicios** en el panel de navegación izquierdo.
4. En la página **Servicios**, localice la instancia de servicio que desea suprimir y pulse el icono **Suprimir**.
5. En la ventana **Suprimir servicio**, revise las consideraciones o los avisos, si los hay. Seleccione **Lo entiendo** y pulse **Suprimir**.

### Resultados de la eliminación de un servicio

Una vez aceptada su solicitud de eliminación del servicio, el estado del servicio pasa a ser **Eliminando**.

Cuando la eliminación del servicio finalice correctamente, recibirá una notificación por correo electrónico y el servicio se eliminará de la página **Servicios** de la instancia.

Se le facturará por los servicios eliminados hasta el final del ciclo de facturación de la infraestructura {{site.data.keyword.cloud_notm}}.
{:note}

### Enlaces relacionados

* [Preguntas frecuentes](../vmonic/faq.html)
