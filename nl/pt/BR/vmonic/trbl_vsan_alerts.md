---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Avisos e alertas de funcionamento do SAN virtual
{: #trbl_vsan_alerts}

## Problema
{: #trbl_vsan_alerts-problem}

Na página **Monitorar** do VMware vSphere Web Client, você pode ver alertas e avisos relacionados a problemas de funcionamento do SAN virtual.

## Resolução
{: #trbl_vsan_alerts-resolution}

Esses avisos não são problemas e não indicam problemas funcionais. No entanto, se você quiser limpar os avisos do vSphere Web Client,
use o seguinte procedimento.

1. Acesse http://partnerweb.vmware.com/service/vsan/all.json e salve o arquivo JSON, com o nome `all.json`, em seu sistema local.
2. Assegure-se de ter concluído as etapas em [Tempo limite do console do vCenter](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_timeout_vc_console).
3. Na página de detalhes da instância do Cloud Foundation, clique em **Console do vCenter** e efetue login no vSphere Web Client usando as credenciais exibidas no console do {{site.data.keyword.vmwaresolutions_full}}.
4. No vSphere Web Client, acesse **Gerenciar > Configurações** e abra a seção **SAN Virtual > Funcionamento > Banco de Dados HCL**. Clique em **Atualizar do arquivo** e, em seguida, faça upload do arquivo `all.json` que você salvou anteriormente.
5. Para limpar os avisos, acesse a área de janela **Alarmes** na parte superior direita do vSphere Web Client. Clique com o botão direito em cada um dos alarmes e selecione **Reconfigurar como verde**.

Para obter mais informações, veja [Como fazer download do arquivo vSAN HCL off-line para o Plug-in de Verificação de Funcionamento vSAN](http://www.virtuallyghetto.com/2015/05/how-to-download-offline-vsan-hcl-file-for-vsan-health-check-plugin.html){:new_window}.
