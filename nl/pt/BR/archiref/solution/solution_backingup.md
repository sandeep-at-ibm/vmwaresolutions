---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-16"

subcollection: vmware-solutions


---

# Fazendo backup de componentes
{: #solution_backingup}

Você é responsável pela configuração, o gerenciamento e o monitoramento de todos os componentes de software, incluindo o backup e a disponibilidade de sua infraestrutura de gerenciamento e de cargas de trabalho.

Como parte da solução, é possível implementar opcionalmente os serviços de complemento IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} ou Veeam on {{site.data.keyword.cloud_notm}}. O Veeam e o IBM Spectrum Protect Plus podem ajudar a satisfazer o requisito para fazer backup dos componentes de gerenciamento.

Esses serviços de complemento são implementados juntos com o armazenamento do {{site.data.keyword.cloud_notm}} Endurance. Os serviços ajudam a fazer backup de suas cargas de trabalho e dos componentes de gerenciamento. A [Visão geral da arquitetura do IBM Spectrum Protect Plus](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_spplus){:new_window} e a [Visão geral da arquitetura do Veeam](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_veeam){:new_window} fornecem orientação útil sobre planejamento e dimensionamento de sua implementação. Também é possível solicitar [serviços gerenciados](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services) para a sua implementação do Veeam.

Componentes de solução diferentes requerem estratégias diferentes para backup. Alguns componentes são protegidos usando o backup no nível de imagem e outros são protegidos usando o backup baseado em arquivo para sua configuração e dados.

## Servidor de arquivo para backup baseado em arquivo
{: #solution_backingup-fileserver-backup}

Alguns componentes, como o VMware vCenter Server com um Platform Services Controller (PSC) integrado e o VMware NSX, requerem que a sua configuração seja submetida a backup para um servidor de arquivos.

Para hospedar esses backups, implemente um servidor de arquivos Linux em seu cluster usando as etapas a seguir:

1. Solicite uma sub-rede portátil privada por meio da infraestrutura do {{site.data.keyword.cloud_notm}} e localize-a na mesma VLAN que os componentes do sistema. Esta é a VLAN privada na qual residem os endereços IP de gerenciamento para seus hosts.
2. Faça upload de uma imagem do sistema operacional para o armazenamento de dados de gerenciamento do VMware, como Ubuntu Server 18.04 LTS, por meio do espelho privado do {{site.data.keyword.cloud_notm}}.
3. Implemente essa máquina virtual (MV) em seu cluster no grupo de portas de gerenciamento usando um endereço IP móvel privado pedido anteriormente. Assegure-se de que a MV esteja configurada para apontar para seus servidores AD/DNS e, opcionalmente, inclua a MV no DNS de seu subdomínio.
4. Crie um ID de usuário de backup não raiz nesse servidor e assegure-se de que todos os serviços necessários sejam configurados e iniciados para transferências de arquivos. Por exemplo, FTP ou SSH.
5. Assegure-se de que essa MV esteja incluída em sua tarefa de backup de gerenciamento do Veeam ou do IBM Spectrum Protect Plus.

## Backup baseado em arquivo do vCenter
{: #solution_backingup-vcenter}

O VMware vCenter Server com o PSC integrado fornece uma interface com o usuário de gerenciamento de dispositivo do [ e a API para exportar o banco de dados e a configuração para um servidor de arquivos ](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.install.doc/GUID-3EAED005-B0A3-40CF-B40D-85AD247D7EA4.html){:new_window} usando vários protocolos. O VMware documenta um exemplo de como é possível configurar isso para [ ser executado periodicamente como uma tarefa cron](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vsphere.vcsapg-rest.doc%2FGUID-222400F3-678E-4028-874F-1F83036D2E85.html){:new_window} diretamente no vCenter Server Appliance e no PSC, que você pode adaptar para seu uso.

Se você tiver um PSC externo, deverá fazer backup do vCenter Server Appliance e do PSC separadamente usando essa
técnica. Se você tiver um PSC integrado, o backup do PSC será incluído no backup do vCenter. Familiarize-se e planeje as considerações e limitações documentadas pelo VMware. Além disso, planeje uma rotação e expiração regulares dos backups de arquivos em seu servidor de arquivos.

O VMware requer que o local de backup seja uma pasta vazia, portanto, planeje a sua rotação de backup ou automação para deixar o local vazio para cada tarefa de backup subsequente.
{:note}

## Backup baseado em arquivo NSX
{: #solution_backingup-nsx}

O backup adequado de todos os componentes NSX é crucial para restaurar o sistema para seu estado de funcionamento se ocorrer uma falha. O design requer que você configure o backup do NSX por meio da função de backup do NSX Manager. Para esse propósito, é possível [configurar o NSX Manager para executar backups regularmente](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window} em seu servidor de arquivos. Assegure-se de que o servidor de arquivos ou seus dados sejam submetidos a backup corretamente e assegure a rotação de backups antigos do NSX.

## Backup baseado em imagem de máquinas virtuais de gerenciamento
{: #solution_backingup-image}

Após a implementação da sua instância e do serviço do IBM Spectrum Protect Plus ou do serviço de backup do Veeam, configure uma tarefa de backup para suas máquinas virtuais de gerenciamento. Planeje fazer backup das MVs a seguir com pelo menos 7 dias de backups diários:

* Se presente, o VMware SDDC Manager
* Se estiverem presentes, servidores Active Directory
* Servidor de backup de arquivo

Planeje alocar licenças suficientes do Veeam ou do IBM Spectrum Protect Plus para fazer backup dessas máquinas virtuais e planeje pelo menos 2 TB de armazenamento de backup para as MVs.

## Serviços de complemento
{: #solution_backingup-addons}

Se você implementar componentes de solução de complemento em sua instância, também será necessário planejar o backup destes componentes como parte de sua estratégia de backup de gerenciamento:

* Zerto Virtual Replication: o sistema Zerto Virtual Manager (ZVM) é implementado como uma Virtual Server Instance (VSI) do {{site.data.keyword.cloud_notm}} e seu backup não é suportado pelo Veeam ou pelo IBM Spectrum Protect Plus. Se a sua estratégia de recuperação de desastre requerer que você recupere o ZVM sem executar um failover do site, será necessário usar sua solução de backup preferencial do Windows para fazer backup e restaurar o ZVM.
* F5 BIG-IP: o F5 recomenda [backup baseado em arquivo da configuração do F5](https://support.f5.com/csp/article/K13132){:new_window}, que pode ser direcionado para o seu servidor de arquivos.
* FortiGate Security Appliance ou MV: a Fortinet recomenda [backup baseado em arquivo da configuração do FortiGate](https://help.fortinet.com/fos50hlp/54/Content/FortiOS/fortigate-best-practices-54/Firmware/Performing_Config_Backup.htm){:new_window}, que é possível direcionar para seu servidor de arquivos.
* HyTrust Cloud Control e Data Control: o HyTrust suporta backup de imagem e baseado em arquivo dos dispositivos do servidor HyTrust. Para obter mais informações, veja os guias de administração do HyTrust.
* VMware HCX: a interface de gerenciamento do dispositivo HCX permite criar e fazer download de um backup baseado em arquivo da configuração do gerenciador do HCX semelhante ao vCenter Server Appliance.

## Mais considerações
{: #solution_backingup-considerations}

Se você escolher implementar seu servidor AD/DNS como uma Virtual Server Instance (VSI) do {{site.data.keyword.cloud_notm}}, não será possível fazer backup dele usando o Veeam ou o IBM Spectrum Protect Plus. Nesse caso, use sua solução de backup Windows preferencial para operações de backup e restauração ou planeje a implementação de sua instância usando MVs AD/DNS dentro do cluster do VMware, que pode ter backup efetuado pelo Veeam ou pelo IBM Spectrum Protect Plus.

A partir do VMware vCenter 6.5u2, o VMware suporta o backup do banco de dados Postgres do vCenter usando backups baseados em imagem, com scripts integrados de suspensão e continuação para o banco de dados durante a janela de backup, para assegurar a integridade do banco de dados. Se você fizer upgrade da sua instância do VMware para o vCenter 6.5u2, será possível escolher usar o Veeam ou o IBM Spectrum Protect Plus para fazer backup do vCenter Server e do PSC em vez de usar backups baseados em arquivo. Caso faça isso, deve-se usar o recurso de quiesce do Veeam ou do IBM Spectrum Protect Plus para assegurar a integridade de banco de dados.

## Restaurando a partir do backup
{: #solution_backingup-restore}

Há várias considerações especiais ao restaurar os backups de gerenciamento:

* Para vCenter e PSC, o VMware fornece um instalador que pode implementar um novo dispositivo virtual e restaurar a configuração por meio de backup.
* Quando você restaura um dispositivo por meio do backup, o instalador detecta o tipo de dispositivo (vCenter Server com o PSC integrado) com base nas informações de backup que você fornece.
* Como você implementa diretamente em um de seus hosts, talvez não seja capaz de implementar em um comutador ou grupo de portas distribuído. Talvez seja necessário criar um comutador padrão temporário e um grupo de portas para implementar os dispositivos recuperados e migrar um de seus vmnics temporariamente para esse comutador para fornecer conectividade de rede para suas MVs. Após a implementação, é possível migrar as MVs para o grupo de portas distribuído e retornar o vmnic para o dvSwitch.
* Para o NSX, talvez seja necessário reimplementar o NSX Manager e os controladores antes de restaurar a configuração por meio de backup.
* Assegure-se de familiarizar-se com as considerações e limitações do VMware para backup e restauração do vCenter.

## Resumo
{: #solution_backingup-summary}

Com o planejamento adequado, é possível assegurar que sua instância do VMware possa sofrer perda de seus componentes de gerenciamento e se recuperar com êxito. Assegure-se de monitorar regularmente o sucesso de suas tarefas de backup e a disponibilidade de seus dados de backup e assegure-se de testar seu plano de backup e restauração regularmente, para sua infraestrutura de gerenciamento e para suas cargas de trabalho.

## Links relacionados
{: #solution_backingup-related}

* [Visão geral da solução](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [ Visão geral do design ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [ Capacidade de Escalação ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling)
