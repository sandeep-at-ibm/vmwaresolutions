---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# Registro de HCX Manager con vCenter
{: #hcx-archi-reg-vcenter}

Registre el plugin de Hybrid Cloud Services en el cliente web de VMware vSphere e inicie el servicio de gestión de Hybrid Cloud Services.

## Antes de empezar
{: #hcx-archi-reg-vcenter-prereq}

El dispositivo virtual Hybrid Cloud Services debe estar encendido para que se pueda registrar.

## Procedimiento para registrar HCX Manager con vCenter
{: #hcx-archi-reg-vcenter-proc-register}

1. Inicie la sesión en el dispositivo virtual de servicio de Hybrid Cloud Services.
2. Pulse el separador **Gestionar valores**.
  1. En el panel izquierdo, en **Configurar sistemas**, seleccione vCenter.
  2. Pulse **Añadir vCenter** en la parte superior derecha.
  3. Escriba la dirección IP de vCenter Server en el formato `https:vCenter-host-name` o `https:vCenter-IP-address`. Por ejemplo, `https:My-vCenter` o `https:10.108.26.211`.
  4. Escriba el nombre de usuario y la contraseña de vCenter Server. La cuenta que se utilice debe tener el rol de administrador de vCenter.
  5. Pulse **Aceptar**. No se reinicie cuando aparezca el mensaje _Se tiene que reiniciar la app_.
3. Configure el servicio de búsqueda.
  1. Pulse el separador **Gestionar**.
  2. Pulse el botón **Editar** en la parte derecha del recuadro de texto **URL de servicio de búsqueda**.
  3. Especifique el punto final del servicio de búsqueda en el formato siguiente:
    * Para vCenter Server 5.5u3 `https://ssoip:/7444/lookupservice/sdk`
    * Para vCenter Server 6.0u2 `https://ssoip/lookupservice/sdk`
  4. Pulse **Aceptar**. No reinicie cuando aparezca un mensaje para reiniciar el motor web.
4. Pulse el separador **Resumen** y busque la sección **Componentes de gestión de Hybridity**. Detenga e inicie tanto el motor de aplicaciones y el motor web.
5. Para finalizar el registro, finalice la sesión en el cliente web de vSphere. Vuelva a iniciar la sesión para verificar que se ha actualizado la pantalla.

## Resultados
{: #hcx-archi-reg-vcenter-results}

Observe el icono **Nube híbrida** existente y el elemento de menú **Hybrid Cloud Services** de la izquierda. El registro de Hybrid Cloud Services actualiza estas etiquetas. En el inventario, la etiqueta de icono pasa a ser **Hybrid Cloud Services**.

## Enlaces relacionados
{: #hcx-archi-reg-vcenter-related}

* [Instalación y configuración de servicios híbridos](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-hybrid)
