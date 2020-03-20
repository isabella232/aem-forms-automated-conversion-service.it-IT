---
title: Novità? Note sulla versione - Servizio di conversione moduli automatizzati
description: 'Informazioni sulle funzioni più recenti e sui bug corretti per il servizio di conversione moduli automatizzati '
translation-type: tm+mt
source-git-commit: 01dfd20951314017d47713bfb1a2a5f2d563f434

---


# Servizio di conversione moduli automatizzati: Note sulla versione

Automated Forms Conversion Service riceve continuamente dei miglioramenti. Per restare aggiornati sugli ultimi sviluppi, visita questa pagina regolarmente. Questa pagina fornisce informazioni su:

* Versioni più recenti
* Nuove funzioni
* Correzioni di bug
* Funzionalità obsoleta
* Istruzioni speciali
* Piani futuri per le modifiche

Questa pagina viene aggiornata mensilmente, quindi riutilizzarla regolarmente.

## 20 marzo 2020 (AFC-2020.03.1)

### Novità

**Rilevamento automatico delle sezioni logiche in un modulo**

Per impostazione predefinita, il servizio crea un pannello di primo livello separato per ciascuna pagina di un modulo PDF di input. Ora è possibile selezionare l&#39; **[!UICONTROL Auto-detect logical sections]** opzione per rimuovere la nozione di creazione di un pannello di livello principale separato per ciascuna pagina PDF e rilevare automaticamente le sezioni logiche. I club di servizi correlati campi di un modulo a una sezione logica. Ad esempio, tutti i campi relativi all&#39;indirizzo di fatturazione sono raggruppati in una sezione e tutti i campi relativi all&#39;indirizzo di spedizione sono raggruppati in una sezione diversa. Il servizio crea inoltre un pannello di livello principale separato per ciascuna sezione logica rilevata automaticamente.

### Miglioramenti

**Miglioramenti nel rilevamento degli elenchi**

Il servizio ora è più efficiente nel rilevamento degli elenchi puntati e numerati. Ora è possibile rilevare facilmente gli elenchi a più livelli.

### Istruzioni speciali

**Installare il pacchetto del connettore del servizio di conversione di moduli automatizzati**

Per utilizzare le funzioni e i miglioramenti più recenti forniti nella release AFC-2020.03.1 è necessario il pacchetto di connettori 1.1.38 o superiore. Potete scaricare il pacchetto del connettore da [AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/fd/AEM-Forms-6.5.4.0-WIN).

Se si dispone già di un ambiente del servizio di conversione dei moduli automatizzati, per utilizzare le funzioni più recenti del servizio di conversione, installare il service pack più recente, il pacchetto aggiuntivo AEM Forms più recente e l&#39;ultimo pacchetto di connettori nell&#39;ordine indicato. Per istruzioni dettagliate, vedere l&#39;articolo [Configurare il servizio](configure-service.md) di conversione moduli automatizzati.
