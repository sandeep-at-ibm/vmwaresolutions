---

copyright:

  years:  2019, 2021

lastupdated: "2021-10-21"

subcollection: vmwaresolutions


---

{{site.data.keyword.attribute-definition-list}}

# IBM Hyper Protect Crypto Services overview
{: #htdc-hpcs-hpcs-overview}

IBM Hyper Protect Crypto Services (IBM HPCS) is a single-tenant key management service, backed by a FIPS140-2 level 4 certified Hardware Security Module (HSM), that supports Keep Your Own Key (KYOK). With IBM HPCS, you can move your most mission critical workloads to the {{site.data.keyword.cloud_notm}} while using the highest level of security to prevent unauthorized access to their sensitive data. You maintain complete control over their keys and data in the cloud and no one, including {{site.data.keyword.cloud_notm}} admins, has access to the customer data. 

Additionally, no single person has access to the full key. At a high level, the IBM HPCS has the following components:
* Crypto unit - a singular unit that represents a piece of hardware, the HSM, and the corresponding software stack, both are dedicated to a single tenant.
* Service instance - a cluster of crypto units, which operates as a single logical entity to provide redundancy and scalability.

The IBM HPCS service has the following key features:
* It is built on IBM LinuxONE technology and it uses Secure Service Container (SSC) to provide enterprise-level security.
* Supports Enterprise Public-Key Cryptography Standards (PKCS) #11, so your applications can integrate cryptographic operations such as digital signing and validation through Enterprise PKCS#11 (EP11 API). The EP11 library provides an interface similar to the industry-standard PKCS #11 application programming interface (API). For more information about EP11 library structure, see the EP11 library structure reference guide.
* Uses frameworks such as gRPC to enable remote application access. gRPC is a modern open source high-performance remote procedure call (RPC) framework that can connect services in and across data centers for load balancing, tracing, health checking, and authentication. Applications access Hyper Protect Crypto Services by calling EP11 API remotely over gRPC.
* Dedicated keystore to ensure data isolation and security. Privileged users are locked out for protection against abusive use of system administrator credentials or root user credentials.

**Next topic:** [System context](/docs/vmwaresolutions?topic=vmwaresolutions-htdc-hpcs-system-context)

## Related links
{: #htdc-hpcs-hpcs-overview-related}

* [Getting started with {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services](/docs/hs-crypto?topic=hs-crypto-get-started)
