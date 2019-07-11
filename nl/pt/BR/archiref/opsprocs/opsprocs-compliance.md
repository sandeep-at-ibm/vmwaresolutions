---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-31"

---

# Conformidade
{: #opsprocs-compliance}

A conformidade é um conjunto de requisitos necessários para atender aos controles mínimos estabelecidos por uma agência regulamentar ou pelas melhores práticas do mercado. As estruturas de conformidade de regularidade são geralmente estruturas amplas que fornecem orientação sobre uma ampla variedade de tecnologias, enquanto as melhores práticas da indústria de fornecedores são geralmente tecnologia específica para tratar dos riscos tecnológicos.

Para sua instância do vCenter Server, recomenda-se que a segurança seja gerenciada usando uma pós-implementação de equipe dedicada. Essa separação de obrigações deve aumentar e monitorar a postura de segurança de sua instância. O HyTrust CloudControl pode ajudar suas equipes com a separação baseada em função.

O HyTrust DataControl e o KeyControl podem ajudá-lo na entrega de proteção de carga de trabalho, como criptografia e geofencing em repouso. Você pode estar interessado em implementar o serviço Caveonix RiskForesight para ajudá-lo, não apenas em seus requisitos de conformidade, mas também em risco cibernético e gerenciamento forense.

Os Guias de reforço de segurança do VMware fornecem orientação prescritiva sobre como implementar e operar produtos VMware de maneira segura. Os guias para o vSphere são fornecidos em um formato de planilha fácil de usar, com metadados ricos para permitir a classificação de diretrizes e a avaliação de risco. Eles também incluem exemplos de script para permitir a automação de segurança. São fornecidos documentos de comparação que listam as mudanças na orientação em versões sucessivas do guia.

Embora muitos dos controles documentados nos Guias de reforço de segurança do VMware tenham sido incorporados na arquitetura de referência do {{site.data.keyword.vmwaresolutions_full}} e, portanto, implementados automaticamente, certifique-se de customizar a postura de segurança da plataforma às suas próprias necessidades e à política corporativa. Os Guias de reforço de segurança do VMware fornecem os controles específicos de tecnologia que são necessários para a execução dessa revisão. O Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} automatiza essa tarefa de conformidade e fornece orientação adicional de agência regulamentar.

O vRealize Operations Manager permite monitorar objetos do VMware em busca de violações com relação às regras de conformidade no Guia de configuração de segurança do vSphere. Os alertas de conformidade são acionados na instância, nos hosts, nas máquinas virtuais, nos grupos de portas distribuídos ou nos comutadores distribuídos do vCenter Server, permitindo a investigação da violação de conformidade. Além disso, para clientes que estão interessados na conformidade do Health Insurance Portability and Accountability Act (HIPAA) e do Padrão de Segurança de Dados do Setor de Cartão de Pagamento (PCI DSS), os vRealize Operations Manager Compliance Packs podem ser transferidos por download por meio do website do VMWare Solutions Exchange, licenciados e instalados. Eles fornecem Alertas, Políticas e Relatórios para validar os recursos do vSphere com relação aos guias de reforço da HIPAA e do PCI.


## Links relacionados
{: #opsprocs-compliance-links}

* [Guia de reforço de segurança do VMware](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Guia de segurança do vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-security-guide.pdf){:new_window}
* [Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Gerenciamento de operações no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
