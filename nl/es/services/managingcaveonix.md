---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestión de Caveonix RiskForesight on IBM Cloud
{: #managingcaveonix}

## Acceso a la consola de Caveonix RiskForesight
{: #managingcaveonix-access-console}

Para gestionar el servicio Caveonix RiskForesight on {{site.data.keyword.cloud}}, debe acceder a la consola de Caveonix RiskForesight siguiendo estos pasos:

1. Utilice la VPN de la infraestructura de IBM Cloud o un servidor de gestión para permitir el acceso a la dirección IP de la máquina virtual de Caveonix RiskForesight. Encontrará la dirección IP en la página de detalles del servicio de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} en la consola de {{site.data.keyword.vmwaresolutions_short}}. En concreto:
   1. Cree una contraseña de VPN desde el portal de clientes de infraestructura de {{site.data.keyword.cloud_notm}}.
   2. Inicie una sesión en el portal de VPN del centro de datos utilizando las credenciales de VPN de la infraestructura {{site.data.keyword.cloud_notm}}.
   3. Añada la correlación entre dirección IP y nombre de host al archivo de host local con el siguiente formato:

      ```javascript
      IPAddress              HostName
      ```
2. Para acceder a la consola de Caveonix RiskForesight, pulse **Ver consola de RiskForesight** en la página de detalles de servicio para Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} y, a continuación, inicie sesión con las credenciales listadas en la misma página de detalles de servicio.

## Aplicación de actualizaciones a Caveonix RiskForesight on IBM Cloud
{: #managingcaveonix-update}

El usuario es el responsable de mantener Caveonix RiskForesight actualizado al nivel de la versión más reciente. Puede descargar las actualizaciones necesarias desde el [portal proveedor de servicios de Caveonix](https://support.caveonix.com).

## Actualización de licencias de Caveonix RiskForesight

La licencia de Caveonix RiskForesight es válida durante un año. Puede actualizar la licencia de Caveonix RiskForesight cuando caduque utilizando el procedimiento siguiente:
1. Solicite una nueva licencia de Caveonix RiskForesight y cópiela en la consola de Caveonix RiskForesight. Para obtener más información, consulte [Procedimiento de solicitud de licencias de Caveonix RiskForesight](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_ordering#caveonix_license_ordering-procedure).
2. Suprima la licencia caducada de la tabla **Licencias de Caveonix RiskForesight** en la consola de {{site.data.keyword.vmwaresolutions_short}}. Para obtener más información, consulte [Procedimiento de supresión de licencias de Caveonix RiskForesight](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_license_managing#caveonix_license_managing_procedure-delete).

## Enlaces relacionados
{: #managingcaveonix-related}

* [Visión general de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Solicitud de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
