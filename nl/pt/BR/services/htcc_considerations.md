---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# HyTrust CloudControl on IBM Cloud Visão Geral

O serviço HyTrust CloudControl on {{site.data.keyword.cloud}} cumpre e controla a conformidade com relação a padrões de segurança e fornece os recursos detalhados de controle de acesso baseado na função (RBAC), aprovação e auditoria. Quando combinado com o HyTrust DataControl, o serviço pode assegurar que as máquinas virtuais e os dados de carga de trabalho não deixem uma região, um cluster ou um servidor ESXi específico no {{site.data.keyword.CloudDataCent_notm}}.

**Disponibilidade:** esse serviço está disponível apenas para instâncias que estão executando o vSphere 6.5 e que são implementadas ou submetidas a upgrade para a V2.3 ou liberações mais recentes.

## Componentes do HyTrust CloudControl on IBM Cloud

Um par altamente disponível (HA) de dispositivos HyTrust CloudControl (HTCC) é implementado no cluster padrão no modo ativo-passivo.

Cada par de dispositivos HTCC é implementado na mesma sub-rede móvel privada que é especificada para as máquinas virtuais (VMs) de gerenciamento, como NSX Manager, vCenter Server Appliances e Platform Services Controller. O par de dispositivos age como um proxy para os hosts vSphere, dispositivo vCenter Server e NSX Manager de uma instância. Portanto, os usuários acessam os hosts do vSphere, vCenter Server Appliance e NSX Manager por meio de um endereço published IP (PIP) que é designado pelo administrador em vez do endereço real IP (RIP) que é designado pelo IBM Cloud.

Os dispositivos HTCC são integrados ao Microsoft Active Directory para cumprir o controle de acesso baseado na função.

## Considerações ao remover o HyTrust CloudControl on IBM Cloud

Antes de remover o serviço HyTrust CloudControl no {{site.data.keyword.cloud_notm}}, assegure-se de desativar **Criação de área segura de senha raiz**, se configurado, e de excluir todos os hosts protegidos do CloudControl.

## Links relacionados

* [Solicitando HyTrust CloudControl no {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Gerenciando o HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [HyTrust Website](https://www.hytrust.com/)
