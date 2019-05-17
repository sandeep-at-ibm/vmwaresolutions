---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-18"

subcollection: vmware-solutions


---

# Despliegue de cliente y de nube
{: #vcshcx-deployment}

Una instalación de HCX mínima consiste en un único despliegue del lado del cliente y de la nube. El lado del cliente de HCX se puede instalar en cualquier versión de vSphere admitida por HCX, asumiendo que hay conectividad de red entre el lado del cliente y la nube.

## Requisitos
{: #vcshcx-deployment-req}

- HCX Manager – Recuento de CPU 4, Memoria de 12G, Disco de 60G
- CGW - Recuento de CPU 8, Memoria de 3G, Disco de 2G
- L2C - Recuento de CPU 8, Memoria de 3G, Disco de 2G
- Optimización de WAN – Recuento de CPU 8, Memoria de 14G, Disco de 100G

## Nube
{: #vcshcx-deployment-cloud}

El despliegue de HCX del lado de la nube se gestiona mediante la automatización de {{site.data.keyword.vmwaresolutions_full}}. La configuración predeterminada utiliza el grupo de puertos públicos para configurar cualquier conectividad de punto final de componentes de flota. Los componentes de flota en el lado de la nube se despliegan con sus interfaces de punto final configuradas con direcciones IP públicas, ya que son dispositivos de seguridad reforzada. Se pueden desplegar detrás del cortafuegos. No se da soporte a la conexión de los lados de cliente y de nube entre sí a través de un túnel VPN existente. Si quiere utilizar la red privada para la conectividad de puntos finales de HCX, puede solicitar HCX del lado de la nube para el despliegue de la flota de red privada para su uso en un enlace dedicado, como MPLS.

## Cliente
{: #vcshcx-deployment-client}

El HCX del lado del cliente es desplegado por el usuario y requiere permisos a nivel de administrador para el vCenter de origen. A partir de esta escritura, el archivo OVA del gestor del lado del cliente de HCX es de aproximadamente 1,7 GB. Cuando se utiliza la consola de {{site.data.keyword.vmwaresolutions_short}} para solicitar HCX, se proporciona un URL con un enlace para descargar la versión de HCX para el lado del cliente que coincida con la versión de HCX desplegada en el lado de la nube. Este enlace se proporciona en la interfaz de usuario de HCX Manager del lado de la nube.

También se proporciona una clave de registro de un solo uso. Utilice los pasos siguientes para configurar el registro de uso.

1. Descargue el OVA de cliente de HCX (empresa) desde el enlace que se proporciona en la interfaz de usuario de HCX del lado de la nube.
    1. Inicie la sesión en la interfaz de usuario de HCX del lado de la nube utilizando la interfaz de usuario de registro de HCX proporcionada por IBM.
    2. Utilice el ID y contraseña de la nube de vCenter para iniciar sesión en la interfaz de usuario.
    3. En el separador **Administración**, seleccione **solicitar enlace de descarga** para descargar el OVA del lado del cliente. Utilice un "jump box" que sea local para el vCenter de origen en el que se despliega el OVA para completar este paso.
2. Inicie la sesión en el cliente de vSphere C++ (o cliente web con el complemento de integración de cliente en funcionamiento) e importe el OVA que utiliza el asistente de importación de vCenter.
    1. Asegúrese de que la red en la que está configurado el gestor de HCX tenga acceso tanto a la vCenter de origen como a Internet.  
    2. Especifique la clave de registro cuando se le solicite. (Utilice el cliente web si tiene la configuración de complemento de herramientas de cliente).  
3. Cierre sesión y vuelva a iniciarla en el cliente web de vCenter. Aparece el icono de selección de menú **HCX** bajo el menú de la pantalla de inicio.
4. Para los certificados autofirmados, seleccione el elemento de menú de HCX para acceder a la interfaz de usuario de complementos de HCX. Seleccione el separador **Administración**.
    1. Seleccione la importación de certificados desde URL y clave en el URL de registro del lado de la nube que proporciona la consola de {{site.data.keyword.vmwaresolutions_short}} para HCX.
    2. Seleccione **Nuevo emparejamiento de sitios** en el panel de ventana **Emparejamientos de sitios** en el separador **Panel de control**.
    3. Siga las indicaciones y proporcione el URL de registro del lado de la nube de HCX y el ID y la contraseña del administrador de vCenter del lado de la nube.
    4. Continúe con las indicaciones del asistente de registro del sitio para la configuración de los componentes de flota, incluidos Cloud Gateway, Concentrador de capa 2 y Optimizador de WAN.  

Para el lado del cliente, utilice el menú **Tareas** para supervisar el despliegue de los componentes de flota. Para el despliegue del lado de la nube, utilice el menú **Tareas** de la interfaz de usuario web de vCenter para la instancia de vCenter Server específica.

Si se produce un error de despliegue en cualquiera de los dos lados, los despliegues de componentes de flota se restituyen y se suprimen. Tras determinar la causa del error, pulse el separador **Interconexión** en la interfaz de usuario web de HCX vCenter del lado del cliente y, a continuación, seleccione **Instalar componentes de HCX** en la parte superior de la pantalla.

Una vez que el despliegue de los componentes de flota se completa correctamente y transcurridos varios minutos, el estado del túnel para los componentes de CGW y L2C se visualiza como **Activo** en el separador **Interconexión**.

## Enlaces relacionados
{: #vcshcx-deployment-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
