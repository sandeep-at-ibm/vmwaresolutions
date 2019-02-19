---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Step 3 - Application configuration
{: #caveonix-step3}

This step uses the Caveonix RiskForesight configuration script. For the “all-in-one” deployment, this script is started through the IC4VS automation. For scaling, the client needs to call the script to deploy the partially or fully distributed deployment topologies. The script configures the RiskForesight services:
-	Caveonix Apps (API, Central Collector)
-	Elastic Search
- PostgresSQL
-	Remote Collector
-	UI
-	Kafka
-	Kibana
-	Certificates for all services

At the end of this step, the application components are installed on the required virtual machines (VMs).

## Related links
{: #caveonix-step3-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
