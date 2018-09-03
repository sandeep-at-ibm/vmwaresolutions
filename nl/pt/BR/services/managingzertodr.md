---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-24"

---

# Gerenciando o Zerto on IBM Cloud

Depois que o serviço Zerto on {{site.data.keyword.cloud}} é implementado em sua instância, é possível configurar ou atualizar o Zerto Virtual Replication e implementar mais Dispositivos de Replicação Virtual nos servidores ESXi recém-incluídos.

## Usando seu próprio certificado para Zerto

Como uma melhor prática, deve-se usar seu próprio certificado SSL para o Zerto Virtual Manager (ZVM). Depois de ter implementado o Zerto on {{site.data.keyword.cloud_notm}}, substitua o certificado SSL para o ZVM pelo seu próprio certificado seguindo as instruções em [Como usar um Certificado SSL CER para substituir o certificado autoassinado para o ZVM, ZSSP ou ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window}.

## Gerenciando a configuração de replicações do Zerto

Para gerenciar a configuração de replicações do Zerto (como emparelhar novamente as instâncias do Zerto ou configurar grupos de proteção virtual para replicar máquinas virtuais), efetue login no console do Zerto Virtual Replication usando as credenciais do vCenter com permissões de administrador.

Se você estiver replicando entre diferentes instâncias do Zerto do {{site.data.keyword.cloud_notm}}, será possível configurar a replicação diretamente entre as instâncias do Zerto. Se estiver replicando entre a instância do Zerto do {{site.data.keyword.cloud_notm}} e o seu próprio data center, você mesmo deverá instalar o Zerto on seu próprio data center. Essa instância do Zerto que você instala no seu próprio data center pode licenciá-lo automaticamente quando você o emparelha com a instância do Zerto do {{site.data.keyword.cloud_notm}}.

Como a replicação do Zerto não suporta a passagem do Conversão de Endereço de Rede (NAT), estabelecer conectividade entre a instância do Zerto do {{site.data.keyword.cloud_notm}} e o seu próprio data center pode exigir a customização de rotas nos dispositivos do Zerto Virtual Manager (ZVM) ou nos Zerto Virtual Replication Appliances (VRAs) em ambos os lados e pode também requerer o tunelamento seguro entre os sites. Ao configurar ou reconfigurar rotas nos dispositivos ZVM, deve-se assegurar que todos os dispositivos ZVM possam se conectar com êxito a `zerto.com` para o relatório de uso. É possível verificar essa conexão abrindo uma sessão do navegador para `https://www.zerto.com` do dispositivo ZVM.

**Nota**: O Management VMware NSX Edge Services Gateway (ESG) de instâncias do Cloud Foundation e do vCenter Server no {{site.data.keyword.cloud_notm}} é pré-configurado para permitir comunicações HTTPS (TCP porta 443) de saída que se originam do ZVM.

## Atualizando o Zerto Virtual Replication

Para atualizar o Zerto Virtual Replication, efetue login no console do Zerto Virtual Replication.

## Implementando VRAs em servidores ESXi recém-incluídos

Quando você inclui ou remove servidores ESXi para o cluster primário de sua instância, os VRAs são automaticamente implementados ou removidos. Os VRAs não são implementados automaticamente nos servidores ESXi nos clusters secundários de sua instância, mas você mesmo pode implementá-los no console do Zerto Virtual Replication.

### Links relacionados

* [ Zerto on  {{site.data.keyword.cloud_notm}}  visão geral ](addingzertodr.html)
* [Solicitando serviços gerenciados para o Zerto on {{site.data.keyword.cloud_notm}}](managing_zerto_services.html)
* [Website zerto.com](https://www.zerto.com){:new_window}
* [Documentação técnica do Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Recuperação de desastre Zerto](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:new_window}
* [Explicação de alertas do Zerto Virtual Replication](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)
