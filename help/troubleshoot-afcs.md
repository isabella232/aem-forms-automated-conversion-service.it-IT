---
title: 'Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli '
seo-title: 'Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli (AFCS) '
description: 'Problemi AFCS comuni e relative soluzioni '
seo-description: Problemi AFCS comuni e relative soluzioni
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 4b9f3f4fe3b3901cb99c9374ff40e8f49855237f

---


# Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli


L&#39;articolo fornisce informazioni sui problemi di installazione, configurazione e amministrazione che possono verificarsi in un ambiente di produzione di Automated Forms Conversion Service. Il documento fornisce inoltre istruzioni e procedure di base per la risoluzione dei problemi e spiegazioni sui messaggi di errore più comuni.

## Errori comuni {#commonerrors}

| Errore | Esempio |
|--- |--- |
| **Messaggio** di errore <br> L&#39;intestazione del token di accesso non è disponibile. <br><br>**Motivo **<br>: un amministratore ha creato più configurazioni IMS o la configurazione IMS non è in grado di raggiungere il servizio AFCS su Adobe Cloud.<br><br>**Risoluzione**<br> In presenza di più configurazioni, eliminate tutte le configurazioni e [create una nuova configurazione](configure-service.md#obtainpubliccertificates). <br> Se è presente una singola configurazione, utilizzate **[!UICONTROL Health Check]** per [controllare la connettività](configure-service.md#createintegrationoption). | ![L&#39;intestazione del token di accesso non è disponibile](assets/invalid-ims-configuration.png) |
| **Messaggio** di errore <br> Impossibile connettersi al servizio.  <br><br>**Motivo **<br>: l&#39;URL del servizio non corretto o l&#39;URL del servizio non è indicato nei servizi cloud di Automated Forms Conversion Service.<br><br>**URL** <br> del [servizio di correzione della risoluzione](configure-service.md#configure-the-cloud-service) nei servizi cloud Automated Forms Conversion Service. | ![Impossibile connettersi al servizio.](assets/wrong-endpoint-configured.png) |
| **Messaggio** di errore <br> Impossibile convertire il modulo.  <br><br>**Motivo **<br>: problemi di connettività di rete al termine del servizio o problemi di manutenzione pianificati o di interruzione del servizio in Adobe Cloud.<br><br>**Risoluzione**<br> dei problemi di connettività di rete al termine dell&#39;evento e verifica lo stato del servizio su https://status.adobe.com/ per verificare l&#39;eventuale interruzione pianificata o non pianificata. | ![Impossibile connettersi al servizio.](assets/service-failure.png) |
| **Messaggio** di errore <br> Il numero di pagine è superiore a 15.  <br><br>**Motivo **<br>La cartella contenente i moduli XDP e PDF di origine contiene più di 15 file.<br><br>**Risoluzione**<br> Portare il numero di moduli in una cartella a meno o uguale a 15. Portate il numero totale di pagine in una cartella inferiore a 50. Portate le dimensioni della cartella a meno di 10 MB. Non tenere i moduli in una sottocartella. Organizzate i documenti sorgente in un batch di 8-15 documenti. | ![Impossibile connettersi al servizio.](assets/number-of-pages.png) |
| **Messaggio** di errore <br> Il formato del file di origine non è supportato.  <br><br>**Motivo **<br>: nella cartella contenente i moduli di origine sono presenti alcuni file non supportati.<br><br>**Risoluzione** <br> Il servizio supporta solo i file .xdp e .pdf. Rimuovete i file con qualsiasi altra estensione dalla cartella ed eseguite la conversione. | ![Impossibile connettersi al servizio.](assets/unsupported-file-formats.png) |
| **Messaggi** <br> di errore I moduli analizzati non sono supportati.  <br><br>**Motivo **<br>Il modulo PDF contiene solo l&#39;immagine del modulo digitalizzata e non contiene alcuna struttura di contenuto.<br><br>**Risoluzione** <br> Il servizio non supporta la conversione di moduli digitalizzati o di un&#39;immagine di un modulo in un modulo adattativo out-of-the-box. Tuttavia, è possibile utilizzare Adobe Acrobat per convertire l&#39;immagine di un modulo in un modulo PDF. Quindi, utilizzare il servizio per convertire il modulo PDF in un modulo adattivo. Utilizzare sempre un&#39;immagine di alta qualità del modulo per la conversione in Acrobat. Migliora la qualità della conversione. | ![Impossibile connettersi al servizio.](assets/scanned-forms-error.png) |