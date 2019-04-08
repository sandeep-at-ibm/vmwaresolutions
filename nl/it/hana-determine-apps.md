---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, SAP applications

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 3. Determinazione delle tue applicazioni SAP

Devi determinare quali applicazioni basate su SAP pianifichi di eseguire sul tuo {{site.data.keyword.baremetal_long}}. Gli elementi da considerare durante la determinazione includono:

 * Quanto a lungo viene utilizzato il database? Esistono due modi in cui può essere distribuito SAP HANA. Il primo è un database in uno stack SAP NetWeaver, in cui funge principalmente come origine dati. Il secondo metodo di distribuzione è di eseguire SAP HANA in una modalità autonoma con le applicazioni distribuite direttamente al sistema SAP HANA. In ogni caso, il processo di ridimensionamento e gli altri requisiti e dipendenze del sistema possono essere diversi in base a come utilizzi il tuo sistema (sviluppo e test, PoC (proof of concept) o produzione).
 * Come intendi utilizzare le applicazioni? L'utilizzo previsto è per lo sviluppo e il test o la produzione?
 * Utilizzi un SSL-servizio VPN (Virtual Private Network) {{site.data.keyword.cloud_notm}} o un Point-to-Point Tunneling Protocol (PPTP)?

## Passi successivi

  [4. Ridimensionamento del server](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server)

  [5. Determinazione della tua configurazione](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#determine_configuration)
