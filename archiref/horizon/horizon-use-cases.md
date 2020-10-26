---

copyright:

  years:  2019, 2020

lastupdated: "2020-10-22"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Use case definitions and desktop assessments
{: #horizon-use-cases}

A successful VMware Horizon 7 deployment requires a thorough understanding of the users and applications that are onboarded into the service. Without a good understanding of these items, the resources that are provided to the users are not sized correctly, leading to a bad user experience that hurts adoption of the service.

Use case definition creates a detailed definition of the users that are onboarded into the service. This definition contains details about the users and their expected work patterns. It can include information like which business unit they are a part of, which applications they use, the hours they are primarily expected to use the service, where they access the service from, and any other requirements they might have. Use Case Definitions help drive the service design and ensure that all business and user requirements are met.

Desktop assessments provide two functions when designing a Horizon 7 service. A desktop assessment validates the use case definitions and complete any gaps that might exist in those definitions. They also provide performance metrics around the desktops, and these metrics are utilized for sizing the environment to ensure that there is enough CPU, RAM, and storage resources.

A desktop assessment requires a tool like Liquidware Stratusphere or Lakeside Systrack to collect data from endpoints. The tool should run for at least 30 days to gather enough information to understand the performance trends for the environment.  

## Estimating data egress cost
{: #horizon-use-cases-estimate-egress}

Unlike on-premises, deploying Horizon 7 incurs data egress cost based on the amount of data egress traffic your environment generates. It is important to understand and estimate the data egress traffic.

### Understanding different types of data egress traffic
{: #horizon-use-cases-understand-egress-traffic}

Depending on your deployment use case, you might be incurring cost for some or all of the following types of data egress traffic:
* End-user traffic via internet - You have configured your environment where your users connect to their virtual desktops on {{site.data.keyword.cloud_notm}} remotely via the internet. Any data leaving the {{site.data.keyword.cloud_notm}} data center incurs egress charge. Egress data consists of the following components: outbound data from Horizon 7 protocols and outbound data from remote experience features (for example, remote printing). While the former is typically predicable, the latter has more variance and depends on the exact activity of the user
* End-user traffic via on-premises - You have configured your environment where your users connect to their virtual desktops on {{site.data.keyword.cloud_notm}} via your on-premises data center. In this case, you must link your data center with the {{site.data.keyword.cloud_notm}} data center using VPN. Any data traffic leaving the {{site.data.keyword.cloud_notm}} data center back to your data center incurs egress charge. And if you have Cloud Pod Architecture (CPA) configured between the on-premises environment and the {{site.data.keyword.cloud_notm}} environment, you incur egress charge for any CPA traffic between the two pods (although CPA traffic is typically fairly light)
* External application traffic - You have configured your environment where your virtual desktops on {{site.data.keyword.cloud_notm}} has to access applications hosted either in your on-premises environment or in another cloud. Any data traffic leaving the {{site.data.keyword.cloud_notm}} data center to these other data centers incurs egress charge

Data ingress (that is, data flowing into the {{site.data.keyword.cloud_notm}} data center, and data between {{site.data.keyword.cloud_notm}} data centers, is free of charge.

### Estimating Data Egress Traffic with SysTrack from Lakeside
{: #horizon-use-cases-estimate-data-egress}

Since the data egress cost is priced per GB, the best way to estimate your data egress cost is to estimate your likely data egress traffic by using a monitoring tool in your existing on-premises environment (whether it’s already virtualized or not). Make sure that you estimate the different types of data egress traffic listed above separately as applicable. One such monitoring tool is SysTrack from Lakeside Software.

[Lakeside’s SysTrack](https://www.lakesidesoftware.com/product){:external} workplace analytics solution contains an extensive set of tools to provide relevant planning information for [desktop transformation](https://www.lakesidesoftware.com/solutions/desktop-transformation){:external}. For information about the SysTrack Desktop Assessment (SDA), see the [SysTrack Desktop Assessment (SDA) - Solution Brief](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/solutionbrief/microsites/latitude/docs/solution-brief.pdf){:external}. Through the SDA, customers can collect detailed environmental information, including recommendations for deployment options and resource requirements, with only the need to deploy the SysTrack agent to systems being considered for transformation. For advanced cases, the on-premises version of SysTrack can be used as well. This guide  makes the assumption that such a deployment is already in place. For more setup details or questions about the SDA, the [Quick Start Guide](https://assessment.vmware.com/SDA/ViewDocument?document=Quick_Start_Guide){:external} is a good resource.

After SysTrack is deployed in the environment, it immediately begins collecting relevant information from devices on which it’s installed. For this guide we’ll focus on the most interesting facets of data collection for the network:
* Per Device Network Usage
* Per Session Protocol Bandwidth Usage
* Per Application (and Destination) Bandwidth Usage

The key is thinking about how best to combine these pieces of information into something that’s useful for planning costs. Because the ingress data is free for {{site.data.keyword.cloud_notm}}, we’ll focus on the egress data as observed from the devices in the collection. That takes the form of “transmitted” data from that device to other destinations, and you’ll see more details about this as we go into methodology we suggest.

With SysTrack, you can make use of two different styles of calculation depending on the level of detail you’d like to see. We’ve created several dashboards that customers can use to easily visualize this information in SysTrack.

All numbers in the dashboards are measured in bits, not bytes.
{:note}

### Basic network egress bandwidth calculation
{: #horizon-use-cases-basic-egress}

The Horizon Sizing Tool dashboard provides some basic numbers to help you plan your migration to the VMware cloud. The following table breaks users down into categories based on egress bandwidth consumption. Resource consumption metrics are supplied for each category as well as egress bandwidth consumption for applications and three remote display protocols: ICA, Blast, and PCoIP.

The resource consumption metrics can be fed into some of VMware’s sizing tools such as the [Horizon Sizing Tool](https://code.vmware.com/article-detail/-/asset_publisher/8n011DnrSCHt/content/horizon-sizing-tool-intro){:external} (Requires VMware Partner Central account). These tools provide guidance on how to plan for the number and size of systems you are deploying.

### Advanced network egress bandwidth calculation
{: #horizon-use-cases-advanced-egress}

The Advanced Horizon Sizing Tool offers advanced sizing calculations, which can be used to estimate costs around migrating to the {{site.data.keyword.cloud_notm}}. {{site.data.keyword.cloud_notm}} pricing is based around the level of data that is transmitted from the cloud back to the client (that is, egress bandwidth consumption).

Within the dashboard, each user is put into a category based on egress bandwidth consumption. This can be based on actual SysTrack data if you are migrating from an existing virtual environment or estimated if migrating from a physical environment.

You can select the protocol you would like to use to estimate values for users on physical machines, as well as the type of egress data displayed – protocol, application, or a combination of both.

A summary table shows these categories and tells you the total and average for egress bandwidth consumption. This same data is also presented in graph form for a more visual presentation:

You can also see more detail on a per user basis depending on the category selected in the summary table. The Selected Category Users table shows total and average bandwidth consumption as well as calculation type, which indicates which data source was used to generate the consumption values.

Here is an example of how to determine monthly egress bandwidth per VM in gigabytes.

If you want to calculate the egress bandwidth for an average VM, you can take the “Total Tb 30 Days” and “Users” values in the advanced dashboard summary table and perform the following calculation:

`Monthly GB egress bandwidth per VM = (([Total Tb 30 Days]/8) * 1024) / [Users]`

If the Total TB 30 Days result is 9.67, and the number of users is 92, the calculation would become this:

`Monthly GB egress bandwidth per VM = ((9.67/8) * 1024) / 92 = 13.5 GB`
