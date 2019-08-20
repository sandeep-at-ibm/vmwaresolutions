---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-09"

subcollection: vmware-solutions


---

# Despliegue del cliente de HCX
{: #hcxclient-vcs-client-deployment}

Una instalación de HCX mínima consiste en un único despliegue del lado del cliente y de la nube.

El lado del cliente de HCX se puede instalar en cualquier versión de vSphere admitida por HCX, asumiendo que hay conectividad de red entre el lado del cliente y la nube.

## Requisitos
{: #hcxclient-vcs-client-deployment-req}

| Componente | Recuento de CPU | Memoria (GB) | Disco (GB) |
|--------|--------|---------|-------|
| HCX Manager | 4 | 12G |  60G |
| HCX Interconnect (HCX-IX) | 4 | 3G |  2G |
| HCX Network Extension (HCX-NE) | 4 | 3G |  2G |
| HCX WAN Optimizer (HCX-WAN) | 8 | 14G |  100G |

## Licencias de cliente
{: #hcxclient-vcs-client-deployment-licensing}

HCX es un servicio. HCX se ofrece con licencia por sitio y por máquina virtual (VM) gestionada a través de servidores de licencia mantenidos por VMware. Las instancias del lado del cliente y la nube de HCX requieren comunicación con el sitio de registro de VMware durante todo su ciclo de vida.
- El tráfico de 80 y 443 debe estar permitido en `https://connect.hybridity.vmware.com`
- La consola de {{site.data.keyword.vmwaresolutions_full}} proporciona una clave de registro de un solo uso para la instalación del lado del cliente. Se necesita una clave para cada instalación de HCX del lado del cliente.

### Procedimiento de solicitud de licencias de HCX para instalaciones locales
{: #hcxclient-vcs-client-deployment-license-ordering-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. Desplácese a la tabla **Licencias locales de HCX** y pulse **Suministrar nuevo**.
3. Especifique el nombre de licencia.
4. Pulse el enlace o enlaces de los términos que se aplican a su pedido y asegúrese de que acepta estos términos antes de solicitar la licencia.
5. Pulse **Suministro**.

## Requisitos de las direcciones IP
{: #hcxclient-vcs-client-deployment-client-ip-reqs}

Para desplegar HCX, se debe disponer del número adecuado de direcciones IP tanto en el entorno local como en IBM Cloud de destino.

* Dirección de vMotion
  Resulta habitual mantener una red separada para vMotion en el centro de datos local. La pasarela de nube debe tener acceso a la red de vMotion. Si no es así, se necesita una dirección IP adicional para comunicarse con la red de vMotion.

* Local
  * Una dirección IP para el dispositivo HCX Manager.
  * Una para cada InterConnect Appliance, más una si hay una red de vMotion separada.
  * Uno para cada extensión de red estándar

* IBM Cloud
  * Dos direcciones IP por dispositivo de HCX Manager conectadas a IBM Cloud. Las direcciones se pueden utilizar para conectarse a Internet o a una o más líneas de Direct Connect.
  * Una más una si hay una conexión de red de vMotion separada.

## Descarga OVA del lado del cliente
{: #hcxclient-vcs-client-deployment-client-ova}

El HCX del lado del cliente es desplegado por el usuario y requiere permisos a nivel de administrador para el vCenter de origen. A partir de esta escritura, el archivo OVA del gestor del lado del cliente de HCX es de aproximadamente 1,7 GB. Cuando se utiliza la consola de {{site.data.keyword.vmwaresolutions_short}} para solicitar HCX, se proporciona un URL con un enlace para descargar la versión de HCX para el lado del cliente que coincida con la versión de HCX desplegada en el lado de la nube. Este enlace se proporciona en la interfaz de usuario de HCX Manager del lado de la nube.

También se proporciona una clave de registro de un solo uso. Utilice los pasos siguientes para configurar el registro de uso.

1. Descargue el OVA de cliente de HCX (empresa) desde el enlace que se proporciona en la interfaz de usuario de HCX del lado de la nube.
    1. Inicie la sesión en la interfaz de usuario de HCX del lado de la nube utilizando la interfaz de usuario de registro de HCX proporcionada por IBM.
    2. Utilice el ID y contraseña de la nube de vCenter para iniciar sesión en la interfaz de usuario.
    3. En el separador **Administración**, seleccione **solicitar enlace de descarga** para descargar el OVA del lado del cliente. Utilice un "jump box" que sea local para el vCenter de origen en el que se despliega el OVA para completar este paso.

## Instalación y configuración de HCX en el origen
{: #hcxclient-vcs-client-deployment-install-cfg-src}

La instalación local implica desplegar el dispositivo de gestión de HCX y registrarlo con el entorno de vCenter.

### Instalación del dispositivo HCX Manager
{: #hcxclient-vcs-client-deployment-install-cfg-src-install-hma}

Instale el dispositivo HCX Manager en el vCenter local.
1. Inicie la sesión en **Mi VMware** y descargue el archivo OVA de Hybrid Cloud Services desde la página de descargas del producto.
2. Abra un navegador e inicie una sesión en el cliente web de vSphere. Visualice el separador **Inicio**.
3. En la lista **Árboles de inventario**, pulse **Host y clústeres**.
4. Expanda la jerarquía para mostrar los centros de datos.
5. Pulse con el botón derecho del ratón en el centro de datos de destino y seleccione **Desplegar plantilla de OVF** en el menú. Es posible que el elemento de menú **Desplegar plantilla de OVF** tarde unos segundos en aparecer.
6. Seleccione **Desplegar plantilla de OVF**.
  1. Seleccione **Archivo local** y pulse **Examinar** para encontrar el archivo OVA descargado en el sistema. Pulse **Siguiente**.
  2. En la página **Revisar detalles**, marque el recuadro **Aceptar opciones de configuración adicionales** y pulse **Siguiente**.
  3. En la página **Aceptar EULA**, desplácese hacia abajo para revisar el acuerdo de licencia de usuario de VMware. Pulse **Aceptar** y **Siguiente**.
  4. En la página **Seleccionar nombre y carpeta**, edite el nombre si es necesario y seleccione la ubicación de Hybrid Cloud Services. Pulse **Siguiente**.
  5. En la página **Seleccionar un recurso**, seleccione la ubicación de instalación.
  6. En la página **Seleccionar almacenamiento**, seleccione el almacenamiento para Hybrid Cloud Services y pulse **Siguiente**. En la lista **Seleccionar formato de disco virtual**, puede seleccionar **suministro ligero** o **suministro grueso**.
  7. En la página **Configuración de redes**, correlacione el adaptador de Hybrid Cloud Services con una red de host seleccionada en la lista **Destino**.
7. En la página **Plantilla personalizada**, escriba los valores específicos del entorno:
  * Para las contraseñas, el nombre de usuario predeterminado tanto para la interfaz de línea de mandatos (CLI) como para la interfaz de usuario web es **admin**. Se necesita el usuario y la contraseña **admin** para iniciar una sesión en la interfaz de usuario web y se necesita una cuenta de usuario **root** que tenga una contraseña que se pueda establecer.
  * Escriba y vuelva a escribir la contraseña de usuario de CLI **admin**.
  * Escriba y vuelva a escribir la contraseña de usuario **root**. En el futuro, si se necesita ayuda de VMware Global Support Services (GSS), es posible que se tenga que compartir esta contraseña para que se pueda resolver el problema del sistema.
  * Para las propiedades de red, especifique el nombre de host para la VM de HCX Manager. Escriba la dirección IPv4 de red, el prefijo IPv4 (el CIDR) y la pasarela predeterminada. En la tabla siguiente se muestran valores de ejemplo:

Tabla 1. Valores de ejemplo para propiedades de red

| Campo                    | Valor           |
|--------------------------|-----------------|
| Nombre de host                 | HCM_1           |
| Dirección IPv4 de red 1   | 192.168.200.101 |
| Prefijo IPv4 de red 1    | 24              |
| Pasarela IPv4 predeterminada     | 192.168.200.1   |
| Dirección IPv6 de red 1   |                 |
| Prefijo IPv6 de red 1    |                 |

8. Revise la página de enlaces de vService. Pulse **Siguiente** para
continuar.
9. En la página **Preparado para completar**, siga estos pasos:
  * Marque el recuadro **Encender tras despliegue**.
  * Revise los valores de Hybrid Cloud Services y pulse **Finalizar**. El dispositivo Hybrid Cloud Services puede tardar varios minutos en encenderse.
  * Para comprobar el estado, vaya a la página de inicio de vSphere Web Client y, en el separador **Inicio**, vaya a **Inventarios** y pulse **Hosts y clústeres**. Amplíe la jerarquía del centro de datos y pulse la máquina virtual de servicio de Hybrid Cloud Services para visualizar un resumen en el panel central.
  * Examine el separador **Resumen**; la consola muestra **Encendido** y el icono **Reproducir** está en verde.
10. HCX Manager está encendido y listo para que se registre con vCenter en instalación local.

## Configuración inicial del dispositivo HCX Manager
{: #hcxclient-vcs-client-deployment-inital-config}

1. Asegúrese de que el dispositivo virtual Hybrid Cloud Service tiene acceso de salida a
`https://connect.hcx.vmware.com`
2. Inicie la sesión en la interfaz de administración de dispositivos virtuales Hybrid Cloud Services `https://<IP>:9443` con **admin**
3. Proporcione la clave de licencia recopilada en los requisitos previos del lado del cliente.
4. Ubicación del centro de datos de HCX Cloud
    - Especifique la ciudad más cercana al centro de datos donde reside la instancia de HCX Cloud. Si la ciudad no está presente, seleccione la ciudad principal más cercana.
5. Proporcione el nombre del sistema

## Importar certificado de servidor de vSphere
{: #hcxclient-vcs-client-deployment-import-cert}

1. Inicie la sesión en la interfaz de administración de HCX Manager `https://<IP>:9443`
2. Seleccione el separador **Administración**, bajo **Certificado** -> **Certificado CA de confianza**
3. Importar sitio web del servidor de vSphere
   1. Seleccione la importación de certificados desde URL y clave en el URL de registro del lado de la nube HCX.
     * Sao Paulo: `https://ssao01dirhcx01.vmware-solutions.cloud.ibm.com`

## Procedimiento para registrar HCX Manager con vCenter/SSO/NSX
{: #hcxclient-vcs-client-deployment-reg-vcenter}

1. Inicie la sesión en el dispositivo virtual de servicio de Hybrid Cloud Services.
2. En el panel **Panel de control**, complete los pasos siguientes:
  1. En el panel izquierdo, en **Configurar sistemas**, seleccione vCenter.
  2. Pulse **Añadir vCenter** en la parte superior derecha.
  3. Escriba la dirección IP de vCenter Server en el formato `https://vCenter-host-name` o `https://vCenter-IP-address`. Por ejemplo, `https://My-vCenter` o `https://10.108.26.211`
  4. Escriba el nombre de usuario y la contraseña de vCenter Server. La cuenta que se utilice debe tener el rol de administrador de vCenter.
  5. Pulse **Aceptar**. No se reinicie cuando aparezca el mensaje _Se tiene que reiniciar la app_.
3. Configure el servicio de SSO/búsqueda.
  6. Pulse el separador **Gestionar**.
  7. Pulse **Editar** junto al cuadro de texto **URL del servicio de
búsqueda**.
  8. Especifique el punto final de servicio de red de búsqueda en el formato siguiente:
    * Para vCenter Server 6.5 `https://psc/`
  9.  Proporcione los detalles de NSX si es necesario.
  10. Pulse **Aceptar**. No reinicie cuando aparezca un mensaje para reiniciar el motor web.
4. Pulse el separador **Resumen** y busque la sección **Componentes de gestión de Hybridity**. Detenga e inicie tanto el motor de aplicaciones y el motor web.
5. Para finalizar el registro, finalice la sesión en el cliente web de vSphere. Vuelva a iniciar la sesión en el cliente web de vSphere para verificar que el separador HCX esté presente.

## Resultados
{: #hcxclient-vcs-client-deployment-reg-vcenter-results}

Observe el icono **Nube híbrida** existente y el elemento de menú **Hybrid Cloud Services** de la izquierda. El registro de Hybrid Cloud Services actualiza estas etiquetas. En el inventario, la etiqueta de icono pasa a ser **Hybrid Cloud Services**.

## Enlaces relacionados
{: #hcxclient-vcs-client-deployment-related}

* [Glosario de componentes y términos de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparación del entorno de instalación](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Malla de servicio en instalaciones locales de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migraciones de VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Supervisión de parámetros y componentes](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Resolución de problemas de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
