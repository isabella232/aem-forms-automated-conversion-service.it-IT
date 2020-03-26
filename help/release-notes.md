---
title: Novità? Note sulla versione - Servizio di conversione moduli automatizzati
description: 'Informazioni sulle funzioni più recenti e sui bug corretti per il servizio di conversione moduli automatizzati '
translation-type: tm+mt
source-git-commit: dc17dfcb331df6144b8a7ce3c9c9d840b1182a95

---


# Servizio di conversione moduli automatizzati: Note sulla versione

Automated Forms Conversion Service riceve continuamente dei miglioramenti. Per restare aggiornati sugli ultimi sviluppi, visita questa pagina regolarmente. Questa pagina fornisce informazioni su:

* Accesso anticipato
* Versioni più recenti
* Nuove funzioni
* miglioramenti
* Correzioni di bug
* Funzionalità obsoleta
* Istruzioni speciali
* Progetti futuri per le modifiche

## 20 marzo 2020 (AFC-2020.03.1)

### Accesso anticipato

**Rilevamento automatico delle sezioni logiche in un modulo**

La versione AFC-2020.03.1 fornisce l&#39;accesso anticipato alla **[!UICONTROL Auto-detect logical sections]** funzione.

Per impostazione predefinita, il servizio crea un pannello di primo livello separato per ciascuna pagina di un modulo PDF. Ora è possibile utilizzare l&#39; **[!UICONTROL Auto-detect logical sections]** opzione per rilasciare pannelli a livello di pagina (pannelli basati su numeri di pagina) e creare solo pannelli logici.  Inoltre unisce i campi che non appartengono ad alcuna sezione con la sezione logica precedente e i campi di una sezione logica sparsi su due pagine adiacenti in un&#39;unica sezione logica. Ad esempio, se alcuni campi di una sezione logica si trovano alla fine della pagina 1 e alcuni si trovano all&#39;inizio della pagina 2, tutti questi campi sono raggruppati in una singola sezione logica.

Per utilizzare la **[!UICONTROL Auto-detect logical sections]** funzione è necessario disporre del connettore 1.1.38 o superiore. Potete scaricare il pacchetto del connettore da [AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).

### Miglioramenti

**Miglioramenti nel rilevamento degli elenchi**

Il servizio ora è più efficiente nel rilevamento degli elenchi puntati e numerati.