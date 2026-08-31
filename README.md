# Chess Move Error Detection

Progetto per il corso di Deep Learning (Magistrale, Primo anno): identificare quale
mossa (tra le prime 10 di una partita di scacchi in notazione SAN) è stata sostituita
con una mossa presa da un'altra partita reale.

## Vincoli del progetto

- Nessuna conoscenza esterna sugli scacchi (no motori, no move generator, no
  controlli di legalità, no modelli pre-addestrati sugli scacchi).
- Modello con al massimo **6.000.000** di parametri addestrabili.
- Metrica ufficiale: **Accuracy@1** sulla posizione dell'errore (classi 1..10).

## Stack

- **Framework:** TensorFlow / Keras
- **Piattaforma di training:** Google Colab (GPU runtime)
- **Experiment tracking:** Weights & Biases (`wandb`)
- Tutto il lavoro vive in un unico notebook: `chess_error_detection.ipynb`.

## Struttura del repo

```
.
├── chess_error_detection_student_specification.ipynb   # specifica del docente (non modificare)
├── chess_error_detection.ipynb                          # notebook di lavoro (setup + baseline)
├── requirements.txt                                     # dipendenze per esecuzione locale
├── .gitignore
└── README.md
```

I dataset (`chess_error_detection_train.csv`, `chess_error_detection_test.csv`) **non**
vengono versionati su GitHub: vengono scaricati da Google Drive direttamente dentro
Colab tramite `gdown` (vedi la sezione "Download the datasets" del notebook).

## Come lavorare sul progetto

1. Apri `chess_error_detection.ipynb` in Google Colab.
2. Imposta il runtime su GPU (Runtime → Cambia tipo di runtime → GPU).
3. Esegui le celle nell'ordine: download dati → tokenizer/pipeline → modello baseline
   → training (loggato su Weights & Biases) → valutazione su test set.
4. Alla fine di una sessione di lavoro, fai commit e push del notebook aggiornato
   sul repository GitHub (vedi sezione dedicata nel notebook o i comandi git manuali).

## Weights & Biases

Il progetto logga metriche e configurazione su un progetto W&B chiamato
`chess-error-detection`. È richiesta una API key gratuita da
https://wandb.ai/authorize.

## Prossimi passi

Vedi la sezione "Next steps" alla fine del notebook per le idee di miglioramento
dell'architettura (tokenizzazione a livello di carattere, meccanismo pointer/attention,
Transformer, sweep di iperparametri, ecc.).
