---
title: Revisione dei moduli convertiti
seo-title: Revisione dei moduli convertiti
description: Esaminare e correggere i moduli adattivi convertiti dal servizio di conversione Forms automatizzata.
seo-description: Esaminare e correggere i moduli adattivi convertiti dal servizio di conversione Forms automatizzata
uuid: 5a0a6d24-dff6-4732-b607-24848b07b26d
topic-tags: forms
discoiquuid: f45ab2d7-5234-42d6-aeb6-b2cb1a7ce3c2
translation-type: tm+mt
source-git-commit: 3c12751cad2b3c04ad66a98ac17f20f648530d0f
workflow-type: tm+mt
source-wordcount: '2536'
ht-degree: 0%

---


# Revisione dei moduli convertiti{#review-and-correct-converted-forms}

 AEM Forms Automated Forms Conversion Service identifica campi, contenuto e layout del documento PDF di input e converte il documento PDF in un modulo adattivo. Il modulo adattivo di output può contenere alcuni campi mancanti o convertiti in modo non corretto. È possibile utilizzare l&#39;editor Revisione e Correzione per apportare miglioramenti ai campi identificati e rigenerare il modulo adattivo per ottenere un output più vicino all&#39;esperienza desiderata. Dopo la prima conversione, è possibile aprire il documento PDF di input nell&#39;editor per:

* Visualizza tutti i campi e i contenuti identificati durante la conversione
* Identificare i campi e il contenuto persi durante la conversione
* Verificare il tipo di campo e modificarne il tipo, se necessario
* Verificare le tabelle identificate, ridimensionare le colonne e modificare il contenuto delle celle
* Rimozione di campi erroneamente identificati

Dopo aver apportato le modifiche necessarie, inviate nuovamente i PDF forms al servizio di conversione. In caso di conversione riuscita, le risorse aggiornate, inclusi il modulo adattivo e lo schema, vengono scaricate nell&#39;istanza AEM Forms . Potete ripetere il processo fino a ottenere l&#39;esperienza desiderata. ![](assets/stages-of-form-2.gif)

È necessario Google Chrome, Mozilla FireFox o Microsoft Edge browser per utilizzare revisione e correzione editor. L&#39;editor non supporta Internet Explorer.

## Editor di revisione e correzione {#welcome-to-review-and-correct-editor}

L&#39;editor di revisione e correzione fornisce un&#39;interfaccia di facile utilizzo. Contiene i seguenti componenti:

* Browser contenuto: Potete utilizzare il browser del contenuto per cambiare la posizione di un elemento. Il browser del contenuto consente di trascinare un oggetto modulo per modificarne la posizione. Ad esempio, spostare una tabella prima di una casella di testo. Cambia di conseguenza l&#39;ordine di tabulazione del modulo adattivo di output.
* Browser proprietà: Visualizza le proprietà di un campo selezionato. È inoltre possibile modificare le proprietà.
* Barra degli strumenti: La barra degli strumenti si trova nella parte superiore dell’editor. Visualizza gli strumenti per aggiungere, modificare, raggruppare, separare ed eliminare i campi.
* Proprietà di apertura: L&#39;opzione Apri proprietà viene visualizzata toccando l&#39; ![](assets/properties.png) icona. È possibile fare clic su Apri proprietà per aprire le proprietà del modulo e visualizzare altre opzioni.
* Pulsante Filtro: Il pulsante del filtro ![](assets/toggle_eye.png) si trova nella parte superiore dell’editor. Consente di filtrare i campi per visualizzare solo testo, campi, gruppi di scelta, pannelli o tutti i componenti.
* Pulsante Salva: Il **[!UICONTROL Save]** pulsante si trova nell’angolo superiore destro dell’editor. È inoltre possibile utilizzare la freccia accanto al pulsante Salva per visualizzare l&#39;opzione per inviare il modulo per la conversione.

* Modulo PDF: L&#39;editor visualizza il documento PDF di origine e lo sovrappone con i campi identificati. È possibile utilizzare gli strumenti disponibili nella barra degli strumenti per modificare i campi.
* Pagine: Un modulo di origine può avere più pagine. L&#39;editor fornisce un pulsante nell&#39;angolo superiore destro per spostarsi tra le pagine.

![Interfaccia utente di revisione e correzione](assets/reviewcorrectui.png)

**A.** Browser dei contenuti **B.** Browser proprietà **C.** Barra degli strumenti **D.** Pulsante Proprietà **E.** Pulsante Filtro **F.** Pulsante Salva **G.** Modulo PDF sovrapposto con campi identificati

Dopo la prima conversione, il servizio di conversione sovrappone il documento PDF di origine con campi e componenti identificati. Questi campi o componenti sono di tipo: Testo, Campo, Pannello, Gruppo di scelta e tabella:

* Testo: Testo normale nel documento PDF di origine. Ad esempio, il testo dell&#39;applicazione di prestito nell&#39;immagine visualizzata sopra.
* Campo: Combinazione di testo o etichetta di icona associata a un valore o a una casella di input. Ad esempio, il nome del campo Primo nell&#39;immagine precedente. Contiene un&#39;etichetta di testo e una casella di input. Un campo supporta i tipi di dati testo, numerici, a discesa, data, e-mail, numeri di telefono, firma, valuta e password.
* Pannello: Raccolta logica di contenuti e componenti. Ad esempio, Dettagli personali dei pannelli Persona 1 e Persona 2 nell&#39;immagine precedente.
* Gruppo di scelta: Combinazione di testo associato a opzioni a scelta multipla: casella di controllo e pulsante di scelta. Ad esempio, Stato civile e cliente esistente nell&#39;immagine precedente.\
   In base alla didascalia del gruppo di scelta e alle relative opzioni a scelta multipla, il servizio di conversione converte automaticamente un gruppo di scelta in un pulsante di scelta a selezione singola o in una casella di controllo a selezione multipla. Ad esempio, se è presente **Selezionare una** qualsiasi **didascalia del gruppo di scelta o le opzioni a scelta multipla consentono di selezionare una sola opzione,** Sì **o** No, il servizio di conversione converte automaticamente il gruppo di scelta in un pulsante di scelta a selezione singola. Allo stesso modo, se è presente **Select all che si applica** o **Select multiple** come didascalia del gruppo di scelta o se le opzioni a scelta multipla consentono di selezionare più opzioni, il servizio di conversione converte automaticamente il gruppo di scelta in una casella di controllo a selezione multipla.

* Tabella: Una tabella da 2 d con informazioni rappresentate in colonne e righe. È possibile aggiungere o rimuovere righe o colonne da una tabella.

## Avvio della revisione di una conversione {#start-reviewing-a-conversion}

Dopo la prima conversione, il servizio di conversione sovrappone il documento PDF di origine con campi e componenti identificati. È possibile apportare miglioramenti ai campi identificati e rigenerare il modulo adattivo per ottenere un output più vicino all&#39;esperienza desiderata. È possibile iniziare a rivedere una conversione solo dopo la prima conversione.

### Prima di iniziare {#before-you-start}

* L&#39;editor di revisione e correzione non supporta i frammenti. Non utilizzate l&#39;editor per esaminare le conversioni per le quali è stata abilitata l&#39;opzione **Estrai frammento** durante le conversioni. Per tali conversioni è possibile utilizzare l’editor [di moduli](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html) adattivi.

* L&#39;editor di revisione e correzione non dispone di azioni di annullamento. Utilizzate il pulsante Salva solo per salvare in modo permanente le modifiche.

### Avviare la revisione {#start-the-review}

Per avviare la revisione delle conversioni, selezionare il documento PDF di origine utilizzato per la conversione, quindi selezionare e toccare **Rivedi conversioni**. L&#39;editor Revisione e Correzione si apre in una nuova scheda. Potete iniziare a rivedere le conversioni. Effettuate i seguenti controlli di base prima di iniziare a risolvere qualsiasi altro problema:

![](assets/usingreviewandcorrecteditor.png)

1. **Controllare il tipo di tutti i campi**: Il servizio di conversione può assegnare un tipo errato a un campo. Ad esempio, al campo del telefono cellulare viene assegnato il testo anziché il tipo telefono. È possibile passare il puntatore del mouse su un campo per individuare il tipo di campo.

   Per modificare il tipo di campo, selezionare il campo, aprire il browser delle proprietà, selezionare un valore dal **[!UICONTROL Type]** menu a discesa e toccare **[!UICONTROL Save]**. Il tipo viene modificato.

   ![](assets/check-typex75.gif)

1. **Rimuovere altri pannelli**: Il servizio di conversione può generare ulteriori pannelli. Ad esempio, nel pannello principale è incluso un ulteriore sottopannello, lo spazio vuoto viene convertito in un pannello, una casella di controllo viene convertita in un pannello. Esaminate i bordi di tutti i pannelli e rimuovete altri pannelli. Potete utilizzare il ![](assets/toggle_eye.png) pulsante del filtro o il browser del contenuto per visualizzare tutti i pannelli.

   Potete eliminare o separare un pannello per rimuoverlo. Quando usate l’opzione di eliminazione, vengono eliminati anche i campi secondari o i componenti del pannello:

   * Per eliminare un pannello, selezionatelo e toccate l’icona Elimina ![](assets/delete-icon.png) nella barra degli strumenti. Nella finestra di dialogo di conferma, toccate **[!UICONTROL Confirm]**. Toccate **[!UICONTROL Save]** per salvare le modifiche.

   * Per separare un pannello, selezionatelo e toccate l’icona di separazione nella barra degli strumenti. Il pannello è separato e i campi secondari del pannello non raggruppato sono regolati in base al campo padre. Toccate **[!UICONTROL Save]**per salvare le modifiche.

1. **Creare gruppi logici di testo**: Convalidare i testi identificati per completezza e correttezza. Controllate inoltre che i testi siano inseriti logicamente in pannelli o gruppi corretti. Ad esempio, in un layout a più colonne, i testi di un gruppo logico e inseriti in un altro gruppo.

   * Per verificare la completezza e la correttezza del testo, utilizzate il ![](assets/toggle_eye.png) pulsante del filtro per visualizzare solo il testo, fate clic su ciascun testo e convalidate. Correggete eventuali errori di ortografia, errori di battitura o grammatica.

   * Per aggiungere del testo al modulo, toccate il pulsante +, quindi toccate **[!UICONTROL Text]**. Disegnate la casella, aprite il browser delle proprietà e digitate il testo da aggiungere alla casella Contenuto.

1. **Esaminare le tabelle:** Assicurarsi che tutti i bordi della tabella siano identificati. Inoltre, verificare che il contenuto delle celle sia identificato correttamente.

   * Per identificare i bordi mancanti, utilizzare l&#39; **[!UICONTROL Add Column]** opzione o **[!UICONTROL Add Row]** .

   * Per rimuovere bordi aggiuntivi, utilizzare l&#39; **[!UICONTROL Delete Column]** opzione o **[!UICONTROL Delete Row]** .

Dopo aver apportato le modifiche necessarie, toccate il **[!UICONTROL Save & Convert]** pulsante per inviare nuovamente i PDF forms al servizio di conversione. Ogni campo viene convertito in un componente campo adattivo corrispondente. Dopo la conversione, le risorse aggiornate, incluso il modulo adattivo e lo schema, vengono scaricate nell&#39;istanza AEM Forms . A seconda della complessità del modulo, il completamento della conversione potrebbe richiedere del tempo.

![Salva e converti](assets/save-and-convert.png)

Dopo aver eseguito i controlli di base, è possibile esaminare il modulo per risolvere i problemi specifici dell&#39;organizzazione. Questi problemi possono essere correlati all&#39;aggiunta di campi mancanti e molto altro. Potete visualizzare la sezione [Utilizzare gli strumenti](review-correct-ui-edited.md#use-the-review-and-correct-editor-tools) di revisione e correzione dell&#39;editor per apprendere tutti gli strumenti forniti dall&#39;editor per risolvere tali problemi.

È inoltre possibile riconoscere gli stessi problemi che si verificano in quasi tutti i moduli e segnalare tali pattern al Adobe . Utilizzate l&#39;editor Review e correct fino a ottenere l&#39;esperienza desiderata.

## Utilizzare gli strumenti di modifica Revisione e Correzione {#use-the-review-and-correct-editor-tools}

Con l&#39;editor Review e Correction, potete:

* [Aggiunta di un componente al modulo](review-correct-ui-edited.md#add-a-component-to-the-form)
* [Aggiunta o modifica di una tabella](review-correct-ui-edited.md)
* [Modificare il tipo di componente](review-correct-ui-edited.md#change-type-a-component)

* [Creare o rimuovere un pannello](review-correct-ui-edited.md#create-or-remove-a-panel)
* [Eliminare un pannello o un componente](review-correct-ui-edited.md#delete-a-panel-or-component)
* [Impostazione delle proprietà di un componente](review-correct-ui-edited.md#set-properties-of-a-component)
* [Inviare un modulo per la conversione](review-correct-ui-edited.md#send-a-form-for-conversion)

### Aggiunta di un componente al modulo {#add-a-component-to-the-form}

Il servizio di conversione potrebbe non identificare alcuni componenti del modulo di stampa. Ad esempio, in un componente **Data di nascita** di un modulo non viene identificato durante la conversione. Potete usare lo strumento **+** per identificare tali componenti. Consente di aggiungere testo, campi, gruppi di scelta, tabelle e componenti per pannelli.

![](assets/add-component.gif)

Per aggiungere un componente al modulo, toccate **[!UICONTROL +]** e toccate **[!UICONTROL Field]**. Disegnare una casella che copra l&#39;etichetta e la casella di input del campo. Ad esempio, l&#39;immagine di esempio precedente utilizza il componente Campo per aggiungere al modulo l&#39;etichetta **Data di nascita** e la casella del valore al di sotto di esso. Quando si disegna la casella, il servizio di conversione identifica il tipo di campo. Se necessario, è possibile modificare il tipo di campo dal browser delle proprietà. Dopo aver creato il componente, aprite il browser delle proprietà e impostate le proprietà del componente.

Toccate **[!UICONTROL Save]** il pulsante per salvare le modifiche o usate il **[!UICONTROL Save & Convert]** pulsante per inviare nuovamente i PDF forms al servizio di conversione.

### Aggiunta o modifica di una tabella {#addedittable}

La conversione può lasciare non identificate alcune celle, bordi o contenuto di una cella di tabella. Ad esempio, una riga di una tabella non è identificata. Potete utilizzare l&#39;editor Revisione e correzione per identificare tali elementi. Per una tabella è possibile eseguire le azioni seguenti:

* Per selezionare una tabella, fare clic su una cella qualsiasi della tabella.
* Per modificare le proprietà di una cella come nome, titolo o tipo, fare doppio clic su una cella. È inoltre possibile fare doppio clic sulla cella per modificare il contenuto, contrassegnare un campo obbligatorio e selezionare altre proprietà.
* Per aggiungere o identificare al modulo una tabella completamente non identificata o nuova, utilizzare lo **[!UICONTROL +]** strumento.
* Per ridimensionare le celle o le righe di una tabella, fare clic su un&#39;area vuota della tabella, passare il puntatore del mouse sul contorno di una riga o di una colonna, quando il puntatore del mouse cambia, selezionare e spostare il contorno. Dopo il ridimensionamento, fate clic **[!UICONTROL Done]** per salvare le modifiche. È possibile premere il **[!UICONTROL ESC]** tasto per eliminare il ridimensionamento.

* Per aggiungere o eliminare righe o colonne, selezionare una cella nella riga della tabella e selezionare l&#39; **[!UICONTROL Add Row]**, **[!UICONTROL Add Column]**, **[!UICONTROL Delete Row]** o **[!UICONTROL Delete Column]** opzione dal ![](assets/table_18x18.png) menu.

* Per dividere una cella in una tabella, selezionare l&#39; **[!UICONTROL Spilt Vertical]** opzione o **[!UICONTROL Split Horizontal]** dal ![](assets/table_18x18.png) menu.

* Per unire le celle di una tabella, selezionare le celle da unire, quindi selezionare l&#39; **[!UICONTROL Merge Cells]** opzione dal menu ![](assets/table_18x18.png) della tabella.

### Modificare il tipo di componente {#change-type-a-component}

Il servizio di conversione può creare alcuni campi di tipo errato. Ad esempio, nell&#39;immagine seguente, il campo **Genere** non è correttamente identificato come campo di **testo** . Inoltre, il contenuto dell&#39;etichetta è errato. Il campo deve essere un tipo di campo di scelta e l&#39;etichetta deve essere Genere. Per modificare il tipo di un componente e correggerne l’etichetta:

Selezionare il campo da convertire, toccare ![](assets/smock_shuffle_18_n.svg) e toccare un tipo di campo. Il campo è convertito in un tipo di campo selezionato. Un campo può essere convertito solo in tipi elencati nella tabella seguente. Un componente di un pannello può essere solo separato, non trasformato.

| **Componente** | **Converte in** |
|---|---|
| Testo | Campo o gruppo di scelta |
| Campo | Testo o gruppo di scelta |
| Gruppo di scelta | Testo o pannello |

Dopo la conversione, aprite il browser delle proprietà, specificate l&#39;etichetta e specificate le altre proprietà richieste. Toccate **[!UICONTROL Save]** il pulsante per salvare le modifiche o usate il pulsante Salva e converti per inviare nuovamente i PDF forms al servizio di conversione.

### Creare o rimuovere un pannello {#create-or-remove-a-panel}

Il servizio di conversione aggrega i componenti correlati e il contenuto dei moduli di stampa in un pannello. Ad esempio, il modulo può avere un pannello di indirizzi con campi quali nome, numero del grafico, area, città, stato, CAP e paese. Questi campi sono raggruppati in un pannello. Un modulo può avere più pannelli.

Il servizio di conversione può creare pannelli con componenti che non hanno alcuna relazione con altri componenti o che escono dal pannello da un componente relativo. Potete usare gli strumenti di gruppo o di separazione dei gruppi per correggere tali pannelli:

* Per rimuovere un pannello, selezionatelo e toccate Separa ![gruppo](assets/ungroupX18.png). Il pannello viene rimosso e i componenti secondari del pannello vengono spostati sul componente principale. Potete anche usare l’opzione [Elimina componente](review-correct-ui-edited.md#delete-a-panel-or-component) per eliminare un pannello e i relativi elementi secondari.

* Per creare un pannello, usate il tasto Ctrl (in Windows o Linux) o il tasto Ctrl (in Mac) per selezionare i componenti correlati, quindi toccate ![il gruppo](assets/group.jpg) per creare un pannello. Aprite il browser delle proprietà per specificare le proprietà del pannello.

Toccate **[!UICONTROL Save]** il pulsante per salvare le modifiche o usate il **[!UICONTROL Save & Convert]** pulsante per inviare nuovamente i PDF forms al servizio di conversione.

### Eliminare un pannello o un componente {#delete-a-panel-or-component}

Il servizio di conversione può identificare alcuni pannelli o componenti non corretti. La maggior parte di questi componenti di questi pannelli non sono correlati. Potete eliminare tali pannelli o componenti.

Per eliminare un pannello o un componente, selezionate un pannello o un componente e toccate l’ ![](assets/delete-icon.png) icona Elimina. Nella finestra di dialogo di conferma toccate **[!UICONTROL Confirm]**. Il pannello o il componente selezionato viene eliminato. Quando eliminate un pannello, vengono eliminati anche tutti gli elementi secondari del pannello. Potete usare il tasto Ctrl (in Windows o Linux) o il tasto Ctrl (in Mac) per selezionare più componenti o pannelli.

### Impostazione delle proprietà di un componente {#set-properties-of-a-component}

Ogni componente del modulo dispone di un set di proprietà come nome, titolo, tipo. Per impostare le proprietà di un componente, selezionate il componente e toccate il browser delle proprietà. Vengono visualizzate le proprietà del componente selezionato. Modificate o impostate le proprietà.

Toccate **[!UICONTROL Save]** il pulsante per salvare le modifiche o usate il **[!UICONTROL Save & Convert]** pulsante per inviare nuovamente i PDF forms al servizio di conversione.

### Inviare un modulo per la conversione {#send-a-form-for-conversion}

Dopo aver apportato tutte le modifiche necessarie nell&#39;editor di revisione e correzione, è possibile inviare nuovamente il modulo per la conversione. Per inviare il modulo per la conversione, toccate **[!UICONTROL Save & Convert]**. Il modulo **[!UICONTROL Sent for conversion label]** viene applicato alla cartella contenente il documento di origine e il modulo di origine aggiornato viene caricato nel servizio di conversione in esecuzione  I/O Adobe.

A seconda della complessità del modulo, il servizio di conversione può richiedere del tempo per convertire il modulo. Una volta completata la conversione, il modulo adattivo convertito e le risorse correlate vengono scaricati nel computer. È possibile esaminare il modulo nell&#39;editor dopo che la conversione è stata completata e aprire il modulo adattivo nell&#39;editor [di moduli](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html) adattivi per il set finale di correzioni, se necessario.

Se si invia nuovamente un modulo per la conversione dopo l&#39;aggiornamento del modulo nell&#39;editor di moduli adattivi, tutte le modifiche apportate nel modulo adattivo andranno perse. È possibile aprire un modulo in revisione e nell&#39;editor corretto solo dopo la conversione.

<!--
Comment Type: draft

<h3>Open adaptive forms editor</h3>
-->

<!--
Comment Type: draft

<p>There can be instances where you require adaptive forms editor to make the changes like, applying a different theme to the form or fixing tables. Once you have made all the required changes in Review and Correct editor and converted the form, you can open your form in adaptive forms editor to make the final set of changes.</p>
<p>To open the form with adaptive forms editor, tap the <img src="assets/properties.png" /> icon, and tap <strong>Open Adaptive Form Editor</strong>. The form opens in adaptive form editor. </p>


## Previous {#previous}

[Use Automated Forms Conversion service](convert-existing-forms-to-adaptive-forms.md)
-->
