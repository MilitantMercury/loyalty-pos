# Contribuire a Loyalty

`main` deve restare stabile e leggibile. Non si lavora direttamente su `main`: ogni modifica passa da una pull request.

## Documentazione obbligatoria

Ogni modifica al repository richiede l'aggiornamento della documentazione pertinente nella stessa pull request. Questa regola vale per chiunque contribuisca al progetto, inclusi fondatori, maintainer e persone che lavorano con Codex.

Non esistono eccezioni basate sulla dimensione della modifica: anche una correzione piccola deve aggiornare almeno il documento, la decisione, il flusso o il commento operativo che ne risulta cambiato.

## Flusso

1. Lavora su una branch con un solo obiettivo.
2. Aggiorna codice e documentazione insieme.
3. Apri una pull request usando la checklist del repository.
4. Richiedi una revisione prima del merge in `main`.

5. Dopo approvazione, usa lo squash merge e cancella la branch.

## Nomi delle branch

Usa un prefisso e parole separate da trattini:

- `feat/identificazione-cliente`
- `fix/duplicazione-comanda`
- `docs/archivio-documenti`
- `chore/configurazione-ci`

Se esiste un'issue, aggiungi il suo numero dopo il prefisso: `feat/12-identificazione-cliente`.

## Commit

Usa messaggi brevi, in minuscolo, con un prefisso coerente:

- `feat: aggiunge l'archivio documenti`
- `fix: evita l'invio duplicato della comanda`
- `docs: definisce il flusso di chiusura`
- `chore: configura i controlli automatici`

## Pull request

Una PR deve avere uno scopo singolo, una descrizione comprensibile e la checklist completata. Le decisioni che cambiano il prodotto, i flussi fiscali o l'architettura richiedono anche un aggiornamento in `docs/decisions/`.

## Quando arriverà il codice

Prima del merge saranno obbligatori i controlli automatici disponibili: formattazione, lint e test. Nessun controllo verrà inventato finché non sarà scelto lo stack tecnico.

Per le regole complete, consulta [il flusso di collaborazione](docs/05-flusso-collaborazione.md).
