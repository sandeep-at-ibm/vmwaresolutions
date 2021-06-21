---

copyright:

  years:  2016, 2020

lastupdated: "2020-04-15"

subcollection: vmwaresolutions


---

# Step 3 - Application configuration
{: #caveonix-step3}

This step uses the Caveonix RiskForesight configuration script. For the “all-in-one” deployment, this script is started through the {{site.data.keyword.vmwaresolutions_full}} automation.

For scaling, the client needs to call the script to provision the partially distributed topology or the fully distributed topology. 

The script configures the following RiskForesight services:
- Caveonix Apps (API, Central Collector)
- Elastic Search
- PostgresSQL
- Remote Collector
- UI
- Kafka
- Kibana
- Certificates for all services

At the end of this step, the application components are installed on the required virtual machines.

**Next topic:** [Step 4 - Application setup](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix-step4)
