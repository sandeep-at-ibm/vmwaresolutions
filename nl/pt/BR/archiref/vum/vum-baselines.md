---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Criando linhas de base e anexando a objetos de inventário

As linhas de base contêm uma coleção de uma ou mais correções, extensões, service packs, correções de bug ou upgrades e podem ser classificadas como linhas de base de correção, extensão ou upgrade. Os grupos de linhas de base são montados por meio de linhas de base existentes. Os grupos de linhas de base do host podem conter uma única linha de base de upgrade e várias linhas de base de correção e extensão. Os grupos de linhas de base de máquina virtual e de dispositivo virtual podem conter até três linhas de base de upgrade: uma linha de base de upgrade do VMware Tools, uma linha de base de upgrade de hardware de máquina virtual e uma linha de base de upgrade de dispositivo virtual.

O VUM inclui linhas de base predefinidas, que não podem ser editadas nem excluídas. É possível usar as linhas de base predefinidas, ou criar linhas de base de correção, extensão e upgrade que atendem a seus critérios. As linhas de base customizadas que você cria e as linhas de base predefinidas podem ser combinadas em grupos de linhas de base.

O VUM inclui linhas de base padrão que podem ser usadas para varrer qualquer um dos dispositivos a seguir, a fim de determinar se os hosts em seu ambiente são atualizados com as correções mais recentes ou se os dispositivos virtuais e as máquinas virtuais são submetidos a upgrade para a versão mais recente:
* Qualquer máquina virtual
* Qualquer dispositivo virtual
* Qualquer host

Essas linhas de base predefinidas são as seguintes:
* **Correções críticas do host (predefinidas)** - verifica os hosts ESXi quanto à conformidade com todas as correções críticas.
* **Correções não críticas do host (predefinidas)** - verifica os hosts ESXi quanto à conformidade com todas as correções opcionais.
* **Upgrade do VMware Tools para corresponder ao host (predefinido)** - verifica as máquinas virtuais quanto à conformidade com a versão mais recente do VMware Tools no host. O Update Manager suporta o upgrade do VMware Tools para máquinas virtuais em hosts que estão executando o ESXi 5.5.x e mais recente.
* **Upgrade de hardware da VM para corresponder ao host (predefinido)** - verifica o hardware virtual de uma máquina virtual quanto à conformidade com a versão mais recente que é suportada pelo host. O Update Manager suporta upgrade para o hardware virtual versão vmx-13 em hosts que estão executando o ESXi 6.5.
* **Upgrade do VA para mais recente (predefinido)** - verifica a conformidade do dispositivo virtual com a versão mais recente liberada do dispositivo virtual.

Para usar linhas de base e grupos de linhas de base, deve-se anexá-los a objetos de inventário selecionados, como objetos contêiner, máquinas virtuais, dispositivos virtuais ou hosts. Embora seja possível anexar linhas de base e grupos de linhas de base a objetos individuais, um método mais eficiente é anexá-los a objetos contêiner, como pastas, vApps, clusters ou data centers. Nesta etapa, nós vamos usar as linhas de base predefinidas com relação aos hosts no cluster.

1. Usando o vSphere Web Client, acesse **Página inicial** > **Hosts e clusters**.
2. Clique no objeto de cluster que você deseja varrer.
3. Clique em **Anexar linha de base** e, em seguida, selecione as duas Linhas de base de correção predefinidas, em seguida, clique em **OK**.

### Links relacionados

* [VMware HCX no	{{site.data.keyword.cloud}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Soluções de VMware no	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
