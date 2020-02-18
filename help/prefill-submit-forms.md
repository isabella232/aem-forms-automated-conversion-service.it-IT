---
title: Flussi di lavoro di precompilazione e invio basati sull'origine dati consigliati per i moduli adattivi
seo-title: Opzioni di precompilazione e invio per i moduli adattivi
description: Flussi di lavoro di precompilazione e invio basati sull'origine dati per i moduli adattivi generati utilizzando Automated Forms Conversion Service.
seo-description: Flussi di lavoro di precompilazione e invio basati sull'origine dati per i moduli adattivi generati utilizzando Automated Forms Conversion Service.
uuid: 91409a82-141c-4233-82b1-1539a0b250f8
contentOwner: khsingh
topic-tags: forms
discoiquuid: cad34fff-7f9f-4a27-8b5c-d0a523903eec
privatebeta: true
translation-type: tm+mt
source-git-commit: f598871fd41c402f98d94d7b2174ab8b2e487075

---


# Flussi di lavoro di precompilazione e invio basati sull&#39;origine dati consigliati per i moduli adattivi {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

È possibile utilizzare una delle origini dati seguenti con moduli adattivi convertiti utilizzando il servizio di conversione moduli automatizzati:

* Modello dati modulo, OData o qualsiasi altro servizio di terze parti
* Schema JSON
* schema XSD

In base all&#39;origine dati, è possibile scegliere di generare un modulo adattivo con o senza un modello dati.

Questo articolo descrive i flussi di lavoro consigliati per precompilare i valori dei campi e le opzioni di invio dopo aver selezionato un&#39;origine dati e generato un modulo adattivo utilizzando il servizio di conversione.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Sorgente dati</strong></th> 
   <th><strong>Flusso di lavoro consigliato</strong></th> 
  </tr> 
  <tr> 
   <td><p>Modello dati modulo, OData o qualsiasi altro servizio di terze parti</p></td> 
   <td> 
    <p><strong>Opzione 1</strong>: È possibile selezionare il modello dati del modulo, OData o qualsiasi altro servizio di terze parti come origine dati. È <a href="#generate-adaptive-forms-with-no-data-binding">possibile generare un modulo adattivo senza alcun binding</a> di dati utilizzando il servizio di conversione moduli automatizzati. È possibile eseguire manualmente il binding dei campi modulo adattivo alle entità del modello dati del modulo e utilizzare l'opzione Servizio di precompilazione modello dati modulo per precompilare i valori dei campi. Per inviare il modulo adattivo è possibile utilizzare l'opzione Invia utilizzando il modello dati modulo.</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>Opzione 2</strong>: È possibile selezionare il modello dati del modulo, OData o qualsiasi altro servizio di terze parti come origine dati. È <a href="#generate-adaptive-forms-with-no-data-binding">possibile generare un modulo adattivo senza alcun binding</a> di dati utilizzando il servizio di conversione moduli automatizzati. I campi modulo adattivo vengono associati utilizzando l'editor di regole per precompilare i valori dei campi. Se necessario, modificare i valori dei campi e inviare i dati al repository crx.</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>Per istruzioni dettagliate sull'esecuzione di questi flussi di lavoro, vedere <a href="#sqldatasource">Uso di database, OData o qualsiasi servizio di terze parti come origine dati.</a></p> </td> 
  </tr>
  <tr>
  <td><p>Schema JSON</p></td> 
   <td> 
    <p>È possibile selezionare lo schema JSON come origine dati. In base all'origine dati selezionata:</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opzione 1</strong>: È possibile <a href="#generate-adaptive-forms-with-no-data-binding">generare un modulo adattivo senza alcun binding</a> di dati utilizzando il servizio di conversione moduli automatizzati e configurare lo schema JSON come origine dati. Eseguire il binding manuale dei campi modulo adattivi allo schema JSON e <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">utilizzare uno dei protocolli</a> supportati per precompilare i valori dei campi. Se necessario, modificare i valori dei campi e inviare i dati al repository crx.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Per istruzioni dettagliate sull'esecuzione dei flussi di lavoro, vedere <a href="#jsondatasource">Uso dello schema JSON come origine dati.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opzione 2</strong>: È <a href="#generate-adaptive-forms-with-json-binding">possibile generare un modulo adattivo con il binding</a> dei dati JSON utilizzando il servizio di conversione moduli automatizzata. Il servizio di precompilazione e la funzione di invio del modulo risultano perfettamente visibili. Non sono necessari passaggi di configurazione.</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>Per istruzioni dettagliate sull'esecuzione dei flussi di lavoro, vedere <a href="#jsonwithdatabinding">Uso dello schema JSON come origine dati.</a></p> </td> 
  </tr>
  <tr>
  <td><p>schema XSD</p></td> 
   <td> 
    <p>Selezionare lo schema XSD come origine dati. In base all'origine dati selezionata, è possibile <a href="#generate-adaptive-forms-with-no-data-binding">generare un modulo adattivo senza binding</a> di dati utilizzando il servizio di conversione moduli automatizzata e configurare lo schema XSD come origine dati. Eseguire il binding manuale dei campi modulo adattivo allo schema XSD e <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">utilizzare uno dei protocolli</a> supportati per precompilare i valori dei campi. Se necessario, modificare i valori dei campi e inviare i dati al repository crx.</p>
    </td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Per istruzioni dettagliate sull'esecuzione dei flussi di lavoro, vedere <a href="#xsddatasource">Uso dello schema XSD come origine dati.</a></p>
    </td> 
  </tr>
 </tbody> 
</table>


Per ulteriori informazioni sul servizio di conversione dei moduli automatizzati, vedere i seguenti articoli:

* [Introduzione al servizio di conversione dei moduli automatizzati](introduction.md)
* [Configurare il servizio di conversione dei moduli automatizzati](configure-service.md)
* [Conversione di moduli per la stampa in moduli adattivi](convert-existing-forms-to-adaptive-forms.md)
* [Revisione e correzione dei moduli convertiti](review-correct-ui-edited.md)

Le informazioni fornite in questo articolo si basano sul presupposto che chiunque le legga abbia conoscenze di base sui concetti dei moduli adattivi.

## Prerequisiti {#pre-requisites}

* Configurare un’istanza di creazione [AEM](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html)
* Configurare il servizio di conversione [automatica dei moduli nell’istanza di creazione di AEM](configure-service.md)

## Esempio di modulo adattivo {#sample-adaptive-form}

Per eseguire i casi di utilizzo per precompilare i valori dei campi in un modulo adattivo e inviarli all&#39;origine dati, scaricare il seguente file PDF di esempio.

Modulo di richiesta di prestito di esempio

[Ottieni file](assets/sample_loan_application_form.pdf)

Il file PDF funge da input per il servizio di conversione automatizzata dei moduli. Il servizio converte questo file in un modulo adattivo. Nell&#39;immagine seguente viene illustrata l&#39;applicazione di prestito di esempio in formato PDF.

![modulo di richiesta di prestito di esempio](assets/sample_form_new.png)

## Preparare i dati per il modello di modulo {#prepare-data-for-form-model}

AEM Forms Data Integration consente di configurare e connettersi a origini dati diverse. Dopo aver generato un modulo adattivo utilizzando il processo di conversione, è possibile definire il modello di modulo in base a un modello dati del modulo, a uno schema XSD o JSON. È possibile utilizzare un database, Microsoft Dynamics o qualsiasi altro servizio di terze parti per creare un modello dati del modulo.

Questa esercitazione utilizza il database MySQL come origine per creare un modello dati del modulo. Creare uno schema **di applicazione** di prestito nel database e aggiungere una tabella **richiedente** allo schema in base ai campi disponibili nel modulo adattivo.

![Dati di esempio mysql](assets/sample_data_mysql.png)

È possibile utilizzare la seguente istruzione DDL per creare la tabella **richiedente** nel database.

```sql
CREATE TABLE `applicant` (
   `name` varchar(45) DEFAULT NULL,
   `address` varchar(45) DEFAULT NULL,
   `phonenumber` int(11) NOT NULL,
   `email` varchar(45) DEFAULT NULL,
   `occupation` varchar(45) DEFAULT NULL,
   `annualsalary` varchar(45) DEFAULT NULL,
   `familymembers` int(11) DEFAULT NULL,
   PRIMARY KEY (`phonenumber`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

Se si utilizza uno schema XSD come modello di modulo per eseguire i casi di utilizzo, creare un file XSD con il testo seguente:

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="http://adobe.com/sample.xsd"
                    xmlns="http://adobe.com/sample.xsd"
                    xmlns:xs="http://www.w3.org/2001/XMLSchema">

<xs:element name="sample" type="SampleType"/>

  <xs:complexType name="SampleType">
    <xs:sequence>
      <xs:element name="name" type="xs:string"/>
   <xs:element name="address" type="xs:string"/>
   <xs:element name="phonenumber" type="xs:int"/>
   <xs:element name="email" type="xs:string"/>
   <xs:element name="occupation" type="xs:string"/>
   <xs:element name="annualsalary" type="xs:string"/>
   <xs:element name="familymembers" type="xs:string"/>
 </xs:sequence>
  </xs:complexType>

  </xs:schema>
```

In alternativa, scaricate lo schema XSD nel file system locale.

Schema XSD dell&#39;applicazione di prestito di esempio

[Ottieni file](assets/loanapplication.xsd)

Per ulteriori informazioni sull&#39;uso dello schema XSD come modello di modulo nei moduli adattivi, vedere [Creazione di moduli adattivi con schema](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html)XML.

Se si utilizza uno schema JSON come modello di modulo per eseguire i casi di utilizzo, creare un file JSON con il testo seguente:

```JSON
{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "definitions": {
        "loanapplication": {
            "type": "object",
            "properties": {
                "name": {
                    "type": "string"
                },
                "address": {
                    "type": "string"
                },
    "phonenumber": {
                    "type": "number"
                },
    "email": {
                    "type": "string"
                },
    "occupation": {
                    "type": "string"
                },
    "annualsalary": {
                    "type": "string"
                },
    "familymembers": {
                    "type": "number"
                }
            }
        }
 },
 "type": "object",
    "properties": {
        "employee": {
            "$ref": "#/definitions/loanapplication"
        }
    }
}
```

In alternativa, scaricate lo schema JSON nel file system locale.

Schema JSON dell&#39;applicazione di prestito di esempio

[Ottieni file](assets/demo_schema.json)

Per ulteriori informazioni sull&#39;uso dello schema JSON come modello di modulo nei moduli adattivi, vedere [Creazione di moduli adattivi con lo schema](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html)JSON.

## Generazione di moduli adattivi senza binding dei dati {#generate-adaptive-forms-with-no-data-binding}

Utilizzare il servizio di conversione [automatizzata dei moduli per convertire](convert-existing-forms-to-adaptive-forms.md) il modulo [di domanda di prestito di](#sample-adaptive-form) esempio in un modulo adattivo senza binding dei dati. Assicurarsi di selezionare la **[!UICONTROL Generate adaptive form(s) without data bindings]** casella di controllo per generare il modulo adattivo senza binding dei dati.

![Modulo adattivo senza binding dei dati](assets/generate_af_without_binding.png)

Dopo aver generato un modulo adattivo senza binding dei dati, selezionare un&#39;origine dati per il modulo adattivo:

* [Database, OData o qualsiasi servizio di terze parti](#sqldatasource)
* [Schema JSON](#jsondatasource)
* [schema XSD](#xsddatasource)

>[!NOTE]
> Se il modulo adattivo convertito utilizzando il servizio di conversione moduli automatizzata contiene più campi con lo stesso nome, assicurarsi che tali campi siano associati a entità di origine dati per evitare una possibile perdita di dati durante l&#39;invio.


### Utilizza database, OData o qualsiasi servizio di terze parti come origine dati {#sqldatasource}

Caso di utilizzo: È possibile generare un modulo adattivo senza alcun binding dei dati utilizzando il servizio di conversione moduli automatizzati e configurare il database MYSQL come origine dati. È possibile eseguire manualmente un binding dei campi modulo adattivo alle entità del modello dati del modulo e utilizzare l&#39; **[!UICONTROL Form Data Model Prefill Service]** opzione per precompilare i valori dei campi. È possibile utilizzare l&#39; **[!UICONTROL Submit using Form Data Model]** opzione per inviare il modulo adattivo.

Prima di eseguire il caso di utilizzo:

* [Configurare il database MySQL come origine dati](https://helpx.adobe.com/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [Creare il modello dati del modulo](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html)

In base al caso di utilizzo, creare il modello dati del modulo **di applicazione** di prestito e collegare l&#39;argomento del servizio di lettura a un **[!UICONTROL Literal]** valore. Il valore letterale del numero di telefono deve essere di uno dei record configurati nello schema **richiedente** del database MySQL. I servizi utilizzano il valore come argomento per recuperare i dettagli dall&#39;origine dati. Puoi anche selezionare Attributo profilo [utente o Attributo](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument) richiesta dall&#39;elenco a **[!UICONTROL Binding To]** discesa

![Configurare il modello dati del modulo](assets/configure_model_object.png)

>[!NOTE]
>
>Prima di eseguire l&#39;esempio, assicurarsi di aggiungere servizi **get** e **insert** al modello dati del modulo, configurare e verificare i servizi.

Esegui i seguenti passaggi:

1. Selezionare il modulo **di richiesta di prestito** di esempio convertito disponibile nella **[!UICONTROL output]** cartella e toccare **[!UICONTROL Properties]**.
1. Toccate la **[!UICONTROL Form Model]** scheda, selezionate **[!UICONTROL Form Data Model]** dall&#39;elenco a **[!UICONTROL Select From]** discesa, quindi toccate **[!UICONTROL Select Form Data Model]** per selezionare il modello di dati del modulo **di applicazione** di prestito. Toccate **[!UICONTROL Save & Close]** per salvare il modulo.
1. Selezionare il modulo **di domanda di prestito di** esempio e toccare **[!UICONTROL Edit]**.
1. Nella **[!UICONTROL Content]** scheda, toccate l&#39;icona di configurazione:

   ![configura contenitore modulo](assets/configure_form_container.png)

   1. Nella **[!UICONTROL Basic]** sezione, selezionare **[!UICONTROL Form Data Model Prefill service]** dall&#39;elenco a **[!UICONTROL Prefill Service]** discesa.

   1. Nella **[!UICONTROL Submission]** sezione, selezionare **[!UICONTROL Submit using Form Data Model]** dall&#39;elenco a **[!UICONTROL Submit Action]** discesa.

   1. Selezionare il modello dati utilizzando il **[!UICONTROL Data Model to submit]** campo.
   1. Toccate ![l’icona](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) Fine per salvare le proprietà.

1. Toccate la casella di testo Nome richiedente e selezionate l&#39;icona ![di](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/configure_icon.png) configurazione (Configura).

   1. Nel campo Riferimento binding, selezionare **Ricorrente** > **Nome** e toccare l&#39;icona ![](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) Fine per salvare le proprietà. Allo stesso modo, create un binding dei dati per **Indirizzo**, Numero **** telefono, **E-mail**, **Occupazione**, Salario **annuale (in dollari)****e Numero. dei campi dei membri** della famiglia dipendenti con le entità del modello dati del modulo.
   ![Riferimenti a binding](assets/bind_references.png)

1. Toccate **[!UICONTROL Preview]** per visualizzare i valori dei campi modulo adattivo precompilati.
1. Se necessario, modificare i valori dei campi e inviare il modulo adattivo. I valori dei campi vengono inviati al database MySQL. È possibile aggiornare la tabella **richiedente** nel database per visualizzare i valori aggiornati nella tabella.

**** Caso di utilizzo: È possibile generare un modulo adattivo senza alcun binding dei dati utilizzando il servizio di conversione moduli automatizzati e configurare il database MYSQL come origine dati. I campi modulo adattivo vengono associati utilizzando l&#39;editor di regole per precompilare i valori dei campi. Se necessario, modificare i valori dei campi e inviare i dati al repository crx.

Per richiamare il servizio del modello dati del modulo per eseguire il binding di campi e valori di precompilazione in un modulo adattivo, eseguire i passaggi seguenti per utilizzare l&#39;editor [](https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html) regole:

1. Selezionare il modulo **di domanda di prestito** di esempio nella **[!UICONTROL output]** cartella e toccare **[!UICONTROL Edit]**.
1. Nella **[!UICONTROL Content]** scheda, toccate l&#39;icona di configurazione:

   ![configura contenitore modulo](assets/configure_form_container.png)

   Nella **[!UICONTROL Basic]** sezione, selezionare **[!UICONTROL Form Data Model Prefill service]** dall&#39;elenco a **[!UICONTROL Prefill Service]** discesa.

1. Toccate la casella di **[!UICONTROL Applicant Name]** testo e toccate **[!UICONTROL Edit Rules]**.

   ![Modifica delle regole per creare il binding dei dati](assets/edit_rules_bind_reference.png)

1. Toccate **[!UICONTROL Create]** nella pagina Editor regole.
1. Sulla **[!UICONTROL Rule Editor]** pagina:

   1. Selezionate uno stato per la casella di testo Nome richiedente. Ad esempio, **[!UICONTROL is initialized]**, che determina l&#39;esecuzione della **[!UICONTROL Then]** condizione quando si esegue il rendering del modulo in **[!UICONTROL Preview]** modalità.

   1. Nella **[!UICONTROL Then]** sezione, selezionare **[!UICONTROL Invoke Service]** dall&#39;elenco a **[!UICONTROL Select Action]** discesa. Tutti i servizi nell&#39;istanza di Forms vengono visualizzati nell&#39;elenco a discesa.

   1. Selezionare un **[!UICONTROL Get]** servizio dalla sezione in cui sono elencati i modelli di dati del modulo. Nel campo Input viene visualizzato il **numero di telefono**, che è la chiave primaria definita per il modello dati **richiedente** . Il sistema recupera e precompila i valori nel modulo adattivo per i campi nella sezione Output in base a questo campo.

   1. Creare un binding per i campi modulo adattivo con le entità modello dati modulo utilizzando la sezione Output. Ad esempio, eseguire un binding del campo modulo adattivo con l&#39;entità **[!UICONTROL Applicant Name]** nome **** .

   1. Toccare **[!UICONTROL Done]**. Toccate **[!UICONTROL Done]** di nuovo nella pagina Editor regole.
   ![Editor di regole per eseguire il binding dei riferimenti](assets/rule_editor_bind_references.png)

1. Toccate **[!UICONTROL Preview]** per visualizzare i valori dei campi modulo adattivo precompilati.

   >[!NOTE]
   >
   >Assicurarsi che la proprietà **[!UICONTROL Return Array]** Property sia impostata su OFF per la proprietà **get** service nel modello dati del modulo associato al modulo adattivo.

1. Se necessario, modificare i valori dei campi e inviare il modulo adattivo. I dati inviati sono disponibili nel seguente percorso nell’archivio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Utilizzare lo schema JSON come origine dati {#jsondatasource}

**** Caso di utilizzo: È possibile generare un modulo adattivo senza alcun binding dei dati utilizzando il servizio di conversione moduli automatizzati e configurare lo schema JSON come origine dati. Per precompilare i valori dei campi, è possibile eseguire manualmente il binding dei campi modulo adattivo allo schema JSON e utilizzare l&#39;opzione **Anteprima con i dati** . Se necessario, modificare i valori dei campi e inviare i dati al repository crx.

Prima di eseguire il caso d’uso, accertatevi di disporre di:

* [uno schema JSON valido conforme alla struttura dello schema JSON](#prepare-data-for-form-model)
* [un modulo adattivo senza binding dei dati](#generate-adaptive-forms-with-no-data-binding)

Esegui i seguenti passaggi:

1. Selezionare il modulo **di domanda di prestito** di esempio convertito disponibile nella cartella di **output** e toccare **[!UICONTROL Properties]**.
1. Toccate la **[!UICONTROL Form Model]** scheda, selezionate **[!UICONTROL Schema]** dall&#39;elenco a **[!UICONTROL Select From]** discesa, quindi toccate **[!UICONTROL Select Schema]** per caricare lo schema JSON **** demo.schema salvato nel file system locale. Toccate **[!UICONTROL Save & Close]** per salvare il modulo.
1. Selezionare il modulo **di domanda di prestito di** esempio e toccare **[!UICONTROL Edit]**.
1. Toccate la casella di testo Nome richiedente e selezionate l&#39;icona ![di](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/configure_icon.png) configurazione (Configura).

   Nel campo Riferimento binding, selezionare **Ricorrente** > **Nome** e toccare l&#39;icona ![](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) Fine per salvare le proprietà. Allo stesso modo, create un binding dei dati per **Indirizzo**, Numero **** telefono, **E-mail**, **Occupazione**, Salario **annuale (in dollari)****e Numero. dei campi dei membri** della famiglia dipendenti con le entità dello schema JSON.

1. Selezionare di nuovo il modulo **di domanda di prestito** di esempio convertito disponibile nella **[!UICONTROL output]** cartella e selezionare **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Scarica file di dati di esempio</br>

   [Ottieni file](assets/json_data_file.txt)</br>

1. Se necessario, modificare i valori dei campi e inviare il modulo adattivo. I dati inviati sono disponibili nel seguente percorso nell’archivio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Utilizzare lo schema XSD come origine dati {#xsddatasource}

**** Caso di utilizzo: È possibile generare un modulo adattivo senza alcun binding dei dati utilizzando il servizio di conversione moduli automatizzati e configurare lo schema XSD come origine dati. Eseguire un binding manuale dei campi modulo adattivo allo schema XSD e utilizzare l&#39; **anteprima con i dati** per precompilare i valori dei campi. Se necessario, modificare i valori dei campi e inviare i dati al repository crx.

Prima di eseguire il caso d’uso, accertatevi di disporre di:

* [uno schema XSD valido conforme alla struttura dello schema XML](#prepare-data-for-form-model)
* [un modulo adattivo senza binding dei dati](#generate-adaptive-forms-with-no-data-binding)

Esegui i seguenti passaggi:

1. Selezionare il modulo **di richiesta di prestito** di esempio convertito disponibile nella **[!UICONTROL output]** cartella e toccare **[!UICONTROL Properties]**.
1. Toccate la **[!UICONTROL Form Model]** scheda, selezionate **[!UICONTROL Schema]** dall&#39;elenco a **[!UICONTROL Select From]** discesa, quindi toccate **[!UICONTROL Select Schema]** per caricare lo schema XSD dell&#39;applicazione di **caricamento** salvata nel file system locale. Selezionare l&#39;elemento principale per lo schema XSD e toccare **[!UICONTROL Save & Close]** per salvare il modulo.
1. Selezionare il modulo **di domanda di prestito di** esempio e toccare **[!UICONTROL Edit]**.
1. Toccate la casella di testo Nome richiedente e selezionate l&#39;icona ![di](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/configure_icon.png) configurazione (Configura).
Nel campo Riferimento binding, selezionare **Ricorrente** > **Nome**, quindi toccare ![Icona](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) Fine per salvare le proprietà. Allo stesso modo, create un binding dei dati per **Indirizzo**, Numero **** telefono, **E-mail**, **Occupazione**, Salario **annuale (in dollari)****e Numero. dei campi dei membri** della famiglia dipendenti con le entità dello schema XSD.

1. Selezionare di nuovo il modulo **di domanda di prestito** di esempio convertito disponibile nella cartella di **output** e selezionare **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Scarica file di dati di esempio</br>

   [Ottieni file](assets/loan-application-data-xml-data.zip)</br>


1. Se necessario, modificare i valori dei campi e inviare il modulo adattivo. I dati inviati sono disponibili nel seguente percorso nell’archivio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Generazione di moduli adattivi con binding JSON {#generate-adaptive-forms-with-json-binding}

Utilizzare il servizio di conversione [automatizzata dei moduli per convertire](convert-existing-forms-to-adaptive-forms.md) il modulo [di richiesta di prestito di](#sample-adaptive-form) esempio in un modulo adattivo con binding dei dati. Assicurarsi di non selezionare la **[!UICONTROL Generate adaptive form(s) without data bindings]** casella di controllo durante la generazione del modulo adattivo.

![Modulo adattivo con binding JSON](assets/generate_af_with_data_bindings.png)

### Utilizzare lo schema JSON come origine dati {#jsonwithdatabinding}

**** Caso di utilizzo: È possibile generare un modulo adattivo con il binding dei dati JSON utilizzando il servizio di conversione moduli automatizzati. Il servizio di precompilazione e la funzione di invio del modulo risultano perfettamente visibili. Non sono necessari passaggi di configurazione.

Prima di eseguire il caso di utilizzo, assicurarsi di disporre di [un modulo adattivo con binding](#generate-adaptive-forms-with-json-binding)dei dati.

Esegui i seguenti passaggi:

1. Selezionare di nuovo il modulo **di domanda di prestito** di esempio convertito disponibile nella **[!UICONTROL output]** cartella e selezionare **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Scarica file di dati di esempio</br>

   [Ottieni file](assets/loan_application_data_source_json_data_binding.txt)</br>

1. Se necessario, modificare i valori dei campi e inviare il modulo adattivo. I dati inviati sono disponibili nel seguente percorso nell’archivio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Conversione dei dati JSON del modulo adattivo inviati in formato XML {#convert-submitted-adaptive-form-data-to-xml}

Quando immettete valori nei campi modulo adattivi e li inviate, i dati sono disponibili in formato JSON nell’archivio crx. Potete convertire il formato dei dati JSON in XML utilizzando l&#39;API [org.apache.sling.commons.json.xml](https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString) oppure il seguente codice di esempio:

```
import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;
import org.apache.sling.commons.json.xml.XML;
 
public class ConversionUtils {
 
    public static String jsonToXML(String jsonString) throws JSONException {
        //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
        //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
        //Note: Need to extract boundData part before converting to XML
        return XML.toString(new JSONObject(jsonString));
    }
}
```
