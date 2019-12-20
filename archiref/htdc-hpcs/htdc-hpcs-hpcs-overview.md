---

copyright:

  years:  2019

lastupdated: "2019-12-19"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Hyper Protect Crypto Services overview
{: #htdc-hpcs-hpcs-overview}

IBM Hyper Protect Crypto Services (IBM HPCS) is a single-tenant key management service, backed by a FIPS140-2 level 4 certified Hardware Security Module (HSM), that supports Keep Your Own Key (KYOK). With IBM HPCS, customers can now move their most mission critical workloads to the IBM Cloud with the assurance of using the highest level of security to prevent unauthorized access to their sensitive data. Customers maintain complete control over their keys and data in the cloud and no one, including IBM Cloud admins, has access to the customer data. Additionally, no single person has access to the full key. At a high level the IBM HPCS consists of the following components:

* Crypto unit - a singular unit representing a piece of hardware, the HSM, and the corresponding software stack, both are dedicated to a single tenant.
* Service instance - a cluster of crypto units, which operates as a single logical entity to provide redundancy and scalability.

The IBM HPCS service has the following key features:
* Built on IBM LinuxONE technology and using Secure Service Container (SSC) to provide enterprise-level security.
* Supports Enterprise Public-Key Cryptography Standards (PKCS) #11, so your applications can integrate cryptographic operations such as digital signing and validation via Enterprise PKCS#11 (EP11 API). The EP11 library provides an interface similar to the industry-standard PKCS #11 application programming interface (API). For more information about EP11 library structure, see the EP11 library structure reference guide.
* Uses frameworks such as gRPC to enable remote application access. gRPC is a modern open source high-performance remote procedure call (RPC) framework that can connect services in and across data centers for load balancing, tracing, health checking, and authentication. Applications access Hyper Protect Crypto Services by calling EP11 API remotely over gRPC.
* Dedicated keystore to ensure data isolation and security. Privileged users are locked out for protection against abusive use of system administrator credentials or root user credentials.

**Next topic:** [System context](/docs/services/vmwaresolutions?topic=vmware-solutions-htdc-hpcs-system-context)

## Related links
{: #htdc-hpcs-hpcs-overview-related}

* [Getting started with IBM Cloud Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started)
