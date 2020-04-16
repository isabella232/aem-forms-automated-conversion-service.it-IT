---
title: 'Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli '
seo-title: 'Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli (AFCS) '
description: 'Problemi AFCS comuni e relative soluzioni '
seo-description: Problemi AFCS comuni e relative soluzioni
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 74ff988f097ae3ea90c802c8884a78ba330fcf58

---


# Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## Errori comuni {#commonerrors}

| Errore | Esempio |
|--- |--- |
| **Messaggio** di errore <br> L&#39;intestazione del token di accesso non è disponibile. <br><br>**Motivo **<br>: un amministratore ha creato più configurazioni IMS o la configurazione IMS non è in grado di raggiungere il servizio AFCS su Adobe Cloud.<br><br>**Risoluzione**<br> In presenza di più configurazioni, eliminate tutte le configurazioni e [create una nuova configurazione](configure-service.md#obtainpubliccertificates). <br> Se è presente una singola configurazione, utilizzate **[!UICONTROL Health Check]** per [controllare la connettività](configure-service.md#createintegrationoption). | ![L&#39;intestazione del token di accesso non è disponibile](assets/invalid-ims-configuration.png) |
| **Messaggio** di errore <br> Impossibile connettersi al servizio.  <br><br>**Motivo **<br>: l&#39;URL del servizio non corretto o l&#39;URL del servizio non è indicato nei servizi cloud di Automated Forms Conversion Service.<br><br>**URL** <br> del [servizio di correzione della risoluzione](configure-service.md#configure-the-cloud-service) nei servizi cloud Automated Forms Conversion Service. | ![Impossibile connettersi al servizio.](assets/wrong-endpoint-configured.png) |
| **Messaggio** di errore <br> Impossibile convertire il modulo.  <br><br>**Motivo **<br>: problemi di connettività di rete al termine del servizio, manutenzione programmata o interruzione in Adobe Cloud.<br><br>**Risoluzione**<br> dei problemi di connettività di rete al termine dell&#39;evento e verifica lo stato del servizio su https://status.adobe.com/ per un&#39;interruzione pianificata o non pianificata. | ![Impossibile connettersi al servizio.](assets/service-failure.png) |
| **Messaggio** di errore <br> Il numero di pagine è superiore a 15.  <br><br>**Motivo **<br>La lunghezza del modulo di origine è superiore a 15 pagine.<br><br>**Risoluzione**<br> Utilizzare Adobe Acrobat per suddividere i moduli con più di 15 pagine. Portare il numero di pagine in un modulo a meno di 15. | ![Impossibile connettersi al servizio.](assets/number-of-pages.png) |
| **Messaggio** di errore <br> Il numero di file è superiore a 15.  <br><br>**Motivo **<br>La cartella contiene più di 15 moduli.<br><br>**Risoluzione**<br> Portare il numero di moduli in una cartella a meno o uguale a 15. Portate il numero totale di pagine in una cartella inferiore a 50. Portate le dimensioni della cartella a meno di 10 MB. Non tenere i moduli in una sottocartella. Organizzare i moduli di origine in un batch di 8-15 moduli. | ![Impossibile connettersi al servizio.](assets/number-of-pages.png) |
| **Messaggio** di errore <br> Il formato del file di origine non è supportato.  <br><br>**Motivo **<br>: nella cartella contenente i moduli di origine sono presenti alcuni file non supportati.<br><br>**Risoluzione** <br> Il servizio supporta solo i file .xdp e .pdf. Rimuovete i file con qualsiasi altra estensione dalla cartella ed eseguite la conversione. | ![Impossibile connettersi al servizio.](assets/unsupported-file-formats.png) |
| **Messaggi** <br> di errore I moduli analizzati non sono supportati.  <br><br>**Motivo **<br>Il modulo PDF contiene solo immagini digitalizzate del modulo e non contiene alcuna struttura di contenuto.<br><br>**Risoluzione** <br> Il servizio non supporta la conversione di moduli digitalizzati o di un&#39;immagine di un modulo in un modulo adattativo out-of-the-box. Tuttavia, è possibile utilizzare Adobe Acrobat per convertire l&#39;immagine di un modulo in un modulo PDF. Quindi, utilizzare il servizio per convertire il modulo PDF in un modulo adattivo. Utilizzare sempre un&#39;immagine di alta qualità del modulo per la conversione in Acrobat. Migliora la qualità della conversione. | ![Impossibile connettersi al servizio.](assets/scanned-forms-error.png) |
| **Il modulo PDF crittografato con messaggio** <br> di errore non è supportato.  <br><br>**Motivo **: la cartella contiene moduli PDF crittografati<br>.<br><br>**Risoluzione** <br> Il servizio non supporta la conversione di un modulo PDF crittografato in un modulo adattivo. Rimuovere la cifratura, caricare il modulo non crittografato ed eseguire la conversione. | ![Impossibile connettersi al servizio.](assets/secured-pdf-form.png) |
| **Messaggio** <br> di errore Impossibile analizzare lo schema JSON del metamodello.  <br><br>**Motivo **<br>: lo schema JSON fornito al servizio non è formattato correttamente, contiene caratteri non validi o utilizza una sintassi non valida per mappare i componenti.<br><br>**Risoluzione**<br> Controllare la formattazione del file JSON. È possibile utilizzare qualsiasi validatore JSON online per verificare la formattazione e la struttura dello schema. Consultate [Estendere l&#39;articolo meta-modello](extending-the-default-meta-model.md) predefinito per informazioni sulla sintassi del meta-modello. | ![Impossibile connettersi al servizio.](assets/invalid-meta-model-schema.png) |
