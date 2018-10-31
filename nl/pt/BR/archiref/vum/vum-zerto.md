---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-03"

---

# Zerto

Caso você descubra que um host vSphere ESXi não pode entrar no modo de manutenção durante a correção, pode ser que o Zerto o esteja interrompendo. Se você atualizou o Zerto desde a implementação inicial, realize as etapas a seguir para corrigir isso. Se você não tiver atualizado, siga as instruções em [Como colocar um host com um VRA associado no modo de manutenção](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/).

1. Efetue login na UI da web do Zerto.
2. Selecione **Configurações de site** no menu suspenso.
3. Selecione a **guia de políticas** e assegure-se de que **Permitir que o Zerto sempre insira hosts no modo de manutenção durante a correção** esteja selecionado.
4. Efetue logout de Zerto.

### Links relacionados

* [ VMware HCX on IBM Cloud Solution ](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Soluções VMware no IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
