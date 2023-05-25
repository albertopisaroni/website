---
title: Limiti
slug: rate-limits
untranslated: 0
---

Let's Encrypt prevede alcuni limiti per garantire un utilizzo equo da parte del maggior numero possibile di persone. Riteniamo che questi limiti siano abbastanza alti da funzionare per la maggior parte delle persone per impostazione predefinita. Inoltre, sono stati progettati in modo che il rinnovo di un certificato non raggiunga quasi mai il limite e che le grandi organizzazioni possano aumentare gradualmente il numero di certificati che possono emettere senza richiedere l'intervento di Let's Encrypt.

Se state sviluppando o testando un client Let's Encrypt, utilizzate il nostro ambiente di staging invece dell'API di produzione. Se state lavorando all'integrazione di Let's Encrypt come provider o con un sito web di grandi dimensioni, consultate la nostra Guida all'integrazione.

Il limite principale è costituito dai certificati per dominio registrato (50 a settimana). Un dominio registrato è, in generale, la parte del dominio acquistata dal registrar del nome di dominio. Ad esempio, nel nome www.example.com, il dominio registrato è example.com. In new.blog.example.co.uk, il dominio registrato è example.co.uk. Per calcolare il dominio registrato si utilizza l'elenco dei suffissi pubblici. Il superamento del limite di certificati per dominio registrato viene segnalato con il messaggio di errore Troppi certificati già emessi, eventualmente con ulteriori dettagli.

È possibile creare un massimo di 300 nuovi ordini per account ogni 3 ore. Ogni volta che si richiede un certificato alla CA Boulder viene creato un nuovo ordine, il che significa che per ogni richiesta di certificato viene prodotto un nuovo ordine. Il superamento del limite di nuovi ordini viene segnalato con il messaggio di errore Troppi nuovi ordini di recente.

È possibile combinare più nomi di host in un unico certificato, fino a un limite di 100 nomi per certificato. Per ragioni di prestazioni e di affidabilità, è meglio utilizzare un numero inferiore di nomi per certificato ogni volta che è possibile. Un certificato con più nomi è spesso chiamato certificato SAN, o talvolta certificato UCC.

I rinnovi sono trattati in modo particolare: non vengono conteggiati nel limite dei certificati per dominio registrato, ma sono soggetti al limite di 5 certificati duplicati a settimana. Il superamento del limite di certificati duplicati viene segnalato con il messaggio di errore Troppi certificati già emessi per l'esatto insieme di domini.

Un certificato è considerato un rinnovo (o un duplicato) di un certificato precedente se contiene esattamente lo stesso insieme di nomi di host, ignorando la capitalizzazione e l'ordine dei nomi di host. Ad esempio, se si richiede un certificato per i nomi [www.example.com, example.com], si possono richiedere altri quattro certificati per [www.example.com, example.com] durante la settimana. Se si modifica l'insieme dei nomi host aggiungendo [blog.example.com], si potranno richiedere altri certificati.

La gestione dei rinnovi ignora la chiave pubblica e le estensioni richieste. L'emissione di un certificato può essere considerata un rinnovo anche se si utilizza una nuova chiave.

La revoca dei certificati non azzera i limiti, perché le risorse utilizzate per l'emissione dei certificati sono già state consumate.

Esiste un limite di 5 fallimenti di convalida per account e per host.
