---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Migrando uma máquina virtual
{: #hcx-archi-migrate-vm}

O HCX permite a migração bidirecional: de no local para a nuvem ou da nuvem para o data center no local. O HCX usa a tecnologia de replicação durante o processo de migração. A tecnologia de replicação está integrada ao dispositivo virtual do Hybrid Cloud Gateway. Nenhum software de replicação adicional precisa ser instalado.

## Migração baixa de tempo de in

A migração de tempo de inatividade baixo usa a replicação baseada em host para mover uma máquina virtual em tempo real de um vCenter para um data center virtual ou para a direção oposta. Para reduzir o tempo de inatividade, a MV de origem permanece on-line durante a replicação e é autoinicializada no host ESX de destino após a conclusão da replicação.

1. Uma solicitação de migração aciona as ações a seguir:
  * A replicação inicia uma transferência de sincronização total para um data center virtual do VCS HCX. O tempo que leva para replicar depende do tamanho da MV e da largura de banda disponível.
  * O consumo de largura da banda de replicação varia, dependendo de como a carga de trabalho muda os blocos no disco.
2. Quando a sincronização total é concluída, ocorre uma sincronização delta.
3. Quando a sincronização delta é concluída, o HCX aciona uma comutação. A comutação pode ser iniciada imediatamente ou planejada até um horário específico.
4. Após a comutação, a MV de origem é desligada e a réplica migrada é ligada. Se, por alguma razão, a MV não puder ser ligada, a nova MV será desligada (ou permanecerá desligada) e a original será ligada.
5. O HCX renomeia a MV original desligada para evitar um conflito de nomenclatura com a MV migrada e anexa um registro binário de data e hora ao nome da MV original.
6. Se não tiver sido especificado para ativar **Reter MAC**, a MV migrada obterá um novo endereço MAC.
7. A migração é feita. O Hybrid Cloud Services copia a MV original para a pasta **MVs migradas** na visualização de Modelos do vSphere.

## Nenhum vMotion de tempo de inatividade
{: #hcx-archi-migrate-vm-no-downtime-vm}

O vMotion transfere uma máquina virtual em tempo real de um vSphere vCenter para uma nuvem do VCS. Este vMotion requer uma rede esticada. A transferência do vMotion captura a memória ativa da máquina virtual, seu estado de execução, seu endereço IP e seu endereço MAC.

A versão de hardware da máquina virtual deve ser pelo menos a versão 9 ou o cross-cloud vMotion pode falhar.
{:note}

## Migração fria
{: #hcx-archi-migrate-vm-cold-mig}

A migração fria usa o mesmo plano de dados que o cross-cloud vMotion para transferir uma máquina virtual desligada por meio de uma rede estendida. Seu endereço IP e endereço MAC são preservados. Os requisitos e as restrições da máquina virtual são os mesmos que para o vMotion.

### Migrando MVs usando o assistente bidirecional
{: #hcx-archi-migrate-vm-mig-bidir-wiz}

Usando o vSphere Web Client, o assistente de migração bidirecional é acessível por meio da guia Introdução ao Hybrid Cloud Services. Esse assistente manipula todos os detalhes de migração, incluindo múltiplas máquinas virtuais.

No vSphere Web Client, o assistente de migração bidirecional pode ser acessado por meio da guia Introdução do Hybrid Cloud Services. Esse assistente manipula todos os detalhes de migração, incluindo múltiplas máquinas virtuais.
* Do vSphere para o VCS Hybrid Cloud Services
* Do VCS HCX Cloud para o vSphere

### Verificando as MVs antes da migração
{: #hcx-archi-migrate-vm-check-vms}

Para migrar uma máquina virtual, uma conexão segura que é mantida pelo Hybrid Cloud Gateway é necessária e a MV deve atender aos requisitos a seguir:
* A máquina virtual deve estar ligada.
* A arquitetura subjacente deve ser x86, independentemente do sistema operacional.
* Para usar a migração do vMotion, a versão de hardware deve ser maior que 9.
* A versão de hardware deve ser menor que 10.
* As MVs com o Mapeamento de disco rígido no modo de compatibilidade podem ser migradas.

As MVs com os atributos a seguir não são suportadas para migração:
* Excedeu 2 TB.
* Compartilhe arquivos VMDK.
* Tenha a mídia virtual ou os ISOs conectados.
* Versão de hardware inferior a 9.

### Monitorando uma Migração
{: #hcx-archi-migrate-vm-monitor-mig}

O progresso de uma migração baseada em replicação pode ser monitorado por meio da interface com o usuário ou por meio da linha de comandos. Visualize o console de Tarefa, conforme descrito em Monitorar implementação do dispositivo de serviço, e procure a tarefa **Migrar MV**. Quando
o status é **Concluído**, a MV é migrada e ligada.

Este procedimento usa uma MV não relacionada no mesmo vCenter para rastrear o progresso de uma MV migrada.

1. Identifique a MV para migrar e escolha uma MV do observador que possa executar ping na MV de migração.
2. Na interface com o usuário, inicie a migração da MV e monitore-a por meio do console de Tarefa.
3. Usando SSH, efetue login no host ESXi que executa a MV do observador.
4. Execute o comando a seguir para obter o ID da MV (o vmid):

  ```
  # vim-cmd vmsvc/getallvms | grep -i vmname 5
  ```

5. Execute os comandos a seguir para monitorar o estado de replicação, em que o vmid é o valor obtido na etapa anterior:

  ```
  # vim-cmd hbrsvc/vmreplica.getState vmid
  # vim-cmd hbrsvc/vmreplica.queryReplicationState vmid 6
  ```

6. Ping do ICMP - monitore o ping contínuo iniciado anteriormente.

Uma interrupção pode ocorrer no ping contínuo durante a comutação. No entanto, o ping de teste é rapidamente retomado
após a tarefa **Migrar MV** ser concluída, conforme refletido no console da tarefa.

### Visualizando MVs migradas
{: #hcx-archi-migrate-vm-view-vms}

Quando o Hybrid Cloud Services liga uma máquina virtual migrada com êxito, ele desliga a MV original e armazena-a em uma pasta no vCenter. As máquinas virtuais armazenadas permanecem até que ela seja excluída manualmente.

Após a migração, visualize o vCenter e observe as pastas identificadas como **MVs migradas da nuvem** e **MVs migradas para a nuvem**.
* Como réplicas, as MVs desligadas têm o nome original, com um registro binário de data e hora anexado.
* As MVs migradas podem ser tratadas como quaisquer outras MVs. Por exemplo, elas podem ser movidas para uma localização
diferente e ligadas.
* É possível excluir as MVs não desejadas nessas pastas.
* A exclusão é final, a menos que uma solução de backup esteja em vigor.

## Links relacionados
{: #hcx-archi-migrate-vm-related}

* [Modificando ou desinstalando o HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
