---
title: 'Conversione di moduli PDF in moduli adattivi '
seo-title: Convert PDF forms to adaptive forms
description: Esegui il servizio Automated forms conversion per convertire i PDF forms in moduli adattivi
seo-description: Run the Automated Forms Conversion service to convert PDF forms to adaptive forms
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
exl-id: 415e05b5-5a90-490c-bf7c-d3365ce95e24
source-git-commit: 5f07f5df6369007a491cf0873839f84a61827cb5
workflow-type: tm+mt
source-wordcount: '1631'
ht-degree: 7%

---

# Conversione di moduli PDF in moduli adattivi {#convert-print-forms-to-adaptive-forms}

Il servizio di Automated forms conversion AEM Forms, basato su Adobe Sensei, converte automaticamente i PDF forms in moduli adattivi adattabili facili da usare e reattivi. Sia che si utilizzino PDF forms non interattivi, Acro Forms o basati su XFA, il servizio Automated forms conversion può facilmente convertire questi moduli in moduli adattivi. Per informazioni sulle funzionalità, sul flusso di lavoro di conversione e sull’onboarding, consulta [automated forms conversion](introduction.md) servizio.

## Prerequisiti {#pre-requisites}

* [**Configurare il servizio di conversione**](configure-service.md)

* **Preparare [modelli](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html) da applicare ai moduli convertiti:** L’utilizzo di un modello consente di applicare un branding coerente a tutti i moduli adattivi. Inoltre, il servizio Automated forms conversion non estrae e utilizza l’intestazione e il piè di pagina dei documenti PDF di origine. È possibile utilizzare modelli di modulo adattivo per specificare intestazione e piè di pagina. L’intestazione e il piè di pagina specificati nel modello vengono applicati al modulo adattivo durante la conversione. Quando crei una cartella per i modelli, seleziona la **[!UICONTROL Browse configurations]** opzione per tutti.

* **Preparare [temi](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html) da applicare ai moduli convertiti:** L’utilizzo di un tema consente di applicare uno stile coerente a tutti i moduli adattivi dell’organizzazione.

* **(facoltativo)** [**Convertire gli PDF forms sorgente in Adobe Sign Form**](frequently-asked-questions.md)

## Avvia il processo di conversione {#start-the-conversion-process}

Dopo aver collegato l’istanza AEM con il servizio di conversione AEM Forms, è possibile convertire i PDF forms in moduli adattivi. Esegui i seguenti passaggi nell’ordine elencato per convertire i moduli:

* [Caricare PDF forms nel server AEM Forms](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [Eseguire la conversione](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [Revisione e correzione dei moduli convertiti](review-correct-ui-edited.md)

### Caricare PDF forms nel server AEM Forms {#upload-pdf-forms-to-your-aem-forms-server}

Il servizio di conversione converte i PDF forms disponibili nell’istanza AEM Forms in moduli adattivi. Puoi caricare tutti i PDF forms contemporaneamente o in modo graduale, a seconda delle necessità. Prima di caricare i moduli, considera quanto segue:

* Mantenere il numero di moduli in una cartella inferiore a 15 e mantenere il numero totale di pagine in una cartella inferiore a 50.
* Mantenere la dimensione della cartella inferiore a 10 MB. Non conservare i moduli in una sottocartella.
* Mantenere il numero di pagine in un modulo inferiore a 15.
* Non caricare i moduli protetti. Il servizio non converte i moduli protetti da password e protetti.
* Non caricare moduli di origine con spazi nel nome file. Rimuovi lo spazio dal nome del file prima di caricare i moduli.
* Non caricare [portfolio PDF](https://helpx.adobe.com/it/acrobat/using/overview-pdf-portfolios.html). Il servizio non converte un Portfolio PDF in un modulo adattivo.
* Leggi la sezione [Problemi noti](known-issues.md) e [Procedure consigliate e considerazioni](styles-and-pattern-considerations-and-best-practices.md) e apportare modifiche consigliate ai moduli.

Esegui i seguenti passaggi per caricare i moduli da convertire in una cartella nell’istanza AEM Forms:

1. Accedi all&#39;istanza AEM Forms.

1. Tocca **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Toccare **[!UICONTROL Create]**> **[!UICONTROL Folder]**. Specifica **Titolo** e **Nome** della cartella. Toccare **[!UICONTROL Create]**. Viene creata una cartella.
1. Tocca per aprire la cartella appena creata.
1. Toccare **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. Seleziona i moduli da caricare, fai clic su **[!UICONTROL Open]** e fai clic su **[!UICONTROL Upload]**. I moduli vengono caricati.

### Eseguire la conversione {#run-the-conversion}

Dopo aver caricato i moduli e configurato il servizio, esegui i seguenti passaggi per avviare la conversione:

1. Nell’istanza di AEM Forms, tocca **[!UICONTROL Adobe Experience Manager]** ![Finestra di dialogo Impostazioni conversione](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selezionare un modulo o una cartella contenente PDF forms (moduli da convertire) e toccare **[!UICONTROL Start Automated Conversion]**. La **[!UICONTROL Conversion Settings]** viene visualizzata la finestra di dialogo .

   ![Specifica le configurazioni](assets/conversion-settings-dialog.png)

1. In **[!UICONTROL Basic]** scheda della finestra di dialogo Impostazioni conversione:

   * **[!UICONTROL Select a cloud configuration]**. Quando selezioni una configurazione, vengono già specificati il modello e il tema predefiniti. Se necessario, puoi specificare un modello o un tema diverso.
   * Specificare un percorso per salvare i moduli adattivi generati e lo schema corrispondente. Puoi utilizzare percorsi predefiniti o specificare percorsi personalizzati.
   * Utilizza la **Generare moduli adattivi senza binding dei modelli dati** opzione per selezionare se si desidera generare un modulo adattivo con o senza binding del modello dati.
Se non selezioni questa opzione, il servizio di conversione associa automaticamente i moduli adattivi a uno schema JSON e crea un binding dei dati tra i campi disponibili nel modulo adattivo e nello schema JSON. La **[!UICONTROL Save generated data model schema at]** visualizza il percorso predefinito per salvare lo schema JSON generato. Puoi anche personalizzare la posizione per salvare lo schema generato.
Se selezioni questa opzione, il servizio di conversione genera un modulo adattivo senza binding del modello dati. Dopo una conversione corretta, è possibile associare un modulo adattivo a un modello dati modulo, a uno schema XML o a uno schema JSON. Per ulteriori informazioni, consulta [Creazione di un modulo adattivo](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html).

   <!--

   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. In **[!UICONTROL Additional]** scheda della finestra di dialogo Impostazioni conversione,
   * Seleziona la **[!UICONTROL Extract fragment from adaptive forms]** per consentire al servizio di conversione di identificare, estrarre e scaricare frammenti di modulo per i moduli convertiti. Quando selezioni la **[!UICONTROL Extract fragment from adaptive forms]** le opzioni per specificare i percorsi in cui salvare i frammenti di modulo estratti e gli schemi di frammenti di modulo corrispondenti vengono abilitati.
   * Specifica la posizione di **[!UICONTROL existing adaptive form fragments]**, se si dispone di frammenti di modulo JSON basati su schemi e schema meno adattivi e si intende utilizzarli in moduli adattivi generati automaticamente. Il servizio di conversione associa i frammenti di modulo adattivi basati su schema JSON e quelli basati su schemi meno adattativi con i PDF forms di input (solo PDF forms non interattivi), in presenza di una corrispondenza, il frammento di modulo adattivo corrispondente viene utilizzato nei moduli adattivi corrispondenti.

   >[!NOTE]
   >
   >
   > * Puoi utilizzare solo **[!UICONTROL  Extract Fragment]** o **[!UICONTROL Use existing adaptive form fragments]** per volta. Non è possibile utilizzare entrambe le opzioni contemporaneamente.
   > * È possibile utilizzare **[!UICONTROL Use existing adaptive form fragments]** solo con PDF forms non interattivi. Altri tipi di moduli non sono ancora supportati.
   > * Con il servizio di conversione automatica è possibile utilizzare solo frammenti o frammenti non associati associati a uno schema JSON. Non utilizzare frammenti XFA. I frammenti XFA non sono supportati.


   * Seleziona la **[!UICONTROL Auto-detect multi-column layout of input forms]** per mantenere il layout del modulo di origine per schermi di grandi dimensioni come desktop e laptop. Questa opzione è utile per mantenere il layout a più colonne dei moduli di origine. Ad esempio, quando un PDF di origine ha un layout a due colonne, il servizio genera un modulo adattivo di output con layout a due colonne per schermi di grandi dimensioni e layout a una colonna per dispositivi a schermo piccolo come i telefoni cellulari. La funzionalità presenta alcuni problemi noti relativi alla struttura dello schema dell&#39;origine dati. Per ulteriori informazioni, consulta la sezione [problemi noti](known-issues.md) articolo.
   * Per impostazione predefinita, il servizio crea un pannello di primo livello separato per ciascuna pagina di un modulo PDF. Ora puoi utilizzare il **[!UICONTROL Auto-detect logical sections]** per non creare pannelli a livello di pagina (pannelli basati sul numero di pagina) e creare solo pannelli logici. Questa opzione, inoltre, unisce alla sezione logica precedente i campi che non appartengono ad alcuna sezione e unisce in un’unica sezione logica i campi di una sezione logica suddivisi su due pagine adiacenti. Ad esempio, se alcuni campi di una sezione logica si trovano alla fine della pagina 1 e altri si trovano all’inizio della pagina 2, tutti questi campi sono raggruppati in una singola sezione logica.

      >[!NOTE]
      > Per utilizzare il pacchetto del connettore 1.1.38 o superiore è necessario  **[!UICONTROL Auto-detect logical sections]** funzionalità.


* (Solo AEM Forms as a Cloud Service) Il [Conversione automatica delle sezioni in frammenti] si applica ai PDF forms con più di 15 pagine. Converte le sezioni di primo livello rilevate in frammenti. Abilita inoltre il caricamento lento per tutti i frammenti creati. Consente di migliorare la velocità di rendering dei moduli convertiti e di caricare più facilmente i moduli di grandi dimensioni nell’editor di moduli adattivi.

   >[!NOTE]
   > Non utilizzare il modello di layout dinamico quando si utilizza l’opzione di conversione automatica delle sezioni in frammenti.
   > Utilizza l’editor di revisione e corretto per unire pannelli di piccole dimensioni a uno di grandi dimensioni. Consente di ridurre il numero di frammenti nel modulo adattivo convertito.
   > Se si verifica l&#39;eccezione &quot;troppe chiamate&quot;,
   >
   > * ristrutturare il modulo per creare una gerarchia semplificata
   > * [aumenta il valore del parametro sling.max.Calls]a un numero sufficiente finché l&#39;eccezione non scompare.
   > * [aumentare le dimensioni della cache](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/configure-aem-forms/configure-adaptive-forms-cache.html). L’errore si verifica se il modulo è troppo complesso, presenta un numero elevato di tabelle e una struttura gerarchica a più livelli.


1. Toccare **[!UICONTROL Start Conversion]**. La conversione viene avviata. L’avanzamento della conversione viene visualizzato nella cartella o nel modulo fino a quando la conversione non è in corso. Al termine della conversione, il messaggio viene sostituito da un altro messaggio di stato (Conversione, Conversione parziale o Conversione non riuscita). Al termine della conversione viene inoltre inviata un’e-mail di stato sull’indirizzo e-mail configurato:

   * In caso di conversione riuscita, il modulo adattivo convertito e lo schema correlato vengono scaricati nel percorso specificato in **[!UICONTROL Basic]** scheda della finestra di dialogo di conversione. I frammenti di modulo e lo schema corrispondente vengono scaricati solo se prima di avviare la conversione è selezionata l’opzione Estrai frammento .
   * In caso di conversione non riuscita, il **[!UICONTROL Conversion Failed]** viene visualizzato un messaggio se non è possibile convertire tutti i moduli di input oppure **[!UICONTROL Partially Failed]** viene visualizzato un messaggio quando la conversione di solo alcuni moduli di input non è riuscita. Viene inviata un’e-mail di stato nel [indirizzo e-mail configurato](configure-service.md#configureemailnotification) e viene registrato un errore nel file error.log.

   Se si sta convertendo un modulo PDF basato su XFA in un modulo adattivo, il servizio di conversione associa automaticamente il modulo PDF al modulo adattivo convertito come modello Documento di record. Dopo la conversione, è possibile aprire le proprietà del modulo adattivo per visualizzare il modello Documento di record nel **[!UICONTROL Document of Record Template Configuration]** sezione **[!UICONTROL Form Model]** scheda . </br>

   Il servizio di conversione carica automaticamente il modulo PDF nel modulo adattivo convertito come modello Documento di record solo se si abilita il **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** opzione .

   <!--

   Comment Type: draft

   <note type="note">
   <p>By default, the adaptive form produces a JSON schema instead of XML schema on submission. JSON schema of a converted adaptive form is complaint with XML schema of an XFA-based form. You can use the <a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString">org.apache.sling.commons.json.xml API</a> to convert a JSON schema to XML schema. You can also use the following sample code for conversion:</p>
   <p><code class="code">import org.apache.sling.commons.json.JSONException;
   <discoiqbr /> import org.apache.sling.commons.json.JSONObject;
   <discoiqbr /> import org.apache.sling.commons.json.xml.XML;
   <discoiqbr />
   <discoiqbr /> public class ConversionUtils {
   <discoiqbr />
   <discoiqbr /> public static String jsonToXML(String jsonString) throws JSONException {
   <discoiqbr /> //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
   <discoiqbr /> //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
   <discoiqbr /> //Note: Need to extract boundData part before converting to XML
   <discoiqbr /> return XML.toString(new JSONObject(jsonString));
   <discoiqbr /> }
   <discoiqbr /> }</code><br /> </p>
   </note>
   -->

   >[!NOTE]
   >
   >Se il processo di conversione richiede più di 60 minuti e il modulo PDF non viene ancora convertito in un modulo adattivo, crea una cartella sull’istanza AEM Forms, carica il modulo PDF nella nuova cartella creata e riavvia la conversione.

## Revisione e correzione dei moduli convertiti {#review-and-correct-the-converted-forms}

I moduli nel mondo reale hanno requisiti di acquisizione dati complessi. Una volta completata la conversione automatica, i clienti possono verificare la qualità di conversione del modulo e apportare gli aggiornamenti necessari al modulo. AEM Forms fornisce un [rivedere e correggere](review-correct-ui-edited.md) per apportare le modifiche necessarie. Consente di migliorare l’identificazione automatica dei campi modulo e di convertire i campi identificati da un tipo all’altro. Ad esempio, è possibile identificare il layout a due colonne di un modulo e modificare un campo identificato automaticamente come pulsante di scelta in più campi di scelta.
