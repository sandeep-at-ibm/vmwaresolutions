---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Gráfico de comparación de ofertas

Revise el siguiente gráfico para entender las diferencias en cuanto a soporte de funciones entre las instancias de VMware Cloud Foundation, las instancias de VMware vCenter Server, las instancias de VMware vCenter Server con el paquete híbrido (Hybridity) y los clústeres de VMware vSphere.

Tabla 1. Funciones soportadas para Cloud Foundation, vCenter Server, vCenter Server con el paquete híbrido (Hybridity) y clústeres de vSphere

| Función                          | Cloud Foundation    | vCenter Server | vCenter Server with Hybridity | VMware vSphere |
|:----------------------------------|:--------------------|:---------------|:-------------------------|:-------------- |
| Basado en automatización avanzada de {{site.data.keyword.IBM}} <sup>1</sup> | Sí | Sí | Sí | No. Compilado y configurado automáticamente |
| Opciones de almacenamiento        | vSAN                | vSAN o almacenamiento de nivel de archivo compartido (NFS) | vSAN | vSAN o almacenamiento de nivel de archivo compartido (NFS) |
| Número de servidores ESXi en clúster inicial | 4 | 4 para vSAN y un mínimo de 2 (se recomienda 3) para NFS | 4 | 1 para escalar un clúster existente, 4 para clúster vSAN nuevo y un mínimo de 3 para clúster nuevo con NFS |
| Número máximo de servidores ESXi <sup>2</sup> | 32 por clúster      | 59 por clúster     | 59 por clúster | 60 por clúster     |
| Despliegue automático de varios sitios en la nube | Soportado para instancias nuevas desplegadas en V2.0 o posterior | Soportado para instancias nuevas desplegadas en V2.0 o posterior | Soportado | Soportado. Configuración automática no incluida. |
| Añadir servidores ESXi              | Soportado           | Soportado | Soportado | Soportado. Configuración automática no incluida. |
| Eliminar servidores ESXi           | Soportado           | Soportado | Soportado | Soportado. Configuración automática no incluida. |
| Soporte de varios clústeres         | Cinco clústeres | Diez clústeres | Diez clústeres | Soportado. Configuración automática no incluida. |
| Actualización y aplicación parches gestionadas por cliente de pila VMware | Actualizaciones de VMware | No incluido | No incluido | No incluido |
| Copia de seguridad y restauración            | Manualmente utilizando IBM Spectrum Protect Plus o Veeam | Manualmente utilizando IBM Spectrum Protect Plus o Veeam | Manualmente utilizando IBM Spectrum Protect Plus o Veeam | Solución de copia de seguridad y restauración no incluida |
| Sistema de redes definida por software   | NSX Enterprise   | NSX Base, Advanced o Enterprise | NSX Advanced o Enterprise | NSX Standard, Base o Enterprise. Configuración automática no incluida. |
| BYOL para vSphere y vSAN | Soporte completo por clúster   | Soporte completo por clúster     | No soportado | Soportado |
| BYOL para vCenter y NSX | Soporte completo por instancia   | Soporte completo por instancia     | No soportado | Soportado |
| Opciones de actualización de licencias NSX           | Ninguna   | Actualización disponible desde NSX Base a Advanced o Enterprise y desde NSX Advanced a Enterprise. Está disponible la actualización a vCenter Server con el paquete híbrido (Hybridity). | Actualización disponible desde NSX Advanced a Enterprise  | Ninguna |
| Ediciones de licencias de vSAN         | vSAN Advanced o Enterprise  | vSAN Advanced o Enterprise  | vSAN Advanced o Enterprise | vSAN Advanced o Enterprise  |
| Servicios complementarios               | Soportado, sin incluir HCX on {{site.data.keyword.cloud_notm}}.  | Soportado, sin incluir HCX on {{site.data.keyword.cloud_notm}}. Está disponible la actualización a vCenter Server con el paquete híbrido (Hybridity). | Soportado, incluido HCX on {{site.data.keyword.cloud_notm}}. | No soportado por la automatización de esta solución, pero puede traer e instalar su propio software. |

**Notas:**

<sup>1</sup> Según un diseño validado y con verificación durante el despliegue.

<sup>2</sup> Puede aumentar el número de servidores ESXi en un clúster vSAN a un máximo de 64. Para obtener más información, consulte _¿Cuántos servidores ESXi puedo añadir a un clúster?_ en [Preguntas frecuentes sobre servidores ESXi](faq_esxi.html).

### Enlaces relacionados

* [Preguntas frecuentes](faq.html)
* [Visión general de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Visión general de vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Visión general de vCenter Server Hybridity](../vcenter/vc_hybrid_overview.html)
* [Visión general de VMware vSphere](../vsphere/vs_vsphereclusteroverview.html)
* [Lista de materiales de Cloud Foundation](../sddc/sd_bom.html)
* [Lista de materiales de vCenter Server](../vcenter/vc_bom.html)
* [Lista de materiales de VMware vSphere](../vsphere/vs_bom.html)
