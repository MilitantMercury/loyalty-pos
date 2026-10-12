# Decisioni e questioni aperte

## Decisioni già prese

| Tema | Decisione |
| --- | --- |
| Pubblico iniziale | Bar e piccoli esercenti |
| Priorità | Praticità, velocità, semplicità |
| Flusso iniziale | Comanda dal QR del tavolo, gestione e pagamento alla cassa |
| Tavoli | Numerati; ogni tavolo espone il proprio QR menu |
| Catalogo | Unica fonte dati per menu QR e cassa |
| Prodotto | Nome, categoria, prezzo, disponibilità e allergeni |
| Allergeni | Visibili nel menu QR prima dell'invio della comanda |
| Stati comanda | `Da gestire` → `Consegnata` → `In pagamento` → `Pagata` |
| Pagamento | Avviato dalla cassiera; conto unico o separato guidato |
| POS | La cassa invia l'importo da incassare e riceve l'esito del pagamento |
| Loyalty | Fuori dal primo MVP; tornerà dopo la validazione del flusso di cassa |
| Hardware | Usare la stampante fiscale esistente del locale |
| Prime famiglie | Epson FP-81II RT e RCH |
| Annulli | Inclusi, con documento fiscale di annullamento |
| Resi | Fuori dalla prima versione |
| Archivio documenti | Incluso; archivio operativo collegato ai riferimenti della stampante |
| Chiusura giornaliera | Inclusa; la stampante esegue la Z, la cassa ne conserva l'esito |
| Stato di risposta interrotta | `Da verificare`, senza ristampa o accredito automatico |

## Da decidere

1. Il cliente può modificare o annullare una comanda inviata dal QR? Fino a quando?
2. Come il personale marca `Consegnata`: dalla cassa, da un telefono o da entrambi?
3. Come si divide il conto separato: per persona, per prodotti o per importo libero?
4. Quale POS preciso integrare per primo e con quale protocollo di scambio importo/esito?
5. Quale modello RCH preciso supportare per primo?
6. Quale ambiente usare in cassa: tablet Android, tablet iPad, PC Windows o web app locale?
7. Come gestire comande e pagamenti se Internet non è disponibile?
8. Come ottenere dispositivi reali, documentazione e supporto tecnico per i test?

## Rischi da validare presto

- Differenze nei protocolli e nei firmware delle stampanti fiscali installate.
- Affidabilità della connessione locale con il dispositivo fiscale.
- Affidabilità della consegna in tempo reale di una comanda dal QR alla cassa.
- Tempi reali del flusso con coda al banco e pagamento separato.
- Gestione delle vendite duplicate in caso di errore o riconnessione.
- Disallineamento tra esito POS e documento fiscale in caso di errore o interruzione.
- Adozione: il locale deve percepire un beneficio immediato senza sostituire il proprio hardware.
