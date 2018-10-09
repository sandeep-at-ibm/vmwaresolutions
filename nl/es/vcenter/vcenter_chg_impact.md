---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Consideraciones sobre el cambio de artefactos de vCenter Server

El cambio de usuarios, recursos o subredes reservados para {{site.data.keyword.vmwaresolutions_full}} puede afectar a las operaciones de gestión.

**Importante:** No edite los permisos globales del grupo **ic4v-vCenter** en la página **Usuarios y grupos** del cliente web de VMware vSphere. Estos cambios incluyen: cambiar el nombre de usuario, suprimir el usuario o cambiar su contraseña.

## ID de automatización

El ID de **automatización** es una cuenta de usuario que utilizan las operaciones automáticas que se proporcionan en la consola de {{site.data.keyword.vmwaresolutions_short}}.

Los usuarios y las contraseñas correspondientes a las operaciones automáticas de la consola no se deben modificar porque las operaciones de la consola que dependen de estas credenciales podrían fallar.

## Cuentas de usuario específicas de servicio

Cada servicio crea una cuenta de usuario interna en vCenter Server. Esta cuenta es necesaria para que las operaciones de gestión que están asociadas a un servicio se puedan conectar con vCenter Server para realizar las operaciones en el servicio.

**Importante**: Para evitar interrupciones y problemas de conexión, si cambia el ID de usuario, la contraseña o los valores de caducidad de contraseña de esta cuenta de usuario, asegúrese de actualizar también la información en el servicio asociado.

El ID de usuario de esta cuenta está en el formato `<service_name>-<truncated service_uuid>@test.local` o `<service_name>-<truncated service_uuid>@example-domain.local`. Por ejemplo, el ID de usuario que utiliza el servicio Veeam on {{site.data.keyword.cloud_notm}} para conectarse a vCenter Server para realizar copias de seguridad planificadas es `Veeam-<Veeam_uuid>@test.local`.

**Nota**: `<service_name>` junto con `<service_uuid>` se trunca a 20 caracteres.

## Recursos de VMware para instancias de vCenter Server (V1.9 y posteriores)

Para las instancias desplegadas en V1.9 y posteriores, si la instancia de vCenter Server está en el estado **Listo para su uso**, puede modificar los nombres del centro de datos virtual de VMware, del clúster, de los conmutadores, de los grupos de puertos y de los almacenes de datos del cliente desde el cliente web de VMware vSphere. Sin embargo, no debe modificar el valor predeterminado del nombre del almacén de datos de gestión: **vsanDatastore** para las instancias de vSAN y **management-share** para las instancias de Network File System (NFS).

## Recursos de VMware para instancias de vCenter Server (V1.8 y anteriores)

En la tabla siguiente se muestran las operaciones que podrían verse afectadas si cambia el administrador de SSO cambia los recursos de VMware vCenter Server fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}. Si se dispone de una solución de recuperación, también se muestra.

Esta tabla es aplicable a las instancias desplegadas en V1.8 y anterior, además de las instancias desplegadas en V1.8 y anterior y luego actualizadas a V1.9 o posterior.

Tabla 1. Operaciones que se ven afectadas por el cambio de recursos de VMware

| Cambio intentado  | Operaciones afectadas  | Gravedad  | Método recuperación  |
|:------------- |:------------- |:--------------|:--------------|
| Cambiar el nombre del centro de datos virtual de VMware. | La adición de un centro de datos virtual de VMware puede fallar porque el nuevo servidor ESXi no se puede unir al centro de datos virtual modificado. | Importante | Vuelva a cambiar el nombre del centro de datos virtual de VMware por el nombre original. |
| Cambiar cualquier nombre de grupo de puertos.    | La adición de un servidor ESXi puede fallar. | Importante | Vuelva a cambiar el nombre del grupo de puertos por el nombre original. |
| Cambiar el nombre de clúster. | La adición de un servidor ESXi puede fallar. | Importante | Vuelva a cambiar el nombre del clúster por el nombre original.
| Cambiar el nombre del conmutador virtual distribuido (DVS) público o privado. | La adición de un servidor ESXi puede fallar. | Importante | Cambie el nombre del conmutador virtual distribuido (DVS) público o privado por el nombre original.
| Cambie el nombre del almacén de datos de vSAN en la instancia que utiliza vSAN. | La adición de un servidor ESXi puede fallar.<br><br>La actualización de la instancia puede fallar. | Importante | Vuelva a cambiar el nombre del almacén de datos de vSAN por el nombre original, **vsanDatastore**.
| Cambie el nombre del almacén de datos de NFS de gestión en la instancia que utiliza NFS. | La adición de un servidor ESXi puede fallar.<br><br>La actualización de la instancia puede fallar. | Importante | Vuelva a cambiar el nombre del almacén de datos de NFS por el nombre original, **management-share**, y vuelva a montar el almacén de datos de NFS como de solo lectura en el servidor ESXi.

En la tabla siguiente se muestran las operaciones que podrían verse afectadas si el usuario root de VC/PSC cambia recursos de vCenter Server fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}.

Tabla 2. Operaciones que se ven afectadas para el acceso raíz de VC/PSC (local)

| Cambio intentado  | Operaciones afectadas  | Gravedad  | Método recuperación  |
|:------------- |:------------- |:--------------|:--------------|
| Habilitar o inhabilitar el acceso de shell.    | La aplicación de parches y la actualización correspondiente a PSC y vCenter Server podría fallar.    | Importante    | N/D    |

## Subredes de gestión para instancias de vCenter Server

En la siguiente información se describen las subredes solicitadas por {{site.data.keyword.vmwaresolutions_short}} y se muestran opciones para que pueda solicitar subredes adicionales para su propio uso.

**ATENCIÓN**: no utilice estos componentes para otros fines o la estabilidad del entorno se verá seriamente comprometida.

Con cada pedido de servidor nativo de {{site.data.keyword.cloud_notm}}, se solicitan de forma predeterminada los siguientes rangos de direcciones IP:
*  Un rango público primario de 32 direcciones IP
*  Un rango privado primario de 64 direcciones IP

Además, las siguientes subredes de gestión también están reservadas para {{site.data.keyword.vmwaresolutions_short}}:
*  Dos subredes privadas portátiles de 64 direcciones IP en la primera VLAN: uno para la gestión y la otra para VTEPS
*  Dos subredes privadas portátiles de 64 direcciones IP en la segunda VLAN: uno para VMotion y una para vSAN
*  Una subred pública portátil de 16 direcciones IP en la VLAN pública

Si necesita utilizar más subredes, puede obtener las direcciones IP que puede utilizar de una de las siguientes formas:
*  **Opción 1 (recomendada)**: utilice superposiciones de red virtual VMware NSX. Se proporciona una plantilla de VXLAN de muestra cuando se realiza el pedido. Esta VXLAN se puede utilizar como punto de partida para crear sistemas de redes definidos por software (SDN). Para obtener más información, consulte [Configuración de la red para que utilice la NSX Edge gestionado por el cliente](vc_esg_config.html).
*  **Opción 2**: solicite sus propias redes públicas o privadas portátiles para obtener direcciones IP. Para distinguir las subredes que solicita de las subredes de gestión, puede añadir notas a todas las subredes que solicite.
