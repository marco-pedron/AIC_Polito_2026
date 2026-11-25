# AIC Polito 2026: manuale di AI and Cybersecurity

Manuale in LaTeX, scritto da studenti, del corso **AI and Cybersecurity** (Politecnico di Torino, A.A. 2026/27,
Prof. Danilo Giordano; Prof. Matteo Boffa per NLP e ultima parte). Copre AI e ML per la cybersecurity, fondamenti
di deep learning (perceptron, addestramento, regolarizzazione), FFNN, RNN/LSTM, CNN e GNN, embedding, supervised
vs unsupervised e anomaly detection, NLP (Word2Vec, DarkVec). Si aggiorna lezione per lezione.

## 📄 Scarica il PDF

**[Manuale_AIC.pdf](https://github.com/marco-pedron/AIC_Polito_2026/releases/latest/download/Manuale_AIC.pdf)**: l'ultima versione compilata,
sempre allineata a `main`.

Il PDF non è nel repository: lo genera una GitHub Action (`.github/workflows/manuale.yml`) a ogni push su `main` che
tocca `manuale/`, e lo pubblica nella release [`latest`](https://github.com/marco-pedron/AIC_Polito_2026/releases/latest)
con data e commit di origine. Se la compilazione fallisce, la scheda *Actions* mostra l'errore e resta il PDF
precedente. Per rigenerarlo a mano: *Actions → Manuale PDF → Run workflow*.

> ⚠️ **Non è materiale ufficiale.** Sono appunti rielaborati: possono contenere errori. Per l'esame fanno fede le
> slide, i notebook e le indicazioni dei docenti. Le parti aggiunte da noi, cioè non dette a lezione e non presenti
> nelle slide, sono sempre in un riquadro viola **"Integrazione – non dal corso"**. I punti incerti sono nei
> riquadri arancioni **"Da verificare"**.
>
> I capitoli sui laboratori **non contengono soluzioni**: i report sono valutati e vanno scritti dal proprio gruppo.

## Struttura del repository

```
AIC_Polito_2026/
├── README.md
├── .gitignore              whitelist: entrano solo i sorgenti .tex, latexmkrc e il workflow
├── .github/workflows/
│   └── manuale.yml         compila il manuale e pubblica il PDF nella release "latest"
└── manuale/
    ├── main.tex            documento principale: ordine delle parti e degli \input
    ├── preambolo.tex       pacchetti, riquadri, stile del codice Python, mappe, macro
    ├── premessa.tex        "Come leggere questo manuale": legenda e fonti
    ├── latexmkrc           configurazione di latexmk (output in build/)
    ├── lezioni/            Parte I  – Diario: una lezione per file, AAAA-MM-GG.tex (+ _template.tex)
    ├── manuale/            Parte II – Manuale: un capitolo per argomento, 01-ai-cybersecurity … 11-darkvec
    ├── laboratori/         Parte III – Laboratori: come scrivere il report, lab-NN-nome.tex
    ├── ripasso/            Parte IV – Schemi di ripasso: mappe, schede "quale scelta quando"
    ├── esame/              Parte V – Quiz ed esame: formato, quiz, domande aperte ed esercizi
    └── appendice/          Glossario
```

### Le parti del manuale

| Parte | Contenuto |
|---|---|
| **Diario delle lezioni** | Cronaca lezione per lezione: sintesi, avvisi pratici, contenuti, punti segnalati per l'esame. |
| **Manuale del corso** | Un capitolo per argomento che unisce lezioni, slide e notebook, con rimandi al diario e frammenti di codice PyTorch. |
| **Laboratori** | Come si scrive il report; per ogni lab contesto, consegna, teoria coinvolta, metodo e insidie. |
| **Schemi di ripasso** | Mappe concettuali e tabelle "quale scelta quando". |
| **Quiz ed esame** | Formato dell'esame, quiz a scelta multipla e vero/falso, domande aperte ed esercizi su pipeline e codice, con soluzioni. |
| **Appendice** | Glossario inglese–italiano. |

### Riquadri (definiti in `preambolo.tex`)

| Riquadro | Uso |
|---|---|
| `esame[titolo]` (rosso) | punto indicato dal docente come rilevante per l'esame |
| `integrazione[titolo]` (viola) | contenuto aggiunto dai redattori, **non dal corso** |
| `verifica` (arancione) | informazione non confermata: da controllare |
| `nota[titolo]` (grigio) | nota generica, fonti |
| `soluzione[titolo]` (verde) | soluzioni di quiz ed esercizi |
| `definizione`, `esempio`, `attenzione`, `sintesi` | riquadri didattici con contenuti del corso |
| `\dacompletare{…}` (giallo) | parte ancora da scrivere |
| `\lezione{data}{titolo}{docenti}{argomenti}` | intestazione di una voce del diario |
| `\fonti{lezioni}{slide}` | fonti all'inizio di un capitolo tematico |
| `domanda[tema]` + `opzioni`, `\rif{AAAA-MM-GG}{GG/MM}` | domande dei quiz e rimando cliccabile alla lezione |
| `lstlisting` | codice Python (stile già impostato) |

## Copertura attuale

14 lezioni registrate, dal 21/09 al 23/11/2026, tutte nel diario (l'11/11 è la presentazione del Lab 3).

| Data | Argomento |
|---|---|
| 21/09, 23/09 | Presentazione del corso; perché l'AI nella cybersecurity; paradigmi di apprendimento e uso dei modelli |
| 28/09, 30/09 | Perceptron e struttura di una rete; addestramento, loss e valutazione |
| 05/10, 06/10 | Data handling e progettazione di una FFNN; FFNN in PyTorch |
| 12/10, 14/10 | Recurrent neural network; RNN in PyTorch, CNN e GNN |
| 19/10, 20/10 | GNN in pratica e feature categoriche; embedding, dropout e batch norm |
| 02/11, 09/11 | Anomaly detection: concetti, one-class SVM, k-means; dal clustering agli autoencoder (notebook) |
| 11/11 | Presentazione del Lab 3 (anomaly detection) |
| 23/11 | Verso l'NLP: bag of words, Word2Vec (skip-gram, negative sampling, limiti); DarkVec: darknet e idea |

Il resto di DarkVec (24/11), i transformer (25/11) e il Lab 4 non sono ancora nel manuale.

## Come compilare

Per leggere il manuale non serve compilarlo: basta il [PDF della release](#-scarica-il-pdf). Compila in locale
solo se modifichi i sorgenti.

**In locale (macOS):**

```sh
brew install --cask mactex-no-gui            # una volta (~5 GB; chiede la password)
eval "$(/usr/libexec/path_helper)"           # oppure riapri il terminale
cd manuale && latexmk                        # PDF in manuale/build/main.pdf
```

`latexmkrc` imposta pdfLaTeX e la cartella `build/`, che è esclusa da git. Alternativa leggera: `brew install
tectonic`, poi `cd manuale && tectonic -X compile main.tex --outdir build`. Su Linux si usa TeX Live
(`texlive-full`), su Windows MiKTeX.

**Su Overleaf:** crea uno zip della cartella `manuale/`, poi *New Project → Upload Project*. Il documento principale
è `main.tex`, il compilatore pdfLaTeX.

## Pipeline di lavoro

Il manuale nasce dalle registrazioni delle lezioni:

```
registrazione → audio ottimizzato per ASR → trascrizione (Whisper) → bozza LaTeX → revisione → commit
```

1. **Audio:** si estrae dal video l'audio in FLAC mono a 16 kHz, con filtro passa-alto, riduzione del rumore e
   normalizzazione (ffmpeg).
2. **Trascrizione:** si usa Whisper `large-v3-turbo` in locale su Apple Silicon. Si correggono i loop del modello,
   si tolgono i riempitivi e le parti non utili.
3. **Diario:** per ogni lezione si scrive una voce `lezioni/AAAA-MM-GG.tex` dalla trascrizione, confrontata con le
   slide. Numeri e formule si prendono **sempre** dalle slide.
4. **Manuale, laboratori, ripasso, quiz:** si aggiornano i capitoli per argomento partendo da diario, slide e
   notebook. Ciò che non viene dal corso va nei riquadri `integrazione`.
5. **Controllo:** il documento deve compilare senza errori né riferimenti indefiniti. Si rilegge, poi si fa commit.
   Dopo il push controlla che l'Action *Manuale PDF* sia verde: il PDF nella release si aggiorna da solo.

**Registrazioni, audio, trascrizioni, slide, notebook e dataset del corso non sono e non saranno nel repository**,
per il diritto d'autore dell'ateneo e dei docenti. Il `.gitignore` lascia entrare solo i sorgenti `.tex`.

## Come contribuire

- Correzioni e aggiunte sono benvenute: crea un branch (`git checkout -b fix/rnn-lstm`), fai le modifiche, compila,
  apri una pull request. Per una segnalazione rapida basta una *issue*. Il PDF della release si rigenera solo dopo
  il merge su `main`.
- **Nuova lezione:** copia `lezioni/_template.tex` in `lezioni/AAAA-MM-GG.tex` e aggiungi
  `\input{lezioni/AAAA-MM-GG}` in `main.tex`, in ordine cronologico.
- Scrivi in italiano, lasciando in inglese i termini tecnici del corso. Virgolette ``` ``…'' ```.
- Segnala sempre la fonte. Ciò che non viene da lezioni o slide va in `integrazione`, i dubbi in `verifica`.
- Non caricare slide, PDF, notebook, dataset, registrazioni o trascrizioni. Non pubblicare soluzioni dei lab, nomi
  di altri studenti o voti.
