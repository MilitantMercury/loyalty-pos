# Catalogo, menu e allergeni

## Una sola fonte dati

Il catalogo è usato sia dalla cassa sia dal menu QR. Un prodotto, un prezzo o un allergene si modifica una sola volta e il cambiamento deve essere visibile in entrambi i canali.

Nell'MVP il catalogo viene gestito nell'applicativo installato del locale e pubblicato al servizio web. La pagina QR pubblica lo legge in sola lettura: non è un secondo pannello di gestione.

## Categorie

Ogni categoria ha almeno nome e ordine di visualizzazione. Le categorie servono a rendere rapido il menu del cliente e la selezione dei prodotti in cassa.

Esempi iniziali: `Caffetteria`, `Bevande`, `Brioche`, `Aperitivi`.

## Prodotti

Per la prima versione, ogni prodotto richiede:

- nome;
- categoria;
- prezzo;
- disponibilità;
- allergeni applicabili.

La disponibilità permette di nascondere temporaneamente un prodotto dal menu QR e dalla cassa senza cancellarne lo storico. La cancellazione di un prodotto già presente in una comanda o in un documento emesso non è prevista.

Descrizione e immagine del prodotto sono opzionali: possono rendere il menu più chiaro, ma non devono rallentare la configurazione iniziale del locale.

## Allergeni

Gli allergeni sono un'informazione strutturata associata al prodotto, non testo libero. Devono essere visibili nella pagina del prodotto del menu QR prima che il cliente aggiunga l'articolo alla comanda.

Il primo MVP deve permettere al titolare di selezionare per ogni prodotto gli allergeni pertinenti da un elenco predefinito. Non deve formulare promesse automatiche sull'assenza di contaminazioni o su esigenze alimentari speciali: quelle informazioni richiedono la verifica del locale.

## Aggiornamenti

Un aggiornamento di prezzo, disponibilità o allergeni si applica alle nuove comande. Il servizio salva nella comanda inviata una fotografia dei prodotti, dei prezzi e degli allergeni; le comande già inviate e i documenti emessi conservano quindi i dati con cui sono stati creati.
