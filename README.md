## Nataliia Gordeeva

**Data analytics, econometrics and applied machine learning**

[Русская версия](README.ru.md)

Financial University under the Government of the Russian Federation. BSc in Economics (Business Valuation in the Digital Economy) and MSc in Applied Mathematics and Computer Science (Machine Learning on Texts and Graphs), both with honours.

Nearly six years of applied analytical practice in econometrics and financial analysis. In ML I have taken projects through the full cycle, from building a corpus to fine-tuning a language model with measured results. I currently run two live systems, a daily collection of the Moscow rental market and a search service over Bank of Russia regulations. Contributor to open-source LLM evaluation frameworks, 4 merged pull requests.

---

### Featured repositories

**[msk-rent-market](https://github.com/nata2627/msk-rent-market)** · panel of the Moscow rental market · [live dashboard](https://nata2627.github.io/msk-rent-market/)
Daily collection of long-term rental listings from CIAN since 22 Sep 2026, about 59 thousand listings and 586 thousand observations. The site returns at most 1,512 listings per query, so the search is split recursively into buckets and completeness is checked for each bucket every day. A watchdog checks the run every 20 minutes and reports eight types of failure to Telegram. In the first month 15 days were rescued by automatic restarts, and every incident ended with a new check in the code. Questions answered on the panel:
- **Forecast.** Random walk, seasonal naive, ETS and SARIMA backtested on 140 months of Rosstat data with rolling origins. The selection rule was committed before the first run, and the random walk won (MAPE 1.92% against 2.70% for SARIMA)
- **Rent index.** A hedonic index shows −0.49% over the month, while a chained index on the same listings shows −5.7% and measures listing ageing instead of the market
- **Fair price.** CatBoost against hedonic regression with time-based and duplicate-group splits, MAPE 13.0% against 17.6%, 80% conformal intervals. Weekly retraining tracked in MLflow, served by the bot's `/price` command
- **Price cuts.** Agencies cut prices 9 p.p. more often than owners, controls barely move the gap. Listings that cut leave the market 6-11% faster than similar ones. The pre-registered placebo turned out to be flawed and was fixed, and the estimate is reported as unstable
- **Listing lifetime.** Median 14 days, Kaplan-Meier with late entry
- **Pets.** Allowing pets does not change rent (−0.3% [−1.1; +0.6]), an explicit ban comes with a 2.8% discount

dbt marts, duplicate linking across agencies, a D3 dashboard on GitHub Pages, 471 tests in GitHub Actions.
`PostgreSQL` `dbt` `Playwright` `statsmodels` `CatBoost` `MLflow` `D3` `Docker`

**[ru-fin-rag](https://github.com/nata2627/ru-fin-rag)** · search service over Bank of Russia regulations · [live demo](https://ru-fin-rag.onrender.com)
A corpus of 1,555 regulations and 62,606 chunks, refreshed by a scheduled nightly run. Retrieval quality is measured on 991 labelled queries. Hybrid search with cross-encoder reranking scores 0.704 NDCG@10 against 0.571 for BM25, p < 0.001, and a stemmer in BM25 tokenization added 0.087. FastAPI service deployed on the Render free tier, p50 470.6 ms and p95 669.3 ms measured from Moscow. Under load (locust) a single process sustains 140-165 requests per second with zero failures. Every query is logged as an event, with a 6-model dbt mart on top in ClickHouse. I compared vector stores (numpy, FAISS, Qdrant embedded and over the network) and int8 quantization, which costs 0.005 [0.001; 0.010] in quality. The Airflow DAG for the scheduled pipeline runs in a container in CI.
`FastAPI` `BM25` `cross-encoder` `ClickHouse` `dbt` `Airflow` `Qdrant` `FAISS` `Docker`

**[moex-index-effect](https://github.com/nata2627/moex-index-effect)** · index effect on the Moscow Exchange
What happens to a stock's price and liquidity when it enters or leaves the IMOEX index. 42 events over 2022-2026, market model and cumulative abnormal returns, a control group via nearest-neighbour matching, difference-in-differences on liquidity with a formal parallel trends test, randomization inference on 1,000 placebo dates, Holm and Benjamini-Hochberg corrections. There is no classic index effect. Instead, prices decline steadily after inclusion, CAR −18.3% over 60 days, placebo p = 0.039. The sign holds across all 15 robustness checks, 39 tests.
`pandas` `statsmodels` `event study` `difference-in-differences` `matching`

**[moex-market-analytics](https://github.com/nata2627/moex-market-analytics)** · stock market data mart with all analytics in SQL
46 Moscow Exchange index constituents, 47,672 price rows, `staging → core → marts` layers. Window functions, CTEs, materialized views, beta computed two independent ways and cross-checked. A composite index chosen with `EXPLAIN ANALYZE` cut a market snapshot query from 1.031 to 0.223 ms. Metabase dashboard.
`PostgreSQL` `SQL` `Docker` `Metabase` `ETL`

**[anglicism_detection](https://github.com/nata2627/anglicism_detection)** · master's thesis
Detecting and replacing anglicisms in Russian text. A custom corpus of 50,000+ units, XGBoost against RuRoBERTa-large and XLM-RoBERTa for detection (F1 0.988, ROC-AUC 0.999), fine-tuned Qwen2.5-1.5B-Instruct for rewriting (BLEU 0.807, ROUGE ≈ 0.870).
`PyTorch` `transformers` `XGBoost` `natasha` `hydra`

**[rbc.ru-category-classification](https://github.com/nata2627/rbc.ru-category-classification)** · classifying RBC news into seven sections
Custom scraper, 8,142 articles, four architectures. The simplest bag-of-words network came out best (79%), the recurrent one came last (70%). The section is determined by vocabulary, word order adds almost nothing.
`TensorFlow` `scikit-learn` `BeautifulSoup`

Also [pabd24](https://github.com/nata2627/pabd24) (course ML service for price prediction, DVC, S3, Docker), [gbd](https://github.com/nata2627/gbd) (machine learning on graphs, `ogbn-arxiv`), [rasa_bot](https://github.com/nata2627/rasa_bot), [youtube-subs](https://github.com/nata2627/youtube-subs).

---

### Open-source contributions

| Project | What it is | Contribution |
|---|---|---|
| [EleutherAI/lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness/pulls?q=author%3Anata2627) | reference framework for evaluating language models | 2 PRs merged, 3 in review |
| [comet-ml/opik](https://github.com/comet-ml/opik/pulls?q=author%3Anata2627) | evaluation and tracing for LLM applications | 2 PRs merged |
| [run-llama/llama_index](https://github.com/run-llama/llama_index/pulls?q=author%3Anata2627) | framework for RAG and document agents | 2 PRs in review |

---

### Stack

**Languages** Python · SQL · R · LaTeX

**Data and ML** pandas · numpy · statsmodels · scikit-learn · XGBoost · CatBoost · conformal prediction · MLflow · survival analysis · entity resolution

**Time series** ETS · SARIMA · STL · rolling-origin backtesting · price indices

**NLP and LLM** PyTorch · TensorFlow · transformers · sentence-transformers · LLM fine-tuning and quantization · BM25, hybrid search and cross-encoders · retrieval and generation evaluation

**Econometrics and causal inference** OLS with assumption diagnostics · logit and probit · CAPM · event study · difference-in-differences with fixed effects · matching · randomization inference · clustered standard errors · multiple testing corrections

**Finance** DCF · multiples · fundamental and technical analysis

**Data and infrastructure** PostgreSQL · ClickHouse · dbt · Airflow · FastAPI · Docker · GitHub Actions · Playwright · Qdrant · FAISS · Metabase · D3 · DVC · Excel

---

### Publications

Peer-reviewed journals from the Russian Higher Attestation Commission (VAK) list, indexed in RSCI.

- **Combating Insurance Fraud in the Digital Environment.** Samoupravlenie, 2023, No. 1 (134) · [elibrary](https://elibrary.ru/item.asp?id=50470488)
- **Analysis of the Unit Asking Price of One-Room Apartments in the Secondary Housing Market of Cheboksary**, with S. G. Sternik. Russian Economic Online Journal, 2022, No. 4 · [elibrary](https://elibrary.ru/item.asp?id=50243872)
- **The Impact of the COVID-19 Pandemic on the Financial Performance of Retail Companies.** Samoupravlenie, 2022, No. 4 (132) · [elibrary](https://elibrary.ru/item.asp?id=49288478)

Titles are translated, the papers are in Russian.

---

📫 gordeevanatalia04@gmail.com · Telegram [@daisy_nata](https://t.me/daisy_nata)
