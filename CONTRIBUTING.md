# Contribuire a Loyalty

## Regola principale

`main` deve restare stabile e leggibile. Non si lavora direttamente su `main`: ogni modifica passa da una pull request.

## Flusso

1. Per ogni lavoro, apri un'issue o collega chiaramente il lavoro a una decisione esistente.
2. Crea una branch breve a partire da `main`.
3. Completa il lavoro, aggiorna documentazione e test quando pertinenti.
4. Apri una pull request verso `main`.
5. Una persona diversa dall'autore la revisiona.
6. Dopo approvazione, usa lo squash merge e cancella la branch.

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

