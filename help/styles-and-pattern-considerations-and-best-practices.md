---
title: 'Procedure consigliate e considerazioni '
seo-title: 'Procedure consigliate e considerazioni '
description: Best practice e considerazioni per il servizio Automated forms conversion
seo-description: Elenco di stili e motivi negli PDF forms di origine che il servizio Automated forms conversion trova difficili da identificare
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
translation-type: tm+mt
source-git-commit: e2298422e0af9b1c678e7604be3efb6da377d7dd
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 3%

---


# Best practice e pattern complessi noti {#Best-practices-and-considerations2}

Questo documento contiene le linee guida e le raccomandazioni che gli amministratori, gli autori e gli sviluppatori di moduli possono trarre vantaggio dall&#39;utilizzo di [!DNL Automated Forms Conversion service]. Vengono illustrate le procedure ottimali, dalla preparazione dei moduli di origine alla correzione di pattern complessi che richiedono un ulteriore sforzo per la conversione automatizzata. Queste best practice collettivamente contribuiscono alle prestazioni e all&#39;output complessivi della [!DNL Automated Forms Conversion service].

## Best practice

Il servizio di conversione converte i PDF forms disponibili nell&#39;istanza di AEM [!DNL Forms] in moduli adattivi. Le best practice elencate di seguito consentono di migliorare la velocità e la precisione di conversione. Inoltre, queste best practice consentono di risparmiare tempo dedicato alle attività di conversione.

### Prima di caricare la sorgente

Potete caricare tutti i PDF forms contemporaneamente o in modo graduale, a seconda delle necessità. Prima di caricare i moduli, considera quanto segue:

* Mantenere il numero di moduli in una cartella inferiore a 15 e mantenere il numero totale di pagine in una cartella inferiore a 50.
* Le dimensioni della cartella devono essere inferiori a 10 MB. Non salvare i moduli in sottocartelle.
* Tenere il numero di pagine in un modulo inferiore a 15.
* Organizzate i documenti sorgente in un batch di 8-15 documenti. Tenere i moduli di origine con i frammenti di modulo adattivi più comuni in un unico batch.
* Non caricare i moduli protetti. Il servizio non converte i moduli protetti da password e protetti.
* Non caricare gli Portfoli [PDF](https://helpx.adobe.com/it/acrobat/using/overview-pdf-portfolios.html). Il servizio non converte un Portfolio PDF in un modulo adattivo.
* Non caricare moduli digitalizzati, non in lingua inglese e compilati. Tali moduli non sono supportati.
* Non caricare moduli di origine con spazi nel nome file. Rimuovere lo spazio dal nome del file prima di caricare i moduli.

Quando si utilizza un modulo XDP per la conversione, effettuare le seguenti operazioni prima di caricare i moduli XPD di origine:

* Analizzare il modulo XDP e risolvere i problemi visivi. Assicurarsi che il documento di origine utilizzi i controlli e le strutture previsti. Ad esempio, il modulo di origine potrebbe avere caselle di controllo invece dei pulsanti di scelta per una singola selezione. Le caselle di controllo vengono modificate in pulsanti di scelta per creare un modulo adattivo con i componenti desiderati.
* [Aggiungere i binding al ](http://www.adobe.com/go/learn_aemforms_designer_65) modulo XDP prima di avviare la conversione. Quando nel modulo XDP di origine sono disponibili binding, il servizio applica automaticamente i binding ai campi modulo adattivi corrispondenti durante la conversione. Consente di risparmiare il tempo necessario per applicare manualmente i binding.
* [Aggiungere  ](https://helpx.adobe.com/sign/using/text-tag.html) tag Adobe Sign al file XDP. Il servizio converte automaticamente  tag Adobe Sign nei campi modulo adattivi corrispondenti. L&#39;Forms adattivo supporta un numero limitato di  campi Adobe Sign. Per l&#39;elenco completo dei campi supportati, consultare la [Utilizzo  Adobe Sign in un modulo adattivo](https://docs.adobe.com/content/help/en/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html) documentazione.
* Se possibile, convertite tabelle complesse in tabelle semplici. Una tabella con campi modulo in celle di tabella, celle di dimensioni diverse, celle con estensione di riga o colonna, celle unite, bordi parziali o nessun bordo visibile è considerata una tabella complessa. Una tabella con uno degli elementi di cui sopra è considerata una tabella complessa.
<!-- * Use sub-forms in XDP documents to create panels in adaptive forms. Service converts each sub-form to one or more adaptive form panels during conversion. -->

### Prima di avviare la conversione

* Creare modelli di modulo adattivi. I modelli consentono di specificare una struttura uniforme per i moduli dell&#39;organizzazione o del dipartimento.
* Specificare l&#39;intestazione e il piè di pagina nei modelli di modulo adattivo. Il servizio ignora l’intestazione e il piè di pagina dei documenti sorgente e utilizza il piè di pagina intestazione specificato nel modello di modulo adattivo.
* Creare temi modulo adattivi. I temi consentono di conferire un aspetto uniforme alle forme dell’organizzazione o del dipartimento.
* Configurare il modello dati del modulo per salvare e recuperare da un&#39;origine dati. Creare e configurare i servizi di lettura e scrittura per il modello dati del modulo.
* Creare frammenti di modulo adattivi e configurare il servizio per l’utilizzo dei frammenti di modulo adattivi.
* Preparare modelli di flusso di lavoro comuni per i moduli che richiedono l&#39;automazione dei processi aziendali.
* Configurare  Adobe Analytics, se necessario


## Conoscere pattern complessi

AEM [!DNL Forms Automated Conversion service] utilizza algoritmi di intelligenza artificiale e di machine learning per comprendere il layout e i campi del modulo di origine. Ogni servizio di machine learning impara continuamente dai dati di origine e produce un output migliore con ogni churn. Questi servizi imparano dall&#39;esperienza come gli umani.

[!DNL Automated Forms Conversion service] viene addestrato su una vasta gamma di moduli. Identifica facilmente i campi in un modulo di origine e produce moduli adattivi. Tuttavia, ci sono alcuni campi e stili in PDF forms che sono facilmente visibili all&#39;occhio umano ma difficili da capire per il servizio. Il servizio può assegnare tipi di campi o pannelli diversi da quelli applicabili ad alcuni campi o stili. Tutti questi pattern di campo e stile sono elencati di seguito.

Il servizio inizierebbe a identificare e assegnare campi o pannelli corretti a questi pattern, continuando a imparare dai dati di origine. Al momento, è possibile utilizzare l&#39;editor [Revisione e correzione](review-correct-ui-edited.md) per risolvere tali problemi. Prima di iniziare a risolvere i problemi o a leggere meglio, è necessario conoscere [i componenti per moduli adattivi](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html).

### Pattern generali {#general}

| Pattern | Esempio |
|--- |--- |
| **** <br>PatternService non converte i PDF forms compilati in un modulo adattivo. <br><br>**** <br>Risoluzione: utilizzare moduli adattivi vuoti. | ![Modulo compilato](assets/best-practice-filled-forms.png) |
| **** <br>PatternService potrebbe non riuscire a riconoscere testo e campi in un modulo denso. <br><br>**** <br> Risoluzione: consente di aumentare la larghezza tra il testo e i campi di un modulo denso prima di avviare la conversione. |  |
| **** <br>PatternService non supporta i moduli digitalizzati. <br><br>**** <br>Risoluzione: non utilizzare moduli digitalizzati. | ![Modulo acquisito](assets/scanned-forms.png) |
| **** <br>PatternService non estrae immagini e testo all&#39;interno delle immagini. <br><br>**** <br> Risoluzione: aggiungere manualmente immagini o testo ai moduli convertiti. | ![Immagine con modulo di testo](assets/best-practice-image-with-text.png) |
| **** <br>PatternTables con bordi puntati o non chiari non vengono convertiti. <br><br>**** <br>Risoluzione: utilizzate tabelle con bordi e bordi chiari ed espliciti. supportati. | ![Modulo tabella non chiaro](assets/best-practice-table-dotted-non-clear.png) |
| **I moduli** <br> PatternAdaptive non supportano il testo verticale. Pertanto, il servizio non converte il testo verticale nel testo Forms adattivo corrispondente. <br><br>**** <br> Risoluzione: utilizzate l&#39;editor di moduli adattivi per aggiungere testo verticale, se necessario. | ![Modulo tabella non chiaro](assets/vertical-text.png) |



### Gruppo di scelta {#choice-group}

| Pattern | Risoluzione |
|--- |--- |
| **Le opzioni del gruppo** <br> PatternChoice con forme diverse da caselle o cerchi non vengono convertite nei componenti modulo adattivi corrispondenti. <br><br>**** <br> Risoluzione: consente di modificare le forme delle opzioni di scelta in modo da creare una casella o un cerchio oppure di utilizzare l&#39;editor Revisione e Correzione per identificare le forme. | ![Campi selezionati  ](assets/best-practice-choice-group-options.png) |

### Campi modulo {#form-fields}

| Pattern | Risoluzione |
|--- |--- |
| **** <br> PatternService non identifica i campi senza bordi chiari. <br><br>**** <br> Risoluzione: utilizzate l&#39;editor di revisione e correzione per identificare tali campi. | ![campi con bordi non chiari](assets/best-practice-fields-without-clear-borders.png) |
| **** <br> PatternService potrebbe non essere in grado di identificare alcuni campi modulo di gruppo di scelta con didascalie nella parte inferiore o destra di un modulo. <br><br>**** <br> Risoluzione: utilizzate l&#39;editor di revisione e correzione per identificare tali campi | ![Campi selezionati](assets/best-practice-caption-bottom-right.png) |
| **** <br> PatternService unisce o assegna un tipo errato ad alcuni campi del modulo che si trovano molto vicini tra loro o che non hanno bordi chiari. <br><br>**** <br> Risoluzione: utilizzate l&#39;editor di revisione e correzione per identificare tali campi. | ![Campi selezionati](assets/best-practice-placed-very-near.png) |
| **** <br> PatternService potrebbe non essere in grado di riconoscere i campi con didascalie lontane o una linea tratteggiata tra la didascalia e il campo di input. <br><br>**** <br> Risoluzione: per risolvere tali problemi, utilizzate i campi dei moduli con limiti definiti o l&#39;editor di revisione e correzione. | ![Campi lontani o linea tratteggiata tra i campi della didascalia](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### Elenchi {#lists}

| Pattern | Risoluzione |
|--- |--- |
| **** <br>PatternGli elenchi contenenti campi modulo vengono uniti o non vengono convertiti in corrispondenti componenti modulo adattivi  <br><br>**** <br>RisoluzioneUtilizzare i campi modulo con limiti definiti o utilizzare l&#39;editor Revisione e Correzione per risolvere tali problemi. | ![elenchi contenenti gruppi di scelta](assets/best-practice-lists-containing-form-fields.png) |
| **** <br>PatternService può lasciare alcuni elenchi nidificati non identificati  <br><br>**** <br> RisoluzioneUtilizzare l&#39;editor di revisione e correzione per risolvere tali problemi. | ![elenchi contenenti gruppi di scelta](assets/best-practice-nested-lists.png) |
| **** <br> PatternService unisce alcuni elenchi contenenti gruppi di scelta tra loro  <br><br>**** <br> ResolutionUtilizzare l&#39;editor Review e correct per risolvere tali problemi. | ![elenchi contenenti gruppi di scelta](assets/best-practice-check-box-in-table-cells.png) |

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fields without borders are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->
