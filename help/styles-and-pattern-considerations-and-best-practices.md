---
title: 'Procedure consigliate e considerazioni '
seo-title: 'Procedure consigliate e considerazioni '
description: Best practice e considerazioni per il servizio di conversione dei moduli automatizzati
seo-description: Elenco di stili e pattern nei moduli PDF di origine per i quali il servizio di conversione moduli automatizzata non è in grado di identificare
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
translation-type: tm+mt
source-git-commit: a5d663c2a59895eb71eb5287586bc6b3862927fc

---


# Best practice e pattern complessi noti {#Best-practices-and-considerations2}

Questo documento contiene le linee guida e le raccomandazioni che gli amministratori, gli autori e gli sviluppatori di moduli possono trarre vantaggio dall&#39;utilizzo del servizio di conversione dei moduli automatizzata. Vengono illustrate le procedure ottimali, dalla preparazione dei moduli di origine alla correzione di pattern complessi che richiedono un ulteriore sforzo per la conversione automatizzata. Queste best practice contribuiscono collettivamente alle prestazioni e all&#39;output complessivi del servizio di conversione dei moduli automatizzati.

## Best practice  

Il servizio di conversione converte i moduli PDF disponibili nell’istanza di AEM Forms in moduli adattivi. Le best practice elencate di seguito consentono di migliorare la velocità e la precisione di conversione. Inoltre, queste best practice consentono di risparmiare tempo dedicato alle attività di conversione.

### Prima di caricare la sorgente

È possibile caricare tutti i moduli PDF contemporaneamente o in modo graduale, a seconda delle necessità. Prima di caricare i moduli, considera quanto segue:

* Mantenere il numero di moduli in una cartella inferiore a 15 e mantenere il numero totale di pagine in una cartella inferiore a 50.
* Le dimensioni della cartella devono essere inferiori a 10 MB. Non tenere i moduli in una sottocartella.
* Tenere il numero di pagine in un modulo inferiore a 15.
* Organizzate i documenti sorgente in un batch di 8-15 documenti. Tenere i moduli di origine con i frammenti di modulo adattivi più comuni in un unico batch.
* Non caricare i moduli protetti. Il servizio non converte i moduli protetti da password e protetti.
* Do not upload the [PDF Portfolios](https://helpx.adobe.com/it/acrobat/using/overview-pdf-portfolios.html). Il servizio non converte un portfolio PDF in un modulo adattivo.
* Non caricare moduli digitalizzati, colorati, non in lingua inglese e compilati. Tali moduli non sono supportati.
* Non caricare moduli di origine con spazi nel nome file. Rimuovere lo spazio dal nome del file prima di caricare i moduli.

Quando si utilizza un modulo XDP per la conversione, effettuare le seguenti operazioni prima di caricare i moduli XPD di origine:

* Analizzare il modulo XDP e risolvere i problemi visivi. Verificare che il documento di origine utilizzi i controlli e le strutture previsti. Ad esempio, il modulo di origine potrebbe avere caselle di controllo invece dei pulsanti di scelta per una singola selezione. Le caselle di controllo vengono modificate in pulsanti di scelta per creare un modulo adattivo con i componenti desiderati.
* [Aggiungere i binding al modulo](http://www.adobe.com/go/learn_aemforms_designer_65) XDP prima di avviare la conversione. Quando nel modulo XDP di origine sono disponibili binding, il servizio applica automaticamente i binding ai campi modulo adattivi corrispondenti durante la conversione. Consente di risparmiare il tempo necessario per applicare manualmente i binding.
* [Aggiungere tag](https://helpx.adobe.com/sign/using/text-tag.html) Adobe Sign al file XDP. Il servizio converte automaticamente i tag Adobe Sign nei campi modulo adattivi corrispondenti. I moduli adattivi supportano un numero limitato di campi di Adobe Sign. Per l&#39;elenco completo dei campi supportati, vedere [Utilizzo di Adobe Sign nella documentazione relativa ai moduli](https://docs.adobe.com/content/help/en/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html) adattivi.
* Utilizzare i sottomoduli nei documenti XDP per creare pannelli nei moduli adattivi. Il servizio converte ciascun sottomodulo in un pannello di moduli adattivi durante la conversione.
* Se possibile, convertite tabelle complesse in tabelle semplici. Una tabella con campi modulo in celle di tabella, celle di dimensioni diverse, celle con estensione di riga o colonna, celle unite, bordi parziali o nessun bordo visibile è considerata una tabella complessa. Una tabella con uno dei suddetti elementi è considerata una tabella complessa.

### Prima di avviare la conversione

* Creare modelli di modulo adattivi. I modelli consentono di specificare una struttura uniforme per i moduli dell&#39;organizzazione o del dipartimento.
* Specificare l&#39;intestazione e il piè di pagina nei modelli di modulo adattivo. Il servizio ignora l’intestazione e il piè di pagina dei documenti sorgente e utilizza il piè di pagina intestazione specificato nel modello di modulo adattivo.
* Creare temi modulo adattivi. I temi consentono di conferire un aspetto uniforme alle forme dell’organizzazione o del dipartimento.
* Configurare il modello dati del modulo per salvare e recuperare da un&#39;origine dati. Creare e configurare i servizi di lettura e scrittura per il modello dati del modulo.
* Creare frammenti di modulo adattivi e configurare il servizio per l’utilizzo dei frammenti di modulo adattivi.
* Preparare modelli di flusso di lavoro comuni per i moduli che richiedono l&#39;automazione dei processi aziendali.
* Configurare Adobe Analytics, se necessario


## Conoscere pattern complessi

Il servizio di conversione automatizzata di AEM Forms utilizza algoritmi di intelligenza artificiale e di machine learning per comprendere il layout e i campi del modulo di origine. Ogni servizio di machine learning impara continuamente dai dati di origine e produce un output migliore con ogni churn. Questi servizi imparano dall&#39;esperienza come gli umani.

Il servizio di conversione automatizzata dei moduli è disponibile in una vasta gamma di moduli. Identifica facilmente i campi in un modulo di origine e produce moduli adattivi. Tuttavia, nei moduli PDF sono presenti alcuni campi e stili che possono essere facilmente visibili all&#39;occhio umano ma che sono difficili da comprendere per il servizio. Il servizio può assegnare tipi di campi o pannelli diversi da quelli applicabili ad alcuni campi o stili. Tutti questi pattern di campo e stile sono elencati di seguito.

Il servizio inizierebbe a identificare e assegnare campi o pannelli corretti a questi pattern, continuando a imparare dai dati di origine. Al momento, per risolvere tali problemi è possibile utilizzare l&#39;editor [Revisione e Correzione](review-correct-ui-edited.md) . Prima di iniziare a risolvere i problemi o a leggere meglio, è necessario acquisire dimestichezza con i componenti [dei moduli](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)adattivi.

### Pattern generali {#general}

| Pattern | Esempio |
|--- |--- |
| **Il servizio Pattern**<br> non converte i moduli PDF colorati in moduli adattivi. <br><br>**Risoluzione **<br>Utilizzare moduli PDF in bianco e nero o in scala di grigio. | ![Modulo colorato](assets/best-practice-coloured-forms.png) |
| **Il** servizio Pattern <br>non converte i moduli PDF compilati in moduli adattivi. <br><br>**Risoluzione **<br>Utilizzare moduli adattivi vuoti. | ![Modulo compilato](assets/best-practice-filled-forms.png) |
| **Il** servizio pattern <br>potrebbe non riuscire a riconoscere testo e campi in un modulo denso. <br><br>**Risoluzione **<br>Aumentare la larghezza tra il testo e i campi di un modulo denso prima di avviare la conversione. |  |
| **Il** servizio Pattern <br>non supporta i moduli digitalizzati. <br><br>**Risoluzione **<br>Non utilizzare moduli digitalizzati. | ![Modulo acquisito](assets/scanned-forms.png) |
| **Il** servizio Pattern <br>non estrae immagini e testo all’interno delle immagini. <br><br>**Risoluzione **<br>Aggiunta manuale di immagini o testo ai moduli convertiti. | ![Immagine con modulo di testo](assets/best-practice-image-with-text.png) |
| **Le** tabelle pattern <br>con bordi punteggiati o non chiari non vengono convertite. <br><br>**Risoluzione **<br>Utilizzare tabelle con bordi e bordi chiari ed espliciti. supportati. | ![Modulo tabella non chiaro](assets/best-practice-table-dotted-non-clear.png) |
| **Il modulo adattivo per pattern** <br> non supporta il testo verticale fuori dalla casella. Pertanto, il servizio non converte il testo verticale nel testo dei moduli adattivi corrispondente. <br><br>**Risoluzione **<br>Utilizzate l&#39;editor di moduli adattivi per aggiungere testo verticale, se necessario. | ![Modulo tabella non chiaro](assets/vertical-text.png) |



### Gruppo di scelta {#choice-group}

| Pattern | Risoluzione |
|--- |--- |
| **Le opzioni del gruppo Pattern**<br> Choice con forme diverse da box o cerchio non vengono convertite nei componenti del modulo adattivo corrispondenti. <br><br>**Risoluzione **<br>Consente di modificare le forme delle opzioni di scelta in modo da creare una casella o un cerchio oppure di utilizzare l&#39;editor Revisione e Correzione per identificare le forme. | ![Campi selezionati ](assets/best-practice-choice-group-options.png) |

### Form fields {#form-fields}

| Pattern | Risoluzione |
|--- |--- |
| **Il servizio pattern** <br> non identifica i campi senza bordi chiari. <br><br>**Risoluzione **<br>Utilizzare l&#39;editor di revisione e correzione per identificare tali campi. | ![campi con bordi non chiari](assets/best-practice-fields-without-clear-borders.png) |
| **Il servizio pattern** <br> potrebbe non essere in grado di identificare alcuni campi modulo di gruppo di scelta con didascalie nella parte inferiore o destra di un modulo. <br><br>**Risoluzione **<br>Utilizzare l&#39;editor di revisione e correzione per identificare tali campi | ![Campi selezionati](assets/best-practice-caption-bottom-right.png) |
| **Il servizio Pattern**<br> unisce o assegna un tipo errato ad alcuni campi del modulo che si trovano molto vicini tra loro o che non hanno bordi chiari. <br><br>**Risoluzione **<br>Utilizzare l&#39;editor di revisione e correzione per identificare tali campi. | ![Campi selezionati](assets/best-practice-placed-very-near.png) |
| **Il servizio pattern** <br> non è in grado di riconoscere i campi con didascalie lontane o una linea tratteggiata tra la didascalia e il campo di input. <br><br>**Risoluzione **<br>Utilizzare i campi dei moduli con limiti chiari o utilizzare l&#39;editor di revisione e correzione per risolvere tali problemi. | ![Campi lontani o linea tratteggiata tra i campi della didascalia](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### Elenchi {#lists}

| Pattern | Risoluzione |
|--- |--- |
| **Gli** elenchi di pattern <br>contenenti campi modulo vengono uniti o non vengono convertiti in componenti modulo adattivi corrispondenti <br><br>**Risoluzione **<br>Utilizzare i campi modulo con limiti definiti oppure utilizzare l&#39;editor di revisione e correzione per risolvere tali problemi. | ![elenchi contenenti gruppi di scelta](assets/best-practice-lists-containing-form-fields.png) |
| **Pattern** <br>Service può lasciare alcuni elenchi nidificati non identificati <br><br>**Risoluzione **<br>Utilizzare l&#39;editor di revisione e correzione per risolvere tali problemi. | ![elenchi contenenti gruppi di scelta](assets/best-practice-nested-lists.png) |
| **Il servizio Pattern**<br> unisce alcuni elenchi contenenti gruppi di scelta tra loro, utilizzando l&#39;editor <br><br>**Resolution **<br>Use Review and Correction per risolvere tali problemi. | ![elenchi contenenti gruppi di scelta](assets/best-practice-check-box-in-table-cells.png) |

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
