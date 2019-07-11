---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-15"

subcollection: vmware-solutions


---

#	Perfis do host
{: #vum-host-profiles}

O vCenter tem um recurso chamado Perfis do host. Esse recurso cria um perfil que captura uma configuração de host de referência pré-configurada e validada e ajuda um administrador do sistema a gerenciar as configurações do host em um cluster. Os Perfis do host fornecem um mecanismo automatizado e gerenciado centralmente para a configuração de host e a conformidade de host. Os Perfis do host permitem que a configuração seja tratada como um objeto gerenciado, que tem um catálogo de parâmetros a serem configurados, rede, armazenamento, segurança e outros parâmetros de nível do host. Esses Perfis do host podem ser aplicados a hosts individuais, a um cluster ou a todos os hosts e clusters associados a um perfil do host.

Conforme mais hosts do VMware vCenter Server on {{site.data.keyword.cloud}} vSphere ESXi são implementados pela automação do IBM Cloud for VMware Solutions que implementou o cluster original, há menos desvio de configuração do que com métodos manuais de inclusão de hosts. No entanto, as ações do administrador do sistema, além da automação, podem tornar as configurações de hosts diferentes. Por exemplo, mais armazenamento NFS é incluído ou VLANs extras são incluídas. O uso de Perfis do host para validar a configuração de um novo host verificando a conformidade desse host com relação a um host existente é um caso de uso válido dessa ferramenta no {{site.data.keyword.cloud_notm}}.

Para incluir mais hosts em seu cluster do vCenter Server, veja [ Expandindo e contraindo a capacidade para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers).

Nota:
*	Para instâncias implementadas ou submetidas a upgrade para a V2.1 ou superior, os servidores e clusters ESXi recém-implementados são corrigidos com atualizações recentes, não necessariamente as mais recentes, do ESXi do VMware.
*	Você é responsável por todas as outras atualizações para os componentes do VMware, incluindo assegurar que os servidores e clusters ESXi recém-implementados tenham todas as atualizações mais recentes requeridas.

Aconselhamos que, após um novo host ser incluído no cluster, ele seja colocado no Modo de Manutenção para que possa ser revisado quanto ao desvio de conformidade e corrigido antes de hospedar qualquer carga de trabalho.

A sequência a seguir é necessária para verificar a conformidade:
1.	Crie um Perfil do Host por meio de um host existente.
2.	Anexe o novo host ao Perfil do Host.
3.	Verifique a conformidade do novo host com o Perfil do Host.
4.	Revise falhas de conformidade e corrija.

##	Criando um perfil do host por meio de um host existente
{: #vum-host-profiles-create-host-profile}

1.	Na Página inicial do vSphere Web Client, clique em **Políticas e perfis**.
2.	Clique em **Perfis do host** e navegue até a visualização Perfis do host.
3.	Clique no ícone **Extrair perfil de um host**.
4.	Selecione um host existente que aja como o host de referência e clique em **Avançar**.
5.	Insira o nome e insira uma descrição para o novo perfil e clique em **Avançar**.
6.	Revise as informações de resumo para o novo perfil e clique em **Concluir**.
7.	O novo perfil aparece na lista de perfis.

##	Anexando o novo host ao perfil do host
{: #vum-host-profiles-attach-to-profile}

1.	Na **Lista de perfis** na visualização principal Perfis do host, selecione o Perfil do host que foi criado anteriormente para ser aplicado ao novo host.
2.	Clique no ícone **Anexar/remover um perfil do host para hosts e clusters**.
3.	Selecione o novo host na lista expandida e clique em **Anexar**.
4.	O novo host é incluído na lista Entidades anexadas.
5.	Clique em  ** Avançar **  e, em seguida, clique em  ** Concluir **.

##	Verificando a conformidade do novo host com o perfil do host
{: #vum-host-profiles-check-compliance}

1.	Navegue para o Perfil do host que foi concluído anteriormente.
2.	Clique no ícone **Verificar conformidade do perfil do host**.
3.	Na guia **Objetos**, o status de conformidade é atualizado como _Compliant, Unknown ou _Non-compliant_. Um status fora de conformidade indica uma inconsistência descoberta e específica entre o perfil e o novo host.

##	Revisando falhas de conformidade e correção
{: #vum-host-profiles-review-compliance}

1. Para ver mais detalhes sobre falhas de conformidade, selecione o **Perfil do host** na guia **Objetos** que é usada na verificação de conformidade.
2. Para ver detalhes específicos sobre quais parâmetros diferem entre o host que falhou na conformidade e o Perfil do host, clique na guia **Monitorar** e selecione a visualização **Conformidade**.
3. Expanda a hierarquia de objeto e selecione o host com falha.
4. Os parâmetros diferentes são exibidos na janela Conformidade, sob a hierarquia.
5. Revise os parâmetros e entenda por que o novo host pode variar do host de referência. Para parâmetros em que a conformidade não é aceitável, faça a correção antes de mover o novo host do modo de manutenção. Por exemplo, onde o desvio de configuração é causado pela ação do administrador do sistema.

## Links relacionados
{: #vum-host-profiles-related}

* [Arquitetura da solução VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (demonstrações)
