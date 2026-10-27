## Nataliia Gordeeva

**ML Engineer / Data Scientist · MSc in Machine Learning on Texts and Graphs (with honours)**

[Русская версия ниже](#русская-версия)

I build ML systems end to end, from collecting the data to a measured model and a service that runs on its own. Behind it are nearly six years of applied practice in econometrics and financial analysis, so analytics and causal inference are part of the job too, from forecasts and price indices to event studies and difference-in-differences. Financial University under the Government of the Russian Federation, BSc in Economics and MSc in Applied Mathematics and Computer Science, both with honours. Two systems run daily on a schedule, a search service over Bank of Russia regulations and a panel of the Moscow rental market. Contributor to open-source LLM evaluation frameworks, 4 merged pull requests. Open to remote roles.

---

### Projects

| Project | What it is |
|---|---|
| [ru-fin-rag](https://github.com/nata2627/ru-fin-rag) | Search service over Bank of Russia regulations, [live demo](https://ru-fin-rag.onrender.com). 1,555 regulations and 62,606 chunks, refreshed by a nightly run. On 991 labelled queries hybrid search with cross-encoder reranking scores 0.704 NDCG@10 against 0.571 for BM25 (p < 0.001), a stemmer in BM25 tokenization added 0.087. FastAPI on the Render free tier, p50 470.6 ms and p95 669.3 ms from Moscow, 140-165 requests per second per process under locust with zero failures. Query log in ClickHouse with a 6-model dbt mart, vector stores compared (numpy, FAISS, Qdrant), int8 quantization costs 0.005 [0.001; 0.010], the Airflow DAG runs in a container in CI |
| [anglicism_detection](https://github.com/nata2627/anglicism_detection) | **Master's thesis.** Detecting and replacing anglicisms in Russian text. A custom corpus of 50,000+ units, XGBoost against RuRoBERTa-large and XLM-RoBERTa for detection (F1 0.988, ROC-AUC 0.999), fine-tuned Qwen2.5-1.5B-Instruct for rewriting (BLEU 0.807, ROUGE ≈ 0.870) |
| [msk-rent-market](https://github.com/nata2627/msk-rent-market) | Moscow rental market panel, [live dashboard](https://nata2627.github.io/msk-rent-market/). Daily CIAN collection since 22 Sep 2026, about 59 thousand listings and 586 thousand observations. The search is split recursively around the 1,512-listing cap with a daily completeness check, a watchdog reports eight failure types to Telegram. CatBoost fair price model against hedonic regression (MAPE 13.0% vs 17.6%) with 80% conformal intervals, retrained weekly in MLflow and served by the bot's `/price` command. Forecast backtest on 140 months of Rosstat data (random walk wins, MAPE 1.92% vs 2.70% for SARIMA), hedonic rent index, Kaplan-Meier listing lifetime, effects of price cuts. dbt marts, D3 dashboard on GitHub Pages, 471 tests in GitHub Actions |
| [moex-index-effect](https://github.com/nata2627/moex-index-effect) | What happens to a stock's price and liquidity when it enters or leaves the IMOEX index. 42 events over 2022-2026, market model and cumulative abnormal returns, nearest-neighbour matching, difference-in-differences on liquidity with a parallel trends test, randomization inference on 1,000 placebo dates, Holm and Benjamini-Hochberg corrections. No classic index effect, prices decline after inclusion instead, CAR −18.3% over 60 days, placebo p = 0.039, the sign holds in all 15 robustness checks |
| [ab-test](https://github.com/nata2627/ab-test) | Analysis of a randomized ad experiment on Criteo Uplift v2.1, about 14 million users. Power computed before the analysis and the analysis plan committed before any code read the outcomes. The randomization turned out to be conditional, so the naive difference overstates the effect by 40% (20 standard errors), and the main estimate is stratified by propensity, +0.740 p.p. on visits (95% CI 0.711-0.769). Peeking at 10 looks inflates A/A false positives to 21.2%, a group sequential test brings them back to 5.5% at a power cost of 1.0 p.p. CUPED narrows the interval by 10.4%, the effect of exposure is estimated with assignment as an instrument, and none of the uplift models passed the pre-registered acceptance rule against an outcome model |
| [moex-market-analytics](https://github.com/nata2627/moex-market-analytics) | Stock market data mart with all analytics in SQL. 46 index constituents, 47,672 price rows, `staging → core → marts`, window functions, CTEs, materialized views, beta computed two independent ways and cross-checked. A composite index chosen with `EXPLAIN ANALYZE` cut a market snapshot query from 1.031 to 0.223 ms, Metabase dashboard |
| [rbc.ru-category-classification](https://github.com/nata2627/rbc.ru-category-classification) | Classifying RBC news into seven sections. Custom scraper, 8,142 articles, four architectures. The simplest bag-of-words network came out best (79%), the recurrent one came last (70%) |

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

**Data and ML** pandas · numpy · statsmodels · scikit-learn · XGBoost · CatBoost · conformal prediction · MLflow · survival analysis (Kaplan-Meier) · entity resolution · graph ML (networkx, node embeddings) · matplotlib · seaborn · Jupyter

**Time series** ETS · SARIMA · STL · rolling-origin backtesting · price indices

**NLP and LLM** PyTorch · TensorFlow · transformers · datasets · accelerate · sentence-transformers · LLM fine-tuning and quantization (bitsandbytes, auto-gptq) · BM25, hybrid search and cross-encoders · retrieval and generation evaluation (NDCG, BLEU, ROUGE) · lm-evaluation-harness · LlamaIndex · Haystack · spaCy · nltk · natasha · Rasa

**Econometrics and causal inference** OLS with assumption diagnostics (autocorrelation, heteroskedasticity, multicollinearity) · hypothesis testing · hedonic regression · linear probability and hazard models · logit and probit · CAPM and beta · event study · difference-in-differences with fixed effects · matching · randomization inference and placebo tests · clustered standard errors · multiple testing corrections (Holm, Benjamini-Hochberg)

**Finance** DCF · multiples · fundamental and technical analysis

**SQL** window functions · CTE · materialized views · indexes and `EXPLAIN ANALYZE` · statistical aggregates

**Data and infrastructure** PostgreSQL · ClickHouse · MongoDB · Neo4j · ArangoDB · dbt · Airflow · FastAPI · Docker · Docker Compose · GitHub Actions · pytest · locust · Playwright · BeautifulSoup · Qdrant · FAISS · Metabase · Yandex DataLens · D3 · DVC · S3 · Render · Telegram Bot API · GigaChat API · Git · Excel

---

### Publications

Peer-reviewed journals from the Russian Higher Attestation Commission (VAK) list, indexed in RSCI.

- **Combating Insurance Fraud in the Digital Environment.** Samoupravlenie, 2023, No. 1 (134) · [elibrary](https://elibrary.ru/item.asp?id=50470488)
- **Analysis of the Unit Asking Price of One-Room Apartments in the Secondary Housing Market of Cheboksary**, with S. G. Sternik. Russian Economic Online Journal, 2022, No. 4 · [elibrary](https://elibrary.ru/item.asp?id=50243872)
- **The Impact of the COVID-19 Pandemic on the Financial Performance of Retail Companies.** Samoupravlenie, 2022, No. 4 (132) · [elibrary](https://elibrary.ru/item.asp?id=49288478)

Titles are translated, the papers are in Russian.


---

## Русская версия

### Наталия Гордеева

**ML-инженер / Data Scientist · магистратура «Машинное обучение на текстах и графах», с отличием**

Строю ML-системы целиком, от сбора данных до измеренной модели и сервиса, который работает сам. За этим почти шесть лет прикладной практики в эконометрике и финансовом анализе, поэтому аналитика и причинный вывод тоже моя работа, от прогнозов и индексов цен до event study и разности разностей. Финансовый университет при Правительстве РФ, бакалавриат «Экономика» и магистратура «Прикладная математика и информатика», оба диплома с отличием. Два контура работают каждый день по расписанию, сервис поиска по нормативным актам Банка России и панель рынка аренды Москвы. Контрибьютор открытых фреймворков для оценки языковых моделей, 4 принятых pull request. Рассматриваю удаленную работу.

---

#### Проекты

| Проект | Что это |
|---|---|
| [ru-fin-rag](https://github.com/nata2627/ru-fin-rag) | Сервис поиска по нормативным актам Банка России, [живая ссылка](https://ru-fin-rag.onrender.com). 1555 актов и 62 606 фрагментов, пополняется ночным прогоном. На 991 размеченном запросе гибрид с переранжированием кросс-энкодером дает 0,704 NDCG@10 против 0,571 у BM25 (p < 0,001), стеммер в токенизации BM25 прибавил 0,087. FastAPI на бесплатном тарифе Render, из Москвы p50 470,6 мс и p95 669,3 мс, под нагрузкой (locust) один процесс держит 140-165 запросов в секунду без отказов. Журнал запросов в ClickHouse с витриной из 6 моделей dbt, сравнение векторных хранилищ (numpy, FAISS, Qdrant), квантизация int8 стоит 0,005 [0,001; 0,010] качества, DAG на Airflow прогоняется в контейнере в CI |
| [anglicism_detection](https://github.com/nata2627/anglicism_detection) | **Магистерская работа.** Детекция и замена англицизмов в русских текстах. Собственный корпус на 50 000+ единиц, XGBoost против RuRoBERTa-large и XLM-RoBERTa на детекции (F1 0,988, ROC-AUC 0,999), дообученный Qwen2.5-1.5B-Instruct на перезаписи (BLEU 0,807, ROUGE ≈ 0,870) |
| [msk-rent-market](https://github.com/nata2627/msk-rent-market) | Панель рынка аренды Москвы, [витрина](https://nata2627.github.io/msk-rent-market/). Ежедневный сбор длительной аренды с ЦИАНа с 22.09.2026, около 59 тысяч объявлений и 586 тысяч наблюдений. Выдача рекурсивно делится на корзины в обход лимита 1512 объявлений, полнота сверяется каждый день, сторож пишет в телеграм о восьми видах сбоев. Справедливая цена на CatBoost против гедонической регрессии (MAPE 13,0% против 17,6%) с 80%-интервалом конформным предсказанием, переобучение раз в неделю с учетом в MLflow, отвечает в боте командой `/price`. Бэктест прогноза на 140 месяцах Росстата (выиграло случайное блуждание, MAPE 1,92% против 2,70% у SARIMA), гедонический индекс аренды, срок жизни объявления по Каплану-Мейеру, эффект снижения цены. Витрины в dbt, дашборд на D3 и GitHub Pages, 471 тест в GitHub Actions |
| [moex-index-effect](https://github.com/nata2627/moex-index-effect) | Что происходит с ценой и ликвидностью акции при включении в индекс IMOEX и исключении из него. 42 события за 2022-2026 годы, рыночная модель и накопленная аномальная доходность, матчинг по ближайшему соседу, разность разностей по ликвидности с проверкой параллельных трендов, рандомизационный вывод на 1000 плацебо-дат, поправки Холма и Бенджамини-Хохберга. Классического эффекта нет, зато после включения цена устойчиво снижается, CAR −18,3% за 60 дней, плацебо p = 0,039, знак держится во всех 15 проверках устойчивости |
| [ab-test](https://github.com/nata2627/ab-test) | Разбор рандомизированного рекламного эксперимента на Criteo Uplift v2.1, около 14 млн пользователей. Мощность посчитана до анализа, план анализа закоммичен раньше кода, который читает исходы. Рандомизация оказалась условной, простая разница завышает эффект на 40% (20 стандартных ошибок), поэтому основная оценка стратифицирована по склонности, +0,740 п. п. на визитах (95% ДИ 0,711-0,769). Подглядывание на 10 просмотрах поднимает ложные срабатывания A/A до 21,2%, последовательный тест возвращает их к 5,5% ценой 1,0 п. п. мощности. CUPED сужает интервал на 10,4%, эффект показа оценен с назначением как инструментом, ни одна uplift-модель не прошла заранее заданное правило приемки против модели исхода |
| [moex-market-analytics](https://github.com/nata2627/moex-market-analytics) | Витрина фондового рынка, вся аналитика в SQL. 46 бумаг индекса МосБиржи, 47 672 строки котировок, слои `staging → core → marts`, оконные функции, CTE, материализованные представления, бета двумя независимыми способами со сверкой. Составной индекс по `EXPLAIN ANALYZE` ускорил срез рынка с 1,031 до 0,223 мс, дашборд в Metabase |
| [rbc.ru-category-classification](https://github.com/nata2627/rbc.ru-category-classification) | Классификация новостей РБК по семи рубрикам. Собственный парсер, 8142 статьи, четыре архитектуры. Лучшей оказалась самая простая сеть на мешке слов (79%), рекуррентная заняла последнее место (70%) |

---

#### Вклад в открытые проекты

| Проект | Что это | Вклад |
|---|---|---|
| [EleutherAI/lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness/pulls?q=author%3Anata2627) | референсный фреймворк оценки языковых моделей | 2 PR приняты, 3 на ревью |
| [comet-ml/opik](https://github.com/comet-ml/opik/pulls?q=author%3Anata2627) | оценка и трассировка LLM-приложений | 2 PR приняты |
| [run-llama/llama_index](https://github.com/run-llama/llama_index/pulls?q=author%3Anata2627) | фреймворк для RAG и документных агентов | 2 PR на ревью |

---

#### Стек

**Языки** Python · SQL · R · LaTeX

**Данные и ML** pandas · numpy · statsmodels · scikit-learn · XGBoost · CatBoost · конформные интервалы · MLflow · анализ выживаемости (Каплан-Мейер) · дедупликация объектов · ML на графах (networkx, эмбеддинги вершин) · matplotlib · seaborn · Jupyter

**Временные ряды** ETS · SARIMA · STL · бэктест скользящим началом · индексы цен

**NLP и LLM** PyTorch · TensorFlow · transformers · datasets · accelerate · sentence-transformers · дообучение и квантизация LLM (bitsandbytes, auto-gptq) · BM25, гибридный поиск и кросс-энкодеры · оценка качества поиска и генерации (NDCG, BLEU, ROUGE) · lm-evaluation-harness · LlamaIndex · Haystack · spaCy · nltk · natasha · Rasa

**Эконометрика и причинный вывод** МНК с диагностикой предпосылок (автокорреляция, гетероскедастичность, мультиколлинеарность) · проверка гипотез · гедоническая регрессия · линейная вероятностная модель и модель риска · логит и пробит · CAPM и бета · event study · разность разностей с фиксированными эффектами · matching · рандомизационный вывод и плацебо-тесты · кластеризованные ошибки · поправки на множественность (Холм, Бенджамини-Хохберг)

**Финансы** DCF · мультипликаторы · фундаментальный и технический анализ

**SQL** оконные функции · CTE · материализованные представления · индексы и `EXPLAIN ANALYZE` · статистические агрегаты

**Данные и инфраструктура** PostgreSQL · ClickHouse · MongoDB · Neo4j · ArangoDB · dbt · Airflow · FastAPI · Docker · Docker Compose · GitHub Actions · pytest · locust · Playwright · BeautifulSoup · Qdrant · FAISS · Metabase · Yandex DataLens · D3 · DVC · S3 · Render · Telegram Bot API · GigaChat API · Git · Excel

---

#### Публикации

Журналы перечня ВАК, индексируются в РИНЦ.

- **Борьба со страховым мошенничеством в цифровой среде.** Самоуправление, 2023, № 1 (134) · [elibrary](https://elibrary.ru/item.asp?id=50470488)
- **Анализ удельной цены предложения однокомнатных квартир на вторичном рынке г. Чебоксары**, в соавторстве с С. Г. Стерником. Российский экономический интернет-журнал, 2022, № 4 · [elibrary](https://elibrary.ru/item.asp?id=50243872)
- **Анализ влияния пандемии COVID-19 на финансовые результаты компаний-ритейлеров.** Самоуправление, 2022, № 4 (132) · [elibrary](https://elibrary.ru/item.asp?id=49288478)

---

📫 gordeevanatalia04@gmail.com · Telegram [@daisy_nata](https://t.me/daisy_nata)
