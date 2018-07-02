---

copyright:

  years:  2016, 2018

lastupdated: "2017-12-29"

---

# Resolução de problemas assistida

## Problema

Em algumas situações, pode ocorrer um problema mais complicado e os arquivos de log não serem suficientes para concluir a análise da causa raiz e fornecer uma solução.

## Resolução

Para resolver esse tipo de problemas, a equipe de Suporte {{site.data.keyword.vmwaresolutions_full}} precisa de acesso à máquina virtual (VM) de Gerenciamento do {{site.data.keyword.cloud_notm}}. Essa VM de gerenciamento, chamada IBM CloudDriver, é a interface principal que é usada para gerenciar as instâncias implementadas do VMware Cloud Foundation e do VMware vCenter Server.

Por motivos de segurança, o acesso ao IBM CloudDriver é restrito. A equipe de Suporte {{site.data.keyword.vmwaresolutions_short}} solicitará aprovação do cliente e, depois que a obtiver, a equipe poderá acessar o componente CloudDriver usando um servidor virtual de infraestrutura do {{site.data.keyword.cloud_notm}}. Esse servidor faz uma ponte no ambiente sobre a rede pública do Frontend Customer Router (FCR) da infraestrutura do {{site.data.keyword.cloud_notm}}.

Em seguida, a equipe de Suporte {{site.data.keyword.vmwaresolutions_short}} usa a chave {{site.data.keyword.slapi_short}} de infraestrutura do {{site.data.keyword.cloud_notm}} que foi fornecida para o pedido e a configuração da instância (ou, se necessário, a chave atualizada que é fornecida pelo cliente) para implementar um servidor virtual de infraestrutura do {{site.data.keyword.cloud_notm}} por hora.

A conta do cliente é cobrada pelo uso das ferramentas do IBM CloudBuilder para fins de resolução de problemas. Depois que a depuração e a correção forem concluídas, o componente IBM CloudBuilder será liberado.

O servidor virtual de infraestrutura do {{site.data.keyword.cloud_notm}} que é usado para resolução de problemas é implementado com as seguintes especificações:

* Um VSI (Virtual Service Instance) de nó público CentOS 7 é usado com 1 CPU e 1 GB de RAM.
* O VSI é implementado no mesmo data center na mesma VLAN pública e privada primária em que está a instância.
* Um script de pós-instalação é usado com a implementação do VSI para configurar regras de firewall que permitem apenas conexões SSH recebidas de um conjunto específico de endereços IP que são de propriedade e são usados pela equipe de Suporte {{site.data.keyword.vmwaresolutions_short}}.
* O sistema de ativação de suporte que usa esses endereços IP é executado em uma VM de infraestrutura do {{site.data.keyword.cloud_notm}} que é acessível apenas por meio de uma rede privada de infraestrutura do {{site.data.keyword.cloud_notm}} e é protegido com um par de sistemas Vyatta de infraestrutura do {{site.data.keyword.cloud_notm}} de HA (Alta Disponibilidade).
* Ferramentas do IBM Security, como QRadar®, Nessus e IBM BigFix®, são usadas para monitorar o sistema de ativação de suporte contra todas as ameaças de segurança.
