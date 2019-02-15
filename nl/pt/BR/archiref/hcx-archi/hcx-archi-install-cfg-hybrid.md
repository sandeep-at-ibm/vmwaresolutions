---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# Instalando e configurando serviços híbridos

O instalador provisiona e configura uma máquina virtual para cada dispositivo virtual de serviço. As máquinas virtuais de serviço são implementadas no local e na nuvem.

## Pré-requisitos

* O HCX Manager deve ser instalado no local e registrado com um terminal de nuvem ativado para VCF/VCS HCX.
* O datacenter virtual de destino deve ter recursos suficientes.

## Visão Geral da Configuração

O procedimento de configuração supõe que todos os dispositivos virtuais de serviço serão configurados. No entanto, elas não são todas necessárias.
* O Hybrid Cloud Gateway é necessário.
* A instalação do WAN Optimization é realizada marcando a caixa Serviço WAN Optimization durante a instalação. Nenhuma configuração adicional é necessária.
* Para configurar o serviço Network Extension, veja a seção _Configurando o serviço Network Extension_. A implementação do dispositivo opcional pode ser adiada retornando para a página Serviços híbridos e instalando o dispositivo posteriormente.

## Iniciando a instalação e a configuração do Dispositivo virtual de serviço híbrido

A interface da web simples é usada para instalar os dispositivos virtuais de serviço e para configurar mais Layer 2 Concentrators.

### Pré-requisito para instalar e configurar o Dispositivo virtual de serviço híbrido

O HCX Manager deve ser instalado e registrado com o terminal de nuvem ativado para VCF/VCS HCX.

### Procedimento para instalar e configurar o Dispositivo virtual de serviço híbrido

1. Efetue login no vSphere Web Client.
2. Na guia **Página inicial**, clique no ícone **Hybrid Cloud Services**.
3. Clique na guia  ** Serviços Híbridos ** .
4. Clique em  ** Instalar serviço **.
5. Na página **Escolher serviços híbridos**, selecione os serviços a serem instalados e clique em **Avançar**.

### O que fazer a seguir

1. A próxima etapa é configurar o Hybrid Cloud Gateway, se necessário.
2. Um Layer 2 Concentrator poderá ser incluído em uma instalação existente a qualquer momento se recursos suficientes estiverem disponíveis para suportar a extensão.

## Configurando o Hybrid Cloud Gateway

Configure o dispositivo virtual de serviço do Hybrid Cloud Gateway.

### Pré-requisitos para configurar o Hybrid Cloud Gateway

Siga as etapas em _Iniciando a instalação e a configuração do Dispositivo virtual de serviço híbrido_ e marque Hybrid Cloud Gateway.

### Procedimento para configurar o Hybrid Cloud Gateway

Na página **Hybrid Cloud Gateway**, forneça os valores a seguir e clique em **Avançar**:
* **Rede** - o comutador que conecta a interface de gerenciamento do Hybrid Cloud Gateway. Nos casos de uso 1 e 2, ele pode ser um comutador virtual padrão ou um comutador distribuído virtual. Para qualquer configuração que use a extensão da Camada 2, ele deve ser um comutador distribuído virtual.
* **Cluster/Host** - selecione o Cluster ou o Host no qual o Cloud Gateway deve ser implementado.
* **Armazenamento de dados** - selecione o armazenamento de dados no qual implementar o Cloud Gateway.
* ** MV/Hostname ** -esse valor é opcional.
* Forneça o endereço IP/CIDR, o Gateway padrão e o servidor DNS a serem usados para a interface de gerenciamento do Cloud Gateway.
* Para inserir múltiplos endereços para o servidor DNS, separe-os com vírgulas.
* Em **Estendido (opcional)**, escolha a rede vMotion, se aplicável, e configure as senhas **admin** e **root**. Essas senhas são especificamente para o dispositivo Hybrid Cloud Gateway. O nome do usuário e a senha não precisam corresponder aos que estão configurados para o dispositivo do Hybrid Cloud Services.

## Configurando o Serviço de Extensão de Rede

Configure um serviço Network Extension para a implementação de caminho único ou para uma extensão de rede independente em um caminho alternativo.

### Pré-requisitos para configurar o serviço Network Extension

Selecione o serviço de Extensão de Rede. Se a configuração de Caminho único estiver instalada, **Network Extension** será sua única opção.

### Procedimento para Configurar o serviço Network Extension

1. Na página **Serviço Network Extension**, selecione um comutador distribuído virtual no menu **Comutador distribuído**. Quando você instala um Layer 2 Concentrator padrão, a caixa de seleção **Rotear redes estendidas por meio do Hybrid Cloud Gateway** está disponível. Ela não está lá para o L2C de alto rendimento.
2. Se **Rotear redes estendidas por meio do Hybrid Cloud Gateway** for selecionado, o instalador determinará um posicionamento razoável para o Layer 2 Concentrator (com base no comutador) e preencherá as informações de posicionamento. Caso contrário, as informações de posicionamento deverão ser inseridas manualmente na próxima etapa.
3. Configure a rota para o posicionamento do L2 Concentrator. Se **Rotear redes estendidas por meio do Hybrid Cloud Gateway** foi selecionado, esses valores não podem ser editados.
  * **Rede** - a rede de implementação para a interface de gerenciamento do Layer 2 Concentrator.
  * **Cálculo** - o cluster ou host de implementação para o Layer 2 Concentrator.
  * **Armazenamento de dados** - armazenamento de dados de implementação para o Layer 2 Concentrator.
  * ** MV/Hostname ** -esse valor é opcional.
4. Especifique os Parâmetros da rede para o Layer 2 Concentrator local.
  * Se essa opção estiver desativada, use os parâmetros padrão que são fornecidos pelo instalador.
  * Se o grupo de portas selecionado no menu **Rede** na página Hybrid Cloud Gateway não fizer parte do comutador distribuído, marque **Especificar os parâmetros de rede para Layer 2 Concentrator local** e edite as caixas de texto **Configurações estendidas**.
5. (Opcional) **Configurações estendidas** - configure as senhas **admin** e **root** para esse Layer 2 Concentrator específico.
6. Clique em **Avançar**. Na página **Pronto para concluir**, revise as informações e clique em **Concluir**.

## Monitorando a implementação do dispositivo de

O console de tarefas pode ser usado para monitorar o progresso de implementação para uma máquina virtual de serviço.

### Procedimento para monitorar a implementação do dispositivo de serviço

1. Efetue login no vSphere Web Client. Na guia **Página inicial**, clique no ícone **Hybrid Cloud Services**.
2. Na área de janela **Hybrid Cloud Services**, clique na guia **Serviços híbridos**. A implementação de dispositivo virtual pode ser monitorada por meio do console de Tarefa.
3. Acesse a área de janela **Tarefas recentes** e visualize as **Tarefas de todos os usuários**.
4. Clique em **Mais tarefas** para abrir o console de Tarefa.
5. No console de Tarefa, observe as tarefas de implementação.
6. Quando todas as tarefas estiverem concluídas, acesse a lista de inventário e clique em **Hybrid Cloud Services**.
7. Na área de janela central, clique na guia **Serviços híbridos**.
8. Revise o resumo de configuração dos dispositivos virtuais de serviço híbrido.

## Visualizando o status do túnel

Visualize o status do túnel do Cloud Gateway.

### Pré-requisitos para visualizar o status do túnel

O serviço Network Extension deverá estar ativo antes que seja possível estender uma rede.

### Procedimento para visualizar o status do túnel

1. Para verificar o status do túnel por meio do Web client, selecione **Hybrid Cloud Services** no inventário e clique na guia **Serviços híbridos**.
2. Para confirmar um túnel bem-sucedido do Hybrid Cloud Gateway, visualize o status do CGW (o acrônimo para o Hybrid Cloud Gateway) como **Ativo** e, no lado direito, o túnel estará codificado pela cor verde.

## Estendendo uma Rede da Camada 2 para o IBM Cloud

Amplie uma rede da Camada 2 do data center no local para a nuvem ativada para VCF/VCS HCX.

### Pré-requisitos para estender uma Rede da Camada 2 para o IBM Cloud

* Somente os grupos de portas identificados por VLAN (diferentes do tipo de VLAN Nenhum ou do ID de VLAN 0) podem ser estendidos. As VXLANs são consideradas VLANs.
* Esse procedimento usa o assistente **Ampliar rede**. Esse assistente deve ser executado por meio da visualização do inventário de rede do vSphere® Web Client. Embora o assistente seja visível em outras visualizações, ele deve ser executado por meio do contexto de inventário para obter as informações corretas.

### Procedimento para estender uma Rede da Camada 2 para o IBM Cloud

1. Efetue login no vSphere Web Client. Na guia **Página inicial** na área de janela central, clique no ícone **Rede** na lista **Inventários**.
2. Na hierarquia **Rede**, identifique o grupo de portas para a rede a ser estendida.
3. Clique com o botão direito no grupo de portas e, no menu, selecione **Ações de hibridismo** e selecione **Ampliar rede**.
4. Na página **Selecionar grupos de portas de origem**, confirme as informações sobre o grupo de portas e insira o **Endereço IP do gateway** e o prefixo da rede. Clique em **Avançar**.
5. Na página **Selecionar gateway de destino**, conclua as etapas a seguir:
  1. Selecione a Organização do VCF/VCS Hybrid Cloud Services Cloud no menu **Organização**.
  2. Selecione o datacenter virtual do VCF/VCS Hybrid Cloud Services Cloud no menu.
  3. Deixe **Roteamento de proximidade** desativado para forçar uma MV na nuvem ativada para VCF/VCS Hybrid Cloud Services para sempre usar o gateway no local para acessar a Internet. Por padrão, o tráfego que se origina de uma MV na nuvem ativada para VCF/VCS Hybrid Cloud Services atravessa o caminho de dados da Camada 2 de volta para o data center no local e para o gateway padrão. Se **Roteamento de proximidade** estiver marcado, uma MV na nuvem ativada para VCF/VCS Hybrid Cloud Services poderá acessar a Internet sem atravessar o caminho de dados da Camada 2 para o vSphere.
  4. Selecione o gateway de destino remoto na lista de gateways clicando na linha. Clique em **Avançar**.
6. Na página **Pronto para concluir**, revise todos os valores fornecidos. Clique em **Concluir**.
7. Para rastrear o progresso da extensão de rede, acesse a janela **Tarefas recentes**, clique na guia **Todos** e visualize **Tarefas de todos os usuários**.
8. Para abrir o console de Tarefa, clique em **Mais tarefas**. A extensão de rede é feita quando o status da tarefa **Ampliar rede** é **Concluído**.

### Links relacionados

* [Modificando ou desinstalando o HCX](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-mod-uninstall.html)
