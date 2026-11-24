# Regime-Detector

Indicatore Pine Script (TradingView, v6) per identificare regimi LONG/SHORT con confidence score, TP/SL dinamici e multi-confluenza.

## Scopo

Identifica regime di mercato (LONG/SHORT) combinando TEMA, Supertrend, WaveTrend, RSI e altre conferme, con gestione dinamica di TP/SL e tooltip su grafico.

## Requisiti

- Account TradingView con Pine Editor.
- Nessun build locale, nessun test runner, nessuna dipendenza esterna.

## Installazione

1. Apri TradingView e crea un nuovo grafico.
2. Apri lo Pine Editor (`Pine Script` → `New`).
3. Incolla il contenuto di `regime_detektor_v2.1.pine` (versione corrente) o `regime_detektor.pine` (v2.0).
4. Salva e aggiungi l'indicatore al grafico.

## Uso

- Il grafico evidenzia i regimi LONG/SHORT e i livelli di ingresso con le relative conferme.
- Parametri sono input dell'indicatore (TEMA, Supertrend, WaveTrend, RSI, timeframe operativo e filtro trend); regolabili dal pannello impostando nel grafico.
- Verifica di compilazione: guardare la barra di stato del Pine Editor (errore o successo) senza errori di sintassi.

Esempio di flusso:
```bash
# Nessun comando locale: l'esecuzione avviene in TradingView
# 1) Apri Pine Editor
# 2) Incolla regime_detektor_v2.1.pine
# 3) Verifica compilazione nel pannello
```

## Struttura delle cartelle

- `regime_detektor.pine` (v2.0, 536 righe): primo rilascio.
- `regime_detektor_v2.1.pine` (v2.1, 773 righe): versione corrente, superset.
- `docs/`: LLM-GUIDA.md e appunti di revisione (`_inventario.tsv`, `_revisione.tsv`, `_guida-lista.txt`).
- `CLAUDE.md`: standard di lavoro.

## Verifica

Non esiste un comando locale di test: la verifica reale è la compilazione in TradingView. Non committare `.pine` con errori di sintassi.
