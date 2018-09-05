---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-02"

---

# Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)

Para desplegar una plataforma virtualizada VMware flexible y personalizable que se adapte perfectamente a sus necesidades de carga de trabajo, solicite una instancia de VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity). El pedido de la instancia de vCenter Server con el paquete híbrido (Hybridity) incluye la licencia de VMware Hybrid Cloud Extension (HCX) y le autoriza al servicio de VMware HCX on {{site.data.keyword.cloud_notm}}. También puede añadir servicios, como [Zerto on {{site.data.keyword.cloud_notm}}](../services/addingzertodr.html), para la recuperación tras desastre.

## Requisitos

Asegúrese de haber realizado las tareas siguientes:
*  Ha configurado las credenciales de la infraestructura de {{site.data.keyword.cloud_notm}} en la página **Configuración**. Para obtener más información, consulte [Gestión de cuentas y valores de usuario](../vmonic/useraccount.html).
*  Ha revisado la información de [Requisitos y planificación para vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_planning.html).
* Ha revisado el formato del nombre de dominio e instancia. El nombre de dominio y la etiqueta de subdominio se utilizan para generar el nombre de usuario y los nombres de servidor de la instancia.

Tabla 1. Formato del valor de nombres de instancia y de dominio

| Nombre        | Formato del valor      |
  |:------------- |:------------- |
  | Nombre de dominio | `<root_domain>` |  
  | Nombre usuario inicio sesión vCenter Server | `<user_id>@<root_domain>` (usuario de Microsoft Active Directory) o `administrator@vsphere.local` |
  | FQDN de vCenter Server | `vcenter.<subdomain_label>.<root_domain>`. La longitud máxima es de 50 caracteres. |
  | Nombre sitio inicio sesión único (SSO) | `<subdomain_label>` |
  | Nombre completo de servidor ESXi | `<host_prefix><n>.<subdomain_label>.<root_domain>`, donde `<n>` es la secuencia del servidor ESXi. La longitud máxima es de 50 caracteres. |  
  | PSC FQDN | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. La longitud máxima es de 50 caracteres. |

**Importante:** no modifique ningún valor definido durante la solicitud y el despliegue de la instancia. Si lo hace, la instancia podría quedar inutilizable. Por ejemplo, el sistema de red pública se podría cerrar, los servidores e instancias de servidor virtual (VSI) podrían moverse detrás de una disposición media de Vyatta o la VSI de IBM CloudBuilder podría detenerse o suprimirse.

## Valores del sistema

Debe especificar los siguientes valores de sistema cuando solicite una instancia de vCenter Server con el paquete híbrido (Hybridity).

### Nombre de instancia

El nombre de instancia debe cumplir los siguientes requisitos:
* Solo se permiten caracteres alfanuméricos y el guión (-).
* El nombre de instancia debe empezar y terminar por un carácter alfanumérico.
* La longitud máxima del nombre de instancia es de 10 caracteres.
* El nombre de instancia debe ser exclusivo dentro de su cuenta.

### Primaria o secundaria

Seleccione si desea solicitar una nueva instancia primaria o una instancia secundaria para una instancia primaria existente.

## Valores de licencia

Las licencias siguientes se incluyen con el pedido de instancia de vCenter Server con el paquete híbrido (Hybridity). Debe especificar **Advanced** o **Enterprise** para la edición de licencia de NSX.

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition (Advanced o Enterprise) 6.4
* Edición de licencia de VMware vSAN 6.6 (Advanced o Enterprise).

**Atención:**
* Las instancias de vCenter Server con el paquete híbrido (Hybridity) no admiten la opción de traer su propia licencia.
* Las ediciones de licencia mínimas se indican en la interfaz de usuario. Si se da soporte a distintas ediciones de componentes, puede seleccionar la edición que desee.

## Valores de Servidor nativo

Los valores de Nativo dependen de la configuración personalizada y de {{site.data.keyword.CloudDataCent_notm}}.

Se necesitan cuatro servidores ESXi para el clúster inicial y los clústeres posteriores al despliegue para las configuraciones de vSAN. Todos los servidores ESXi comparten la misma configuración. Después del despliegue, puede añadir cuatro clústeres más.

### Ubicación del centro de datos

Seleccione el {{site.data.keyword.CloudDataCent_notm}} en el que se alojará la instancia.

### Personalizado

Especifique el modelo de CPU y la cantidad de RAM del servidor nativo personalizado.

Tabla 2. Opciones para {{site.data.keyword.baremetal_short}} personalizado

| Opciones de modelo de CPU        | Opciones de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 núcleos en total, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 núcleos en total, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 núcleos en total, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Silver 4110 / 16 núcleos en total, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Procesador Dual Intel Xeon Gold 5120 / 28 núcleos en total, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon Gold Procesador 6140 / 36 núcleos en total, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
### Número de servidores nativos

De forma predeterminada, se seleccionan cuatro servidores ESXi, y esto no se puede cambiar.

## Valores de almacenamiento

Se incluye VMware vSAN 6.6 en el pedido de la instancia de vCenter Server con el paquete híbrido (Hybridity). Debe especificar los siguientes valores de almacenamiento cuando solicite la instancia:

* **Tipo y tamaño de disco para discos de capacidad vSAN**: seleccione la capacidad que se ajuste a sus requisitos de almacenamiento compartido.
* **Número de discos de capacidad vSAN**: seleccione el número de discos para el almacenamiento compartido vSAN que desea añadir. Las cantidades de disco deben ser 2, 4, 6 u 8.

## Valores de interfaz de red

Debe especificar los siguientes valores de interfaz de red cuando solicite una instancia de vCenter Server con el paquete híbrido (Hybridity).

### Prefijo de nombre de host

  El prefijo del nombre de host debe cumplir los siguientes requisitos:
  *  Solo se permiten caracteres alfanuméricos y el guión (-).
  *  El prefijo de nombre de host debe empezar y terminar por un carácter alfanumérico.
  *  La longitud máxima del prefijo de nombre de host es de 10 caracteres.

### Etiqueta de subdominio

La etiqueta de subdominio debe cumplir los siguientes requisitos:
*  Solo se permiten caracteres alfanuméricos y el guión (-).
*  La etiqueta de subdominio debe empezar y terminar por un carácter alfanumérico.
*  La longitud máxima de la etiqueta de subdominio es de 10 caracteres.
*  La etiqueta de subdominio debe ser exclusiva dentro de su cuenta.

### Nombre de dominio

El nombre del dominio raíz debe cumplir los siguientes requisitos:
* El nombre de dominio debe constar de dos o más series de caracteres separadas por un punto (.)
* La primera serie debe comenzar por un carácter alfabético y terminar por un carácter alfanumérico.
* Todas las series, excepto la última, solo pueden contener caracteres alfanuméricos y caracteres de guión (-).
* La última serie solo puede contener caracteres alfabéticos.
* La longitud de la última serie debe estar comprendida entre 2 y 24 caracteres.

**Nota:** la longitud máxima del FQDN (nombre de dominio completo) para hosts y máquinas virtuales (VM) es de 50 caracteres. Los nombres de dominio deben cumplir con esta longitud máxima.

### Realizar pedido de nuevas VLAN

Seleccione **Realizar pedido de nuevas VLAN** para solicitar una VLAN pública nueva y dos VLAN privadas nuevas.

Se necesita una VLAN pública y dos VLAN privadas para el pedido de la instancia. Las dos VLAN privadas se conectan en modalidad troncal en cada servidor nativo.

### Seleccionar las VLAN existentes

En función del {{site.data.keyword.CloudDataCent_notm}} que haya seleccionado, puede que haya VLAN públicas y privadas existentes disponibles.

Se necesita una VLAN pública y dos VLAN privadas para el pedido de la instancia. Las dos VLAN privadas se conectan en modalidad troncal en cada servidor nativo.

Seleccione **Seleccionar las VLAN existentes** para reutilizar las VLAN públicas y privadas existentes y elegir entre las VLAN y las subredes disponibles.

**Importante:**
* Asegúrese de que la configuración del cortafuegos en las VLAN seleccionadas no bloquee el tráfico de datos de gestión.
* Asegúrese de que todas las VLAN que seleccione estén en el mismo pod, porque no se pueden suministrar servidores ESXi en VLAN en pods mixtos.

### Configuración DNS

Seleccione la configuración de DNS (sistema de nombres de dominio) para la instancia:

* **Una sola VSI pública de Windows para Active Directory/DNS**: Se despliega y se puede consultar una sola VSI de Microsoft Windows Server para Microsoft Active Directory (AD), que funciona como DNS para la instancia en la que se han registrado los hosts y VM.
* **Dos VM dedicadas y altamente disponibles de Windows Server en el clúster de gestión**: Se despliegan dos VM Microsoft Windows, que ayudan a mejorar la seguridad y la solidez.

**Importante:** Debe proporcionar dos licencias de Microsoft Windows Server 2012 R2 si configura la instancia de modo que utilice las dos VM Microsoft Windows. Utilice la licencia de Microsoft Windows Server 2012 R2 Standard Edition, o la licencia de Microsoft Windows Server 2012 R2 Datacenter Edition, o ambas.

Cada licencia solo se puede asignar a un solo servidor físico y cubre un máximo de dos procesadores físicos. Una licencia de Standard Edition puede ejecutar dos VM Microsoft Windows virtualizadas por servidor de 2 procesadores. Por lo tanto, se necesitan dos licencias, ya que se despliegan dos VM Microsoft Windows en dos hosts distintos.

Tiene 30 días para activar las VM.

Para obtener más información sobre cómo solicitar licencias de Windows, consulte la [documentación de Windows Server 2012 R2](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Valores de servicios

Cuando solicite una instancia de vCenter Server con el paquete híbrido (Hybridity), también puede solicitar servicios adicionales. Para obtener más información sobre los servicios, consulte [Servicios disponibles para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingremovingservices.html#available-services-for-vcenter-server-with-hybridity-bundle-instances).

## Resumen del pedido

En función de la configuración seleccionada para la instancia y los servicios de complementos, el coste estimado se genera y se muestra al instante en la sección **Resumen de pedido** en el panel derecho. Pulse **Detalles sobre precios** en la parte inferior del panel derecho para generar un documento PDF que proporcione la información estimada.

## Procedimiento

1. Desde el catálogo de {{site.data.keyword.cloud_notm}}, pulse **VMware** en el panel de navegación izquierdo y pulse **vCenter Server** en la sección **Centros de datos virtuales**.
2. En la página **VMware vCenter Server on IBM Cloud**, pulse la tarjeta **vCenter Server con el paquete híbrido (Hybridity)** y pulse **Crear**.
3. En la página **vCenter Server**, escriba el nombre de la instancia.
4. Seleccione el tipo de instancia:
   * Pulse **Instancia primaria** para desplegar una sola instancia en el entorno o para desplegar la primera instancia en una topología de varios sitios.
   * Pulse **Instancia secundaria** para conectar la instancia con una instancia existente (primaria) en el entorno para conseguir alta disponibilidad y siga estos pasos:
     1. Seleccione la instancia primaria a la que desea conectar la instancia secundaria.
     2. Especifique la contraseña de administrador PSC de la instancia primaria.
5. Seleccione la edición de licencia de NSX y la edición de licencia de vSAN.
6. Complete los valores del servidor nativo.
  1. Seleccione el {{site.data.keyword.CloudDataCent_notm}} que va a alojar la instancia.
  2. Seleccione el modelo de CPU **Personalizado** y la cantidad de **RAM**.

  **Nota:** el **Número de servidores nativos** se establece en cuatro de forma predeterminada y no se puede cambiar.

7. Complete la configuración del almacenamiento.
  1. Seleccione el **Tipo y tamaño de disco para discos de capacidad vSAN**.
  2. Seleccione el **Número de discos de capacidad vSAN**.
8. Complete la configuración de interfaz de red.
  1. Especifique el prefijo de nombre de host, la etiqueta de subdominio y el nombre de dominio raíz.
  2. Seleccione la configuración de VLAN.
     *  Si desea solicitar nuevas VLAN públicas y privadas, pulse **Realizar pedido de nuevas VLAN**.
     *  Si desea reutilizar las VLAN públicas y privadas existentes cuando estén disponibles, pulse **Seleccionar las VLAN existentes** y luego seleccione la VLAN pública, la subred primaria, la VLAN privada, la subred primaria privada y la VLAN privada secundaria.
  3. Seleccione la configuración de DNS.
9. Seleccione los servicios complementarios que desea desplegar en la instancia pulsando la tarjeta del servicio correspondiente. Si un servicio requiere configuración, complete los valores específicos del servicio y pulse **Añadir servicio** en la tarjeta.  
Para obtener información sobre cómo proporcionar valores para un servicio, consulte el tema de solicitud de servicio correspondiente.

8. En el panel **Resumen del pedido**, verifique la configuración de la instancia antes de realizar el pedido.
   1. Revise los valores de la instancia.
   2. Revise el coste estimado de la instancia. Pulse **Detalles sobre precios** para generar un resumen en PDF. Para guardar o imprimir el resumen del pedido, pulse el icono **Imprimir** o **Descargar** en la parte superior derecha de la ventana del PDF.
   3. Pulse el enlace o enlaces de los términos que se aplican a su pedido y confirme que acepta estos términos antes de solicitar la instancia.
   4. Pulse **Suministro**.

## Resultados

El despliegue de la instancia comienza automáticamente. Recibirá una confirmación de que el pedido se está procesando y puede comprobar el estado del despliegue consultando los detalles de la instancia.

Cuando la instancia se haya desplegado correctamente, los componentes que se describen en [Especificaciones técnicas para las instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_overview.html#technical-specifications-for-vcenter-server-with-hybridity-bundle-instances) se instalan en la plataforma virtual de VMware. Los servidores ESXi que ha solicitado se agrupan de forma predeterminada como **cluster1**. Si ha solicitado servicios adicionales, el despliegue de los servicios se inicia después de que se haya completado el pedido.

Cuando la instancia esté lista para ser utilizada, el estado de la instancia pasará a ser **Listo para su uso** y recibirá una notificación por correo electrónico.

Cuando se solicita una instancia secundaria, es posible que el cliente web de VMware vSphere para la instancia primaria (enlazada a la secundaria) se rearranque cuando finalice el pedido de la instancia secundaria.

## Qué hacer a continuación

Puede ver y gestionar la instancia de vCenter Server con el paquete híbrido (Hybridity) que ha solicitado.

**Importante**: solo debe gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}} que se crean en la cuenta de {{site.data.keyword.cloud_notm}} desde la consola de {{site.data.keyword.vmwaresolutions_short}}, no desde el {{site.data.keyword.slportal}} ni mediante ningún otro método fuera de la consola.
Si cambia estos componentes fuera de la consola de {{site.data.keyword.vmwaresolutions_short}}, los cambios no se sincronizan con la consola.

**ATENCIÓN:**: el hecho de gestionar los componentes de {{site.data.keyword.vmwaresolutions_short}} (que se instalaron en la cuenta de {{site.data.keyword.cloud_notm}} al solicitar la instancia) desde fuera de la consola de {{site.data.keyword.vmwaresolutions_short}} podría hacer que el entorno quedara inestable. Estas actividades de gestión incluyen:
*  Añadir, modificar, devolver o eliminar componentes
*  Ampliar o reducir la capacidad de la instancia mediante la adición o eliminación de servidores ESXi
*  Apagar componentes
*  Rearrancar servicios

   Las excepciones a estas actividades incluyen la gestión de comparticiones del archivo de almacenamiento compartido desde el {{site.data.keyword.slportal}}. Estas actividades incluyen: solicitar, suprimir (lo que puede afectar los almacenes de datos si están montados), autorizar y montar comparticiones del archivo de almacenamiento compartido.

### Enlaces relacionados

* [Registro de una cuenta de {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Visualización de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_viewinginstances.html)
* [Configuración de varios sitios para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_multisite.html)
* [Adición y visualización de clústeres correspondientes a instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingviewingclusters.html)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingremovingservers.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingremovingservices.html)
* [Supresión de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_deletinginstance.html)
