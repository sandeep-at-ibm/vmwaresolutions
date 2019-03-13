---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Modificando ou desinstalando o HCX
{: #hcx-archi-mod-uninstall}

As instalações existentes podem ser submetidas a upgrade ou algumas ou todas de uma implementação do Hybrid Cloud Services podem ser removidas.

##  Como desesticar uma rede da Camada 2
{: #hcx-archi-mod-uninstall-unstretch-layer2}

A remoção do estendimento de uma rede da Camada 2 é necessária antes de remover o dispositivo virtual de serviço Layer 2 Concentrator associado ou antes de desinstalar o Hybrid Cloud Services.

1. Verifique as redes estendidas.
2. Na página do plug-in do Hybrid Cloud Services, visualize a guia Serviços híbridos e verifique a seção Serviço Network Extension. Se tarefas ativas ou planejadas estiverem em andamento, aguarde até que elas sejam concluídas ou pare-as antes de continuar.
3. Para remover a rede, clique no ícone Excluir (vermelho X) à direita.
4. Clique em  ** OK **  para confirmar.

## Desinstalando dispositivos virtuais HCX
{: #hcx-archi-mod-uninstall-uninst-hva}

Um dispositivo de serviço pode ser desinstalado na preparação para a desinstalação do Hybrid Cloud Services ou devido a uma mudança na arquitetura de instalação. Use o Hybrid Cloud Services para administrar dispositivos, conforme descrito no procedimento a seguir.

### Pré-requisitos para a desinstalação de dispositivos virtuais HCX
{: #hcx-archi-mod-uninstall-prereq-uninst-hva}

* Cancele ou reconfigure o tempo de execução para quaisquer migrações que possam ocorrer durante a tarefa de desinstalação.
* Verifique o console de tarefa do vSphere Web Client para quaisquer migrações em execução e aguarde até que estejam concluídas.
* Assegure-se de que não haja tarefas ativas do Hybrid Cloud Services de nenhum tipo.

Nunca exclua dispositivos virtuais do inventário do vSphere. Use sempre o portal de gerenciamento para interagir com dispositivos virtuais de serviço.
{:note}

### Procedimento para desinstalar dispositivos virtuais HCX
{: #hcx-archi-mod-uninstall-proc-uninst-hva}

1. Na interface do vSphere Web Client, selecione o plug-in do Hybrid Cloud Services na área de janela esquerda.
2. Na área de janela central, clique na guia **Serviços híbridos**.
3. Localize o dispositivo Hybrid Cloud Gateway e clique na entrada para exibir os detalhes.
4. Na parte inferior direita, clique no ícone Excluir para remover o dispositivo.
5. Se uma rede estendida não compartilha um endereço IP com o Hybrid Cloud Gateway, deve-se removê-lo separadamente. Expanda os detalhes do Serviço Network Extensions e clique no ícone Excluir para remover o Layer 2 Concentrator.

O Hybrid Cloud Gateway e quaisquer dispositivos virtuais de serviço híbrido que usam o Hybrid Cloud Gateway são removidos do vCenter e do VCF/VCS Hybrid Cloud Services Cloud.

## Desinstalando o HCX Manager
{: #hcx-archi-mod-uninstall-unist-hcxm}

O dispositivo HCX Manager deve ser desinstalado antes de você remover a solução HCX do data center no local. Siga estas etapas para desinstalar a máquina virtual do Hybrid Cloud Services.

1. Desenque todas as redes da Camada 2.
2. Remova os dispositivos virtuais de serviço híbrido.
3. No vCenter no local, desligue a máquina virtual do Hybrid Cloud Services.
4. Exclua a máquina virtual do Hybrid Cloud Services.

Todos os dispositivos de serviço virtual são removidos. Os elementos a seguir podem permanecer para trás:
* Registros
* MVs migradas

### O que fazer a seguir
{: #hcx-archi-mod-uninstall-what-next}

As MVs e os logs migrados podem ser submetidos a backup ou excluídos manualmente.

## Efetuando login no Portal de gerenciamento do HCX
{: #hcx-archi-mod-uninstall-log-hcxmp}

A implementação do Hybrid Cloud Services pode ser administrada por meio do Portal de gerenciamento usando uma interface com o usuário baseada no navegador.

1. Em um navegador da web, insira o endereço IP designado ao Hybrid Cloud Services e especifique o número da porta 9443. Por exemplo,  ` https://HCXip: 9443 `.
2. A interface com o usuário do Hybrid Cloud Services é aberta em uma janela do navegador da web usando SSL. Se necessário, aceite o certificado de segurança. A tela de login do VMware Hybridity and Networking é aberta.
3. Insira o nome de usuário e a senha. Por padrão, o nome do usuário é Admin. A senha é o valor que foi fornecido quando o dispositivo virtual do Hybrid Cloud Services foi instalado.

## Links relacionados
{: #hcx-archi-mod-uninstall-related}

* [Resolução de problemas do HCX on IBM Cloud](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-trbl)
