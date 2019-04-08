---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---
# Resolução de problemas do HCX on IBM Cloud
{: #hcx-archi-trbl}

## O registro de nuvem falha
{: #hcx-archi-trbl-cloud-reg}

* O Hybrid Cloud Services não tentará novamente se as credenciais estiverem incorretas. As credenciais devem ser autenticadas antes que o Hybrid Cloud Services tente efetuar login e iniciar o registro em nuvem.
* O registro em nuvem poderá falhar se as credenciais forem digitadas incorretamente ou se as credenciais do VCF/VCS Hybrid Cloud Services Cloud forem mudadas após o registro do Hybrid Cloud Services com o VCF/VCS Hybrid Cloud Services Cloud, causando uma incompatibilidade.
* Para atualizar as credenciais no Web client, acesse a guia Introdução ao Hybrid Cloud Services e, em **Tarefas básicas**, escolha **Registrar nova nuvem**.

## Duplicar endereço MAC
{: #hcx-archi-trbl-dupl-mac-addr}

Após a migração, pode haver problemas de comunicação entre suas máquinas virtuais. Quando o endereço MAC é retido durante uma migração, um endereço MAC duplicado pode ser criado inadvertidamente.

O endereço MAC para a máquina virtual migrada pode ser mudado para resolver esse problema.

1. No cliente vSphere, desligue a máquina virtual.
2. No inventário, clique com o botão direito na máquina virtual e escolha **Editar configurações** no menu.
3. Na guia **Hardware virtual**, expanda o adaptador de Rede.
4. Próximo à caixa de texto Endereço MAC, escolha **Manual** no menu.
5. Especifique um endereço MAC exclusivo e clique em **OK**.
6. Verifique se o endereço MAC exclusivo soluciona o problema de comunicação.

## Consumo de recursos de host alto
{: #hcx-archi-trbl-high-host-resource}

Em casos raros, se todos os dispositivos virtuais de serviço residirem no mesmo host, as máquinas virtuais de serviço Hybrid Cloud Services poderão esgotar os recursos de CPU e disco de um host.

Alguns usuários têm visto esse problema quando todos os dispositivos virtuais foram instalados em um host físico. Dada essa configuração, o desempenho é comprometido quando as coisas a seguir acontecem simultaneamente:
* A rede tem alta latência ou perda de pacote ou ambos. A migração ou o transporte de dados é lento quando você usa a Internet pública ou uma rede ocupada.
* O WAN Optimizer está consumindo a largura da banda para criptografar e compactar (ou decriptografar e descompactar) cargas de trabalho grandes.
* Há um tráfego alto de aplicativo entre MVs no local e MVs migradas.

Para resolver o problema, siga estas etapas:

1. Antes de mudar a configuração do data center, revise os requisitos para o suporte de estado estável.
2. Entre em contato com o suporte de estado estável se os recursos estiverem sendo esgotados. Eles podem aconselhar como reconfigurar o ambiente com uma quantia mínima de tempo de inatividade.

## Links relacionados
{: #hcx-archi-trbl-related}

* [Registrando o HCX Manager com o vCenter](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-reg-vcenter)
* [Modificando ou desinstalando o HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
