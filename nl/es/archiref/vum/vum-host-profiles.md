---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-03"

---

#	Perfil de host

vCenter tiene una característica denominada Perfiles de host. Esta característica crea un perfil que captura una configuración de host de referencia preconfigurada y validada y ayuda a un administrador del sistema a gestionar las configuraciones de host en un clúster. Los perfiles de host proporcionan un mecanismo automatizado y gestionado de forma centralizada para la configuración de host y la conformidad de configuración. Los perfiles de host permiten que la configuración se trate como un objeto gestionado, que contiene un catálogo de parámetros para configurar; la red, el almacenamiento, la seguridad y otros parámetros de nivel de host. Estos perfiles de host se pueden aplicar a hosts individuales, a un clúster o a todos los hosts y clústeres asociados a un perfil de host.

A medida que se despliegan más hosts VCS vSphere ESXi mediante la automatización de IC4VS que ha desplegado el clúster original, habrá menos derivación de configuración que con métodos manuales de adición de hosts. Sin embargo, las acciones de administrador del sistema, fuera de la automatización, pueden hacer que la configuración de hosts sea distinta. Por ejemplo, se han añadido más almacenamiento NFS o VLAN adicionales. Por lo tanto, el uso de Perfiles de host para validar la configuración de un nuevo host mediante la comprobación de la conformidad de este host frente a un host existente es un caso de uso válido de esta herramienta dentro de IBM Cloud.

Para añadir más hosts a su clúster de vCenter Server, consulte [Expandir y contratar capacidad para instancias de vCenter Server](../../vcenter/vc_addingremovingservers.html).

Tenga en cuenta que:
*	Para las instancias desplegadas en, o actualizadas a, V2.1 o superior, se ha aplicado un parche a los servidores ESXi y los clústeres recién desplegados con actualizaciones recientes, pero no necesariamente las más recientes, de ESXi de VMware.
*	El usuario es el responsable de todas las demás actualizaciones de los componentes de VMware, lo que incluye asegurarse de que los clústeres y servidores ESXi recién desplegados tienen las actualizaciones más recientes que necesita.

Aconsejamos que después de añadir un nuevo host al clúster, este se coloque en modalidad de mantenimiento para que se pueda revisar para la comprobación de conformidad y se pueda corregir antes de alojar cualquier carga de trabajo.

Se necesita la secuencia siguiente para comprobar la conformidad:
1.	Crear un Perfil de host a partir de un host existente.
2.	Adjuntar el nuevo host al Perfil de host.
3.	Comprobar la conformidad del nuevo host con el Perfil de host.
4.	Revisar las anomalías de conformidad y la corrección.

##	Creación de un perfil de host a partir de un host existente

1.	Desde el inicio del cliente web de vSphere, pulse **Políticas y perfiles**.
2.	Pulse **Perfiles de host** y vaya a la vista Perfiles de host.
3.	Pulse el icono **Extraer perfil a partir de un icono de host**.
4.	Seleccione un host existente que actuará como el host de referencia y pulse **Siguiente**.
5.	Especifique el nombre y especifique una descripción para el nuevo perfil y pulse **Siguiente**.
6.	Revise la información de resumen para el nuevo perfil y pulse **Finalizar**.
7.	El nuevo perfil aparece en la lista de perfiles.

##	Cómo adjuntar el nuevo host al perfil de host

1.	En la **Lista de perfiles** de la vista principal de Perfiles de host, seleccione el Perfil de host creado anteriormente para aplicarse al nuevo host.
2.	Pulse el icono **Adjuntar/Desconectar un perfil de host a hosts y clústeres**.
3.	Seleccione el nuevo host de la lista expandida y pulse **Adjuntar**.
4.	El nuevo host se añade a la lista de Entidades conectadas.
5.	Pulse **Siguiente** y a continuación pulse **Finalizar**.

##	Comprobación de la conformidad del nuevo host con el perfil de host

1.	Vaya al Perfil de host completado anteriormente.
2.	Pulse el icono de comprobación **Conformidad de perfil de host**.
3.	En el **separador Objetos**, el estado de conformidad se actualiza como: _Conforme, Desconocido o _No conforme_. Un estado de no conformidad indica una incoherencia descubierta y específica entre el perfil y el nuevo host.

##	Revisión de errores de conformidad y de corrección

1.	Para ver más detalles sobre las anomalías de conformidad, seleccione el **Perfil de host** en el separador **Objetos ** que se utiliza en la comprobación de conformidad.
2.	Para ver detalles específicos sobre qué parámetros difieren entre el host que no cumple con la conformidad y el Perfil de host, pulse en el **separador Supervisor ** y seleccione la **Vista de conformidad**.
3.	Expanda la jerarquía de objetos y seleccione el host que falla.
4.	Los distintos parámetros se muestran en la ventana Conformidad, debajo de la jerarquía.
5.	Revise los parámetros y comprenda por qué el nuevo host puede variar desde el host de referencia. Para los parámetros en los que la conformidad no sea aceptable, por ejemplo, cuando la acción de administrador del sistema ha causado la deriva de la configuración, corríjalo antes de mover el nuevo host desde la modalidad de mantenimiento.

### Enlaces relacionados

* [VMware HCX on IBM Cloud Solution](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demos)
