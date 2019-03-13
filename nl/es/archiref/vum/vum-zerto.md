---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Zerto
{: #vum-zerto}

Si detecta que un host de vSphere ESXi no puede entrar en la modalidad de mantenimiento durante la corrección, es posible que sea causa de Zerto. Si ha actualizado Zerto desde el despliegue inicial, lleve a cabo los pasos siguientes para corregirlo. Si no se ha actualizado, siga las instrucciones siguientes sobre [Cómo colocar un host con un VRA asociado en la modalidad de mantenimiento](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/).

1. Inicie una sesión en la interfaz de usuario web de Zerto.
2. Seleccione **Valores de sitio** en el menú desplegable.
3. Seleccione el **separador de políticas** y asegúrese de que la opción **Permitir a Zerto pasar hosts a la modalidad de mantenimiento durante la corrección** esté seleccionada.
4. Cerrar la sesión de Zerto.

## Enlaces relacionados
{: #vum-zerto-related}

* [Solución VMware HCX on {{site.data.keyword.cloud}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demostraciones)
