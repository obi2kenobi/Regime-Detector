---
repo: Regime-Detector
software:
  - regime_detektor_v2.1.pine
  - regime_detektor.pine
aggiornato: 2026-11-25
---

# ISTRUZIONI — Regime-Detector

## regime_detektor_v2.1.pine
Indicazione corrente (v2.1, 773 righe): indicatore Pine v6 per regimi LONG/SHORT, confidence score, TP/SL dinamici, multi-confluenza.

### Requisiti
- Account TradingView con Pine Editor.
- Nessun build locale, nessuna dipendenza esterna.

### Installazione
1. TradingView → nuovo grafico → Pine Editor → New.
2. Incolla il contenuto di `regime_detektor_v2.1.pine`.
3. Salva e aggiungi l'indicatore al grafico.

### Avvio
- Esecuzione in-browser su TradingView; nessun comando locale.
- Regola i parametri nel pannello dell'indicatore (timeframe, TEMA, Supertrend, WaveTrend, RSI).

### Uso
- Il grafico evidenzia regimi LONG/SHORT e livelli di ingresso con conferme.
- Indicatore overlay; input regolabili dal pannello.

### Verifica
- Barra di stato del Pine Editor: nessun errore di sintassi.
- Esito locale: non verificato (nessun test locale disponibile).

### Problemi noti
- Dipendenza totale da TradingView; nessun comando di compilazione locale.

## regime_detektor.pine
Versione v2.0 (536 righe), primo rilascio, superata da v2.1.

### Requisiti / Installazione / Avvio / Uso
- Uguali a v2.1: Pine Editor TradingView, incolla il file, aggiungi al grafico.

### Verifica
- Compilazione manuale in Pine Editor. Esito locale: non verificato.

### Problemi noti
- Versione deprecata: usare v2.1. Non aggiornare entrambi i file insieme senza motivo.
