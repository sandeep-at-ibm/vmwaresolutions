---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

# Etapa 3-Configuração do aplicativo
{: #caveonix-step3}

Esta etapa usa o script de configuração do Caveonix RiskForesight. Para a implementação "tudo em um", esse script é iniciado por meio da automação do IC4VS.

Para o ajuste de escala, o cliente precisa chamar o script para provisionar as topologias parcialmente ou totalmente distribuídas. O script configura os serviços RiskForesight:
- Apps Caveonix (API, Coletor Central)
- Procura Elástica
- PostgresSQL
- Coletor Remoto
- UI
- Kafka
- Kibana
- Certificados para todos os serviços

No final dessa etapa, os componentes do aplicativo são instalados nas máquinas virtuais (MVs) necessárias.

## Links relacionados
{: #caveonix-step3-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
