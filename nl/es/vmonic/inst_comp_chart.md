---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: vmware offering, vmware solutions functions, function support

subcollection: vmware-solutions


---

# Gráfico de comparación de ofertas
{: #inst_comp_chart}

Revise el siguiente gráfico para entender las diferencias en cuanto a soporte de funciones entre las instancias de VMware vCenter Server y los clústeres de VMware vSphere.

| Función | vCenter Server | VMware vSphere |
|:--- |:--- |:--- |:--- |
| Basado en automatización avanzada de {{site.data.keyword.IBM}} <sup>1</sup> | Sí | No. Compilado y configurado automáticamente |
| Opciones de almacenamiento | vSAN o NFS (almacenamiento de nivel de archivo compartido) | vSAN o NFS |
| Número de servidores ESXi en clúster inicial | 4 para vSAN y un mínimo de 2 (se recomienda 3) para NFS | 1 para escalar un clúster existente, 4 para clúster vSAN nuevo y un mínimo de 3 para clúster nuevo con NFS |
| Número máximo de servidores ESXi <sup>2</sup> | 59 por clúster | 60 por clúster |
| Despliegue automático de varios sitios en la nube |Soportado para instancias nuevas desplegadas en V2.0 o posterior | Soportado. Configuración automática no incluida. |
| Añadir servidores ESXi | Soportado | Soportado. Configuración automática no incluida. |
| Eliminar servidores ESXi | Soportado | Soportado. Configuración automática no incluida. |
| Soporte de varios clústeres | El número máximo depende de las directrices de dimensionamiento de VMware | Soportado. Configuración automática no incluida. |
| Actualización y aplicación parches gestionadas por cliente de pila VMware | Actualizaciones gestionadas por el cliente:<br/>Herramientas nativas de VMware (VMware Update Manager) | Actualizaciones gestionadas por el cliente:<br/>Herramientas nativas de VMware (VMware Update Manager) |
| Copia de seguridad y restauración | Manualmente utilizando IBM Spectrum Protect Plus o Veeam | Solución de copia de seguridad y restauración no incluida |
| Sistema de redes definida por software | NSX Base, Advanced o Enterprise | NSX Standard, Base o Enterprise. Configuración automática no incluida. |
| BYOL para vSphere y vSAN | Soporte completo por clúster | Soportado |
| BYOL para vCenter y NSX | Soporte completo por instancia | Soportado |
| Opciones de actualización de licencias NSX | Actualización disponible desde NSX Base a Advanced o Enterprise y desde NSX Advanced a Enterprise. | Ninguna |
| Ediciones de licencias de vSAN | vSAN Advanced o Enterprise | vSAN Advanced o Enterprise  |
| Servicios complementarios | Soportado | No soportado por la automatización de esta solución, pero puede traer e instalar su propio software. |
{: caption="Tabla 1. Funciones soportadas para vCenter Server y clústeres de vSphere" caption-side="top"}

## Notas
{: #inst_comp_chart-notes}

<sup>1</sup> Según un diseño validado y con verificación durante el despliegue.

<sup>2</sup> Puede aumentar el número de servidores ESXi en un clúster vSAN a un máximo de 64. Para obtener más información, consulte _¿Cuántos servidores ESXi puedo añadir a un clúster?_ en [Preguntas frecuentes sobre servidores ESXi](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi).

## Enlaces relacionados
{: #inst_comp_chart-related}

* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Visión general de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Visión general de VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)
* [Lista de materiales de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Lista de materiales de VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
