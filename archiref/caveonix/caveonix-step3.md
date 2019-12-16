---

copyright:

  years:  2016, 2019

lastupdated: "2019-10-21"

subcollection: vmware-solutions


---

# Step 3 - Application configuration
{: #caveonix-step3}

This step uses the Caveonix RiskForesight configuration script. For the “all-in-one” deployment, this script is started through the {{site.data.keyword.vmwaresolutions_full}} automation.

For scaling, the client needs to call the script to provision the partially or fully distributed topologies. The script configures the RiskForesight services:
- Caveonix Apps (API, Central Collector)
- Elastic Search
- PostgresSQL
- Remote Collector
- UI
- Kafka
- Kibana
- Certificates for all services

At the end of this step, the application components are installed on the required virtual machines (VMs).

**Next topic:** [Step 4 - Application setup](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix-step4)
