---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Configuración de la red para que utilice la ESG NSX-T gestionada por el cliente con las VM
{: #vc_nsx-t_esg_config}

Configure la red para las máquinas virtuales de modo que pueda aprovechar el servicio VMware NSX-T Edge Services Gateway (ESG) que se despliega en las instancias de VMware vCenter Server. Para obtener más información sobre las medidas de seguridad en vigor para ayudar a minimizar los riesgos de seguridad, consulte [¿Representa NSX Edge se servicios de gestión un riesgo para la seguridad?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX-T es una plataforma de virtualización de red que permite la virtualización de redes aisladas y proporciona varios servicios de red, como conmutadores, direccionamiento y cortafuegos. Para obtener más información sobre NSX, consulte [Visión general de NSX](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}.

Como parte del proceso de pedido de la instancia de vCenter Server con NSX-T, se llevan a cabo las siguientes acciones en su nombre:
* Se solicita una subred de cliente privada que utilizarán las VM (máquinas virtuales) para acceder a la red privada de la infraestructura de {{site.data.keyword.cloud}}.
* Se solicita una subred de cliente pública que permitirá a las VM acceder a Internet.
* Se despliega y se configura NSX-T en la instancia de vCenter Server con NSX-T.
* Se despliega un conmutador lógico NSX-T de ejemplo que utilizarán las VM de carga de trabajo del cliente.
* Se despliega un direccionador de nivel 1 NSX-T de ejemplo para una potencial comunicación este-oeste entre cargas de trabajo locales conectadas a redes de la capa 2 (L2).
* Se despliega y se configura un dispositivo NSX-T Edge que realiza la conversión de direcciones de red (NAT) entre el rango de direcciones IP del conmutador lógico de carga de trabajo y una dirección IP pública en las reglas NAT.

  NSX-T Edge no se despliega para instancias que solo son privadas.
  {:note}

## Procedimiento para configurar los valores de red para las máquinas virtuales
{: #vc_nsx-t_esg_config-procedure-config-networking}

Para aprovechar el servicio NSX-T para sus VM de carga de trabajo, debe configurar una serie de valores siguiendo los siguientes pasos cuando al crear las VM:

1. Establezca el adaptador de red de la VM en el conmutador lógico de carga de trabajo:
   1. En el recuadro de diálogo **Nueva máquina virtual**, pulse el separador **Personalizar hardware**.
   2. En el menú **nuevo dispositivo**, seleccione **Red** y pulse **Añadir**.
   3. En el adaptador de red recién añadido, seleccione el conmutador lógico de superposición de carga de trabajo en el menú. El nombre de ejemplo del conmutador es **overlay-ls**.

   Asegúrese de no seleccionar el conmutador **Tránsito de carga de trabajo**.
   {:important}

2. Identifique una dirección IP disponible para la VM:
   *  La dirección IP debe estar en el rango `192.168.10.0/24`. Tenga en cuenta que la dirección IP `192.168.10.1` está reservada (consulte el **Paso 3**).
   *  Cuando configure el sistema de redes del sistema operativo que se ejecuta en la máquina virtual, utilice la dirección IP seleccionada y la máscara de `255.255.255.0`.

   El cliente es el responsable de gestionar el rango de direcciones IP a las que ha asignado las VM.
   {:note}

3. Asignar la pasarela predeterminada de la VM como `192.168.10.1`. Esta es la dirección IP del puerto de direccionador de enlace descendente en el direccionador lógico de nivel 1 del cliente y está conectada al mismo conmutador lógico de superposición que las máquinas virtuales de carga de trabajo.

## Habilitación de la regla SNAT
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

NSX-T habilita la regla SNAT de forma predeterminada. Para obtener información sobre cómo modificar las reglas existentes, consulte
[Configurar NAT de origen y de destino en un direccionador lógico de nivel 0](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.4/administration/GUID-45949ACD-9029-4674-B29C-C2EABEB39E1D.html){:new_window}.

## Procedimiento para identificar los detalles de subredes del cliente
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

Los direccionadores lógicos **Customer-T1-LR** y **Customer-T0-LR**, así como los extremos
**cust-nsx-edge0** y **cust-nsx-edge1** están pensados para su propio uso, por lo que los puede modificar para definir más reglas NAT para el tráfico de entrada y de salida. Estas reglas solo deben utilizar direcciones IP de las subredes públicas o privadas del cliente que se han solicitado en su nombre.

Para identificar los detalles de las subredes del cliente para que pueda utilizar las direcciones IP solicitadas, siga los pasos siguientes en el cliente web de NSX-T:

1. Pulse el separador **Redes avanzadas y seguridad**.
2. En el panel de la izquierda, pulse **Entramado** y, a continuación, seleccione
**Nodos** en la lista desplegable.
3. En el separador, seleccione **Nodos de transporte de extremo**.
4. Pulse sobre uno de los extremos de cliente. Por ejemplo, **cust-nsx-edge0**. Se mostrarán las subredes de cliente pública y privada en el campo **Descripción**.

Encontrará más detalles sobre las subredes del cliente siguiendo estos pasos en el {{site.data.keyword.slportal}}:

1. Pulse **Redes > Gestión de IP > Subredes**.
2. Pulse el menú de filtro y en el campo **Subred** escriba el identificador tal como aparece en la descripción de **customer-nsx-edge0** del cliente web de NSX-T.
3. Revise las notas que se muestran para las direcciones IP. Estas notas identifican cuáles de las subredes y direcciones IP se han solicitado y utilizado durante la configuración inicial.

   No utilice las direcciones IP que se ha solicitado y utilizado durante la configuración inicial. Sin embargo, puede utilizar otras direcciones IP en estas subredes según sus requisitos. Para configurar reglas adicionales de conversión de direcciones de red, consulte [Gestión de reglas NAT](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}.
   {:important}

## Enlaces relacionados
{: #vc_nsx-t_esg_config-related}

* [Consideraciones sobre el cambio de artefactos de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
