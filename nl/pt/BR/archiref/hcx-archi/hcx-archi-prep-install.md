---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# Preparando o ambiente de instalação
{: #hcx-archi-prep-install}

A instalação do VMware HCX on IBM Cloud tem os requisitos de software a seguir:
* vSphere 5.5 U3 ou vSphere 6.0u2 ou superior.
* Se o NSX for usado, versão 6.2.2 ou superior. O NSX é necessário para a migração de política.
* Para usar o cross-cloud vMotion, as mesmas restrições de afinidade se aplicam às nuvens como fazem no local. Para obter mais informações, veja o [FAQ do VMware EVC e de Compatibilidade da CPU](http://bit.ly/2vK6Sp5).

## Configurando a conectividade de rede
{: #hcx-archi-prep-install-config-net}

O HCX deve atravessar a Internet pública e as linhas privadas e conectar-se a componentes do data center, como redes, comutadores e grupos de portas.
* Os [Requisitos de acesso à porta](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-port-req) listam as portas que devem ser abertas para que os dispositivos virtuais HCX possam ser instalados com êxito.
* O ambiente do vSphere no local e o ambiente VCF/VCS HCX Cloud devem permitir a sincronização de clock do Network Time Protocol (NTP) entre os dispositivos no local do vSphere e os dispositivos VCF/VCS HCX. A porta UDP 123 deve ser acessível a dispositivos virtuais e redes HCX.

## Ambiente no local
{: #hcx-archi-prep-install-on-prem-env}

Antes de instalar o HCX, verifique se seu ambiente pode suportar as tarefas que você deseja realizar. O ambiente no local deve suportar as tarefas a seguir antes da instalação do HCX.
* Virtual Center com o vSphere 5.5 Atualização 3 ou 6.0 Atualização 2.
* O vMotion e os recursos de migração de política requerem o NSX versão 6.2.2 ou superior.
* Uma conta de serviço do vSphere com a função de sistema Administrador do vCenter Server designada a ele.
* No vCenter, espaço em disco suficiente para os dispositivos HCX a serem instalados.
* Endereços IP suficientes para as MVs locais provisionadas durante a instalação.
* Portas e firewalls abertos conforme necessário, como documentado em Requisitos de acesso à porta.
* Se o servidor de conexão única (SSO) for remoto, a URL do vCenter, do Servidor de SSO externo ou do Platform Services Controller (PSC) que executa o serviço de consulta externa deverá ser identificada. Quando o HCX Manager é registrado com o vCenter, essa URL deve ser fornecida.
* Se um vCenter não tiver sua própria instância interna do serviço de consulta, isso poderá ser por uma das razões a seguir:
  * O vCenter 6.0u2 está executando um Platform Services Controller externo.
  * O vCenter está no modo vinculado (em que o vCenter secundário usa o serviço de SSO do vCenter primário ou de um serviço de SSO externo).

## Verificando o ambiente de instalação da Camada 2
{: #hcx-archi-prep-install-verify-layer-2-inst}

O esticamento da rede da Camada 2 tem os requisitos a seguir:
* Uma edição do vSphere Enterprise Plus.
* O vSphere vCenter deve atender aos requisitos a seguir para suportar a extensão da Camada 2:
  * licença do vSphere Enterprise Plus
  * Deve ter um vSphere Distributed Switch (vDS). O comutador distribuído está disponível com o vSphere Enterprise Plus Edition.
  * Quando instalado, o dispositivo de serviço Layer 2 Concentrator no local deve ter acesso a uma porta vNIC e quaisquer VLANs a serem estendidas.
  * Se a rede deve ser estendida sobre a Internet pública ou uma VPN (em um caminho alternativo), a máquina virtual L2C no VCF/VCS requer um endereço IP. O endereço IP remoto é necessário para configurar o Layer 2 Concentrator.
  * Se múltiplos Layer 2 Concentrators forem desejados, cada um deverá ter um endereço IP no local e na nuvem.

## Links relacionados
{: #hcx-archi-prep-install-related}

* [Instalando e configurando o HCX na origem](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
* [ FAQ de Compatibilidade de EVC e CPU do VMware ](http://bit.ly/2vK6Sp5)
