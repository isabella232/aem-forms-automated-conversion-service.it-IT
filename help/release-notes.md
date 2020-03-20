---
title: Novità? Note sulla versione - Servizio di conversione moduli automatizzati
description: 'Informazioni sulle funzioni più recenti e sui bug corretti per il servizio di conversione moduli automatizzati '
translation-type: tm+mt
source-git-commit: ec3a85ccd4c5d535ebc31c55702adab9aa92cf4e

---


# Servizio di conversione moduli automatizzati: Note sulla versione

Automated Forms Conversion Service riceve continuamente dei miglioramenti. Per restare aggiornati sugli ultimi sviluppi, visita questa pagina regolarmente. Questa pagina fornisce informazioni su:

* Versioni più recenti
* Nuove funzioni
* Correzioni di bug
* Funzionalità obsoleta
* Istruzioni speciali
* Progetti futuri per le modifiche

## 20 marzo 2020 (AFC-2020.03.1)

### Novità

**Rilevamento automatico delle sezioni logiche in un modulo**

Per impostazione predefinita, il servizio crea un pannello di primo livello separato per ciascuna pagina di un modulo PDF. Ora è possibile utilizzare l&#39; **[!UICONTROL Auto-detect logical sections]** opzione per rilasciare pannelli a livello di pagina (pannelli basati su numeri di pagina) e creare solo pannelli logici.  Inoltre unisce i campi che non appartengono ad alcuna sezione con la sezione logica precedente e i campi di una sezione logica sparsi su due pagine adiacenti in un&#39;unica sezione logica. Ad esempio, se alcuni campi di una sezione logica si trovano alla fine della pagina 1 e alcuni si trovano all&#39;inizio della pagina 2, tutti questi campi sono raggruppati in una singola sezione logica.

### Miglioramenti

**Miglioramenti nel rilevamento degli elenchi**

Il servizio ora è più efficiente nel rilevamento degli elenchi puntati e numerati. Ora è possibile rilevare facilmente gli elenchi a più livelli.

### Istruzioni speciali

**Installare il pacchetto del connettore del servizio di conversione di moduli automatizzati**

Per utilizzare le funzioni e i miglioramenti più recenti forniti nella release AFC-2020.03.1 è necessario il pacchetto di connettori 1.1.38 o superiore. Potete scaricare il pacchetto del connettore da [AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/fd/AEM-Forms-6.5.4.0-WIN).

Se si dispone già di un ambiente del servizio di conversione dei moduli automatizzati, per utilizzare le funzioni più recenti del servizio di conversione, installare il service pack più recente, il pacchetto aggiuntivo AEM Forms più recente e l&#39;ultimo pacchetto di connettori nell&#39;ordine indicato. Per istruzioni dettagliate, vedere l&#39;articolo [Configurare il servizio](configure-service.md) di conversione moduli automatizzati.
