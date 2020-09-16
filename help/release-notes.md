---
title: Scopri le novità Note sulla versione - Servizio di conversione automatica dei moduli
description: 'Scopri le ultime funzionalità e i bug corretti per il servizio di conversione automatica dei moduli '
translation-type: tm+mt
source-git-commit: 9b904622fcf421d82a183569d915926a2761d3f5
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 97%

---


# Note sulla versione

Il servizio di conversione automatica dei moduli viene migliorato continuamente. Per rimanere aggiornato sugli sviluppi più recenti, visita questa pagina regolarmente. Questa pagina fornisce informazioni su:

* Accesso anticipato
* Versioni più recenti
* Nuove funzioni
* Miglioramenti
* Correzioni di bug
* Funzionalità obsolete
* Istruzioni speciali
* Modifiche programmate per il futuro


## 16 luglio 2020 (AFC-2020.07.0)

### Novità

È stato aggiunto il supporto per la conversione di PDF forms colorati in moduli adattivi.

### Miglioramenti

Miglioramenti della conversione automatica dei campi di testo, moduli e gruppi di scelta nei corrispondenti componenti dei moduli adattativi.


## 20 marzo 2020 (AFC-2020.03.1)

### Accesso anticipato

**Rilevamento automatico delle sezioni logiche in un modulo**

Per impostazione predefinita, il servizio crea un pannello di primo livello separato per ciascuna pagina di un modulo PDF. Ora è possibile utilizzare l’opzione **[!UICONTROL Auto-detect logical sections]** per eliminare i pannelli a livello di pagina (pannelli basati sul numero di pagina) e creare solo pannelli logici. Questa opzione, inoltre, unisce alla sezione logica precedente i campi che non appartengono ad alcuna sezione e unisce in un’unica sezione logica i campi di una sezione logica suddivisi su due pagine adiacenti. Ad esempio, se alcuni campi di una sezione logica si trovano alla fine della pagina 1 e altri si trovano all’inizio della pagina 2, tutti questi campi sono raggruppati in una singola sezione logica.

### Miglioramenti

**Miglioramenti nel rilevamento degli elenchi**

Il servizio ora è più efficiente nel rilevamento degli elenchi puntati e numerati.

### Istruzioni speciali

**Installazione del pacchetto del connettore del servizio di conversione automatica dei moduli**

Per usufruire delle funzioni e dei miglioramenti più recenti forniti nella versione AFC-2020.03.1, è necessario il pacchetto del connettore 1.1.38 o versioni successive. Puoi scaricare il pacchetto del connettore da [Condivisione pacchetti AEM](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).

Se disponi già di un ambiente attivo del servizio di conversione automatica dei moduli, installa il service pack più recente, il pacchetto aggiuntivo AEM Forms più recente e il pacchetto del connettore più recente nell’ordine indicato per utilizzare le funzioni più recenti del servizio di conversione. Per istruzioni dettagliate, vedi l’articolo [Configurazione del servizio di conversione automatica dei moduli](configure-service.md).