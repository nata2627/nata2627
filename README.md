## Nataliia Gordeeva

**Data analytics, econometrics and applied machine learning**

[Русская версия ниже](#русская-версия)

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

## Русская версия

### Наталия Гордеева

**Аналитика данных, эконометрика и прикладное машинное обучение**

Финансовый университет при Правительстве РФ. Бакалавриат «Экономика» по программе «Оценка бизнеса в цифровой экономике» и магистратура «Прикладная математика и информатика» по программе «Машинное обучение на текстах и графах», оба диплома с отличием.

Почти шесть лет прикладной аналитической практики в эконометрике и финансовом анализе. В ML у меня законченный цикл от сбора корпуса до дообучения языковой модели с измеренным результатом. Сейчас держу два работающих контура, ежедневный сбор рынка аренды Москвы и сервис поиска по нормативным актам Банка России. Контрибьютор открытых фреймворков для оценки языковых моделей, 4 принятых pull request.

---

#### Избранные репозитории

**[msk-rent-market](https://github.com/nata2627/msk-rent-market)** · панель рынка аренды Москвы · [витрина](https://nata2627.github.io/msk-rent-market/)
Ежедневный сбор длительной аренды с ЦИАНа с 22.09.2026, около 59 тысяч объявлений и 586 тысяч наблюдений. Площадка отдает не больше 1512 объявлений на запрос, поэтому выдача рекурсивно делится на корзины, и полнота каждой корзины сверяется каждый день. Сторож проверяет прогон каждые 20 минут и сам пишет в телеграм о восьми видах сбоев. За первый месяц 15 дней спасены автоматическим перезапуском, после каждой аварии в коде появилась проверка. Что посчитано на панели:
- **Прогноз.** Случайное блуждание, сезонный наивный, ETS и SARIMA в бэктесте скользящим началом на 140 месяцах Росстата. Правило выбора запушено до первого расчета, выиграло случайное блуждание (MAPE 1,92% против 2,70% у SARIMA)
- **Индекс аренды.** Гедонический индекс дает −0,49% за месяц, цепной на тех же объявлениях −5,7%, и он меряет старение объявления, рынок почти стоит
- **Справедливая цена.** CatBoost против гедонической регрессии, разбиение по времени и по группам дублей, MAPE 13,0% против 17,6%, 80%-интервал конформным предсказанием. Переобучение раз в неделю с учетом в MLflow, отвечает в боте командой `/price`
- **Снижение цены.** Агентства снижают на 9 п.п. чаще собственников, поправки разрыв почти не двигают. Снизившие уходят с рынка на 6-11% быстрее похожих. Плацебо из протокола оказалось ошибочным и исправлено, оценка признана неустойчивой
- **Срок жизни объявления.** Медиана 14 дней, Каплан-Мейер с поздним вхождением
- **Животные.** Разрешение цену не меняет (−0,3% [−1,1; +0,6]), прямой запрет дает скидку 2,8%

Витрины в dbt, связывание дублей между агентствами, витрина на D3 и GitHub Pages, 471 тест в GitHub Actions.
`PostgreSQL` `dbt` `Playwright` `statsmodels` `CatBoost` `MLflow` `D3` `Docker`

**[ru-fin-rag](https://github.com/nata2627/ru-fin-rag)** · сервис поиска по нормативным актам Банка России · [живая ссылка](https://ru-fin-rag.onrender.com)
Корпус 1555 актов и 62 606 фрагментов, пополняется ночным прогоном по расписанию. Качество поиска измерено на 991 размеченном запросе. Гибрид с переранжированием кросс-энкодером дает 0,704 NDCG@10 против 0,571 у BM25, p < 0,001, а стеммер в токенизации BM25 прибавил 0,087. API на FastAPI развернут на бесплатном тарифе Render, из Москвы p50 470,6 мс и p95 669,3 мс. Под нагрузкой (locust) один процесс держит 140-165 запросов в секунду без отказов. Журнал запросов пишется событием, поверх него витрина из 6 моделей dbt на ClickHouse. Сравнила векторные хранилища (numpy, FAISS, Qdrant встроенный и по сети) и квантизацию int8, потеря качества 0,005 [0,001; 0,010]. DAG регламента на Airflow прогоняется в контейнере в CI.
`FastAPI` `BM25` `cross-encoder` `ClickHouse` `dbt` `Airflow` `Qdrant` `FAISS` `Docker`

**[moex-index-effect](https://github.com/nata2627/moex-index-effect)** · индексный эффект на Московской бирже
Что происходит с ценой и ликвидностью акции при включении в индекс IMOEX и исключении из него. 42 события за 2022-2026 годы, рыночная модель и накопленная аномальная доходность, контрольная группа матчингом по ближайшему соседу, разность разностей по ликвидности с формальной проверкой параллельных трендов, рандомизационный вывод на 1000 плацебо-дат, поправки Холма и Бенджамини-Хохберга. Классического эффекта нет, зато после включения цена устойчиво снижается, CAR −18,3% за 60 дней, плацебо p = 0,039. Знак держится во всех 15 проверках устойчивости, 39 тестов.
`pandas` `statsmodels` `event study` `difference-in-differences` `matching`

**[moex-market-analytics](https://github.com/nata2627/moex-market-analytics)** · витрина фондового рынка, вся аналитика в SQL
46 бумаг индекса МосБиржи, 47 672 строки котировок, слои `staging → core → marts`. Оконные функции, CTE, материализованные представления, бета двумя независимыми способами со сверкой. Составной индекс по `EXPLAIN ANALYZE` ускорил срез рынка с 1,031 до 0,223 мс. Дашборд в Metabase.
`PostgreSQL` `SQL` `Docker` `Metabase` `ETL`

**[anglicism_detection](https://github.com/nata2627/anglicism_detection)** · магистерская работа
Детекция и замена англицизмов в русских текстах. Собственный корпус на 50 000+ единиц, XGBoost против RuRoBERTa-large и XLM-RoBERTa на детекции (F1 0,988, ROC-AUC 0,999), дообученный Qwen2.5-1.5B-Instruct на перезаписи (BLEU 0,807, ROUGE ≈ 0,870).
`PyTorch` `transformers` `XGBoost` `natasha` `hydra`

**[rbc.ru-category-classification](https://github.com/nata2627/rbc.ru-category-classification)** · классификация новостей РБК по семи рубрикам
Собственный парсер, 8142 статьи, четыре архитектуры. Лучшей оказалась самая простая сеть на мешке слов (79%), рекуррентная заняла последнее место (70%). Рубрику определяет словарь, порядок слов почти ничего не добавляет.
`TensorFlow` `scikit-learn` `BeautifulSoup`

Еще [pabd24](https://github.com/nata2627/pabd24) (учебный ML-сервис прогноза цен, DVC, S3, Docker), [gbd](https://github.com/nata2627/gbd) (машинное обучение на графах, `ogbn-arxiv`), [rasa_bot](https://github.com/nata2627/rasa_bot), [youtube-subs](https://github.com/nata2627/youtube-subs).

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

**Данные и ML** pandas · numpy · statsmodels · scikit-learn · XGBoost · CatBoost · конформные интервалы · MLflow · анализ выживаемости · дедупликация объектов

**Временные ряды** ETS · SARIMA · STL · бэктест скользящим началом · индексы цен

**NLP и LLM** PyTorch · TensorFlow · transformers · sentence-transformers · дообучение и квантизация LLM · BM25, гибридный поиск и кросс-энкодеры · оценка качества поиска и генерации

**Эконометрика и причинный вывод** МНК с диагностикой предпосылок · логит и пробит · CAPM · event study · разность разностей с фиксированными эффектами · matching · рандомизационный вывод · кластеризованные ошибки · поправки на множественность

**Финансы** DCF · мультипликаторы · фундаментальный и технический анализ

**Данные и инфраструктура** PostgreSQL · ClickHouse · dbt · Airflow · FastAPI · Docker · GitHub Actions · Playwright · Qdrant · FAISS · Metabase · D3 · DVC · Excel

---

#### Публикации

Журналы перечня ВАК, индексируются в РИНЦ.

- **Борьба со страховым мошенничеством в цифровой среде.** Самоуправление, 2023, № 1 (134) · [elibrary](https://elibrary.ru/item.asp?id=50470488)
- **Анализ удельной цены предложения однокомнатных квартир на вторичном рынке г. Чебоксары**, в соавторстве с С. Г. Стерником. Российский экономический интернет-журнал, 2022, № 4 · [elibrary](https://elibrary.ru/item.asp?id=50243872)
- **Анализ влияния пандемии COVID-19 на финансовые результаты компаний-ритейлеров.** Самоуправление, 2022, № 4 (132) · [elibrary](https://elibrary.ru/item.asp?id=49288478)

---

📫 gordeevanatalia04@gmail.com · Telegram [@daisy_nata](https://t.me/daisy_nata)
