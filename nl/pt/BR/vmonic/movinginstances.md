---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-19"

---

# Fazendo upgrade de suas instâncias de liberações pré-V1.4

## Problema

A topologia de rede da instância na V1.4 e liberações mais recentes é diferente das liberações anteriores à V1.4. Por causa dessa mudança, as instâncias que foram implementadas em liberações pré-V1.4 não podem ser usadas em seu estado na liberação atual.

## Resolução

Na V1.4 e liberações mais recentes, vários aprimoramentos da topologia de rede estão disponíveis para suas instâncias:
* (Aplica-se a todas as instâncias): configuração de rede otimizada. Como a conta {{site.data.keyword.cloud}} que você está usando deve ser uma conta VRF (Virtual Routing and Forwarding) ou deve ter a ampliação da VLAN ativada se for uma conta clássica (não VRF), um segundo endereço IP móvel não é necessário. Apenas o endereço IP móvel da infraestrutura do {{site.data.keyword.cloud_notm}} primário é necessário para implementação.
* (Aplica-se apenas a instâncias do Cloud Foundation): recurso de implementação de vários sites com servidor Microsoft Windows AD SSO (Active Directory Single Sign-On) e Domain Name System (DNS).

Se você não tiver migrado ou excluído suas instâncias de liberações pré-V1.4, elas poderão ainda estar visíveis no console do {{site.data.keyword.vmwaresolutions_short}} no modo somente visualização. Estas instâncias são marcadas na interface com o usuário como **Descontinuadas** com um ícone de símbolo de aviso.

**Nota**: as informações que são exibidas nas propriedades da instância refletem os dados a partir da data de liberação da V1.4 e não são mais atualizadas.

As ações a seguir estão disponíveis nas instâncias pré-V1.4:
*  Visualize as informações na página de detalhes da instância.
*  Visualize informações de backup da instância.
*  Abra o vSphere Web Client e use a instância no vCenter.
*  Solicite a restauração da instância abrindo um chamado de suporte do {{site.data.keyword.cloud_notm}}.
*  Exclua a instância.

Todas as outras ações nas instâncias pré-V1.4 não estão mais disponíveis.

Se você tiver instâncias pré-V1.4 e planejar continuar a usá-las, será possível fazer upgrade delas criando novas instâncias e, em seguida, movendo suas configurações existentes para essas novas instâncias.

Para mover suas instâncias pré-V1.4 para novas instâncias, conclua as etapas a seguir no vSphere Web Client:
1. De sua instância pré-V1.4, exporte todas as VMs (máquinas virtuais).
2. Crie uma nova instância na liberação atual.
3. Importe todas as VMs exportadas da **Etapa 1**.
4. Comece usando sua nova instância.

Para obter informações sobre como exportar e importar VMs, veja a documentação do VMware vSphere.

Se você precisar de assistência com o {{site.data.keyword.vmwaresolutions_short}}, [entre em contato com o Suporte IBM](trbl_support.html) por meio de um dos canais de suporte.
