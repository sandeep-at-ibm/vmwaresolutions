---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Supervisión de parámetros y componentes
{: #vcshcx-monitoring}

## Uso del optimizador de WAN para la supervisión
{: #vcshcx-monitoring-using-wan}

El dispositivo de optimización de Silver Peak WAN que se despliega como parte de HCX no obtiene su interfaz de gestión configurada. La interfaz de usuario web es una herramienta valiosa si quiere maximizar el rendimiento del tráfico de línea base y limitar el uso del ancho de banda de migración de red.

Solo el tráfico del túnel WAN de HCX CGW Gateway fluye a través del dispositivo del optimizador de WAN. Por tanto, no puede supervisar el tráfico de la L2 extendida.
{:note}

### Configuración de la interfaz de usuario
{: #vcshcx-monitoring-config-ui}

Aparte de la configuración de una dirección IP para la interfaz de usuario web, no realice cambios en la configuración del dispositivo optimizador de WAN a menos que se lo indique el personal de soporte de VMware o {{site.data.keyword.IBM}}.   

Para configurar la interfaz de usuario web del optimizador de WAN:
1.	Busque el dispositivo de la máquina virtual (VM) del optimizador de WAN en el cliente de vCenter.
2.	Abra una consola en la máquina virtual que utilice el cliente de vCenter.
3.	Dentro de la consola, pulse **F4** para configurar la interfaz de gestión.
4.	Seleccione la opción para configurar una IP estática.
5.	Utilice una dirección IP en la pasarela predeterminada y el rango de IP portátil asignado de {{site.data.keyword.cloud}} de gestión.
6.	Pulse **Aplicar** en la siguiente pantalla para guardar.
7.  Pulse los valores de edición para la máquina virtual del optimizador de WAN dentro de la consola de vCenter.
8.	Seleccione **Conectado al encender** y **Conectado para el adaptador de red 1**.
9.	Pulse **Aceptar** para guardar.
10.	Busque CGW-<xxx>-WANOPT en vCenter.
11.	Edite los valores en la máquina virtual.
12.	Pulse el recuadro de selección para conectar el adaptador de red 1.
13.	Pulse **Aceptar**.
14.	Vaya a `https://<configured_WAN_OPT_IP>`.
15.	Inicie sesión con el usuario predeterminado `admin` y la contraseña de `admin`.

Ahora ya puede utilizar la interfaz de usuario web del optimizador de WAN para supervisar las tasas de rendimiento, las proporciones de compresión y establecer restricciones de ancho de banda.

### Limitación de ancho de banda de migración
{: #vcshcx-monitoring-mig-bandwidth}

Antes de migrar las máquinas virtuales, realice una evaluación del enlace de red que se utiliza. Trabaje con los ingenieros de redes para la red que contiene la instancia de origen de vSphere o revise el uso de tráfico mensual o semanalmente. Limite el ancho de banda disponible para las migraciones si el tráfico atraviesa un enlace que es crítico para el negocio, especialmente si dicho enlace es inferior a 1 Gbps. Utilice el lado con el ancho de banda más limitado, que suele ser el lado del cliente.

Realice esta acción cuando despliegue los componentes de flota en la interfaz de usuario del cliente de HCX, pero el despliegue posterior requiere que vaya a la interfaz de usuario del optimizador de WAN.

Los cambios se pierden si vuelve a desplegar HCX CGW desde la interfaz de usuario web de HCX.
Esto establece los límites de ancho de banda únicamente para el tráfico de migración. El tráfico de la L2 extendida no se ve afectado por este valor.
{:note}

1. Inicie sesión en la interfaz de usuario web del optimizador de WAN.
2. En el separador **Configuración**, seleccione **Modelador** del menú desplegable.
3. En el recuadro **Ancho de banda máximo**, establezca el ancho de banda máximo disponible en el dispositivo optimizador de WAN en Kbps. No supere el ancho de banda máximo del enlace WAN. Para establecer el valor en Mbps, multiplique por 1.000. Para establecer el valor en Gbps, multiplique por 1.000.000. El valor predeterminado es 10 Gbps (10.000.000 Kbps).
4. Pulse **Aplicar**.

Para la limitación del ancho de banda de la L2 extendida, se puede utilizar QoS para UDP 500 y 4500 para el tráfico de túnel entre los dispositivos L2C.

## Supervisión de los componentes de HCX
{: #vcshcx-monitoring-hcx-comp}

Supervise los componentes de HCX, como HCX Manager, Cloud Gateway, el optimizador de WAN y el Concentrador de capa 2, de las siguientes formas:

- Configure HCX Manager para que envíe registros a un servidor Syslog. Utilice el programa de utilidad de gestión de dispositivos de
HCX Manager para ejecutar el mandato `https://<hcxhostname or
IP>:9443`.
- Configure un ping a una máquina virtual que se migre antes de la oscilación de red para cada red L2 extendida.
- Supervisar el estado de la máquina virtual del componente de HCX con VMware vRealize Operations Manager u otras herramientas de supervisión de máquinas virtuales de VMware.

## Uso de ancho de banda
{: #vcshcx-monitoring-band-use}

Utilice los métodos siguientes para supervisar el uso del ancho de banda y la latencia.

- El tráfico de vMotion se mejora utilizando la interfaz de usuario web del optimizador de WAN. El optimizador de WAN reduce drásticamente el tráfico que pasa por la WAN y reduce la pérdida de paquetes enviando paquetes redundantes. Se ha observado que el ratio típico de uso de ancho de banda de LAN a WAN es de aproximadamente 3:1 (350 Mbps LAN = 90-120 Mbps WAN).

- La migración basada en réplica (masiva) de máquinas virtuales dentro de HCX provoca que las máquinas virtuales se muevan con suministro grueso. Si bien no es un resultado deseado, la interfaz de usuario del optimizador de WAN revela un alto ratio entre el uso de LAN y WAN al mover datos de disco no utilizados. A la inversa, se observa que cuando se migran datos no comprimibles, como los datos de base de datos y medios digitales, el uso de WAN está en su nivel más alto y se acerca al uso de la LAN.

Observaciones:
- La migración de vMotion de una máquina virtual dentro de HCX no genera más rendimiento que la red de vMotion para un único host ESXi.
- Como la migración masiva puede tener múltiples migraciones en curso simultáneamente, logra un uso de ancho de banda mayor que una migración de vMotion. El ratio observado en un lado del cliente con enlaces de vMotion de 1 Gbps a los hosts de ESX era: Ocho réplicas = uso de ancho de banda de 1 vMotion.
- Mover espacio vacío en el disco genera un uso de LAN elevado con un ratio alto y, consecuentemente, un uso de WAN bajo. Tenga en cuenta que 1 Gbps parece ser el límite. De hecho, en este caso en particular, la red de vMotion solo es capaz de 1 Gbps, que es el cuello de botella.
- La migración de vMotion de una base de datos Oracle de múltiples TB. Con un enlace de WAN de 1 Gbps, la limitación es la red de vMotion de 1 Gbps.

## Tráfico de capa 2 extendida
{: #vcshcx-monitoring-stretched-layer-2-traffic}

El Concentrador de capa 2 del componente de flota de HCX tiene una limitación de ancho de banda de aproximadamente 4 Gbps para todo el tráfico de red L2 que lo atraviesa. Las redes extendidas individuales tienen un límite de ancho de banda de aproximadamente 1 Gbps o menos dependiendo del tipo de tráfico. Es posible tener muchas redes L2 extendidas en un único par de L2C (en teoría con un número máximo permitido de 4096
redes por par de L2C). Aunque la L2C está diseñada para detectar y proteger que los flujos de tráfico pequeños no se vean superados por los grandes flujos dentro del mismo par de L2C, podría resultar útil identificar si esta situación se está produciendo y traer más L2C para aumentar la capacidad de ancho de banda general.

El despliegue de varias L2C también puede ser beneficioso cuando existen varias vías de acceso entre el sitio del cliente y {{site.data.keyword.cloud}}, como por ejemplo enlace directo e Internet. Una sola red no se puede hacer redundante ni dar un mayor ancho de banda en múltiples pares de L2C.

Supervise el tráfico en todas las interfaces que utilizan el separador Supervisión de la máquina virtual de L2C. Si la velocidad de datos total se aproxima a 8 Gbps (4 Gbps entrada/salida), considere la posibilidad de añadir otro par de L2 y redistribuir las redes extendidas para equilibrar.

## Enlaces relacionados
{: #vcshcx-monitoring-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
