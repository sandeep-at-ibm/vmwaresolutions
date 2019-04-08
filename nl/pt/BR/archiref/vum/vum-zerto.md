---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# Zerto
{: #vum-zerto}

Caso você descubra que um host vSphere ESXi não pode entrar no modo de manutenção durante a correção, pode ser que o Zerto esteja parando-o. Se você tiver atualizado o Zerto desde a implementação inicial, conclua as etapas a seguir para corrigir isso. Se você não tiver atualizado, conclua as instruções a seguir em [Como colocar um host com um VRA associado no modo de manutenção](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/).

1. Efetue login na interface com o usuário da web Zerto.
2. Selecione **Configurações de site** no menu suspenso.
3. Selecione a **guia de políticas** e assegure-se de que **Permitir que o Zerto sempre insira hosts no modo de manutenção durante a correção** esteja selecionado.
4. Efetue logout de Zerto.

## Links relacionados
{: #vum-zerto-related}

* [Arquitetura de solução do VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (demonstrações)
