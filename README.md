# Analisi-dei-modelli-di-forecasting-per-serie-temporali
Bachelor thesis on time series forecasting for Formula 1 race data.

## Capitolo 4 - Analisi dei modelli di forecasting per serie temporali

**Candidato:** Maral Noori 
**Relatore:** Prof. Francesco Guerra
**Università degli Studi di Modena e Reggio Emilia** - A.A. 2025/2026

---

## Descrizione

Questo repository contiene il codice per la parte sperimentale (Capitolo 4) della tesi di laurea triennale in Ingegneria Informatica. Lo studio applica modelli di forecasting a serie temporali di dati reali di Formula 1 per valutare le prestazioni di diversi approcci previsionali.

## Modelli implementati

| Modello | Sezione | Descrizione |
|---------|---------|-------------|
| Naïve | 4.7.1 | Previsione = ultimo valore osservato (benchmark) |
| Drift | 4.7.2 | Proiezione lineare della variazione media |
| Regressione Lineare | 4.7.4 | Predittori esterni (pneumatici + meteo) |
| ARIMA | 4.7.5 | Selezione automatica dell'ordine via AutoARIMA |
| Regressione Dinamica | 4.7.6 | Combinazione regressione + errori ARIMA |

## Metriche di valutazione

- **MAE** - Mean Absolute Error
- **RMSE** - Root Mean Squared Error
- **MAPE** - Mean Absolute Percentage Error (%)
- **MASE** - Mean Absolute Scaled Error (indicatore principale per il confronto)

## Dati

Il dataset è estratto dalla piattaforma pubblica [OpenF1](https://openf1.org) e contiene i tempi sul giro di Charles Leclerc (Scuderia Ferrari) in cinque Gran Premi delle stagioni 2024 e 2025.

**File CSV richiesti:**
- `kole 2024.csv` - Training set (stagione 2024)
- `kole 2025.csv` - Test set (stagione 2025)

> I file CSV devono essere caricati nella sessione Colab prima di eseguire il notebook.

### Variabili del dataset

| Variabile | Tipo | Descrizione |
|-----------|------|-------------|
| `lap_duration` | Target | Tempo sul giro (secondi) |
| `compound` | Predittore | Mescola pneumatico (SOFT/MEDIUM/HARD) |
| `tyre_age` | Predittore | Età dello pneumatico (giri) |
| `pit_stop` | Predittore | Presenza pit stop (0/1) |
| `air_temperature` | Predittore | Temperatura dell'aria |
| `track_temperature` | Predittore | Temperatura della pista |
| `humidity` | Predittore | Umidità (%) |
| `wind_speed` | Predittore | Velocità del vento |
| `rainfall` | Predittore | Presenza pioggia |

## Struttura del notebook

```
capitolo_4_forecasting.ipynb
├── Import librerie
├── Configurazione
├── [4.3] Caricamento del dataset (CSV già estratti da OpenF1)
├── [4.4] Analisi preliminare del dataset
├── [4.5] Analisi esplorativa (statistiche + istogramma)
├── Funzione metriche di errore
├── [4.7.1-4.7.2] Modelli Benchmark (Naïve + Drift)
├── [4.7.4] Regressione Lineare + anomalia Bahrain
├── [4.7.5] Modello ARIMA + test Ljung-Box
├── [4.7.6] Regressione Dinamica + test innovazioni
└── [4.8] Confronto modelli (heatmap MASE)
```

## Requisiti

```bash
pip install pandas numpy matplotlib scikit-learn statsmodels pmdarima
```

In Google Colab, tutte le dipendenze sono già installate.

## Come eseguire

1. Aprire il notebook in Google Colab
2. Caricare i file `kole 2024.csv` e `kole 2025.csv` nella sessione
3. Eseguire le celle in ordine dall'alto verso il basso

## Referenze

- Hyndman, R.J., Athanasopoulos, G.
Forecasting: Principles and Practice (Python edition).
OTexts.
- OpenF1 API Documentation. https://openf1.org
