---
title: Introduzione
description: 'Conversione più rapida dei moduli per la stampa in moduli adattivi '
translation-type: tm+mt
source-git-commit: ceff5cb56aa9896a28004628c5e26c262b7918bd

---


# Introduzione {#introduction-to-automated-forms-conversion-service}

Il servizio di conversione automatizzata dei moduli consente di accelerare la digitalizzazione e la modernizzazione dell&#39;esperienza di acquisizione dei dati attraverso la conversione automatizzata dei moduli PDF in moduli adattivi. Il servizio, basato su Adobe Sensei, converte automaticamente i moduli PDF in moduli adattivi semplici da periferica, reattivi e basati su HTML5. Sfruttando gli investimenti esistenti in PDF Forms e XFA, il servizio applica anche convalide, stili e layout appropriati ai campi modulo adattivi durante la conversione. Il servizio consente di:

* Risparmio manuale per la conversione dei moduli per la stampa in moduli adattivi
* Applica pattern e convalide appropriate durante la conversione
* Genera documento record durante la conversione
* Raggruppare i campi più comuni in frammenti di modulo riutilizzabili
* Abilita Adobe Analytics durante la conversione

![È semplice. Basta fornirci i moduli di origine e lasciare tutto a noi. Vi forniremo bellissimi moduli adattivi. Naturalmente, si lavorerà con l&#39;output con la vostra soddisfazione. ](assets/pdf-to-adaptive-form-gitx50.gif)

## Onboarding {#onboarding}

Il servizio è disponibile gratuitamente per i clienti a tempo indeterminato di AEM 6.4 Forms e AEM 6.5 Forms e per i clienti enterprise di Adobe Managed Service. Per richiedere l&#39;accesso al servizio, contattate il team vendite Adobe o il rappresentante Adobe.

Adobe consente l’accesso alla vostra organizzazione e fornisce i privilegi richiesti alla persona designata come amministratore nella vostra organizzazione. L&#39;amministratore può concedere l&#39;accesso agli sviluppatori AEM Forms (utenti) dell&#39;organizzazione per connettersi al servizio. Per ulteriori informazioni, vedere [Configurare il servizio](configure-service.md) di conversione moduli automatizzati.

## Moduli e lingue PDF supportati {#supported-languages-and-pdf-forms}

Il servizio supporta i moduli PDF non interattivi, i moduli creati con Adobe Acrobat, denominati AcroForms, e i moduli basati su XFA creati utilizzando AEM Forms o Adobe LiveCycle.

Il servizio può convertire solo moduli in lingua inglese in moduli adattivi. È possibile tradurre i moduli adattivi generati in un&#39;altra lingua utilizzando il flusso di lavoro [di traduzione di](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)AEM.

## Flusso di lavoro di conversione {#conversion-workflow}

Il servizio di conversione automatica dei moduli è eseguito su Adobe Cloud. Collegate l&#39;istanza di AEM al servizio, caricate i moduli nell&#39;istanza di AEM e avviate la conversione. Il processo di conversione completo è riportato di seguito:

![Flusso di lavoro](assets/conversion-workflow.png)

### 1. Configurare l&#39;ambiente {#set-up-the-environment}

Il servizio di conversione automatica dei moduli è eseguito su Adobe Cloud. [Configura l’account di I/O Adobe dell’organizzazione e collega l’istanza](configure-service.md) locale di AEM al servizio di conversione in esecuzione su Adobe Cloud.

### 2. Conversione di moduli PDF in moduli adattivi {#use-the-conversion-service}

Una volta configurato l’ambiente AEM Forms, per convertire i moduli PDF in moduli adattivi è necessario [caricare i moduli](convert-existing-forms-to-adaptive-forms.md) PDF nell’istanza di AEM e [avviare la conversione](convert-existing-forms-to-adaptive-forms.md#run-the-conversion). Prima di caricare i moduli, tenere presente quanto segue:

* Non caricare i moduli protetti. Il servizio non converte i moduli protetti da password e crittografati.
* Non caricare moduli digitalizzati, colorati, non in lingua inglese e compilati. Tali moduli non sono supportati.
* Non caricare moduli PDF con spazi nel nome file.
* Non caricare i portfolio [](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)PDF. Il servizio non converte un portfolio PDF in moduli adattivi.
* Apportare le modifiche suggerite ai moduli PDF descritte nell&#39;articolo [Best practice e considerazioni](styles-and-pattern-considerations-and-best-practices.md) .
* Leggi l’articolo sui problemi [](known-issues.md) noti per evitare possibili insidie.

### 3. Verifica dei moduli convertiti {#review-converted-forms}

I moduli Real World possono presentare complesse esigenze di acquisizione dei dati in termini di layout del campo, denominazione o suggerimenti impliciti che potrebbero non essere catturati con precisione dalla logica di rilevamento basata su AI/ML. Una volta completata la conversione automatizzata, è possibile utilizzare l&#39;editor [](review-correct-ui-edited.md) Revisione e Correzione per rivedere il modulo convertito e apportare gli aggiornamenti necessari e generare un output migliorato più vicino all&#39;esperienza desiderata. Dopo aver apportato le modifiche necessarie, inviare di nuovo il modulo per la conversione.

Il tempo necessario per la conversione automatizzata dipende da una varietà di fattori, come dimensioni del modulo di input, complessità del modulo, prestito sulla coda di elaborazione del servizio. L&#39;utente riceve regolarmente una notifica dei progressi compiuti tramite l&#39;indicatore di stato su cartella/file. Una volta completata la conversione, all&#39;indirizzo e-mail configurato viene inviata anche una notifica e-mail.
