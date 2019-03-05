---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Passo 3 - Configurazione delle applicazioni
{: #caveonix-step3}

Questo passo utilizza lo script di configurazione Caveonix RiskForesight. Per la distribuzione “tutto-in-uno”, questo script viene avviato tramite l'automazione IC4VS. Per il ridimensionamento, il client deve richiamare lo script per distribuire le topologie di distribuzione distribuite parzialmente o completamente. Lo script configura i servizi RiskForesight:
-	Applicazioni Caveonix (API, raccoglitore centrale)
-	Elastic Search
- PostgresSQL
-	Raccoglitore remoto
-	IU
-	Kafka
-	Kibana
-	Certificati per tutti i servizi

Alla fine di questo passo, i componenti dell'applicazione sono installati sulle macchine virtuali (VM, Virtual Machine) richieste.

## Link correlati
{: #caveonix-step3-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
