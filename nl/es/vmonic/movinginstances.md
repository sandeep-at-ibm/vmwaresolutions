---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# Actualización de instancias de releases anteriores a V1.4

## Problema

La topología de la red de las instancias de V1.4 y releases posteriores es distinta de la de los releases anteriores a V1.4. Debido a este cambio, las instancias que se han desplegado en releases anteriores a V1.4 no se pueden utilizar en su estado en el release actual.

## Solución

En V1.4 y releases posteriores, dispone de diversas mejoras en la topología de red para sus instancias:
* (Se aplica a todas las instancias): configuración de red optimizada. Puesto que la cuenta de {{site.data.keyword.cloud}} que utiliza debe ser una cuenta VRF (direccionamiento y reenvío virtual) o debe tener habilitada la expansión de VLAN si es una cuenta clásica (no VRF), no se necesita una segunda dirección IP portátil. Para el despliegue solo se necesita la dirección IP portátil de la infraestructura {{site.data.keyword.cloud_notm}} primaria.
* (Solo se aplica a instancias de Cloud Foundation): capacidad de despliegue de varios sitios con Windows AD SSO (inicio de sesión único de Active Directory) y servidor del Sistema de nombres de dominio (DNS).

Si no ha migrado o suprimido sus instancias de releases anteriores a V1.4, aún podrían estar visibles en la consola de {{site.data.keyword.vmwaresolutions_short}} en modalidad de solo vista. Estas instancias están marcadas en la interfaz de usuario como **En desuso** con un icono con un símbolo de aviso.

**Nota**: la información que se muestra en las propiedades de la instancia refleja los datos en la fecha del release V1.4 y ya no se renueva.

Dispone de las siguientes acciones en las instancias anteriores a V1.4:
*  Ver la información en la página de detalles de la instancia.
*  Ver información de copia de seguridad de la instancia.
*  Abrir el cliente web de vSphere y utilizar la instancia en vCenter.
*  Solicitar la restauración de la instancia abriendo una incidencia de soporte de {{site.data.keyword.cloud_notm}}.
*  Suprimir la instancia.

Las demás acciones ya no están disponibles en instancias anteriores a V1.4.

Si tiene instancias anteriores a V1.4 y piensa seguir utilizándolas, puede actualizarlas creando nuevas instancias y luego pasando las configuraciones existentes a estas nuevas instancias.

Para pasar las instancias anteriores a V1.4 a instancias nuevas, siga estos pasos en el cliente web de vSphere:
1. En la instancia anterior a V1.4, exporte todas las VM (máquinas virtuales).
2. Cree una instancia en el release actual.
3. Importe todas las VM exportadas en el **Paso 1**.
4. Utilice la instancia nueva.

Para obtener más información sobre la exportación e importación de máquinas virtuales, consulte la documentación de VMware vSphere.

Si necesita ayuda con {{site.data.keyword.vmwaresolutions_short}}, [póngase en contacto con el equipo de soporte de IBM](trbl_support.html) a través de uno de los canales de soporte.
