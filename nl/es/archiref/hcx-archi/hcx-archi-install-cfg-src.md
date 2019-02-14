---

copyright:

  years:  2016, 2019

lastupdated: "2018-12-18"

---
# Instalación y configuración de HCX en el origen

La instalación local implica desplegar el dispositivo de gestión de HCX y registrarlo con el vCenter y uno o más puntos finales de nube habilitados para VCF/VCS HCX.

## Instalación del dispositivo HCX Manager

Instale el dispositivo HCX Manager en el vCenter local.

1. Inicie una la sesión en **Mi VMware** y descargue el archivo OVA de Hybrid Cloud Services desde la página de descargas del producto.
2. Abra un navegador e inicie una sesión en el cliente web de vSphere. Esta tarea no se puede realizar desde el cliente de vSphere. Visualice el separador **Inicio**.
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
  * Examine el separador **Resumen**; la consola muestra **Encendido** y el botón **Reproducir** está verde.
10. HCX Manager está encendido y listo para que se registre con vCenter.

### Enlaces relacionados

* [Preparación del entorno de instalación](hcx-archi-prep-install.html)
