---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Paso 3 - Configuración de aplicaciones
{: #caveonix-step3}

En este paso se utiliza el script de configuración de Caveonix RiskForesight. Para el despliegue "todo en uno", este script se inicia a través de la automatización de IBM Cloud for VMware Solutions.

Para el escalado, el cliente tiene que llamar al script para suministrar las topologías parcial o completamente distribuidas. El script configura los servicios de RiskForesight:
- Apps de Caveonix (API, recopilador central)
- Búsqueda elástica
- PostgresSQL
- Recopilador remoto
- Interfaz de usuario
- Kafka
- Kibana
- Certificados para todos los servicios

Al final de este paso, los componentes de la aplicación se instalan en las máquinas virtuales necesarias (VM).
