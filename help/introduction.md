---
title: Introduzione
description: 'Accelerazione della conversione dei moduli di stampa in moduli adattivi '
translation-type: tm+mt
source-git-commit: c4f0d07b38cdb6aa162a0b61abe12fe9d1677a8c
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 100%

---


# Introduzione {#introduction-to-automated-forms-conversion-service}

Il servizio di conversione automatica dei moduli aiuta ad accelerare la digitalizzazione e la modernizzazione dell’esperienza di acquisizione dei dati attraverso la conversione automatica dei moduli PDF in moduli adattivi. Il servizio, basato su Adobe Sensei, converte automaticamente i moduli PDF in moduli adattivi facili da usare su diversi dispositivi, reattivi e basati su HTML5. Pur sfruttando gli investimenti esistenti nei moduli PDF e XFA, il servizio applica anche convalide, stili e layout appropriati ai campi del modulo adattivo durante la conversione. Il servizio consente di:

* Evitare la conversione manuale dei moduli di stampa in moduli adattivi, con risparmio di tempo e risorse
* Applicare modelli e convalide appropriati durante la conversione
* Generare documenti di record durante la conversione
* Raggruppare i campi più comuni in frammenti riutilizzabili per i moduli
* Abilita Adobe Analytics durante la conversione

![È semplice. Tu dovrai solo fornirci i moduli di origine, noi ci occuperemo del resto. Ti forniremo splendidi moduli adattivi. Naturalmente potrai regolare l’output nel modo che preferisci. ](assets/pdf-to-adaptive-form-gitx50.gif)

## Onboarding {#onboarding}

Il servizio è disponibile gratuitamente per i clienti AEM 6.4 Forms e AEM 6.5 Forms On-Premise e per i clienti aziendali di Adobe Managed Service. È possibile contattare il team di vendita Adobe o il proprio rappresentante Adobe per richiedere l’accesso al servizio.

Adobe abilita l’accesso per la tua organizzazione e fornisce i privilegi richiesti alla persona designata come amministratore dell’organizzazione. L’amministratore può concedere agli sviluppatori AEM Forms (utenti) dell’organizzazione l’accesso al servizio. Consulta [Configurazione del servizio di conversione automatica dei moduli](configure-service.md) per maggiori dettagli.

## Moduli PDF e lingue supportati {#supported-languages-and-pdf-forms}

Il servizio supporta moduli PDF non interattivi, moduli creati con Adobe Acrobat noti come AcroForms e moduli basati su XFA creati utilizzando AEM Forms o Adobe LiveCycle.

Il servizio supporta anche i moduli PDF abilitati per Adobe Sign. Se il modulo PDF di origine ha i tag di testo Adobe Sign, il servizio conserva tutte le informazioni relative ad Adobe Sign durante la conversione e associa le informazioni sul firmatario presente nel PDF di origine con i corrispondenti campi del modulo adattivo. La funzione è disponibile solo per AcroForms.

Il servizio è in grado di convertire in moduli adattivi solo i moduli in lingua inglese. Puoi tradurre i moduli adattativi generati in un’altra lingua usando [workflow di traduzione AEM](https://helpx.adobe.com/it/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).

## Workflow di conversione  {#conversion-workflow}

Il servizio di conversione automatica dei moduli è compatibile con Adobe Cloud. Connetti la tua istanza AEM al servizio, carica i moduli nella tua istanza AEM e avvia la conversione. Il processo di conversione completo è descritto di seguito:

![Flusso di lavoro](assets/conversion-workflow.png)

### 1. Configurazione dell’ambiente {#set-up-the-environment}

Il servizio di conversione automatica dei moduli è compatibile con Adobe Cloud. [Configura l’account Adobe I/O della tua organizzazione e connetti la tua istanza AEM locale](configure-service.md) al servizio di conversione in esecuzione su Adobe Cloud.

### 2. Conversione di moduli PDF in moduli adattivi {#use-the-conversion-service}

Dopo aver configurato l’ambiente di AEM Forms per convertire i moduli PDF in moduli adattivi, [carica i moduli PDF](convert-existing-forms-to-adaptive-forms.md) nella tua istanza AEM e [avvia la conversione](convert-existing-forms-to-adaptive-forms.md#run-the-conversion). Prima di caricare i moduli, considera quanto segue:

* Non caricare moduli protetti. Il servizio non può convertire i moduli crittografati e protetti da password.
* Non caricare moduli digitalizzati, colorati, compilati e redatti in lingue diverse dall’inglese. Tali moduli non sono supportati.
* Non caricare moduli PDF con spazi nel nome file.
* Non caricare [portfolio PDF](https://helpx.adobe.com/it/acrobat/using/overview-pdf-portfolios.html). Il servizio non può convertire un portfolio PDF in un modulo adattivo.
* Apporta ai moduli PDF le modifiche descritte nell’articolo [Procedure consigliate e considerazioni](styles-and-pattern-considerations-and-best-practices.md).
* Leggi l’articolo [Problemi noti](known-issues.md) per evitare malfunzionamenti.

### 3. Revisione dei moduli convertiti {#review-converted-forms}

I moduli non digitali possono presentare requisiti di acquisizione dei dati complessi in termini di layout dei campi, denominazione o suggerimenti impliciti che potrebbero non essere acquisiti con precisione da una logica di rilevamento basata su AI o machine learning. Una volta completata la conversione automatica, è possibile utilizzare l’[editor di revisione e correzione](review-correct-ui-edited.md) per rivedere il modulo convertito, apportare gli aggiornamenti necessari e generare un output migliorato più simile all’esperienza desiderata. Dopo aver apportato le modifiche necessarie, invia nuovamente il modulo per convertirlo.

Il tempo impiegato per la conversione automatica dipende da diversi fattori quali le dimensioni del modulo di input, la complessità del modulo e la posizione nella coda di elaborazione del servizio. L’utente viene informato regolarmente dell’avanzamento tramite l’indicatore di stato sulla cartella/sul file. Al termine della conversione, viene inviata anche una notifica e-mail all’indirizzo e-mail configurato.
