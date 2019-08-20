---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Zerto
{: #vum-zerto}

Si detecta que un host de vSphere ESXi no puede entrar en la modalidad de mantenimiento durante la corrección, es posible que sea causa de Zerto. Si ha actualizado Zerto desde el despliegue inicial, lleve a cabo los pasos siguientes para corregirlo. Si no se ha actualizado, siga las instrucciones siguientes sobre [Cómo colocar un host con un VRA asociado en la modalidad de mantenimiento](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/).

1. Inicie una sesión en la interfaz de usuario web de Zerto.
2. Seleccione **Valores de sitio** en el menú desplegable.
3. Seleccione el separador **Políticas** y asegúrese de que **Permitir siempre a Zerto pasar hosts a la modalidad de mantenimiento durante la corrección** esté seleccionado.
4. Cerrar la sesión de Zerto.

## Enlaces relacionados
{: #vum-zerto-related}

* [Arquitectura de la solución VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [Demos de {{site.data.keyword.vmwaresolutions_full}}](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (demostraciones)
