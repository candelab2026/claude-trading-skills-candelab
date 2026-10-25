# Claude Trading Skills

> 🇮🇹 Traduzione italiana di [`README.md`](README.md), a cura del fork [candelab2026/claude-trading-skills-candelab](https://github.com/candelab2026/claude-trading-skills-candelab). Progetto originale di [tradermonty](https://github.com/tradermonty/claude-trading-skills), licenza MIT (vedi [`LICENSE`](LICENSE)). In caso di discordanza fa fede la versione inglese.

Claude Trading Skills è nato come progetto personale per usare l'AI e migliorare il proprio processo di trading.

Claude Trading Skills è un toolkit di workflow di trading basato sulle Claude Skills, pensato per investitori individuali con poco tempo a disposizione.

È pensato per chi usa investimenti a lungo termine, ETF e azioni a dividendo come nucleo (core) del portafoglio, e usa lo swing trading disciplinato come strategia satellite quando le condizioni di mercato sono favorevoli.

L'obiettivo non è delegare all'AI le decisioni di acquisto e vendita. L'obiettivo è dare struttura a revisione del mercato, gestione del rischio, pianificazione dei trade, diario operativo e miglioramento continuo. È open source perché i workflow, le checklist e le abitudini di revisione che stanno dietro a decisioni migliori possono crescere con la pratica condivisa.

Non è un servizio di segnali né una promessa di profitto. È un toolkit per chi vuole costruire un processo decisionale migliore.

Il progetto segue l'approccio **prima per sé, poi aperto agli altri**: nasce come workflow pratico che l'autore usa davvero, e viene poi condiviso apertamente con chi ha vincoli simili.

📖 **Sito di documentazione (in inglese):** <https://tradermonty.github.io/claude-trading-skills/>

**Visione del progetto:** [`PROJECT_VISION.md`](PROJECT_VISION.md)

English README: [`README.md`](README.md) · 日本語版: [`README.ja.md`](README.ja.md)

## Avvertenza (Disclaimer)

Questo repository è destinato esclusivamente a scopi educativi, di ricerca e di miglioramento del processo. Non costituisce consulenza finanziaria, servizio di consulenza sugli investimenti, consulenza fiscale, consulenza legale, servizio di segnali o piattaforma di esecuzione presso un broker. Trading e investimenti comportano rischi, inclusa la perdita del capitale. Performance passate, backtest, screening, report e analisi generate dall'AI non garantiscono risultati futuri. Tutte le decisioni di trading, il dimensionamento delle posizioni, la conformità fiscale/normativa e l'uso del broker sono responsabilità dell'utente.

Il progetto è distribuito con licenza MIT, **"COSÌ COM'È" (AS IS), SENZA GARANZIE**.

## A chi è rivolto

Questo repository è pensato per:

- Investitori individuali con poco tempo
- Investitori di lungo periodo che vogliono anche il potenziale dello swing trading disciplinato
- Investitori in dividendi ed ETF che vogliono una revisione strutturata del portafoglio
- Trader che vogliono gestire il rischio prima di cercare candidati di trade
- Investitori che vogliono tenere un diario e migliorare il proprio processo decisionale

Non è pensato per il trading completamente automatizzato, per l'outsourcing dei segnali o per lo scalping a breve termine.

## Percorso iniziale consigliato

Chi inizia dovrebbe partire da uno di questi workflow operativi. Ogni link punta a un manifest leggibile da macchina in [`workflows/`](workflows/) che indica in ordine le skill, i punti di controllo decisionali e gli artefatti.

| Obiettivo | Workflow | Skill principali | Profilo API |
| --- | --- | --- | --- |
| Controllo di mercato giornaliero in 15 minuti | [`market-regime-daily`](workflows/market-regime-daily.yaml) | market-breadth-analyzer, uptrend-analyzer, exposure-coach | Nessuna API per il percorso base |
| Revisione settimanale del portafoglio di lungo periodo | [`core-portfolio-weekly`](workflows/core-portfolio-weekly.yaml) ([esempio](examples/workflows/core-portfolio-weekly/sample-run/)) | portfolio-manager, kanchi-dividend-review-monitor, trader-memory-core | Alpaca richiesto; CSV manuale come ripiego limitato |
| Cercare candidati swing solo quando il rischio è consentito | [`swing-opportunity-daily`](workflows/swing-opportunity-daily.yaml) ([esempio](examples/workflows/swing-opportunity-daily/sample-run/)) | vcp-screener, drawdown-circuit-breaker, technical-analyst, position-sizer, trader-memory-core, pre-trade-discipline-gate | FMP per gli screener; stato locale per i controlli di rischio e disciplina |
| Registrare e imparare da ogni trade chiuso | [`trade-memory-loop`](workflows/trade-memory-loop.yaml) | trader-memory-core, signal-postmortem | Nessuna API per il percorso manuale |
| Revisione mensile delle performance e aggiornamento delle regole | [`monthly-performance-review`](workflows/monthly-performance-review.yaml) ([esempio](examples/workflows/monthly-performance-review/sample-run/)) | trader-memory-core, signal-postmortem, backtest-expert | Nessuna API per il percorso manuale |

Vedi [`workflows/README.md`](workflows/README.md) per come leggere un manifest ed eseguirlo manualmente. Per una guida di una pagina su "quale workflow fa per me?" vedi [Find Your Workflow](docs/en/find-your-workflow.md) (in inglese; [日本語](docs/ja/find-your-workflow.md)).

Sei nuovo? Segui [Your First Week](docs/en/your-first-week.md) (in inglese; [日本語](docs/ja/your-first-week.md)): dall'installazione a un controllo di mercato senza API dati a pagamento, alla prima voce di diario e alla prima revisione settimanale.

### Esempi di output

Queste anteprime usano dati fittizi per mostrare il tipo di risultati che puoi ottenere prima di configurare una skill. Sono illustrazioni, non letture di mercato reali né istruzioni di trading.

Seleziona un'anteprima per aprire l'SVG a grandezza naturale; da telefono, ingrandisci dopo l'apertura.

[![Raccomandazione illustrativa del Navigator per un controllo di mercato giornaliero di 15 minuti, con tre skill richieste e un percorso senza API a pagamento](docs/assets/previews/navigator-recommendation.svg)](docs/assets/previews/navigator-recommendation.svg)

**Scegli un workflow:** il [Trading Skills Navigator](docs/en/skills/trading-skills-navigator.md) consiglia un percorso di partenza in base al tuo obiettivo.

[![Market Posture Summary illustrativo con tetto di esposizione al 36%, postura REDUCE_ONLY e confidenza LOW perché mancano input critici](docs/assets/previews/market-posture.svg)](docs/assets/previews/market-posture.svg)

**Valuta il rischio di mercato:** il [workflow market-regime-daily](workflows/market-regime-daily.yaml) termina con una postura di Exposure Coach da sottoporre a revisione umana, non con un ordine.

[![Weekly Performance Digest illustrativo per quattro trade chiusi fittizi, con win rate del 50% e 75 dollari di profitto realizzato](docs/assets/previews/weekly-digest.svg)](docs/assets/previews/weekly-digest.svg)

**Impara dai trade chiusi:** il [Weekly Performance Digest](docs/en/skills/weekly-performance-digest.md) riassume i risultati realizzati e le lezioni di processo.

### Quanto costa davvero

Le Claude Web Skills sono attualmente disponibili sugli account Free, Pro, Max, Team ed Enterprise; consulta la
[guida attuale di Anthropic sulle Skills](https://support.claude.com/en/articles/12512180-use-skills-in-claude)
perché l'accesso può cambiare. Claude Code ha requisiti di account separati, e il piano Claude.ai Free non lo
include; vedi la [guida di configurazione di Claude Code](https://code.claude.com/docs/en/getting-started).
FMP, FINVIZ Elite e Alpaca sono integrazioni opzionali di dati o broker per workflow specifici. Il percorso
di partenza a cinque skill qui sotto funziona con CSV pubblici, screenshot di grafici e file locali, quindi non
richiede un abbonamento a un'API di dati di mercato a pagamento.

### Percorso di partenza senza chiavi API

Se non hai abbonamenti a FMP / FINVIZ / Alpaca, parti da queste cinque skill ed eseguile manualmente:

1. `market-breadth-analyzer` — punteggio di ampiezza del mercato da CSV pubblico; nessuna chiave API
2. `uptrend-analyzer` — partecipazione al trend rialzista da CSV pubblico; nessuna chiave API
3. `position-sizer` — puro calcolo; nessun I/O
4. `trader-memory-core` — diario in YAML locale
5. `signal-postmortem` — schema di revisione

Questo percorso permette di valutare le condizioni di mercato, dimensionare i trade, annotare le decisioni e rivedere i risultati **senza API dati a pagamento**. Nota: "nessuna API" non significa "nessun dato esterno": queste skill hanno comunque bisogno di CSV pubblici, screenshot di grafici o file locali. Per i requisiti esatti di input vedi la voce `integrations:` di ciascuna skill in [`skills-index.yaml`](skills-index.yaml).

> **Fonte canonica:** [`skills-index.yaml`](skills-index.yaml) è l'indice autorevole di tutte le skill. Se questo README, `CLAUDE.md` o la documentazione discordano dall'indice, ha ragione l'indice. Lo stesso vale per i workflow multi-skill: fanno fede i file [`workflows/*.yaml`](workflows/).

## Struttura del repository
- `skills/<nome-skill>/` – Cartella sorgente di ciascuna skill di trading. Contiene `SKILL.md`, materiale di riferimento ed eventuali script di supporto.
- `skills-index.yaml` – Indice canonico dei metadati di ogni skill (id, categoria, integrazioni, riferimenti ai workflow).
- `workflows/` – Manifest dei workflow operativi per le routine Core + Satellite (canonici, verificati dal validatore con `--strict-workflows`).
- `skill-packages/` – Archivi `.skill` precompilati, pronti da caricare nella scheda **Skills** dell'app web di Claude.
- `docs/` – Contenuti del sito di documentazione, pagine delle skill generate e `docs/dev/metadata-and-workflow-schema.md` (specifica dello schema).
- `scripts/` – Automazione a livello di repository, incluso il validatore di schema e l'helper di bootstrap.
- `skillsets/` – Pacchetti di installazione per obiettivo, con skill richieste / consigliate / opzionali per i principali scopi (5 skillset: market-regime, core-portfolio, swing-opportunity, trade-memory, strategy-research; usati dal Navigator).

## Per iniziare

Prima volta qui? Leggi le [FAQ](docs/en/faq.md) (in inglese) per piani, costi, sicurezza e ambito.

Consulta il [Changelog](CHANGELOG.md) per le modifiche e la [politica di compatibilità e migrazione delle release](docs/dev/release-compatibility.md) prima di aggiornare una skill già installata.

### Uso con l'app web di Claude
1. Apri l'[ultima GitHub Release](https://github.com/tradermonty/claude-trading-skills/releases/latest) e scarica l'asset `.skill` della skill che ti serve, insieme a `SHA256SUMS`. Verifica l'hash come descritto nella [politica di release](docs/dev/release-compatibility.md). Se la pagina delle Release è vuota, usa l'installazione dalla cartella sorgente qui sotto oppure crea un pacchetto locale con `scripts/package_skills.py`.
2. Per un account individuale, apri **Settings > Capabilities** e abilita **Code execution and file creation**. Gli utenti Team ed Enterprise potrebbero aver bisogno che un owner dell'organizzazione abiliti le Skills.
3. Apri **Customize > Skills**, carica lo ZIP, verifica che compaia nell'elenco e abilitala se necessario (vedi la [guida attuale di Anthropic sulle Skills](https://support.claude.com/en/articles/12512180-use-skills-in-claude)).

### Uso con Claude Code (desktop o CLI)
1. Clona o scarica questo repository.
2. Copia la cartella della skill desiderata (es. `backtest-expert`) in `~/.claude/skills/` per uso personale, oppure in `.claude/skills/` dentro un progetto (vedi la [guida di configurazione di Claude Code](https://code.claude.com/docs/en/getting-started)). Su Windows `~` corrisponde a `C:\Users\<tuo-utente>`.
3. Claude Code rileva le modifiche in una cartella skills già esistente. Riavvialo solo se hai creato la cartella skills di primo livello dopo l'avvio della sessione.

> Suggerimento: i pacchetti `.skill` sono costruiti dalle cartelle sorgente, omettendo test e artefatti di build locali. Se vuoi personalizzare una skill, modifica la cartella sorgente e poi esegui `python3 scripts/package_skills.py --skill <nome-skill>` prima di caricarla sull'app web.

## Piattaforme supportate

L'ambiente di progetto condiviso supporta Python **dalla 3.10 alla 3.13** su Linux, Windows e macOS. Le skill pacchettizzate in modo autonomo mantengono come minimo Python **3.9**. Una combinazione del progetto radice è considerata
*supportata* solo se è verificata dalla CI del progetto; le altre combinazioni in quell'intervallo sono
best-effort e non verificate. Vedi [docs/dev/compatibility-matrix.md](docs/dev/compatibility-matrix.md)
per la matrice esatta e come viene fatta rispettare.

## Pacchetto di lavoro complementare

Vuoi un workflow in stile agente già pronto? Vedi il pacchetto complementare
[Hermes Trading Research Agent Work Package](https://github.com/tradermonty/hermes-trading-research-agent-work-package).

Raccoglie queste skill in un profilo Hermes con routine a comandi slash orientate ai compiti, come
`/pre-market-routine`, `/after-close-review`, `/trade-journal`, `/weekly-portfolio-review` e
`/monthly-performance-review`.

È un assistente per ricerca, diario e revisione del rischio, **non** un sistema di trading automatico.
**Non** invia ordini, non offre un servizio di segnali e non esegue attività pianificate nascoste;
**i punti di controllo decisionali umani restano centrali**.

## Aree principali delle skill

Il repository contiene skill nelle seguenti aree:

| Area | Skill di esempio |
| --- | --- |
| Market Regime (regime di mercato) | `market-breadth-analyzer`, `uptrend-analyzer`, `exposure-coach` |
| Core Portfolio (portafoglio core) | `portfolio-manager`, `value-dividend-screener`, `kanchi-dividend-sop` |
| Swing Opportunities (opportunità swing) | `vcp-screener`, `canslim-screener`, `breakout-trade-planner` |
| Trade Planning (pianificazione dei trade) | `position-sizer`, `technical-analyst`, `pre-trade-discipline-gate` |
| Trade Memory (memoria dei trade) | `trader-memory-core`, `signal-postmortem` |
| Strategy Research (ricerca di strategie) | `backtest-expert`, `manifoldbt-backtester`, `edge-pipeline-orchestrator` |
| Advanced Satellite (satellite avanzato) | `parabolic-short-trade-planner`, `earnings-trade-analyzer`, `options-strategy-advisor` |

## Catalogo dettagliato delle skill

Il catalogo completo è **generato automaticamente** da `skills-index.yaml` tramite `scripts/generate_catalog_from_index.py` ed è mantenuto in inglese nel [`README.md`](README.md#detailed-skill-catalog). Per evitare che una copia tradotta vada fuori sincronia a ogni aggiornamento dell'indice, qui non lo duplichiamo: consulta direttamente [`skills-index.yaml`](skills-index.yaml) o il [catalogo nel sito di documentazione](docs/en/skill-catalog.md).

Per una panoramica auto-generata su ciclo di vita, copertura dei test e stato di salute delle skill, vedi la [Quality Dashboard](https://tradermonty.github.io/claude-trading-skills/en/quality-dashboard/).

## Esempi di workflow aggiuntivi

Il percorso principale Core + Satellite è descritto sopra. Gli esempi seguenti mostrano altri modi di combinare le skill, inclusi workflow avanzati per il satellite e per i contributori.

### Monitoraggio giornaliero del mercato
1. Usa **Economic Calendar Fetcher** per controllare gli eventi ad alto impatto di oggi (FOMC, NFP, CPI)
2. Usa **Earnings Calendar** per individuare le grandi società che pubblicano oggi i risultati
3. Usa **Market News Analyst** per rivedere gli sviluppi notturni e il loro impatto sul mercato
4. Usa **Breadth Chart Analyst** per valutare lo stato di salute generale del mercato e il posizionamento

### Revisione settimanale della strategia
1. Usa **Sector Analyst** per scaricare i dati CSV e individuare le rotazioni (facoltativamente fornendo i grafici)
2. Usa **Technical Analyst** sugli indici e sulle posizioni chiave per confermare il trend
3. Usa **Market Environment Analysis** per un quadro macro completo
4. Usa **US Market Bubble Detector** per valutare eccessi speculativi e livelli di rischio

### Ricerca su un singolo titolo
1. Usa **US Stock Analysis** per una revisione completa fondamentale e tecnica
2. Usa **Earnings Calendar** per verificare le prossime date dei risultati
3. Usa **Market News Analyst** per rivedere le notizie recenti sulla società e sul settore
4. Usa **Backtest Expert** per validare le strategie di ingresso/uscita prima del dimensionamento della posizione

### Posizionamento strategico
1. Usa **Stanley Druckenmiller Investment** per individuare i temi macro
2. Usa **Economic Calendar Fetcher** per scegliere i tempi d'ingresso attorno ai principali dati macro
3. Usa **Breadth Chart Analyst** e **Technical Analyst** per i segnali di conferma
4. Usa **US Market Bubble Detector** per la gestione del rischio e indicazioni sulla presa di profitto

### Trading sul momentum degli utili
1. Usa **Earnings Trade Analyzer** per valutare le reazioni agli utili recenti (dimensione del gap, trend, volume, posizione rispetto alle medie mobili)
2. Usa **PEAD Screener** (Modalità B) con l'output dell'analyzer per trovare setup PEAD (ritracciamenti con candela rossa → segnali di breakout)
3. Usa **Technical Analyst** per confermare i pattern sul grafico settimanale e i livelli di supporto/resistenza
4. Usa i filtri di **liquidità** del PEAD Screener per assicurarti che il dimensionamento della posizione sia fattibile
5. Monitora i titoli SIGNAL_READY per ingressi in breakout con stop-loss definito (minimo della candela rossa) e obiettivi a 2R

### Costruzione di un portafoglio a reddito
1. Usa **Value Dividend Screener** per individuare titoli a dividendo di qualità con rendimenti sostenibili
2. Usa **Dividend Growth Pullback Screener** per trovare titoli a dividendo in crescita in punti d'ingresso tecnici interessanti
3. Usa **US Stock Analysis** per un'analisi fondamentale approfondita sui candidati migliori
4. Usa **Earnings Calendar** per seguire i prossimi risultati delle società in portafoglio
5. Usa **Market Environment Analysis** per valutare il contesto macro per le strategie a dividendo
6. Usa **Backtest Expert** per validare strategie di dividend capture o di crescita

### Workflow Kanchi sui dividendi (azioni USA)
1. Usa **Kanchi Dividend SOP** per eseguire il processo in 5 passi di Kanchi e creare piani d'acquisto con condizioni di invalidazione
2. Usa **Kanchi Dividend Review Monitor** con cadenza giornaliera/settimanale/trimestrale per generare code `OK/WARN/REVIEW`
3. Usa **Kanchi Dividend US Tax Accounting** per allineare le posizioni alle ipotesi di dividendi qualificati e alla collocazione nei conti
4. Riporta i risultati `REVIEW` in **Kanchi Dividend SOP** prima di aumentare le posizioni

### Sviluppo di strategie in opzioni
1. Usa **Options Strategy Advisor** per simulare e confrontare strategie in opzioni con il pricing di Black-Scholes
2. Usa **Technical Analyst** per individuare il momento d'ingresso ottimale e i livelli di supporto/resistenza
3. Usa **Earnings Calendar** per pianificare strategie in opzioni legate ai risultati
4. Usa **US Stock Analysis** per validare la tesi fondamentale prima di impiegare capitale
5. Rivedi le greche e gli scenari di P/L per scegliere la strategia ottimale (covered call, spread, straddle, ecc.)

### Revisione e ribilanciamento del portafoglio
1. Usa **Portfolio Manager** per recuperare le posizioni attuali tramite Alpaca MCP e analizzare la salute del portafoglio
2. Rivedi asset allocation, diversificazione settoriale e metriche di rischio (beta, volatilità, concentrazione)
3. Rivedi i segnali a livello di posizione (candidati HOLD/ADD/TRIM/SELL) in base alla validazione della tesi
4. Usa **Market Environment Analysis** e **US Market Bubble Detector** per valutare il contesto macro
5. Rivedi un piano di ribilanciamento e decidi manualmente quali azioni intraprendere, se ce ne sono

### Opportunità di arbitraggio statistico
1. Usa **Pair Trade Screener** per individuare coppie di titoli cointegrati all'interno dei settori
2. Analizza le metriche di mean reversion (half-life, z-score) e i rapporti di copertura
3. Usa **Technical Analyst** per confermare i setup tecnici di entrambe le gambe della coppia
4. Monitora i segnali di ingresso/uscita in base alle soglie di z-score
5. Segui la convergenza dello spread e gestisci le posizioni market-neutral

### Qualità e automazione delle skill

- **Data Quality Checker** (`data-quality-checker`)
  - Verifica la qualità dei dati nei documenti di analisi di mercato e negli articoli prima della pubblicazione.
  - 5 categorie di controllo: incoerenze di scala dei prezzi (ETF vs futures), coerenza della notazione degli strumenti, discrepanze data/giorno della settimana (inglese + giapponese), errori nei totali di allocazione (limitati alla sezione) e discrepanze di unità.
  - Modalità consultiva: segnala i problemi come avvisi per la revisione umana, exit 0 anche in presenza di segnalazioni.
  - Supporta i caratteri giapponesi a larghezza piena (％, 〜), la notazione per intervalli (50-55%) e l'inferenza dell'anno per le date senza anno esplicito.
  - Nessuna chiave API richiesta: funziona offline su file markdown locali.

- **Skill Designer** (`skill-designer`)
  - Genera prompt per Claude CLI per progettare nuove skill a partire da specifiche strutturate.
  - Inserisce nel prompt le convenzioni del repository (guida alla struttura, checklist di qualità, template di SKILL.md).
  - Elenca le skill esistenti per evitare duplicazioni. Usata dal flusso giornaliero della pipeline di auto-generazione delle skill.
  - Nessuna chiave API richiesta.

- **Dual-Axis Skill Reviewer** (`dual-axis-skill-reviewer`)
  - Valuta la qualità delle skill con un metodo a doppio asse: punteggio automatico deterministico (struttura, workflow, sicurezza di esecuzione, artefatti, test) e revisione approfondita opzionale tramite LLM.
  - Asse automatico a 5 categorie (0-100): Metadati e caso d'uso (20), Copertura del workflow (25), Sicurezza di esecuzione e riproducibilità (25), Artefatti di supporto (10), Stato dei test (20).
  - Riconosce le skill `knowledge_only` (senza script, solo riferimenti) e adatta le aspettative di punteggio per evitare penalizzazioni ingiuste.
  - Asse LLM opzionale per la revisione qualitativa (correttezza, rischio, logica mancante, manutenibilità) con peso configurabile.
  - Supporta `--all` per rivedere tutte le skill in una volta, `--skip-tests` per un triage rapido e `--project-root` per la revisione di altri progetti.
  - Nessuna chiave API richiesta.

- **Skill Idea Miner** (`skill-idea-miner`)
  - Analizza i log delle sessioni di Claude Code per trovare idee di nuove skill, le valuta per novità/fattibilità/valore per il trading e mantiene un backlog prioritizzato.
  - Usata dalla pipeline settimanale di auto-generazione delle skill. Può essere eseguita anche manualmente.
  - Nessuna chiave API richiesta.

## Automazione per i contributori

Le pipeline di auto-miglioramento e di generazione delle skill sono workflow per i maintainer,
non passi di trading per principianti. Vedi la [Skill Automation Quickstart](docs/dev/skill-automation.md)
([日本語](docs/dev/skill-automation.ja.md)) per comportamento, effetti collaterali, comandi manuali e pianificazione su macOS.

## Personalizzazione e contributi
- Modifica i file `SKILL.md` per ritoccare le descrizioni di attivazione o le note sulle capacità; assicurati che il nome nel frontmatter coincida con il nome della cartella quando crei lo ZIP.
- Estendi i documenti di riferimento o aggiungi script dentro ciascuna cartella di skill per supportare nuovi workflow.
- Quando distribuisci aggiornamenti, rigenera il file `.skill` corrispondente in `skill-packages/` così gli utenti dell'app web ricevono l'ultima versione:
  ```bash
  python3 scripts/package_skills.py --skill <nome-skill>
  ```

## Requisiti API

Diverse skill richiedono chiavi API per l'accesso ai dati:

### Skill che richiedono API

| Skill | FMP API | FINVIZ Elite | Alpaca | Note |
|-------|---------|--------------|--------|------|
| **Economic Calendar Fetcher** | ✅ Richiesta | ❌ Non usata | ❌ Non usata | Recupera eventi economici |
| **Earnings Calendar** | ✅ Richiesta | ❌ Non usata | ❌ Non usata | Recupera le date dei risultati |
| **Institutional Flow Tracker** | ✅ Richiesta | ❌ Non usata | ❌ Non usata | Analisi dei 13F; il piano gratuito basta |
| **Value Dividend Screener** | ✅ Richiesta | 🟡 Opzionale | ❌ Non usata | FINVIZ riduce i tempi di esecuzione del 70-80% |
| **Dividend Growth Pullback Screener** | ✅ Richiesta | 🟡 Opzionale | ❌ Non usata | FINVIZ per il pre-screening sull'RSI |
| **Kanchi Dividend SOP** | ❌ Non usata | ❌ Non usata | ❌ Non usata | Workflow di conoscenza; usa output di altre skill o elenchi manuali |
| **Kanchi Dividend Review Monitor** | ❌ Non usata | ❌ Non usata | ❌ Non usata | Motore di regole locale; consuma JSON di input normalizzato |
| **Kanchi Dividend US Tax Accounting** | ❌ Non usata | ❌ Non usata | ❌ Non usata | Workflow di conoscenza per classificazione/collocazione nei conti |
| **Pair Trade Screener** | ✅ Richiesta | ❌ Non usata | ❌ Non usata | Analisi di arbitraggio statistico |
| **Options Strategy Advisor** | 🟡 Opzionale | ❌ Non usata | ❌ Non usata | FMP per i dati azionari; il pricing teorico funziona senza |
| **Portfolio Manager** | ❌ Non usata | ❌ Non usata | ✅ Richiesta | Posizioni in tempo reale tramite Alpaca MCP |
| **CANSLIM Stock Screener** | ✅ Richiesta | ❌ Non usata | ❌ Non usata | Fase 3.1 (7 componenti, RS multi-periodo); il piano gratuito basta per 35 titoli; scraping web di Finviz per i dati istituzionali |
| **VCP Screener** | ✅ Richiesta | ❌ Non usata | ❌ Non usata | Screening Stage 2 + pattern VCP; il piano gratuito basta |
| **Parabolic Short Trade Planner** | ✅ Richiesta | ❌ Non usata | ✅ Fase 3 / 🟡 Fase 2 | FMP per lo screener della Fase 1; Alpaca richiesta per le barre intraday della Fase 3 (feed paper OK), opzionale per i controlli di borrow della Fase 2. Nessun SDK: `requests` diretto |
| **FTD Detector** | ✅ Richiesta | ❌ Non usata | ❌ Non usata | Prezzi degli indici per rilevare rally/FTD |
| **IBD Distribution Day Monitor** | ✅ Richiesta | ❌ Non usata | ❌ Non usata | OHLCV giornaliero di QQQ/SPY per i Distribution Day |
| **Macro Regime Detector** | 🟡 Opzionale | ❌ Non usata | ❌ Non usata | Storico ETF da yfinance senza chiave; dati FMP di mercato e Treasury opzionali |
| **Market Breadth Analyzer** | ❌ Non usata | ❌ Non usata | ❌ Non usata | Usa CSV gratuiti su GitHub |
| **Uptrend Analyzer** | ❌ Non usata | ❌ Non usata | ❌ Non usata | Usa CSV gratuiti su GitHub |
| **Sector Analyst** | ❌ Non usata | ❌ Non usata | ❌ Non usata | Usa CSV gratuiti su GitHub; immagini di grafici opzionali |
| **Theme Detector** | 🟡 Opzionale | 🟡 Opzionale | ❌ Non usata | Core: FINVIZ pubblico + yfinance (gratis). FMP per le holdings degli ETF, FINVIZ Elite per gli elenchi di titoli |
| **FinViz Screener** | ❌ Non usata | 🟡 Opzionale | ❌ Non usata | Screener pubblico gratuito; FINVIZ Elite rilevato automaticamente da `$FINVIZ_API_KEY` |
| **Edge Candidate Agent** | ❌ Non usata | ❌ Non usata | ❌ Non usata | Generazione YAML locale; valida contro il repository locale della pipeline |
| **Trade Hypothesis Ideator** | ❌ Non usata | ❌ Non usata | ❌ Non usata | Pipeline locale di ipotesi in JSON con export opzionale della strategia |
| **Edge Strategy Reviewer** | ❌ Non usata | ❌ Non usata | ❌ Non usata | Punteggio deterministico su bozze YAML locali |
| **Edge Pipeline Orchestrator** | ❌ Non usata | ❌ Non usata | ❌ Non usata | Orchestra le skill edge locali via subprocess |
| **Edge Signal Aggregator** | ❌ Non usata | ❌ Non usata | ❌ Non usata | Aggrega gli output JSON/YAML delle skill edge locali in segnali ordinati con pesi |
| **Trader Memory Core** | 🟡 Opzionale | ❌ Non usata | ❌ Non usata | FMP solo per MAE/MFE nel postmortem; le funzioni principali lavorano offline |
| **Exposure Coach** | 🟡 Opzionale | ❌ Non usata | ❌ Non usata | FMP solo se si includono i dati di institutional-flow-tracker |
| **Signal Postmortem** | 🟡 Opzionale | ❌ Non usata | ❌ Non usata | FMP per recuperare i rendimenti realizzati; supportato anche l'inserimento manuale dei prezzi |
| Dual-Axis Skill Reviewer | ❌ Non usata | ❌ Non usata | ❌ Non usata | Punteggio deterministico + revisione LLM opzionale |

### Configurazione delle API

**Financial Modeling Prep (FMP) API:**
- Piano gratuito: 250 richieste/giorno (sufficiente per la maggior parte degli usi)
- Registrazione: https://financialmodelingprep.com/developer/docs
- Imposta la variabile d'ambiente: `export FMP_API_KEY=la_tua_chiave` (su Windows PowerShell: `$env:FMP_API_KEY = "la_tua_chiave"`)
- Oppure fornisci la chiave da riga di comando quando richiesto

**FINVIZ Elite API:**
- Abbonamento: 39,50 $/mese o 299,50 $/anno
- Registrazione: https://elite.finviz.com/
- Imposta la variabile d'ambiente: `export FINVIZ_API_KEY=la_tua_chiave`
- Offre un pre-screening rapido per gli screener sui dividendi

**Alpaca Trading API:**
- Disponibile un conto paper trading gratuito
- Registrazione: https://alpaca.markets/
- Richiede la configurazione di Alpaca MCP Server
- Imposta le variabili d'ambiente:
  ```bash
  export ALPACA_API_KEY="il_tuo_api_key_id"
  export ALPACA_SECRET_KEY="la_tua_secret_key"
  export ALPACA_PAPER="true"  # oppure "false" per il trading reale
  ```

> Non inserire mai le chiavi API nei file né in chat: usa solo variabili d'ambiente. Usa il paper trading come impostazione predefinita.

## Supporto e approfondimenti
- Presentazione delle Claude Skills: https://www.anthropic.com/news/skills
- Guida alle Skills di Claude Code: https://docs.claude.com/en/docs/claude-code/skills
- Financial Modeling Prep API: https://financialmodelingprep.com/developer/docs

Domande o suggerimenti? Apri una issue oppure aggiungi indicazioni accanto alla cartella della skill pertinente, così i futuri utenti sapranno come ottenere il meglio da questi assistenti di trading.

## Licenza

Tutte le skill e i materiali di riferimento in questo repository sono forniti a scopo educativo e di ricerca. Il progetto è distribuito con licenza MIT; il copyright originale appartiene a tradermonty (vedi [`LICENSE`](LICENSE)).
