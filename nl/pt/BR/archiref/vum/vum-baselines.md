---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-29"

subcollection: vmware-solutions


---

# Criando linhas de base e anexando a objetos de inventário
{: #vum-baselines}

As linhas de base têm uma coleção de uma ou mais correções, extensões, service packs, correções de bug ou upgrades e podem ser classificadas como linhas de base de correção, extensão ou upgrade. Os grupos de linhas de base são montados por meio de linhas de base existentes. Os grupos de linhas de base do host podem ter uma única linha de base de upgrade e várias linhas de base de correção e extensão. Os grupos de linhas de base da máquina virtual e do dispositivo virtual podem ter até três linhas de base de upgrade: uma linha de base de upgrade do VMware Tools, uma linha de base de upgrade de hardware de máquina virtual e uma linha de base de upgrade de dispositivo virtual.

O VMware Update Manager (VUM) inclui linhas de base predefinidas, que não podem ser editadas ou excluídas. É possível usar as linhas de base predefinidas, ou criar linhas de base de correção, extensão e upgrade que atendem a seus critérios. As linhas de base customizadas que você cria e as linhas de base predefinidas podem ser combinadas em grupos de linhas de base.

O VUM inclui linhas de base padrão que podem ser usadas para varrer qualquer um dos dispositivos a seguir, a fim de determinar se os hosts em seu ambiente são atualizados com as correções mais recentes ou se os dispositivos virtuais e as máquinas virtuais são submetidos a upgrade para a versão mais recente:
* Qualquer máquina virtual
* Qualquer dispositivo virtual
* Qualquer host

Essas linhas de base predefinidas são as seguintes:
* **Correções críticas do host (predefinidas)** - verifica os hosts ESXi quanto à conformidade com todas as correções críticas.
* **Correções não críticas do host (predefinidas)** - verifica os hosts ESXi quanto à conformidade com todas as correções opcionais.
* **Upgrade do VMware Tools para corresponder ao host (predefinido)** - verifica as máquinas virtuais quanto à conformidade com a versão mais recente do VMware Tools no host. O Update Manager suporta o upgrade do VMware Tools para máquinas virtuais em hosts que estão executando o ESXi 5.5.x e mais recente.
* **Upgrade de hardware da MV para corresponder ao host (predefinido)** - verifica o hardware virtual de uma máquina virtual quanto à conformidade com a versão mais recente que é suportada pelo host. O Update Manager suporta upgrade para o hardware virtual versão vmx-13 em hosts que estão executando o ESXi 6.5.
* **Upgrade do VA para mais recente (predefinido)** - verifica a conformidade do dispositivo virtual com a versão mais recente liberada do dispositivo virtual.

Para usar linhas de base e grupos de linhas de base, deve-se anexá-los a objetos de inventário selecionados, como objetos contêiner, máquinas virtuais, dispositivos virtuais ou hosts. Embora seja possível anexar linhas de base e grupos de linhas de base a objetos individuais, um método mais eficiente é anexá-los a objetos contêiner, como pastas, vApps, clusters ou data centers. Nesta etapa, usaremos as linhas de base predefinidas com relação aos hosts no cluster.

1. Usando o vSphere Web Client, acesse **Página inicial** > **Hosts e clusters**.
2. Clique no objeto de cluster que você deseja varrer.
3. Acesse o VUM, clique em **Anexar linha de base** e, em seguida, selecione as duas Linhas de base de correção predefinidas. Clique em **OK**.

## Links relacionados
{: #vum-baselines-related}

* [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [Demos do {{site.data.keyword.vmwaresolutions_full}}](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (demonstrações)
