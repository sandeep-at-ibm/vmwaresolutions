---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

subcollection: vmware-solutions


---
# Registrando o HCX Manager com o vCenter
{: #hcx-archi-reg-vcenter}

Registre o plug-in do Hybrid Cloud Services no VMware vSphere Web Client e inicie o serviço de gerenciamento do Hybrid Cloud Services.

## Antes de iniciar
{: #hcx-archi-reg-vcenter-prereq}

O dispositivo virtual do Hybrid Cloud Services deve ser ligado antes que ele possa ser registrado.

## Procedimento para registrar o HCX Manager com o vCenter
{: #hcx-archi-reg-vcenter-proc-register}

1. Efetue login no dispositivo virtual de serviço Hybrid Cloud Services.
2. Clique no tile  ** Gerenciar configurações ** .
  1. Na área de janela esquerda, em **Configurar sistemas**, selecione vCenter.
  2. Clique em **Incluir vCenter** na parte superior direita.
  3. Insira o endereço IP do vCenter Server no formato `https:vCenter-host-name` ou `https:vCenter-IP-address`. Por exemplo,  ` https: My-vCenter `  ou  ` https:10.108.26.211 `.
  4. Insira o nome do usuário e a senha do vCenter Server. A conta que é usada deve ter a função de Administrador do vCenter.
  5. Clique em **OK**. Não reinicie quando a mensagem _Você precisa reiniciar o app_ for exibida.
3. Configure o serviço de consulta.
  1. Clique na guia  ** Gerenciar ** .
  2. Clique no botão **Editar** na extrema direita da caixa de texto **URL de serviço de consulta**.
  3. Insira o terminal em serviço de rede de consulta no formato a seguir:
    * Para o vCenter Server 5.5u3  ` https://ssoip:/7444/lookupservice/sdk `
    * Para o vCenter Server 6.0u2 `https://ssoip/lookupservice/sdk`
  4. Clique em **OK**. Não reinicie quando uma mensagem para reiniciar o mecanismo da web for exibida.
4. Clique na guia **Resumo** e localize a seção **Componentes de gerenciamento de hibridismo**. Pare e inicie o mecanismo de aplicativo e o mecanismo da web.
5. Para finalizar o registro, efetue logout do vSphere Web Client. Efetue login novamente para verificar se a atualização de tela ocorreu.

## Resultados
{: #hcx-archi-reg-vcenter-results}

Observe o ícone **Nuvem híbrida** existente e o item de menu **Hybrid Cloud Services** à esquerda. O registro do Hybrid Cloud Services atualiza esses rótulos. No inventário, o rótulo do ícone se torna **Hybrid Cloud Services**.

## Links relacionados
{: #hcx-archi-reg-vcenter-related}

* [Instalando e configurando serviços híbridos](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-hybrid)
