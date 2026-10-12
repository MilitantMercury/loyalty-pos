# Roadmap per il pilota

## Regola di sviluppo

La roadmap è divisa in blocchi autonomi, non assegnati a una persona fissa. Chi prende un blocco ne definisce i dettagli tecnici con Codex, apre la propria branch e porta una pull request verificabile. Si lavora insieme soltanto sui contratti fra blocchi e sulle decisioni che cambiano il prodotto.

## Blocco 1 — Fondazione e catalogo

Definire progetto, configurazione locale, modello dati, `local_units`, tavoli e QR casuali. Realizzare gestione locale di categorie, prodotti, prezzi, disponibilità e allergeni, con pubblicazione al servizio web.

**Pronto quando:** un locale ha catalogo e tavoli configurati e il servizio espone il catalogo pubblicato.

## Blocco 2 — Menu QR e invio comanda

Realizzare la pagina web pubblica del QR: categorie, prodotti, allergeni, carrello e conferma `Sei sicuro di inviare la comanda?`. Al successo salva lo snapshot, svuota il carrello e mostra `Comanda inviata`; l'idempotenza impedisce doppie comande.

**Pronto quando:** una comanda dal telefono è associata al tavolo corretto e viene salvata una sola volta.

## Blocco 3 — Ricezione e gestione alla cassa

Realizzare la sincronizzazione affidabile servizio-app, con ricevuta tecnica, lista `Da gestire`, dettaglio comanda e azione `Consegnata`. Il servizio conserva comande e stati; l'app mantiene la copia operativa. Più comande dello stesso tavolo restano indipendenti.

**Pronto quando:** una comanda inviata compare nell'app e può essere marcata consegnata senza duplicati dopo una riconnessione.

## Blocco 4 — Vendita e pagamento simulati

Realizzare selezione di una o più comande consegnate dello stesso tavolo, conto unico e prima divisione guidata del conto. Introdurre `sales`, `sale_orders` e `payment_parts`; usare adapter POS e fiscale simulati.

**Pronto quando:** una vendita simulata chiude correttamente le comande incluse e compare nello storico dei documenti.

## Blocco 5 — POS, fiscale e chiusure

Integrare il primo POS e il primo dispositivo fiscale testato fisicamente, partendo da Epson FP-81II RT. Implementare emissione, annullo, riconciliazione `Da verificare`, archivio documenti e chiusura Z. Gli eventi tecnici POS restano nel journal append-only locale, non nel database.

**Pronto quando:** una vendita di prova passa da incasso a documento fiscale senza doppio incasso o doppio documento in caso di risposta interrotta.

## Blocco 6 — Pilota controllato

Configurare catalogo, tavoli e QR reali, fare un turno assistito in una fascia tranquilla e misurare tempo fra invio e cassa, tempo di pagamento e blocchi osservati. Si correggono prima i problemi che impediscono il servizio.

**Pronto quando:** il locale svolge un turno limitato senza foglietti paralleli né assistenza continua.

## Dipendenze

```text
Fondazione e catalogo
        ├── Menu QR e invio ──┐
        └── Gestione cassa ───┼── Vendita simulata ── POS e fiscale ── Pilota
                              │
                         contratti condivisi
```

## Cose da non anticipare

- loyalty e premi;
- magazzino;
- prenotazioni e gestione tavoli avanzata;
- delivery;
- supporto generalizzato a stampanti fiscali e POS;
- app mobile nativa, finché il menu web QR copre il bisogno del cliente.
