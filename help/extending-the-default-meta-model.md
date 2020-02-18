---
title: Estende il metamodello predefinito
seo-title: Estende il metamodello predefinito
description: Estende il meta-modello predefinito per aggiungere pattern, convalide ed entità specifici dell'organizzazione e applica configurazioni ai campi modulo adattivi durante l'esecuzione del servizio Conversione automatizzata dei moduli.
seo-description: Estende il meta-modello predefinito per aggiungere pattern, convalide ed entità specifici dell'organizzazione e applica configurazioni ai campi modulo adattivi durante l'esecuzione del servizio Conversione automatizzata dei moduli.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: 5d4dba8fea7439b991a7a15872e6f4ed48156ac9

---


# Estende il metamodello predefinito {#extend-the-default-meta-model}

Il servizio di conversione automatizzata dei moduli identifica ed estrae gli oggetti dei moduli dai moduli di origine. Mapper semantico consente al servizio di decidere in che modo gli oggetti estratti vengono rappresentati in un modulo adattivo. Ad esempio, un modulo di origine può avere diversi tipi di rappresentazioni di una data. Il mappatore semantico consente di mappare tutte le rappresentazioni degli oggetti modulo data del modulo di origine con il componente data dei moduli adattivi. Mappatore semantico consente inoltre al servizio di preconfigurare e applicare convalide, regole, pattern di dati, testo della Guida e proprietà di accessibilità ai componenti dei moduli adattivi durante la conversione.

![](assets/meta-model.gif)

Meta-model è uno schema JSON. Prima di iniziare con il meta-modello, assicurati di avere una buona esperienza con JSON. Devi avere esperienza nella creazione, modifica e lettura dei dati salvati in formato JSON.

## meta-modello predefinito {#default-meta-model}

Il servizio di conversione moduli automatizzati dispone di un meta-modello predefinito. Si tratta di uno schema JSON e risiede in Adobe Cloud con altri componenti del servizio di conversione dei moduli automatizzata. Puoi trovare una copia del meta-modello sul server AEM locale all’indirizzo:

http://&lt;server>:&lt;porta>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json.

Lo schema del meta-modello è derivato dalle entità dello schema all&#39;indirizzo https://schema.org/docs/schemas.html. Dispone di Persona, IndirizzoPostale, AffariLocali e più entità, come definito in https://schema.org. Ogni entità del meta-modello aderisce al tipo di oggetto schema JSON. Il codice seguente rappresenta una struttura di metadati di esempio:

```
   "Entity": {
      "id": "Entity",
      "properties": {
        "name": {
          "type": "string"
        },

        "description": {
          "type": "string",
          "description": "Description of the item"
        }
      }
    }
```

## Download del metamodello predefinito {#download-the-default-meta-model}

Per scaricare il meta-modello predefinito nel file system locale, procedere come segue:

1. Accedi alla tua istanza di AEM Forms.
1. Passate alla cartella **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** **>** **[!UICONTROL Meta Model]** .
1. Selezionate il **[!UICONTROL global.schema.json]** file e toccate **[!UICONTROL Download]**. Viene visualizzata una finestra di dialogo per il download. Selezionate l’ **[!UICONTROL Download asset(s) as binary files]** opzione. Toccare **[!UICONTROL Download]**. Viene scaricato un archivio.

   <!--
   Comment Type: draft

   <li><p>Extract the archive and open the global.schema.json file for editing. </p> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

## Comprendere il meta-modello {#understanding-the-meta-model}

Un meta-modello fa riferimento a un file di schema JSON che contiene entità. Tutte le entità nel file di schema JSON includono un nome e un ID. Ciascuna entità può includere più proprietà. Le entità e le relative proprietà possono variare a seconda del dominio. È possibile aggiungere un file di schema con parole chiave e configurazioni di campi per mappare le proprietà dello schema ai componenti dei moduli adattivi.

```
"Event": {
      "id": "Eventid",
      "allOf": [
        {
          "$ref": "#Entity"
        },
        {
          "properties": {
            "startDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the start date and time of the event in ISO 8601 date format."
            },
            "endDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the end date and time of the event in ISO 8601 date format."
            },
            "location": {
              "$ref": "#PostalAddress",
              "description": "Specify the location of the event."
            }
          }
        }
      ]
    }
```

In questo esempio, **Event** rappresenta il nome di un&#39;entità con un valore **id** come **Eventid**. L&#39;entità Evento include più proprietà:

* startDate
* endDate
* location

Il costrutto **allOf** nel meta-modello consente l&#39;ereditarietà tra le entità.

Ogni proprietà può includere:

* [Proprietà dello schema JSON](#jsonschemaproperties)
* [Ricerca basata su parole chiave per applicare proprietà ai campi modulo adattivo generati](#keywordsearch)
* [Ulteriori proprietà](#additionalproperties)

![Proprietà dei metadati](assets/meta_model_elements.gif)

In base alle parole chiave a cui si fa riferimento utilizzando **aem:affKeyword**, il servizio di conversione esegue un&#39;operazione di ricerca nei campi del modulo di origine. Il servizio di conversione applica le proprietà dello schema JSON e le proprietà aggiuntive ai campi che soddisfano i criteri di ricerca.

In questo esempio, il servizio di conversione cerca il telefono, il telefono, il cellulare, il telefono di lavoro, il telefono di casa, il numero di telefono, il numero di telefono e le parole chiave del numero di telefono nel modulo di origine. In base ai campi che includono queste parole chiave, il servizio di conversione applica i campi tipo, pattern e aem:afProperties ai campi modulo adattivi dopo la conversione.

### Proprietà dello schema JSON per i campi modulo adattivo generati {#jsonschemaproperties}

Il meta-modello supporta le seguenti proprietà comuni dello schema JSON per i campi modulo adattivi generati utilizzando il servizio di conversione moduli automatizzati:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Nome proprietà</strong></th> 
   <th><strong>Descrizione</strong></th> 
  </tr> 
  <tr> 
   <td><p>titolo</p></td> 
   <td> 
    <p>Il testo menzionato nella proprietà title in un metamodello funge da parola chiave di ricerca per eseguire azioni sui campi modulo adattivo generati. Ad esempio, modificare l'etichetta di un campo modulo adattivo. Per ulteriori informazioni, vedere <strong>Modificare l'etichetta di un campo</strong> modulo negli esempi di metadati <a href="#custommetamodelexamples">personalizzati.</a></p> </td> 
  </tr>
  <td><p>descrizione</p></td> 
   <td> 
    <p>La proprietà description imposta il testo della Guida relativo al campo modulo adattivo generato. Per ulteriori informazioni, vedere <strong>Aggiungere il testo della Guida a un campo</strong> modulo in esempi di metadati <a href="#custommetamodelexamples">personalizzati.</a></p> </td> 
  </tr>
  <td><p>tipo</p></td> 
   <td> 
    <p>La proprietà type definisce il tipo di dati per il campo modulo adattivo generato. I valori possibili per la proprietà title includono:</p>
    <ul> 
     <li>stringa: Genera un campo modulo adattivo di tipo dati testo.</li> 
     <li>numero: Genera un campo modulo adattivo di tipo numerico.</li>
     <li>integer: Genera un campo modulo adattivo di tipo numerico con sottotipo impostato su numero intero.</li>
     <li>booleano: Genera un componente per modulo adattivo switch.</li>
     </ul><p>Per ulteriori informazioni sull'utilizzo della proprietà type in un meta-modello, vedere <strong>Modificare il tipo di un campo</strong> modulo negli esempi di meta-modelli <a href="#custommetamodelexamples">personalizzati.</a></p></td> 
  </tr>
  <td><p>pattern</p></td> 
   <td> 
    <p>La proprietà pattern limita il valore del campo modulo adattivo generato in base a un'espressione regolare. Ad esempio, il seguente codice nel meta-modello limita il valore del campo modulo adattivo generato a dieci cifre:<br>"pattern": "/\\d{10}/"<br>Allo stesso modo, il seguente codice nel meta-modello limita il valore di un campo a un formato data specifico.<br> "pattern": "date{DD MMMM, YYYY}",</p> </td> 
  </tr>
  <td><p>format</p></td> 
   <td> 
    <p>La proprietà format limita il valore del campo modulo adattivo generato in base a un pattern denominato anziché a un'espressione regolare. I valori possibili per la proprietà format includono:<ul><li>email: Genera un componente per modulo adattivo per e-mail.</li><li>hostname: Genera un componente modulo adattivo per la casella di testo.</li></ul>Per ulteriori informazioni sull'utilizzo della proprietà format in un metamodello, vedere <strong>Modificare il formato di un campo</strong> modulo negli esempi di meta-modelli <a href="#custommetamodelexamples">personalizzati.</a></p> </td> 
  </tr>
  <td><p>enum e enumNames</p></td> 
   <td> 
    <p>Le proprietà enum e enumNames limitano i valori dei campi a discesa, casella di controllo o pulsante di scelta a un set fisso. I valori elencati in enumNames vengono visualizzati nell’interfaccia utente. I valori elencati utilizzando la proprietà enum vengono utilizzati per il calcolo.<br>Per ulteriori informazioni, vedere <strong>Conversione di un campo modulo in caselle di controllo a scelta multipla nel modulo</strong>adattivo, <strong>Conversione di un campo di testo in un elenco a discesa nel modulo</strong>adattivo e <strong>Aggiunta di opzioni aggiuntive all'elenco</strong> a discesa negli esempi di metadati <a href="#custommetamodelexamples">personalizzati.</a></p> </td> 
  </tr>
 </tbody> 
</table>

### Ricerca basata su parole chiave per applicare proprietà ai campi modulo adattivo generati {#keywordsearch}

Durante la conversione, il servizio di conversione automatica dei moduli esegue una ricerca per parole chiave nel modulo di origine. Dopo aver filtrato i campi che soddisfano i criteri di ricerca, il servizio di conversione applica le proprietà definite per tali campi nel meta-modello ai campi modulo adattivo generati.

Alle parole chiave viene fatto riferimento tramite la proprietà **aem:affKeyword** .

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

In questo esempio, il servizio di conversione utilizza il testo all’interno di **aem:affKeyword** come parola chiave di ricerca. Dopo aver recuperato il testo relativo al numero **del conto** bancario nel modulo, il servizio di conversione converte il campo in un tipo di **numero** utilizzando la proprietà **type** .

### Proprietà aggiuntive per i campi modulo adattivo generati {#additionalproperties}

È possibile utilizzare la proprietà **aem:afProperties** nel meta-modello per definire le seguenti proprietà aggiuntive per i campi modulo adattivo generati utilizzando il servizio di conversione moduli automatizzati:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Nome proprietà</strong></th> 
   <th><strong>Descrizione</strong></th> 
  </tr> 
  <tr> 
   <td><p>multiline</p></td> 
   <td> 
    <p>La proprietà multiline converte un campo modulo di origine in un campo multiriga del modulo adattivo dopo la conversione. Per ulteriori informazioni, vedere <strong>Convertire un campo stringa in un campo</strong> multiriga negli esempi di metadati <a href="#custommetamodelexamples">personalizzati.</a></p> </td> 
  </tr>
  <td><p>mandatory</p></td> 
   <td> 
    <p>La proprietà mandatory imposta come obbligatorio l'input per un campo modulo adattivo dopo la conversione.<br>Per ulteriori informazioni, vedere <strong>Aggiunta di convalide ai campi</strong> dei moduli adattivi negli esempi di modelli meta-modelli <a href="#custommetamodelexamples">personalizzati.</a></p>
    </td> 
  </tr>
  <td><p>jcr:title</p></td> 
   <td> 
    <p>La proprietà jcr:title, con la proprietà dello schema JSON title, consente di modificare l'etichetta di un campo modulo adattivo dopo la conversione.<br>Per ulteriori informazioni, vedere <strong>Modificare l'etichetta di un campo</strong> modulo negli esempi di metadati <a href="#custommetamodelexamples">personalizzati.</a><br>Per informazioni su ulteriori proprietà da applicare ai campi modulo adattivi mediante lo schema <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html" target="_blank">JSON, vedere</a> Creazione di moduli adattivi con schemaJSON.</p>
    <p></p></td> 
  </tr>
  <td><p>sling:resourceType e guideNodeClass</p></td> 
   <td> 
    <p>le proprietà sling:resourceType e guideNodeClass consentono di mappare un campo modulo a un componente modulo adattivo corrispondente.<br>Per ulteriori informazioni, vedere <strong>Conversione di un campo modulo in caselle di controllo a scelta multipla nel modulo</strong> adattivo e <strong>Conversione di un campo di testo in un elenco a discesa nel modulo</strong> adattivo negli esempi di metadati <a href="#custommetamodelexamples">personalizzati.</a></p> </td> 
  </tr>
  <td><p>validatePictureClause</p></td> 
   <td> 
    <p>La proprietà validatePictureClause imposta una convalida sul formato consentito nel campo modulo adattivo dopo la conversione.<br>Per ulteriori informazioni, vedere <strong>Aggiunta di convalide ai campi</strong> dei moduli adattivi negli esempi di modelli meta-modelli <a href="#custommetamodelexamples">personalizzati.</p> </td> 
  </tr>
 </tbody> 
</table>

## Modificare i campi modulo adattivi utilizzando il metamodello personalizzato {#modify-adaptive-form-fields-using-custom-meta-model}

L&#39;organizzazione può disporre di pattern e convalide oltre a quelli elencati nel meta-modello predefinito. È possibile estendere il meta-modello predefinito per aggiungere pattern, convalide ed entità specifici dell&#39;organizzazione. Il servizio di conversione automatizzata dei moduli applica il meta-modello personalizzato ai campi del modulo durante la conversione. È possibile continuare ad aggiornare il meta-modello mano a mano che vengono scoperti nuovi pattern, convalide ed entità specifici della propria organizzazione.

Il servizio di conversione automatizzata dei moduli utilizza un meta-modello predefinito salvato nella posizione seguente per mappare i campi del modulo sorgente ai campi del modulo adattivo durante la conversione:

http://&lt;server>:&lt;porta>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json

Tuttavia, potete salvare un meta-modello personalizzato in una cartella e modificare le proprietà del servizio di conversione per utilizzare il meta-modello personalizzato durante la conversione.

### Utilizzare un metamodello personalizzato durante la conversione {#use-custom-meta-model-during-conversion}

Per utilizzare un meta-modello personalizzato durante la conversione, eseguire i seguenti passaggi:

1. Create una cartella in **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** e caricate il file di schema JSON del meta-modello personalizzato nella cartella.
1. Apri le proprietà del servizio di conversione utilizzando:

   **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]**> **&lt;** Proprietà della configurazione **selezionata>**

1. Nella **[!UICONTROL Basic]** scheda, specificate la posizione del meta-modello personalizzato nel **[!UICONTROL Custom Meta-model]** campo e toccate **[!UICONTROL Save & Close]**.
1. [Eseguire la conversione](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) per applicare il meta-modello personalizzato al processo di conversione.

### Esempi di meta-modelli personalizzati {#custommetamodelexamples}

Alcuni esempi comuni dell&#39;utilizzo di un meta-modello personalizzato per modificare le proprietà dei campi modulo adattivi sono:

* Modificare l&#39;etichetta di un campo modulo
* Modifica del tipo di campo modulo
* Aggiunta di testo della Guida a un campo modulo
* Conversione di un campo modulo in pulsanti di scelta a scelta multipla nel modulo adattivo
* Modificare il formato di un campo modulo
* Aggiunta di convalide ai campi modulo adattivi
* Conversione di un campo modulo in opzioni di elenco a discesa nel modulo adattivo
* Aggiungere ulteriori opzioni all&#39;elenco a discesa
* Conversione di un campo stringa in un campo multiriga

#### Modificare l&#39;etichetta di un campo modulo {#modify-the-label-of-a-form-field}

**** Esempio: Modificare l&#39;etichetta del numero di conto bancario nel modulo su Numero di conto personalizzato nel modulo adattivo dopo la conversione.

In questo meta-modello personalizzato, il servizio di conversione utilizza la proprietà **title** come parola chiave di ricerca. Dopo aver recuperato il testo del numero **di conto** bancario nel modulo, il servizio di conversione sostituisce il testo con la stringa numero **di conto** cliente menzionata con la proprietà **jcr:title** nella sezione **aem:afProperties** .

```
{
  "numberfields": {
      "type": "number",
   "title": "Bank account number",
   "aem:afProperties" : {
    "jcr:title" : "Customer account number"
   }
   }
}
```

#### Modifica del tipo di campo modulo {#modify-the-type-of-a-form-field}

**Esempio**: Modificare il campo Numero **conto** bancario del tipo di testo nel modulo prima della conversione in un campo tipo di numero nel modulo adattivo dopo la conversione.

In questo meta-modello personalizzato, il servizio di conversione utilizza il testo all&#39;interno di **aem:affKeyword** come parola chiave di ricerca. Dopo aver recuperato il testo del numero **del conto** bancario nel modulo, il servizio di conversione converte il campo in un tipo di numero utilizzando la proprietà **type** .

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

#### Aggiunta di testo della Guida a un campo modulo {#add-help-text-to-a-form-field}

**Esempio**: Aggiungere il testo della Guida al campo Numero **conto** bancario del modulo adattivo.

In questo meta-modello personalizzato, il servizio di conversione utilizza il testo all&#39;interno di **aem:affKeyword** come parola chiave di ricerca. Dopo aver recuperato il testo relativo al numero **di conto** bancario nel modulo, il servizio di conversione aggiunge il testo della Guida al campo modulo adattivo utilizzando la proprietà **description** .

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "description": "Specify your bank account number."
 }
}
```

#### Conversione di un campo modulo in caselle di controllo a scelta multipla nel modulo adattivo {#convert-a-form-field-to-multiple-choice-check-boxes-in-the-adaptive-form}

**Esempio**: Convertire il campo **Paese** di tipo stringa nel modulo prima della conversione in caselle di controllo nel modulo adattivo dopo la conversione.

In questo meta-modello personalizzato, il servizio di conversione utilizza il testo all&#39;interno di **aem:affKeyword** come parola chiave di ricerca. Dopo aver recuperato il testo **Paese** nel modulo, il servizio di conversione converte il campo nelle seguenti caselle di controllo utilizzando la proprietà **enum** :

* India
* Inghilterra
* Australia
* Nuova Zelanda

**le proprietà sling:resourceType** e **guideNodeClass** mappano un campo modulo al componente modulo adattivo della casella di controllo.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### Modificare il formato di un campo modulo {#modify-the-format-of-a-form-field}

**Esempio**: Modificate il formato del campo Indirizzo **** e-mail in un formato e-mail.

In questo meta-modello personalizzato, il servizio di conversione utilizza il testo all&#39;interno di **aem:affKeyword** come parola chiave di ricerca. Dopo aver recuperato il testo Indirizzo **e-** mail nel modulo, il servizio di conversione converte il campo in un formato e-mail utilizzando la proprietà **format** .

```
{
   "additionalDetails" : {
      "aem:affKeyword": ["E-mail Address"],
       "type" : "string",
       "format" : "email"
  } 
}
```

#### Aggiunta di convalide ai campi modulo adattivi {#add-validations-to-adaptive-form-fields}

**** Esempio 1: Aggiungere una convalida al campo Codice **** postale del modulo adattivo.

In questo meta-modello personalizzato, il servizio di conversione utilizza il testo all&#39;interno di **aem:affKeyword** come parola chiave di ricerca. Dopo aver recuperato il testo del codice **** postale nel modulo, il servizio di conversione aggiunge una convalida al campo utilizzando la proprietà **validatePictureClause** definita nella sezione **aem:afProperties** . In base alla convalida, l&#39;input specificato per il campo Codice **** postale nel modulo adattivo dopo la conversione deve includere sei caratteri.

```
{
   "postalCode" : {
      "aem:affKeyword": ["Postal Code"],
      "type" : "string",
      "aem:afProperties" : {
        "validatePictureClause" : "\\d{6}"
      } 
   }
}
```

**** Esempio 2: Aggiungere una convalida al campo Numero **conto** bancario del modulo adattivo.

In questo meta-modello personalizzato, il servizio di conversione utilizza il testo all&#39;interno di **aem:affKeyword** come parola chiave di ricerca. Dopo aver recuperato il testo relativo al numero **di conto** bancario nel modulo, il servizio di conversione aggiunge una convalida al campo utilizzando la proprietà **mandatory** definita nella sezione **aem:afProperties** . In base alla convalida, è necessario specificare un valore per il campo Numero **conto** bancario prima di inviare il modulo dopo la conversione.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "aem:afProperties" : {
        "mandatory": "true"
      }   
   }
}
```

#### Conversione di un campo di testo in un elenco a discesa nel modulo adattivo {#convert-a-text-field-to-drop-down-list-in-the-adaptive-form}

**Esempio**: Convertire il campo **Paese** di tipo stringa nel modulo prima della conversione in opzioni a discesa nel modulo adattivo dopo la conversione.

In questo meta-modello personalizzato, il servizio di conversione utilizza il testo all&#39;interno di **aem:affKeyword** come parola chiave di ricerca. Dopo aver recuperato il testo **Paese** nel modulo, il servizio di conversione converte il campo nelle seguenti opzioni dell&#39;elenco a discesa utilizzando la proprietà **enum** :

* India
* Inghilterra
* Australia
* Nuova Zelanda

**le proprietà sling:resourceType** e **guideNodeClass** mappano un campo modulo al componente modulo adattivo a discesa.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidedropdownlist",
      "guideNodeClass": "guideDropDownlist"
    }
  }
}
```

#### Aggiungere ulteriori opzioni all&#39;elenco a discesa {#add-additional-options-to-the-drop-down-list}

**** Esempio: Aggiungi **Sri Lanka** come opzione aggiuntiva a un elenco a discesa esistente utilizzando un meta-modello personalizzato.

Per aggiungere un&#39;opzione aggiuntiva, aggiornate la proprietà **enum** con la nuova opzione. In questo esempio, aggiornate la proprietà **enum** con **Sri Lanka** come opzione aggiuntiva. I valori elencati nella proprietà **enum** vengono visualizzati nell&#39;elenco a discesa.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand",
   "Sri Lanka"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### Conversione di un campo stringa in un campo multiriga {#convert-a-string-field-to-a-multi-line-field}

**** Esempio: Dopo la conversione, convertire il campo **Indirizzo** di tipo stringa in un campo multiriga del modulo.

In questo meta-modello personalizzato, il servizio di conversione utilizza il testo all&#39;interno di **aem:affKeyword** come parola chiave di ricerca. Dopo aver recuperato il testo **Indirizzo** nel modulo, il servizio converte il campo di testo in un campo a più righe utilizzando la proprietà **multiline** definita nella sezione **aem:afProperties** .

```
{
 "multiline" : {
   "aem:affKeyword": [
      "Address"
    ],
    "type" : "string",
    "aem:afProperties": {
      "multiline": "true"
    }
  }
}
```
