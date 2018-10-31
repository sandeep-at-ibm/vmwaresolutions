---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-03"

---

#	Perfis do host

o vCenter tem um recurso chamado Perfis do host. Esse recurso cria um perfil que captura uma configuração de host de referência pré-configurada e validada e ajuda um administrador do sistema a gerenciar as configurações do host em um cluster. Os Perfis do host fornecem um mecanismo automatizado e gerenciado centralmente para a configuração de host e a conformidade de host. Os Perfis do host permitem que a configuração seja tratada como um objeto gerenciado, que contém um catálogo de parâmetros para configurar; rede, armazenamento, segurança e outros parâmetros de nível do host. Esses Perfis do host podem ser aplicados a hosts individuais, a um cluster ou a todos os hosts e clusters associados a um perfil do host.

À medida que mais hosts VCS vSphere ESXi forem implementados pela automação do IC4VS que implementou o cluster original, haverá menos desvio de configuração do que com métodos manuais de inclusão de hosts. No entanto, ações do administrador do sistema fora da automação podem fazer com que a configuração de hosts seja diferente. Por exemplo, mais armazenamento NFS foi incluído ou VLANs extras foram incluídas. Portanto, o uso de Perfis do host para validar a configuração de um novo host, verificando a conformidade desse host com relação a um host existente, é um caso de uso válido dessa ferramenta no IBM Cloud.

Para incluir mais hosts em seu cluster do vCenter Server, veja [ Expandindo e contraindo a capacidade para instâncias do vCenter Server](../../vcenter/vc_addingremovingservers.html).

Observe que:
*	Para instâncias implementadas ou submetidas a upgrade para a V2.1 ou superior, os servidores e clusters ESXi recém-implementados são corrigidos com atualizações recentes, não necessariamente as mais recentes, do ESXi do VMware.
*	Você é responsável por todas as outras atualizações para componentes do VMware, incluindo assegurar que clusters e servidores ESXi recém-implementados tenham todas as atualizações mais recentes que você exigir.

Recomendamos que após um novo host ser incluído no cluster, ele seja colocado no Modo de Manutenção para que possa ser revisado quanto ao desvio de conformidade e corrigido antes de hospedar qualquer carga de trabalho.

A sequência a seguir é necessária para verificar a conformidade:
1.	Crie um Perfil do Host por meio de um host existente.
2.	Anexe o novo host ao Perfil do Host.
3.	Verifique a conformidade do novo host com o Perfil do Host.
4.	Revise falhas de conformidade e corrija.

##	Criando um perfil do host por meio de um host existente

1.	Na Página inicial do vSphere Web Client, clique em **Políticas e perfis**.
2.	Clique em **Perfis do host** e navegue até a visualização Perfis do host.
3.	Clique no ícone **Extrair perfil de um host**.
4.	Selecione um host existente que agirá como o host de referência e clique em **Avançar**.
5.	Insira o nome e insira uma descrição para o novo perfil e clique em **Avançar**.
6.	Revise as informações de resumo para o novo perfil e clique em **Concluir**.
7.	O novo perfil aparece na lista de perfis.

##	Anexando o novo host ao perfil do host

1.	Na **Lista de perfis** na visualização principal Perfis do host, selecione o Perfil do host que foi criado anteriormente para ser aplicado ao novo host.
2.	Clique no ícone **Anexar/remover um perfil do host para hosts e clusters**.
3.	Selecione o novo host na lista expandida e clique em **Anexar**.
4.	O novo host é incluído na lista Entidades anexadas.
5.	Clique em  ** Avançar **  e, em seguida, clique em  ** Concluir **.

##	Verificando a conformidade do novo host com o perfil do host

1.	Navegue para o Perfil do host que foi concluído anteriormente.
2.	Clique no ícone **Verificar conformidade do perfil do host**.
3.	Na guia **Objetos**, o status de conformidade é atualizado como _Em conformidade, Desconhecido ou _Fora de conformidade_. Um status fora de conformidade indica uma inconsistência descoberta e específica entre o perfil e o novo host.

##	Revisando falhas de conformidade e corrigindo

1.	Para ver mais detalhes sobre falhas de conformidade, selecione o **Perfil do host** na guia **Objetos** que é usada na verificação de conformidade.
2.	Para ver detalhes específicos sobre quais parâmetros diferem entre o host que falhou na conformidade e o Perfil do host, clique na **guia Monitor** e selecione a **visualização Conformidade**.
3.	Expanda a hierarquia de objeto e selecione o host com falha.
4.	Os diferentes parâmetros são exibidos na janela Conformidade, abaixo da hierarquia.
5.	Revise os parâmetros e entenda por que o novo host pode variar do host de referência. Para parâmetros em que a conformidade não é aceitável, por exemplo, quando o desvio de configuração foi causado pela ação do administrador do sistema, corrija antes de mover o novo host do modo de manutenção.

### Links relacionados

* [ VMware HCX on IBM Cloud Solution ](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Soluções VMware no IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)
