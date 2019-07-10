---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: HTDC WebGUI, HTDC console, enable internet HTDC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestión de HyTrust DataControl on IBM Cloud
{: #managinghtdc}

Para gestionar el servicio HyTrust DataControl on {{site.data.keyword.cloud}} (HTDC), acceda a la HTDC WebGUI desde la consola de {{site.data.keyword.vmwaresolutions_short}}, o acceda a la consola de HTDC desde el cliente web de vSphere.

## Acceso a la HyTrust DataControl WebGUI desde la consola de IBM Cloud for VMware Solutions
{: #managinghtdc-accessing-webgui}

Para iniciar sesión en la WebGUI del dispositivo HTDC primario o secundario, utilice las credenciales de WebGUI que encontrará en la página de detalles del servicio HyTrust DataControl on {{site.data.keyword.cloud_notm}}.

## Acceso a la consola de HyTrust DataControl desde el cliente web de vSphere
{: #managinghtdc-accessing-console}

Para acceder a la consola de HTDC desde el cliente web de vSphere, siga el siguiente procedimiento:
1. En el cliente web de vSphere, busque las máquinas virtuales denominadas **KC1** y **KC2**. 
2. Pulse con el botón derecho del ratón sobre **KC1** o **KC2** y pulse **Abrir consola**.
3. Inicie una sesión en la consola utilizando las credenciales de la consola que encontrará en la página de detalles del servicio HyTrust DataControl on {{site.data.keyword.cloud_notm}}.

Para obtener más información, consulte [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Habilitación del acceso a Internet para las VM de HyTrust DataControl
{: #managinghtdc-internet-access}

Para HTDC 4.3.2 y posteriores, {{site.data.keyword.vmwaresolutions_short}} proporciona soporte de renovación automática para licencias de HyTrust que tienen habilitada la función de llamada al centro de soporte. Para las instancias de vCenter Server que no son sólo privadas, HTDC se despliega con reglas de cortafuegos y SNAT (conversión de direcciones de red de origen) que están definidas en los servicios de gestión ESG **mgmt-nsx-edge**. 

Estas reglas le permiten habilitar el acceso a Internet para las máquinas virtuales HyTrust (VM). Si el acceso a Internet no está habilitado, la licencia que se aplica a la instalación de HTDC caducará después de un año. 

Para entornos de servidor de vCenter sólo privados, no se añade el VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge**, por lo que las reglas de cortafuegos y SNAT no están definidas. En consecuencia, la conectividad de Internet no se puede habilitar para las instancias que son sólo privadas, y las licencias HyTrust caducan anualmente. {:note}

### Procedimiento para encontrar las reglas de cortafuegos y SNAT definidas
{: #managinghtdc-proc-find-firewall}

1. Inicie la sesión en el cliente web de VMware vSphere (FLEX) y busque el ESG **mgmt-nsx-edge**.
2. Pulse **Inicio > Redes y seguridad > NSX Edges**. 
3. Efectúe una doble pulsación en el ESG **mgmt-nsx-edge** y pulse el separador **Gestionar**. 
4. Acceda al separador **Cortafuegos** y busque las reglas de HyTrust. Anote las direcciones IP de origen. Se trata de las direcciones IP de las máquinas virtuales HyTrust.
5. Acceda al separador **NAT** y busque las reglas SNAT que se crean para las máquinas virtuales HyTrust. Las direcciones IP de origen coincidirán con las direcciones IP que ha anotado en el paso anterior. 

### Procedimiento para habilitar la conectividad de Internet para HTDC
{: #managinghtdc-proc-enable-internet}

1. Complete los pasos 1-3 en el procedimiento anterior.
2. Pulse **Valores** y, a continuación, **Interfaces**. Anote la dirección IP para el enlace ascendente privado. Esta dirección será la nueva pasarela predeterminada. 
3. Pulse **Inicio > Hosts y clústeres** y busque las máquinas virtuales HyTrust. Pulse el botón derecho del ratón sobre una de las máquinas virtuales y pulse **Abrir consola**. 
4. Inicie sesión en la consola utilizando las credenciales de la consola que puede encontrar en la página de detalles del servicio HyTrust DataControl on IBM Cloud, en la consola de {{site.data.keyword.vmwaresolutions_short}}. 
5. Para obtener la dirección IP de pasarela predeterminada actual de la máquina virtual, pulse **Gestionar Network Settings > Mostrar configuración de red actual**. Anote la dirección IP que aparece en la lista de **Pasarela**. Esta dirección se convierte en la pasarela que se utiliza para la ruta estática. 
6. Para establecer una ruta estática para la máquina virtual, pulse **Gestionar valores de
red > Gestionar rutas estáticas > Añadir ruta estática**. Establezca **Dirección de red** en `10.0.0.0/8` y **Pasarela** en la dirección IP indicada en el paso anterior. 
7. Para establecer la IP de pasarela predeterminada para la máquina virtual, pulse **Gestionar valores de red > Cambiar configuración de red actual**. Si obtiene un mensaje de aviso, pulse **Aceptar** y, a continuación, pulse **Configuración personalizada**. Establezca el campo **Pasarela** en la dirección IP de enlace ascendente privada que se indica en el paso 2 y pulse en **Aceptar**. Espere hasta que se instale la nueva configuración de red y se reinicien los servicios de red. 
8. Si ve un mensaje que solicita la reautenticación de HyTrust SecureOS, pulse **Aceptar** y especifique la dirección IP de la otra máquina virtual de HyTrust para esta instalación. Si se le solicita una frase de contraseña de 16 caracteres, pulse Intro para volver al menú principal. Verifique la configuración de red actual para asegurarse de que se aplican los cambios. 
9. Para confirmar que la máquina virtual tiene acceso a Internet, haga ping a una dirección IP pública o a un sitio web. Pulse en **Gestionar valores de red > Herramientas de diagnóstico de red > Ping a otro servidor**. Escriba una dirección de sitio web pública, por ejemplo, `www.ibm.com`, pulse **Aceptar** y espere a que se visualice un mensaje, por ejemplo, `www.ibm.com responde a ping`. 
10. Repita los pasos 3 a 9 para la otra VM de HyTrust.


## Enlaces relacionados
{: #managinghtdc-related}

* [Visión general de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sitio web de HyTrust](https://www.hytrust.com/)
