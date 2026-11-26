---
repo: Regime-Detector
linguaggi: Pine Script (TradingView), v6
stato: attivo (v2.1)
aggiornato: 2026-11-26
---

# Scheda tecnica — Regime-Detector

## Scopo
Indicatore Pine Script v6 per TradingView che identifica regimi LONG/SHORT con confidence score, TP/SL dinamici, divergenze e multi-confluenza (TEMA, Supertrend, WaveTrend, RSI, ADX, filtro trend HTF, footprint).

## Architettura
- Due file `.pine`: v2.0 (primo rilascio, superato) e v2.1 (versione corrente, superset).
- Nessun build, test runner o linter locale. Verifica reale solo in Pine Editor di TradingView.
- Nessuna dipendenza esterna, nessun pacchetto npm/pip, nessun binario.
- `docs/` contiene revisione e guide; `CLAUDE.md` standard operativi.

## Componenti
| Nome | Ruolo | File |
|------|-------|------|
| TEMA | Trend-enhanced moving average (finestra 32/9/21) | regime_detektor_v2.1.pine |
| Supertrend | Trend/ATR flip (factor 2.6, period 10) | regime_detektor_v2.1.pine |
| WaveTrend | Momentum (n1=10, n2=21) | regime_detektor_v2.1.pine |
| RSI | Condizioni di ipercomprato/venduto + divergenza | regime_detektor_v2.1.pine |
| ADX | Forza trend (min 20, strong 30) | regime_detektor_v2.1.pine |
| Footprint | Delta/POC/imbalance (Piano Premium/Ultimate) | regime_detektor_v2.1.pine |
| HTF filter | Short valido solo sotto TEMA 200 sull'HTF | regime_detektor_v2.1.pine |

## Dati e interfacce
- Input da pannello Pine Editor (timeframe operativo, TEMA, Supertrend, WaveTrend, RSI, ADX, filtri, footprint).
- Uscite: plot, labels e tooltip sul grafico (overlay=true, max_labels_count=500).
- Nessun endpoint di rete, nessun database, nessun file di dati consumato.

## Dipendenze
- Nessun package esterno; solo la sintassi Pine Script v6 di TradingView.
- Footprint richiede piano Premium/Ultimate (opzionale, input `useFP`).

## Configurazione
- Variabili/input (nomi, valori default, nessun segreto): `tf`, `tf_filter`, `temaLen`, `temaLen_fast`, `temaLen_slow`, `stFactor`, `stPeriod`, `wtN1`, `wtN2`, `wtOverbought`, `wtOversold`, `rsiLen`, `rsiOverbought`, `rsiOversold`, `rsiDivLen`, `adxLen`, `adxThreshold`, `adxStrongTrend`, `maxDistATR`, `volMultiplier`, `slopeThreshold`, `useStrongBearBoost`, `useFP`, `fpTicksPerRow`, `fpVAPercent`, `fpImbalancePercent`, `fpDeltaDivBars`, `fpBoostEnabled`.
- Nessun segreto: nessun dato reale in repo.

## Build e test
- Nessun comando di build locale. Comando di verifica reale: incollare lo script in Pine Editor e controllare la barra di stato (nessun errore di sintassi).
- Esito locale: non verificato (nessun test eseguito in locale).
- Verifica documentazione: `docs/_inventario.tsv`, `docs/ISTRUZIONI.md`, `CLAUDE.md` aggiornati al 2026-11-25/26.

## Deploy
- Nessun deploy automatico: l'indicatore viene caricato manualmente in TradingView dallo Pine Editor.
- Repo: github.com/obi2kenobi/Regime-Detector, ramo default `main`.

## Rischi e debito tecnico
- Dipendenza totale da TradingView: senza esecuzione manuale non si può validare una modifica.
- Due file `.pine` paralleli: non aggiornarli insieme senza motivo.
- `_revisione.tsv` ed `_inventario.tsv` contengono dati di revisione, non source-of-truth.
- Footprint richiede piano a pagamento; se disabilitato, comportamento identico a v2.0.
