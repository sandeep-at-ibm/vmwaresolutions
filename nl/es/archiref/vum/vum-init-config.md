---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-06"

subcollection: vmware-solutions


---

# Configuración inicial
{: #vum-init-config}

La automatización de {{site.data.keyword.vmwaresolutions_full}} configura el VCSA con una pasarela establecida en {{site.data.keyword.cloud}} Backend Customer Router (BCR). Sin embargo, no hay vía de acceso a Internet a través del BCR. La ruta estándar a Internet desde la instancia de VMware vCenter Server on {{site.data.keyword.cloud_notm}} se realiza a través de Management ESG. Como no se aconseja cambiar la configuración del VCSA o el ESG de gestión, se recomienda implementar el servidor proxy en la subred del cliente para habilitar VUM.

Este enfoque significa que no tiene que volver a configurar ni el VCSA ni la ESG de gestión. Sin embargo, se debe instalar una máquina virtual (VM) o un dispositivo pequeño. Un servidor proxy es un sistema, que se encuentra entre dos dispositivos de punto final y actúa como un dispositivo intermedio. En este caso, se encuentra entre el VUM y los servidores de actualización en VMware.

Cuando VUM solicita un recurso desde el servidor de actualizaciones en VMware, la solicitud se envía primero al servidor proxy y después el servidor proxy envía la solicitud al servidor de actualizaciones. Una vez que el servidor proxy ha obtenido el recurso, este lo envía a VUM. Se puede utilizar un servidor proxy para facilitar la seguridad, los controles administrativos y los servicios de almacenamiento en memoria caché.

Puede utilizar un servidor proxy basado en CentOS y Squid. Squid Proxy es un proxy de almacenamiento en memoria caché de código abierto para la web y admite muchos protocolos, incluidos HTTP y HTTPS. Dispone de varios proxies de VM y basados en dispositivos, y debe seleccionar el adecuado en función de los requisitos de la empresa y lo tiene que instalar y configurar siguiendo la guía del proveedor. Los clientes que opten por utilizar una implementación de CentOS/Squid deben continuar con el proceso siguiente.

* Descargar CentOS ISO en un servidor de saltos
* Crear una biblioteca vCenter
* Cargar la ISO a la biblioteca de vCenter
* Crear una VM, instalar y configurar CentOS e instalar Squid

## Búsqueda de la información de subred
{: #vum-init-config-subnet}

Para poder empezar esta tarea, primero debe recopilar la información para rellenar la tabla siguiente. Revise los valores sugeridos y asegúrese de que son adecuados para su entorno. Esta configuración se basa solo en un pequeño proxy para VUM que utiliza CentOS-Minimal y Squid.

Para encontrar la subred portátil privada del cliente:

1. Vaya a la página **Recursos** de la consola de {{site.data.keyword.vmwaresolutions_short}}.
2. Seleccione la **Instancia** necesaria, seleccione **Infraestructura** y, a continuación, el
**Clúster** necesario.
3. Seleccione **VLAN privada** y localice la subred etiquetada con `Private subnet for customer workload edge`.
4. Seleccione la **subred** y se le redirigirá a la página de detalles de la subred, que muestra la dirección IP y sus asignaciones.
5. Utilizando la información, seleccione una dirección IP no asignada y actualice la **Nota** con comentarios pertinentes. Utilice esta dirección IP para el parámetro
`IP de proxy` de la tabla siguiente.

Tabla 1. Valores de despliegue

| Parámetro | Valores sugeridos | Notas |
|:--------- |:-------------- |:------ |
| CPU de proxy | 1 vCPU | Squid no tiene requisitos mínimos |
| RAM de proxy | 2 GB | Squid no tiene requisitos mínimos |
| Disco de proxy | 25 | GB Squid no tiene requisitos mínimos |
| Nombre de host | Proxy01 | |
| Dirección | ip proxy | Se debe utilizar una dirección IP de repuesto de la subred portátil privada del cliente asignada durante el proceso de suministro. Solo se reservarían dos direcciones IP en esta subred; una para el BCR y otra para el cliente-esg
| Máscara de red | 255.255.255.192 | |
| Pasarela| ip enlace ascendente privada customer-nsx-edge | Este es el valor de pasarela predeterminado para el servidor proxy, que es la dirección IP de enlace ascendente privada de customer-nsx-edge. Para encontrar la dirección IP, consulte el separador **Configuración** de **customer-nsx-edge**. |
| Servidor DNS | ip de AD/DNS | Encontrará esta dirección IP en la página de la instancia de la consola de {{site.data.keyword.vmwaresolutions_short}}, en la página **Recursos**. |
| IP de BCR | ip de bcr | Es la dirección IP del direccionador de cliente de {{site.data.keyword.cloud_notm}} Backend y es la pasarela para 10.0.0.0/8 y 161.26.0.0/16. Esta dirección se utiliza en una ruta estática en el servidor proxy para que pueda llegar a la VCSA y al servidor de AD/DNS. |

## Configuración de NSX
{: #vum-init-config-config-nsx}

Los valores de NSX Customer ESG y de NAT son necesarios para habilitar el tráfico del servidor proxy.

### Cortafuegos
{: #vum-init-config-firewall}

1. Vaya a **Inicio** > **Redes y seguridad**.
2. Seleccione **NSX Edges**, customer-nsx-edge y, a continuación, **Cortafuegos**.
3. Pulse el símbolo **+** y añada una regla de cortafuegos.
4. Proporcione los parámetros necesarios según aparece en la tabla siguiente. La nueva regla de cortafuegos debe ir antes de la última regla, la regla Denegar predeterminada.

Tabla 2. Regla de cortafuegos

| Parámetro | Valores sugeridos |
|:--------- |:-------------- |
| Nombre | Proxy01 de salida |
| Tipo | Usuario |
| Origen | ip del servidor proxy |
| Destino | cualquiera |
| Servicio | Eco HTTP/HTTPS/ICMP |
| Acción | Aceptar |

Una vez que se hayan proporcionado los parámetros, pulse **Publicar cambios**.

### NAT
{: #vum-init-config-nat}

1. Seleccione **NAT**.
2. Pulse sobre el símbolo **+** y añada una regla SNAT.
3. Proporcione los parámetros necesarios según aparece en la tabla siguiente y pulse **Aceptar**. A continuación, pulse
**Publicar cambios**.

Tabla 3. Regla NAT

| Parámetro | Valores sugeridos |
|:--------- |:-------------- |
| Tipo de regla | USER |
| Acción | SNAT |
| Aplicada en | Enlace ascendente público |
| Protocolo original | cualquiera |
| IP de origen original | ip del servidor proxy |
| Puertos de origen originales | cualquiera |
| IP de destino original | cualquiera |
| Puertos de destino originales | cualquiera |
| Dirección IP convertida | IP de NAT |
| Rango de puertos convertido | cualquiera |
| Estado | Habilitar |
| Registro | Habilitar |
| Descripción | SNAT Proxy01 |

### Instalación y configuración de un servidor proxy
{: #vum-init-config-inst-cfg-proxy}

El proceso siguiente despliega una VM para alojar CentOS y Squid desde la Biblioteca de contenido y consta de los pasos siguientes. Se da por supuesto que tiene un VSI de Windows suministrado para su uso como un salto y que utiliza el protocolo de escritorio remoto para conectarse a la interfaz pública de VSI:

* Descargue el archivo CentOS-Mínimo ISO
* Configure una biblioteca de contenido vCenter y llénela con el archivo ISO de CentOS
* Configure la VM de proxy, instale CentOS y Squid

### Descarga del archivo ISO CentOS-Minimal
{: #vum-init-config-downloading-centos}

Utilice un navegador en el servidor de saltos para descargar el archivo ISO de CentOS-Minimal de [CentOS](https://www.centos.org/download/). Tenga en cuenta que {{site.data.keyword.cloud_notm}} mantiene un duplicado de muchas distribuciones de Linux populares. Este duplicado solo está disponible en la red privada, y los ISO de CentOS están disponibles en la dirección siguiente: `http://mirrors.service.softlayer.com/centos/7/isos/x86_64/`

### Configurar una biblioteca de contenido y llenarla con el archivo ISO de CentOS
{: #vum-init-config-config-conent-library}

Cree una biblioteca de contenido de vCenter local. Solo se puede acceder a la biblioteca en la instancia de vCenter Server en la que se crea. Rellene la biblioteca con plantillas e ISO necesarias para desplegar VM.

1. A través del cliente web de vSphere, vaya a **Inicio** > **Biblioteca de contenido** > **Objetos** > **Crear una nueva biblioteca de contenido** > **Crear biblioteca suscrita en el vCenter**.
2. Especifique un nombre para la biblioteca de contenido, por ejemplo, ISO y, en el recuadro de texto Notas, especifique una descripción para la biblioteca y pulse **Siguiente**.
3. Seleccione **Biblioteca de contenido local** y pulse **Siguiente**.
4. Seleccione un almacén de datos y luego pulse en un almacén de datos adecuado, como por ejemplo `vsanDatastore`.
5. Revise la información de la página **Preparado para completar** y pulse **Finalizar**.

### Configuración de la VM de proxy, instalación de CentOS y Squid
{: #vum-init-config-config-proxy}

Esta actividad tiene las tareas siguientes:

*	Crear una VM nueva
*	Instalar CentOS
*	Instalar Squid

#### Crear una VM nueva
{: #vum-init-config-create-new-vm}

Esta tarea crea una nueva máquina virtual lista para su uso como servidor proxy. Los valores de la tabla 1 Valores de despliegue debería utilizarse para rellenar la configuración.

1.	Mediante el cliente web de vSphere, vaya a **Inicio** > **Máquinas y plantillas**.
2.	En el panel Navegador, pulse **datacenter1** y, a continuación, pulse con el botón derecho del ratón y seleccione; **Nueva máquina virtual** > **Nueva máquina virtual**.
3.	Seleccione **Crear una nueva máquina virtual** y, a continuación, pulse **Siguiente**.
4.	Especifique un nombre para la máquina virtual, por ejemplo Proxy01, y seleccione **datacenter1** y, a continuación, pulse **Siguiente**.
5.	Seleccione **cluster1** y, a continuación, pulse **Siguiente**.
6.	Seleccione un almacén de datos adecuado, por ejemplo, vsanDatastore y pulse **Siguiente** y **Siguiente** de nuevo.
7.	En **Familia de SO invitado**, seleccione **Linux** y, en **Versión de sistema operativo invitado**, seleccione **CentOS 7 (64 bits)** y pulse **Siguiente**.
8.	En el separador **Hardware personalizado** de hardware virtual, establezca **CPU en 1**, **Memoria en 2048 MB** y **Nuevo disco duro en 25 GB**. En **Nueva unidad de CD/DVD**, seleccione **Archivo ISO de la biblioteca de contenido** y, a continuación, **CentOS-7-x86_64-Minimal**, pulse **Aceptar** y la marca del recuadro **Conectado**.
9.	En el recuadro Nuevo dispositivo, seleccione **Red** y, a continuación, pulse **Añadir**.
10.	Seleccione la red **SDDC-DPortGroup-Mgmt**, asegúrese de que el recuadro de selección Conectar esté marcado y pulse **Siguiente**.
11.	Revise las opciones y pulse **Finalizar**.

#### Instalar CentOS
{: #vum-init-config-install-centos}

Esta tarea instala y configura la máquina virtual recién creada lista para la instalación de Squid

1.	En el panel Navegador del cliente web de vSphere, seleccione la **VM** que acaba de crear, Proxy01 y, a continuación, seleccione el separador **Resumen**.
2.	Pulse **"Reproducir"** para encender la VM.
3.	La máquina virtual se enciende y arranca desde CentOS 7 ISO. Inicie una **Consola remota o una consola web** en la máquina virtual. Debe instalar la consola remota y el sistema que ejecuta el navegador web debe resolver por nombre los hosts ESXi de vSphere.
4.	En la pantalla Bienvenido a CentOS 7, seleccione el idioma necesario y pulse **Continuar**.
5.	En la pantalla **LOCALIZACIÓN**, pulse **FECHA Y HORA** y seleccione el huso horario; a continuación, pulse **Terminado**.
6.	En la pantalla **LOCALIZACIÓN**, pulse **TECLADO** para cambiar el valor predeterminado si es necesario y, a continuación, pulse **Terminado**.
7.	En la pantalla **LOCALIZACIÓN**, pulse **DESTINO DE LA INSTALACIÓN**, pulse el **icono de disco virtual de VMware** y, a continuación, pulse **Terminado**.
8.	En la pantalla **LOCALIZACIÓN**, pulse **REDES Y NOMBRE DE HOST**, cambie el nombre de host por el nombre de host elegido; por ejemplo, Proxy01.
9.	Pulse **Configurar** y luego **Valores de IPv4**. En el recuadro **Método**, seleccione **Manual**.
10.	Con el botón **Añadir**, inserte _Máscara de red de dirección_ y la _Pasarela_ de la _Tabla 1 -Valores de despliegue_.
11.	Especifique la _dirección IP del servidor DNS_ de la Tabla 1 - Valores de despliegue.
12.	Pulse el botón **Rutas** y añada las siguientes rutas estáticas; _10.0.0.0/8 y 161.26.0.0/16_ con una dirección IP de pasarela de la _Dirección IP de BCR_ de la Tabla 1 Valores de despliegue, como la pasarela. Esta ruta estática permite al servidor proxy llegar al servidor DNS.
13.	Pulse **Guardar** y, a continuación, asegúrese de que la interfaz de Ethernet esté Activada y aparezca como conectada. Pulse **Terminado** e **Iniciar instalación**.
14.	A medida que avance la instalación, defina una contraseña de root y configure un usuario.
15.	Cuando finalice la instalación, inicie sesión como el usuario y, a continuación, escriba el mandato _ping vmware.com_. El nombre se resuelve en una dirección IP y el usuario recibe una respuesta. Si no obtiene respuestas, compruebe las direcciones IP, las reglas de cortafuegos y los valores de NAT.

#### Instalar y configurar Squid
{: #vum-init-config-install-cfg-squid}

Squid no tiene ningún requisito mínimo de hardware, pero la cantidad de RAM puede variar en función de los usuarios que acceden a Internet mediante su proxy y de los objetos almacenados en la memoria caché. Como solo la VUM acceda al servidor proxy y la caché no esté habilitada, solo se configura una VM pequeña.

1. Inicie la sesión en el servidor proxy como usuario mediante la consola web o la consola remota desde el cliente web de vSphere y, a continuación, haga `su` para convertirse en usuario root.
2. Antes de instalar cualquier paquete, debe utilizar el mandato siguiente para actualizar el sistema y los paquetes: `yum -y update`

3. Para instalar Squid, tiene que instalar el repositorio de EPEL en el sistema porque Squid no está disponible en el repositorio de yum predeterminado. Ejecute el mandato siguiente para instalar el repositorio de EPEL: `yum -y install epel-release`

4. Actualice y limpie mediante los mandatos siguientes:

  `yum -y update`  `yum clean all`

5. Squid se instala con el mandato siguiente: `yum -y install squid`.
6. Una vez instalado, inicie Squid inmediatamente con el mandato siguiente: `systemctl start squid`.
7. Ejecute el siguiente mandato para iniciar automáticamente Squid durante el arranque: `systemctl enable squid`.
8. Ejecute el mandato siguiente para asegurarse de que se ejecuta Squid: `systemctl status squid`.
9. El cortafuegos CentOS tiene que permitir el acceso al puerto Squid, TCP 3128 con el siguiente mandato: `firewall-cmd -add-port=3128/tcp -permanent`.
10. Para guardar la regla y reiniciar el servicio, utilice el mandato siguiente: `firewall-cmd –reload`.

## Configuración inicial de VUM
{: #vum-init-config-init-setup-vum}

Configure VUM para que utilice el servidor proxy para acceder a los repositorios de internet.
1. Con el cliente web de vSphere, vaya a **Inicio** > **Actualizar gestor**. Pulse el servidor de vCenter.
2. Seleccione el separador **Gestionar** y pulse **Configuración**.
3. Seleccione **Descargar valores** y, a continuación, en _Valores de proxy_ pulse **Editar**.
4. Marque el recuadro **Utilizar proxy** y especifique la _dirección IP del servidor proxy_ y el _puerto 3128_, pulse **Aceptar**. El estado de conectividad cambia a _Validación_ y, a continuación, a _Conectado_.
    **Nota**: no se preocupe si recibe el mensaje ``Se ha accedido correctamente a algunos URL, pero otros son inaccesibles`` al probar la conexión con el servidor proxy.
5. Pulse **Descargar ahora**. En el panel _Tareas recientes_, debería ver esta actividad completada.
6. Si esta actividad falla, rearranque vCenter Server Appliance (vCSA):
  1. Inicie sesión en la interfaz de gestión de vCSA en `https://vcsaFQDN:5480` como
**root**.
  2. Pulse **Resumen** y pulse **Rearrancar**.
  3. En el recuadro de confirmación, pulse **Sí** para confirmar la operación.

## Enlaces relacionados
{: #vum-init-config-related}

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (demostraciones)
