---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-26"

---

# Creación de líneas base y conexión a objetos de inventario

Las líneas base tienen una colección de uno o varios parches, extensiones, paquetes de servicio, arreglos de errores o actualizaciones, y se pueden clasificar como líneas base de parches, extensiones o actualización. Los grupos de línea base se ensamblan desde las líneas base existentes. Los grupos de línea base de host pueden tener una sola línea base de actualización y varias líneas base de parche y extensión. Los grupos de línea base de la máquina virtual y del dispositivo virtual pueden tener hasta tres líneas base de actualización: una línea base de actualización de VMware Tools, una línea base de actualización de hardware de máquina virtual y una línea base de actualización de dispositivo virtual.

VUM incluye líneas base predefinidas que no se pueden editar ni suprimir. Puede utilizar las líneas base predefinidas o crear las líneas base de parche, extensión y actualización que cumplan sus criterios. Las líneas base personalizadas que cree y las líneas base predefinidas se pueden combinar en grupos de línea base.

VUM incluye líneas base predeterminadas que puede utilizar para explorar cualquiera de los dispositivos siguientes para determinar si los hosts de su entorno se actualizan con los últimos parches o si los dispositivos virtuales y las máquinas virtuales se actualizan a la última versión:
* Cualquier máquina virtual
* Cualquier dispositivo virtual
* Cualquier host

Estas líneas base predefinidas son las siguientes:
* **Parches de host críticos (predefinido)**: Comprueba los hosts ESXi para su conformidad con todos los parches críticos.
* **Parches de host no críticos (predefinido)**: Comprueba los hosts ESXi para su conformidad con todos los parches opcionales.
* **Actualización de VMware Tools Upgrade para que coincida con el host (predefinido)**: Comprueba máquinas virtuales para la conformidad con la última versión de VMware Tools en el host. El gestor de actualizaciones da soporte a la actualización de las herramientas de VMware para máquinas virtuales en hosts que ejecutan ESXi 5.5.x y posteriores.
* **Actualización de hardware de VM para que coincida con el host (predefinido)**: Comprueba el hardware virtual de una máquina virtual para la conformidad con la versión más reciente que admita el host. Update Manager admite la actualización a la versión de hardware virtual vmx-13 en hosts que ejecuten ESXi 6.5.
* **Actualización de VA a más reciente (predefinido)**: Comprueba la conformidad del dispositivo virtual con la última versión de dispositivo virtual lanzada.

Para utilizar las líneas base y los grupos de línea base, debe adjuntarlos a los objetos de inventario seleccionados, como los objetos de contenedor, las máquinas virtuales, los dispositivos virtuales o los hosts. Aunque puede adjuntar líneas base y grupos de línea base a objetos individuales, hay un método más eficiente que consiste en adjuntarlos a objetos de contenedor, como por ejemplo carpetas, vApps, clústeres o centros de datos. En este paso, utilizaremos las líneas base predefinidas contra los hosts del clúster.

1. Mediante el cliente web de vSphere, vaya a **Inicio ** > **Hosts y clústeres**.
2. Pulse el objeto de clúster que desee explorar.
3. Pulse **Adjuntar línea base**, seleccione las dos líneas base de parches predefinidas y, a continuación, pulse **Aceptar**.

### Enlaces relacionados

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demostraciones)
