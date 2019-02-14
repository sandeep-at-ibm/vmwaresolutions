---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-19"

---

# Actualización de VCSA y vCenters enlazados por SSO

## Actualización de VCSA

VUM no actualiza VCSA. En la información siguiente se describe el proceso de actualización de este dispositivo. El VCSA desplegado en una instancia de VMware vCenter Server on {{site.data.keyword.cloud}} no tiene acceso a Internet, por lo que el paquete de actualización se debe descargar primero en un servidor de saltos.

El VCSA se actualiza mediante la consola de gestión de dispositivos, no con el cliente web de vSphere. Se accede a la consola de gestión de dispositivos VCSA mediante un navegador, la dirección IP VCSA y el puerto 5480.

Debe iniciar una instancia del dispositivo o una copia de seguridad del VCSA antes de actualizar. Asegúrese de que todo funcione según lo previsto y, a continuación, elimine la instantánea dentro de unos días para evitar la degradación del rendimiento. Revise también las notas del release antes de intentar cualquier actualización.

Para actualizar el VCSA, siga estos pasos:
1. Puede descargar actualizaciones al ir al [Centro de descargas](https://my.vmware.com/group/vmware/patch#search) de parches de VMware, iniciar sesión y elegir VC desde el menú **Buscar por producto**. Seleccione el parche adecuado y pulse **Descargar**.
2. Mediante el cliente web de vSphere, cargue el archivo ISO en el repositorio de almacén de datos de vCenter.
3. Monte el archivo ISO de actualización al servidor de vCenter.
4. Tome una instantánea del servidor de vCenter.
5. Inicie la sesión en la consola de gestión de dispositivos de vCenter en: `https://vcenterip:5480`
6. Vaya a la sección **Actualizar** y seleccione **Comprobar actualizaciones** y, a continuación, **Comprobar CDROM**. La actualización aparece en la lista.
7. Seleccione **Instalar actualizaciones** y **Aceptar** el EULA. Se instala la actualización.
8. Una vez completada la actualización, debe volver a la consola de gestión de dispositivos y seleccionar para reiniciar la consola.
9. Vuelva a iniciar la sesión en el cliente web de vSphere y compruebe si hay algún error. Lleve a cabo una exploración manual de VUM, **Inicio** > **Hosts y Clúster** y, a continuación, seleccione un centro de datos o un clúster y seleccione el **separador Gestor de actualizaciones** y, a continuación, pulse **Explorar para actualizaciones**. Si la exploración manual da lugar a un error, consulte [Restablecimiento de la base de datos de VMware Update Manager en un dispositivo de vCenter Server 6.5 (2147284)](https://kb.vmware.com/s/article/2147284).
10. Después de hacer pruebas, si tiene que hacer una copia de seguridad, revierta a la instantánea o restaure el vCenter con una copia de seguridad anterior.

## Centros enlazados por SSO

Si tiene instancias de vCenter Server primarias y secundarias, los VCSA se configuran para que estén en un único dominio de inicio de sesión único de vCenter (SSO). Cada VCSA tiene una instancia de VUM desplegada. Las propiedades de configuración que modifique se aplicarán únicamente a la instancia de VUM que especifique y no se propagarán a las demás instancias del grupo.

Puede especificar una instancia de VUM seleccionando el nombre del VCSA con el que se ha registrado la instancia de VUM desde la barra de navegación. También puede gestionar líneas bases y grupos de líneas base, así como explorar y corregir solo los objetos de inventario que gestiona el VCSA con el que se registra la instancia de VUM.

### Enlaces relacionados

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demostraciones)
