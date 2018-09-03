---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Requisitos e planejamento para instâncias do vCenter Server with Hybridity Bundle

Revise os requisitos a seguir antes de pedir sua instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle. Planeje sua instância com base no {{site.data.keyword.CloudDataCent_notm}} local, nos requisitos de capacidade de carga de trabalho e nos requisitos de serviço adicionais.

## Requisitos da conta do IBM Cloud

A conta do {{site.data.keyword.cloud_notm}} que você está usando deve atender a determinados requisitos. Para obter mais informações, veja [Requisitos para a conta do {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilidade do data center do IBM Cloud

A implementação do vCenter Server with Hybridity Bundle tem requisitos estritos na infraestrutura física. Portanto, é possível implementar instâncias apenas em {{site.data.keyword.CloudDataCents_notm}} que atendam aos requisitos. Os {{site.data.keyword.CloudDataCents_notm}} a seguir estão disponíveis para implementação do vCenter Server with Hybridity Bundle:

Tabela 1. Instâncias disponíveis do {{site.data.keyword.CloudDataCents_notm}} for vCenter Server with Hybridity Bundle

| {{site.data.keyword.CloudDataCent_notm}} | Localização | Região |
|:-----|:----------------|
| AMS03 | Amsterdã | Europa |
| CHE01 | Chennai | Ásia Pacífico |
| DAL09 | Dallas | NA Sul |
| DAL10 | Dallas | NA Sul |
| DAL12 | Dallas | NA Sul |
| DAL13 | Dallas | NA Sul |
| FRA02 | Frankfurt | Europa |
| FRA04 | Frankfurt | Europa |
| HKG02 | Hong Kong | Ásia Pacífico |
| LON02 | Londres | Europa |
| LON04 | Londres | Europa |
| LON06 | Londres | Europa |
| MEL01 | Melbourne | Ásia Pacífico |
| MEX01 | Querétaro | NA Sul |
| MIL01 | Milão | Europa |
| MON01 | Montreal | NA Leste |
| OSL01 | Oslo | Europa |
| PAR01 | Paris | Europa |
| SAO01 | São Paulo | América do Sul |
| SEO01 | Seul | Ásia Pacífico |
| SJC03 | São José | Oeste ND |
| SJC04 | São José | Oeste ND |
| SNG01 | Cingapura | Ásia Pacífico |
| SYD01 | Sydney | Ásia Pacífico |
| SYD04 | Sydney | Ásia Pacífico |
| TOK02 | Tóquio | Ásia Pacífico |
| TOR01 | Toronto | NA Leste |
| WDC04 | Washington, DC | NA Leste |
| WDC06 | Washington, DC | NA Leste |
| WDC07 | Washington, DC | NA Leste |

Dependendo da disponibilidade e do fornecimento do inventário, o {{site.data.keyword.CloudDataCents_notm}} pode exibir um indicador de status no console do {{site.data.keyword.vmwaresolutions_short}} para ajudá-lo a planejar suas implementações.

Tabela 2. Indicadores de status para {{site.data.keyword.CloudDataCents_notm}} ao pedir instâncias do vCenter Server with Hybridity Bundle

| Barra de Status | Detalhes do status |
|:------------------------------|:--------------------------------------------------|
| Em breve                   | O {{site.data.keyword.CloudDataCent_notm}} não está disponível atualmente. |
| Provisoriamente fora do inventário  | O {{site.data.keyword.CloudDataCent_notm}} não possui disponibilidade neste momento. |
| Inventário limitado             | O {{site.data.keyword.CloudDataCent_notm}} limitou a disponibilidade e o pedido pode não estar concluído. |

## Backup de componentes de gerenciamento

Você é responsável por manter e assegurar a disponibilidade de todos os componentes da instância. É altamente recomendável planejar o backup ou a alta disponibilidade de todos os componentes de gerenciamento. Para obter mais informações, consulte [Fazendo backup de componentes](../archiref/solution/solution_backingup.html).

## Serviços para instâncias do vCenter Server with Hybridity Bundle

A instância do vCenter Server with Hybridity Bundle inclui o licenciamento do VMware Hybrid Cloud Extension (HCX) que o autoriza para o serviço VMware HCX on {{site.data.keyword.cloud_notm}}. Este serviço pode ampliar continuamente as redes de data centers locais para o {{site.data.keyword.cloud_notm}}, permitindo que as máquinas virtuais (VMs) sejam migradas de e para o {{site.data.keyword.cloud_notm}} sem nenhuma conversão ou mudança.

Quando você implementar esse serviço, conclua as configurações a seguir:
* Especifique o **Tipo de interconexão do HCX** selecionando uma das opções a seguir:
  * **Rede pública**: o HCX cria uma conexão criptografada entre sites na rede pública.
  * **Rede privada**: o HCX cria uma conexão criptografada entre sites na rede privada.
* Especifique o **Tipo de certificado de terminal**. Se selecionar **Certificado de autoridade de certificação**, configure as definições a seguir:
  * **Conteúdo do certificado**: insira o conteúdo do certificado de autoridade de certificação.
  * **Chave privada**: insira a chave privada do certificado de autoridade de certificação.
  * (Opcional) **Senha**: insira a senha para a chave privada se ela estiver criptografada.
  * (Opcional) **Inserir a senha novamente**: insira a senha para a chave privada novamente.
  * (Opcional) **Nome do host**: insira o nome do host a ser mapeado para o nome comum (CN) do certificado de autoridade de certificação. O HCX on {{site.data.keyword.cloud_notm}} requer o certificado de autoridade de certificação para estar em um formato que seja aceito pelo NSX Edge. Para obter mais informações sobre os formatos de certificados do NSX Edge, veja [Importando SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).

É possível pedir outros serviços de complemento para sua instância com base em suas necessidades, por exemplo, recuperação de desastre. Para obter mais informações, veja [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservices.html).

## Considerações sobre capacidade

Para obter informações e considerações de capacidade, consulte [Capacidade de ajuste de escala](../archiref/solution/solution_scaling.html).

### Links relacionados

* [vCenter Server com visão Hybridity Bundle](vc_hybrid_overview.html)
* [Pedindo instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_orderinginstance.html)
* [Expandindo e contraindo a capacidade para instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservers.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservices.html)
