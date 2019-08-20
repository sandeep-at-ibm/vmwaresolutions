---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: Caveonix view license, Caveonix manage license, delete Caveonix license

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestión de licencias de Caveonix RiskForesight
{: #caveonix_license_managing}

Puede ver, editar notas o suprimir las licencias de Caveonix RiskForesight que ha solicitado para uso autónomo.

## Procedimiento de visualización de licencias de Caveonix RiskForesight
{: #caveonix_license_managing_procedure-view}

1. Pulse **Recursos** en el panel de navegación izquierdo y desplácese a la tabla **Licencias de Caveonix RiskForesight**.

   | Elemento | Descripción |
   |:-----|:------------|
   | Nombre | El nombre de la licencia. |
   | Hora de creación | La fecha y hora en que se ha creado la licencia. |
   | Estado | El estado de la licencia: <br>Modificando: Se está creando la licencia.<br>Instalado: La licencia está lista para su uso.<br>Eliminando: La licencia se está suprimiendo. |
   {: caption="Tabla 1. Descripción de los elementos de licencia de Caveonix RiskForesight" caption-side="top"}

2. Para ver los detalles de una licencia específica, pulse la licencia.

## Procedimiento para editar notas para las licencias de Caveonix RiskForesight
{: #caveonix_license_managing_procedure-edit}

1. Pulse **Recursos** en el panel de navegación izquierdo.
2. Desplácese hacia abajo hasta la tabla **Licencias de Caveonix RiskForesight** y pulse la licencia para la que desea editar las notas.
3. En la página de detalles de licencia, edite las notas de la licencia y, a continuación, pulse **Confirmar**.

## Problemas conocidos acerca de la visualización de la fecha de la licencia
{: #caveonix_license_considerations-date}

Si utiliza Mozilla Firefox como navegador, es posible que las fechas de inicio y de finalización de la licencia no muestren ningún valor en la consola de Caveonix RiskForesight. Para resolver el problema, visualice la información de la licencia en otro navegador, como Google Chrome.

Si tiene este problema y el único navegador que puede utilizar es Firefox, póngase en contacto con el
[Soporte de Caveonix](https://www.caveonix.com/support/){:external} para obtener ayuda.
{:note}

## Procedimiento de supresión de licencias de Caveonix RiskForesight
{: #caveonix_license_managing_procedure-delete}

Supresión de una licencia de Caveonix RiskForesight no elimina el servicio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} que está instalado en una instancia de vCenter Server. Para eliminar el servicio, debe hacerlo en la consola de {{site.data.keyword.vmwaresolutions_short}}. Para obtener más información, consulte [Procedimiento para eliminar servicios para instancias de vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-removing-procedure).
{:note:}

1. Pulse **Recursos** en el panel de navegación izquierdo.
2. Desplácese hacia abajo hasta la tabla **Licencias de Caveonix RiskForesight** y busque la licencia que desea suprimir.
3. En la columna **Acciones**, pulse el icono Suprimir.
4. En la ventana **Suprimir licencia**, pulse **Aceptar**.
   El estado de la licencia pasa a ser **Eliminando**. Cuando finaliza la supresión de la licencia, esta deja de estar disponible en la tabla **Licencias de Caveonix RiskForesight**.

## Enlaces relacionados
{: #caveonix_license_managing-related}

* [Visión general de Caveonix RiskForesight]()
* [Solicitud de licencias de Caveonix RiskForesight](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)
