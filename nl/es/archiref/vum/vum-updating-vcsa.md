---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Actualización de VCSA y vCenters enlazados con SSO
{: #vum-updating-vcsa}

## Actualización de PSC y VCSA
{: #vum-updating-vcsa-psc-vcsa-update}

Esta sección hace referencia tanto a vCenter Server Appliance (VCSA) como a Platform Services Controller (PSC). Ambos dispositivos son dispositivos VCSA, pero con roles distintos. Al actualizar vSphere con un PSC externo, primero actualice el PSC, luego el VCSA, luego los hosts ESXi y, finalmente, las versiones de hardware y VMware Tools en las máquinas virtuales.

VUM no actualiza el PSC/VCSA. En la información siguiente se describe el proceso de actualización de estos dispositivos. El PSC/VCSA desplegado en una instancia de VMware vCenter Server on {{site.data.keyword.cloud}} no tiene acceso a Internet, por lo que el paquete de actualización se debe descargar primero en un servidor de saltos.

El PSC/VCSA se actualiza mediante la consola de gestión de dispositivos, no con el cliente web de vSphere. Se accede a la consola de gestión de dispositivos PSC/VCSA mediante un navegador, la dirección IP de PSC/VCSA y el puerto 5480.

Debe iniciar una instancia del dispositivo o una copia de seguridad del PSC/VCSA antes de actualizar. Asegúrese de que todo funcione según lo previsto y, a continuación, elimine la instantánea dentro de unos días para evitar la degradación del rendimiento. Revise también las notas del release de VMware antes de intentar cualquier actualización para comprender las instrucciones específicas del release correspondiente.

Para actualizar el PSC/VCSA, siga estos pasos:
1. Puede descargar actualizaciones accediendo al
[Centro de descarga de parches de VMware](https://www.vmware.com/patchmgr/findPatchByReleaseName.portal), iniciando sesión y eligiendo VC en el menú **Buscar por producto**. Seleccione el parche adecuado y pulse **Descargar**.
2. Mediante el cliente web de vSphere, cargue el archivo ISO en el repositorio de almacén de datos de vCenter.
3. Monte el archivo ISO de actualización al servidor de vCenter.
4. Tome una instantánea del servidor de vCenter.
5. Inicie la sesión en la consola de gestión de dispositivos de vCenter en: `https://pscip:5480` (para el PSC) o `https://vcenterip:5480` (para el VCSA).
6. Vaya a la sección **Actualizar** y seleccione **Comprobar actualizaciones** y, a continuación, **Comprobar CDROM**. La actualización aparece en la lista.
7. Seleccione **Instalar actualizaciones** y **Aceptar** el EULA. Se instala la actualización.
8. Una vez completada la actualización, debe volver a la consola de gestión de dispositivos y seleccionar para reiniciar la consola.
9. Vuelva a iniciar la sesión en el cliente web de vSphere y compruebe si hay algún error. Realice una exploración manual de VUM, **Inicio** > **Hosts y clúster**, seleccione luego un centro de datos o clúster, seleccione el separador
**Update Manager** y, a continuación, pulse **Explorar actualizaciones**. Si la exploración manual da lugar a un error, consulte [Restablecimiento de la base de datos de VMware Update Manager en un dispositivo de vCenter Server 6.5 (2147284)](https://kb.vmware.com/s/article/2147284).
10. Después de hacer pruebas, si tiene que hacer una copia de seguridad, revierta a la instantánea o restaure el vCenter con una copia de seguridad anterior.

## Instancias de vCenter Server enlazadas con SSO
{: #vum-updating-vcsa-sso-vcenter}

Si tiene instancias de vCenter Server primarias y secundarias, los VCSA se configuran para que estén en un único dominio de inicio de sesión único (SSO) de vCenter. Cada VCSA tiene una instancia de VUM desplegada. Las propiedades de configuración que modifique se aplicarán únicamente a la instancia de VUM que especifique y no se propagarán a las demás instancias del grupo.

Puede especificar una instancia de VUM seleccionando el nombre del VCSA con el que se ha registrado la instancia de VUM desde la barra de navegación. También puede gestionar líneas bases y grupos de líneas base, así como explorar y corregir solo los objetos de inventario que gestiona el VCSA con el que se registra la instancia de VUM.

## Enlaces relacionados
{: #vum-updating-vcsa-related}

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [Demos de {{site.data.keyword.vmwaresolutions_full}}](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (demostraciones)
