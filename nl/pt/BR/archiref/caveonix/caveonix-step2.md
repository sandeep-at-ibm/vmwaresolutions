---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Etapa 2-Implementação da máquina virtual
{: #caveonix-step2}

A automação do {{site.data.keyword.vmwaresolutions_full}} solicita uma sub-rede de IP privado móvel adicional e a máquina virtual (MV) "tudo em um" está configurada com um endereço IP dessa sub-rede para que os componentes do Caveonix RiskForesight possam:

- Conectar-se ao vCenter e ao NSX Manager por meio do BCR.
- Conectar-se aos Remote Collectors, em VXLANs ou hospedados fora do local.
- Permitir que o cliente gerencie o espaço de endereço IP ao aumentar a capacidade.


## Links relacionados
{: #caveonix-step2-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
