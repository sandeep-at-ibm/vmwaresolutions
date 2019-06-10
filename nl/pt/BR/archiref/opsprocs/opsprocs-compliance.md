---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-16"

---

# Conformidade
{: #opsprocs-compliance}

A conformidade é um conjunto de requisitos necessários para atender aos controles mínimos estabelecidos por uma agência regulamentar ou pelas melhores práticas do mercado. As estruturas de conformidade de regulamentação são geralmente amplas e fornecem orientação sobre uma grande gama de tecnologia e a melhor prática do mercado dos fornecedores é geralmente uma tecnologia específica para lidar com os riscos tecnológicos.

Para sua instância do vCenter Server, sugerimos que a segurança seja gerenciada usando uma pós-implementação de equipe dedicada. Essa separação de obrigações deve aumentar e monitorar a postura de segurança de sua instância. O HyTrust CloudControl pode ajudar suas equipes com a separação baseada em função.

O HyTrust DataControl e o KeyControl podem auxiliar no fornecimento de proteção de carga de trabalho, como a criptografia de itens inativos e o geofencing. Talvez você se interesse em implementar o serviço Caveonix RiskForesight para obter ajudar em requisitos de conformidade, além de gerenciamento forense e risco cibernético.

Os Guias de reforço de segurança do VMware fornecem orientação prescritiva sobre como implementar e operar produtos VMware de maneira segura. Guias para o vSphere são fornecidos em um formato de planilha de fácil compreensão, com metadados ricos para permitir a classificação de diretrizes e a avaliação de risco. Eles também incluem exemplos de script para permitir a automação de segurança. São fornecidos documentos de comparação que listam as mudanças na orientação em versões sucessivas do guia.

Embora muitos dos controles documentados nos Guias de reforço de segurança do VMware tenham sido incorporados na arquitetura de referência do {{site.data.keyword.vmwaresolutions_full}} e, portanto, implementados automaticamente, certifique-se de customizar a postura de segurança da plataforma às suas próprias necessidades e à política corporativa. Os Guias de reforço de segurança do VMware fornecem os controles específicos de tecnologia necessários para a realização dessa revisão. O Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} automatiza essa tarefa de conformidade e fornece orientação adicional de agência regulamentar.

O vRealize Operations Manager permite monitorar objetos do VMware em busca de violações com relação às regras de conformidade no Guia de configuração de segurança do vSphere. Os alertas de conformidade são acionados na instância, nos hosts, nas máquinas virtuais, nos grupos de portas distribuídos ou nos comutadores distribuídos do vCenter Server, permitindo a investigação da violação de conformidade. Além disso, para clientes interessados na conformidade da Health Insurance Portability and Accountability Act (HIPAA) e do Padrão de Segurança de Dados do Setor de Cartão de Pagamento (PCI DSS), os Pacotes de Conformidade do vRealize Operations Manager podem ser transferidos por download no website do VMWare Solutions Exchange, licenciados e instalados. Eles fornecem Alertas, Políticas e Relatórios para validar os recursos do vSphere com relação aos guias de reforço da HIPAA e do PCI.


## Links relacionados
{: #opsprocs-compliance-links}

* [Guia de reforço de segurança do VMware](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Guia de segurança do vSphere](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-security-guide.pdf){:new_window}
* [Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-fsa_considerations#fsa_considerations)
* [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)
* [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-f5_considerations#f5_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htcc_considerations.html#hytrust-cloudcontrol-on-ibm-cloud-overview)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_considerations.html#hytrust-datacontrol-on-ibm-cloud-overview)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htkc_considerations.html#hytrust-keycontrol-on-ibm-cloud-overview)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/caveonix/caveonix-intro.html#caveonix-riskforesight)
* [Gerenciamento de operações no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
