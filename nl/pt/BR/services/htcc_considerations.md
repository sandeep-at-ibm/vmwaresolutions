---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# HyTrust CloudControl on IBM Cloud Visão Geral

O serviço HyTrust CloudControl on {{site.data.keyword.cloud}} cumpre e controla a conformidade com relação a padrões de segurança e fornece os recursos detalhados de controle de acesso baseado na função (RBAC), aprovação e auditoria. Quando combinado com o HyTrust DataControl, o serviço pode assegurar que as máquinas virtuais e os dados de carga de trabalho não deixem uma região, um cluster ou um servidor ESXi específico no {{site.data.keyword.CloudDataCent_notm}}.

**Disponibilidade:** esse serviço está disponível somente para instâncias
que estão executando o vSphere 6.5 e que são implementadas na (ou atualizadas para) a V2.3 ou liberações mais recentes.

## Componentes do HyTrust CloudControl on IBM Cloud

Um par altamente disponível (HA) de dispositivos HyTrust CloudControl (HTCC) é implementado no cluster padrão no modo ativo-passivo.

Cada par de dispositivos HTCC é implementado na mesma sub-rede móvel privada que é especificada para as máquinas virtuais (VMs) de gerenciamento, como NSX Manager, vCenter Server Appliances e Platform Services Controller.

O par de dispositivos age como um proxy para os hosts vSphere, dispositivo vCenter Server e NSX Manager de uma instância. 
Portanto, os usuários acessam o hosts vSphere, o vCenter Server Appliance e o NSX Manager por meio de um endereço IP publicado (PIP)
que é designado pelo administrador em vez de o endereço IP real (RIP) que é designado pelo {{site.data.keyword.cloud}}.

Os dispositivos HTCC se integram ao Microsoft Active Directory para cumprir o controle de acesso baseado em função.

## Considerações ao remover o HyTrust CloudControl on IBM Cloud

Antes de remover o serviço HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, certifique-se de
desativar a **Transferência de senha raiz**, se configurada, e de excluir todos os hosts protegidos do
HyTrust CloudControl.

## Links relacionados

* [Solicitando HyTrust CloudControl no {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Gerenciando o HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas mais frequentes](../vmonic/faq.html)
* [HyTrust Website](https://www.hytrust.com/)
