---

copyright:

  years:  2016, 2020

lastupdated: "2020-05-05"

keywords: disaster recovery, request DR services, DR managed service

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}

# Managed Disaster Recovery Services
{: #managing_zerto_services}

The Zerto service provides replication and disaster recovery capabilities. These capabilities can be integrated into the deployment offerings to protect and recover data in your VMware virtual environment on {{site.data.keyword.cloud}}.

When you request Managed Disaster Recovery Services, a fully managed disaster recovery (DR) environment can be deployed by using both Zerto DR software and IBM Resiliency Services.

The following models for Managed Disaster Recovery Services are available.

## IBM Orchestrated Managed Disaster Recovery Services
{: #managing_zerto_services-orchestrated}

This model is suitable if you're using the Zerto offering.

In this model, the {{site.data.keyword.cloud_notm}} Resiliency Orchestration service is provisioned for Zerto. This model can continuously protect the virtual machines, operating systems, and data on the {{site.data.keyword.cloud_notm}}, with uninterrupted DR testing, RTO/RPO (Recovery Time Objective/Recovery Point Objective) visibility, fail-over and fail-back capability.

All functions are managed from the {{site.data.keyword.cloud_notm}} Resiliency Orchestration dashboard by IBM Resiliency Services Global Command Center.

For more information, see [IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration){:external}.

## IBM-Managed Disaster Recovery Services (without Orchestration)
{: #managing_zerto_services-without-orchestrated}

In this model, a fully managed DR solution is provisioned for Zerto. This model is suitable if you want a managed service for Zerto Virtual Replication only, without the {{site.data.keyword.cloud_notm}} Resiliency Orchestration service on the {{site.data.keyword.cloud_notm}}.

For more information, see [IBM Resiliency Disaster Recovery as a Service](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top){:external}.

## Procedure to request Managed Disaster Recovery Services
{: #managing_zerto_services-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Overview** from the left navigation pane.
2. Scroll down to the **Services** section, and then click **Managed Disaster Recovery Services** on the **Professional Services** card.
3. On the **Zerto** page, review the description and technical specifications for Zerto as a managed service, and then click **Continue**.
4. Specify the configuration settings according to your requirements or accept the default values.
5. Click **vCenter Server** to add the service to one of your instances.
6. To add the service while you order a new instance, click **Add to New Instance**, and then continue with ordering a new [vCenter Server](/docs/vmwaresolutions?topic=vmwaresolutions-vc_orderinginstance) instance.
7. To add the service to an existing instance, click **Add to Existing Instance**, select the instance that you want from the list, and then confirm that you want to proceed with the order by clicking **Provision**.

## Related links
{: #managing_zerto_services-related}

* [Ordering, viewing, and deleting services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
