---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: HTCC WebGUI, HTCC console, enable internet HTCC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestión de HyTrust CloudControl on IBM Cloud
{: #managinghtcc}

Para gestionar el servicio HyTrust CloudControl on {{site.data.keyword.cloud}} (HTCC), acceda a la HTCC WebGUI desde la consola de {{site.data.keyword.vmwaresolutions_short}}, o acceda a la consola de HTCC desde el cliente web de vSphere.

## Acceso a la HyTrust CloudControl WebGUI desde la consola de IBM Cloud for VMware Solutions
{: #managinghtcc-accessing-webgui}

Para iniciar sesión en la WebGUI del dispositivo HTCC primario o secundario, utilice las credenciales de WebGUI que encontrará en la página de detalles del servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}.

## Acceso a la consola de HyTrust CloudControl desde el cliente web de vSphere
{: #managinghtcc-accessing-console}

Para acceder a la consola de HTCC desde el cliente web de vSphere, siga el siguiente procedimiento:
1. En el cliente web de vSphere, busque las máquinas virtuales denominadas **CC1** y **CC2**. 
2. Pulse con el botón derecho del ratón sobre **CC1** o **CC2** y pulse **Abrir consola**.
3. Inicie una sesión en la consola utilizando las credenciales de la consola que encontrará en la página de detalles del servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}.

Para obtener más información, consulte [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Habilitación del acceso a Internet para las VM de HyTrust CloudControl
{: #managinghtcc-internet-access}

Para HTCC 5.5.1 y posteriores, {{site.data.keyword.vmwaresolutions_short}} proporciona soporte de renovación automática para licencias de HyTrust que tienen habilitada la función de llamada al centro de soporte. Para las instancias de vCenter Server que no son sólo privadas, HTCC se despliega con reglas de cortafuegos y SNAT (conversión de direcciones de red de origen) que están definidas en los servicios de gestión ESG **mgmt-nsx-edge**. 

Estas reglas le permiten habilitar el acceso a Internet para las máquinas virtuales HyTrust (VM). Si el acceso a Internet no está habilitado, la licencia que se aplica a la instalación de HTCC caducará después de un año. 

Para entornos de servidor de vCenter sólo privados, no se añade el VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge**, por lo que las reglas de cortafuegos y SNAT no están definidas. En consecuencia, la conectividad de Internet no se puede habilitar para las instancias que son sólo privadas, y las licencias HyTrust caducan anualmente. {:note}

### Procedimiento para encontrar las reglas de cortafuegos y SNAT definidas
{: #managinghtcc-proc-find-firewall}

1. Inicie la sesión en el cliente web de VMware vSphere (FLEX) y busque el ESG **mgmt-nsx-edge**.
2. Pulse **Inicio > Redes y seguridad > NSX Edges**. 
3. Efectúe una doble pulsación en el ESG **mgmt-nsx-edge** y pulse el separador **Gestionar**. 
4. Acceda al separador **Cortafuegos** y busque las reglas de HyTrust. Anote las direcciones IP de origen. Se trata de las direcciones IP de las máquinas virtuales HyTrust.
5. Acceda al separador **NAT** y busque las reglas SNAT que se crean para las máquinas virtuales HyTrust. Las direcciones IP de origen coincidirán con las direcciones IP que ha anotado en el paso anterior. 

### Procedimiento para habilitar la conectividad de Internet para HTCC
{: #managinghtcc-enable-internet}

Estos pasos se aplican a la actualización de los valores de red HTCC en la máquina virtual primaria (VM), que se utiliza para las actualizaciones de licencias. No es necesario que actualice los valores para la máquina virtual secundaria.{:note}

1. Complete los pasos 1-3 en el procedimiento anterior. 
2. Pulse **Valores** y, a continuación, **Interfaces**. Anote la dirección IP para el enlace ascendente privado, que se convierte en la nueva pasarela predeterminada. 
3. Vaya a la página de detalles del servicio HyTrust CloudControl on IBM Cloud, pulse **Ver IU web de HTCC** e inicie sesión con las credenciales de la página de detalles de servicio. 
4. Anote la pasarela predeterminada existente. Por ejemplo, para HTCC 5.5.1, pulse **Configuración > Red**. Anote la dirección IP de pasarela que aparece en la lista, que se convierte en la pasarela para la ruta estática.
5. Añada una ruta estática. Por ejemplo, para HTCC 5.5.1, pulse **Configuración > Rutas estáticas**. Pulse **Añadir**, especifique la información siguiente y pulse en **Aceptar**.

  ```
  Dirección de red: 10.0.0.0
  Máscara: 255.0.0.0
  Pasarela: IP del paso 4
  Dispositivo: Red 1
  ```

6. Cambie la pasarela predeterminada. Por ejemplo, para HTCC 5.5.1, pulse **Configuración > Red** y sustituya la dirección IP del campo **Pasarela** por la que ha anotado
en el paso 3, y pulse **Guardar**. 

  Asegúrese de establecer la ruta estática antes de cambiar la pasarela predeterminada, de lo contrario, podría perderse la comunicación con la consola web. {:important}

  La máquina virtual primaria ya tendrá acceso a Internet. 

7. Para confirmar que la máquina virtual primaria tiene acceso a Internet, ejecute un mandato `ping` a una dirección IP o sitio web que sean públicos. Para ello, vuelva a vCenter y pulse el botón derecho del ratón en **CC1 > Abrir consola**. Inicie la sesión en la consola utilizando las credenciales de la consola de la página de detalles del servicio HyTrust CloudControl on IBM Cloud. Ejecute un mandato `ping` como, por ejemplo, `ping www.ibm.com`, y deberá obtener una respuesta inmediata. Pulse `Ctrl + C` para finalizar el mandato ping y asegúrese de que la pérdida de paquetes es 0%.

## Enlaces relacionados
{: #managinghtcc-related}

* [Visión general de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sitio web de HyTrust](https://www.hytrust.com/)
