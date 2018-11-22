---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Zerto

Si detecta que un host de vSphere ESXi no puede entrar en la modalidad de mantenimiento durante la corrección, es posible que sea causa de Zerto. Si ha actualizado Zerto desde el despliegue inicial, lleve a cabo los pasos siguientes para corregirlo. Si no se ha actualizado, siga las instrucciones de [Cómo colocar un host con un VRA asociado en la modalidad de mantenimiento](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/).

1. Inicie una sesión en la interfaz de usuario web de Zerto.
2. Seleccione **Valores de siti ** en el menú desplegable.
3. Seleccione el **separador de políticas** y asegúrese de que la opción **Permitir a Zerto pasar hosts a la modalidad de mantenimiento durante la corrección** esté seleccionada.
4. Cerrar la sesión de Zerto.

### Enlaces relacionados

* [Solución VMware HCX on {{site.data.keyword.cloud}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demos)
