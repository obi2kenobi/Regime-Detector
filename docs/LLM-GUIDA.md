# LLM-GUIDA — Regime-Detector

## Scopo
Indicatore Pine Script (TradingView, v6) per identificare regimi LONG/SHORT con confidence score, TP/SL dinamici e multi-confluenza.

## Struttura
- `regime_detektor.pine` (v2.0, 536 righe): primo rilascio.
- `regime_detektor_v2.1.pine` (v2.1, 773 righe): versione corrente, superset.
- `docs/`: `_inventario.tsv`, `_revisione.tsv`, `_guida-lista.txt` (documentazione di revisione).
- `CLAUDE.md`: standard di lavoro operativo (max 100 righe; originale conservato in `docs/REGOLE-CLAUDE-originale.md`).

## Avvio / test
- Nessun build, test runner o linter locale. Verifica reale: incollare lo script nello Pine Editor di TradingView e controllare la compilazione.
- Esito locale: non verificato (nessun test eseguito in locale).

## Convenzioni
- Chiavi: commit `<type>: <short description>`; nessuna force push; commit dopo ogni step funzionante.
- Funzioni corte (30-40 righe); un file una responsabilità; niente codice morto.
- Non fare modifiche non richieste.

## Punti fragili
- Dipendenza totale dal Pine Editor/TradingView: senza esecuzione manuale non si può validare una modifica.
- Due file `.pine` paralleli: non aggiornarli insieme senza motivo.
- `_revisione.tsv` e `_inventario.tsv` contengono dati di revisione, non source-of-truth del codice.

## Archivio
- R1: Integra M-003.3 (9167fee). R2/R3/R4: catena `op/M-004-3-r2` su docs/razionalizzazione-2026-11.
- Repo: github.com/obi2kenobi/Regime-Detector, default `main`.

## Istruzioni duso
- Vedi docs/ISTRUZIONI.md per le istruzioni duso di ogni software.

## Scheda tecnica
Vedi [docs/SCHEDA-TECNICA.md](docs/SCHEDA-TECNICA.md).
