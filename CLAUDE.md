# CLAUDE.md — Regime-Detector

Standard di lavoro operativo per questo repo. Il file originale (106 righe, completo delle regole di processo/codice/git) è conservato in `docs/REGOLE-CLAUDE-originale.md`.

## Scopo
Indicatore Pine Script v6 (TradingView) per regimi LONG/SHORT con confidence score, TP/SL dinamici e multi-confluenza.

## Struttura
- `regime_detektor.pine` (v2.0) — primo rilascio.
- `regime_detektor_v2.1.pine` (v2.1, versione corrente) — superset.
- `docs/` — documentazione di revisione: `_inventario.tsv`, `_revisione.tsv`, `_guida-lista.txt`. `_revisione.tsv` ha lo schema fissato (file/classe/affermazione/atteso/trovato/esito).

## Build / test / deploy
- Nessun build, test runner o linter locale.
- Verifica reale: incollare lo script nello Pine Editor di TradingView e controllare la compilazione.
- Esito locale: non verificato (nessun test eseguito in locale).

## Convenzioni
- Commit: `<type>: <short description>`; nessuna force push; commit dopo ogni step funzionante.
- Funzioni corte (30-40 righe); un file = una responsabilità; niente codice morto.
- Niente modifiche non richieste; non toccare le due versioni .pine insieme senza motivo.

## Cosa non toccare
- Non modificare codice/logica Pine senza mandato esplicito.
- Non aggiungere file o dipendenze fuori dal perimetro.
- Non committare segreti: nessun dato reale, solo segnaposto (`.env.example`).

## Segreti
Non presenti in repo. I valori reali non vanno mai committati; solo segnaposto in `.env.example`.

## Dove guardare
- Guida LLM: `docs/LLM-GUIDA.md`.
- Regole complete originali: `docs/REGOLE-CLAUDE-originale.md`.
