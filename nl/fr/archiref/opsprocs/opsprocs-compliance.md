---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-31"

---

# Conformité
{: #opsprocs-compliance}

La conformité est un ensemble d'exigences nécessaires pour respecter les contrôles minimaux établis par un organisme de réglementation ou les pratiques exemplaires de l'industrie. Les structures de conformité réglementaire sont généralement des structures générales qui fournissent des orientations sur un large éventail de technologies, tandis que les meilleures pratiques des fournisseurs de l'industrie sont généralement des technologies spécifiques qui permettent de traiter les risques technologiques.

Pour votre instance vCenter Server, il est recommandé que la sécurité soit gérée par une équipe dédiée après le déploiement. Cette séparation des tâches devrait augmenter et surveiller la posture de sécurité de votre instance. HyTrust CloudControl peut aider vos équipes avec la séparation basée sur les rôles.

HyTrust DataControl et KeyControl peuvent vous aider à fournir une protection de la charge de travail telle que le chiffrement au repos et la géoprotection. Vous souhaiterez peut-être déployer le service Caveonix RiskForesight pour vous aider non seulement dans vos exigences de conformité, mais aussi dans la gestion des cyber-risques et la gestion contextuelle.

Les guides de renforcement de la sécurité VMware fournissent des conseils normatifs sur la façon de déployer et d'utiliser les produits VMware de manière sécurisée. Les guides vSphere sont fournis sous la forme d'une feuille de calcul facile à utiliser, avec des métadonnées riches pour permettre la classification des directives et l'évaluation des risques. Ils incluent également des exemples de scripts pour activer l'automatisation de la sécurité. Des documents de comparaison sont fournis qui énumèrent les changements apportés à la ligne directrice dans les versions successives du guide.

Bien que de nombreux contrôles documentés dans les guides de renforcement de la sécurité VMware aient été incorporés dans l'architecture de référence de {{site.data.keyword.vmwaresolutions_full}} et, par conséquent, automatiquement déployés, assurez-vous d'adapter la posture de sécurité de la plateforme à vos propres besoins et politiques d'entreprise. Les guides de renforcement de la sécurité VMware fournissent les contrôles technologiques spécifiques dont vous avez besoin pour mener à bien cette révision. Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} automatise cette tâche de conformité et fournit des directives supplémentaires en matière de réglementation.

vRealize Operations Manager vous permet de surveiller les objets VMware en cas de violation des règles de conformité du Guide de configuration de la sécurité vSphere. Les alertes de conformité se déclenchent sur l'instance vCenter Server, les hôtes, les machines virtuelles, les groupes de ports distribués ou les commutateurs distribués, et permettent l'enquête de la violation de conformité. De plus, pour les clients intéressés par la conformité à la Health Insurance Portability and Accountability Act (HIPAA) et à la Payment Card Industry Data Security Standard (PCI DSS), vous pouvez télécharger les packs de conformité de vRealize Operations Manager du site VMware Solutions Exchange, obtenir une licence et les installer. Ces packs de conformité fournissent des alertes, des politiques et des rapports pour valider les ressources vSphere par rapport aux guides de renforcement HIPAA et PCI.


## Liens connexes
{: #opsprocs-compliance-links}

* [VMware security hardening guide](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [vSphere security guide](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-security-guide.pdf){:new_window}
* [Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Gestion des opérations sur {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
