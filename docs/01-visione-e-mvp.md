# Visione e perimetro MVP

## Problema

Nei bar con servizio al tavolo, raccogliere una comanda e riscuotere il conto può creare attese e passaggi manuali. Nei momenti affollati, ogni attività extra alla cassa diventa un problema.

## Proposta

Una cassa software per bar e piccoli locali. Il cliente usa il QR del tavolo per creare la comanda; la cassa la riceve in tempo reale, la gestisce e la chiude al pagamento con documento fiscale e POS.

## Utenti iniziali

- Cliente al tavolo: apre il menu dal QR e invia la comanda senza attendere il personale.
- Personale di sala: porta la comanda al tavolo e la marca come consegnata.
- Cassiera: vede le comande in arrivo e chiude il pagamento con il minor numero possibile di tocchi.
- Titolare: configura tavoli e catalogo e consulta i documenti emessi.

## Perimetro della prima versione

- Tavoli numerati e un QR menu collegato a ciascun tavolo.
- Catalogo unico, usato sia dalla cassa sia dal QR menu.
- Gestione di categorie, prodotti, prezzi e allergeni.
- Creazione autonoma della comanda dal QR e invio in tempo reale alla cassa.
- Lista `Da gestire` in cassa per le nuove comande.
- Stato `Consegnata` per le comande portate al tavolo e ancora da pagare.
- Avvio del pagamento dalla cassa, con scelta guidata fra conto unico e conto separato.
- Invio del totale da incassare al POS e registrazione del relativo esito.
- Invio della vendita alla stampante fiscale compatibile.
- Passaggio della comanda a `Pagata` solo dopo l'esito fiscale positivo.
- Archivio consultabile dei documenti emessi.
- Annullamento di un documento appena emesso, con documento fiscale di annullamento.
- Chiusura giornaliera richiesta alla stampante fiscale, con storico delle chiusure.

## Fuori dal perimetro iniziale

- Resi.
- Magazzino.
- Prenotazioni, gestione tavoli complessa, spostamento o unione tavoli.
- Delivery e marketplace.
- Fatturazione e gestione contabile completa.
- Loyalty, premi e identificazione cliente.
- Pagamenti gestiti direttamente dalla piattaforma: nella prima versione integriamo il flusso con il POS esistente.
- Compatibilità universale con ogni modello di stampante fiscale.

## Catalogo e menu

Il menu QR e la cassa leggono lo stesso catalogo: un prezzo o un prodotto non può essere aggiornato separatamente nei due canali.

Per il primo MVP, ogni prodotto deve avere almeno:

- nome;
- categoria;
- prezzo;
- disponibilità nel menu;
- elenco degli allergeni applicabili.

La categoria stabilisce l'ordine con cui i prodotti appaiono nel menu e nella cassa. Gli allergeni sono informazione del prodotto e devono essere visibili al cliente prima dell'invio della comanda.

## Misura del successo

Una nuova comanda deve apparire in cassa senza un'azione della cassiera. Il pagamento di un conto unico deve poter essere chiuso con pochi tocchi. Una comanda non può risultare `Pagata` prima della conferma della stampa fiscale.

La fonte fiscale resta sempre la stampante/RT. La nostra applicazione conserva i riferimenti ricevuti dal dispositivo e offre un archivio operativo, senza sostituirsi all'archivio fiscale del registratore.

