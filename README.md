## Наталия Гордеева

**Прикладное машинное обучение и аналитика данных.**

Финансовый университет при Правительстве РФ: магистратура «Прикладная математика и информатика» по программе «Машинное обучение на текстах и графах» и бакалавриат «Экономика» по программе «Оценка бизнеса в цифровой экономике» — оба диплома с отличием.

В ML — полный исследовательский цикл: от сбора и разметки корпуса до дообучения языковой модели с измеримыми результатами. Контрибьютор открытых фреймворков для оценки языковых моделей и построения RAG. Отдельно — шесть лет прикладной аналитической практики: эконометрическое моделирование, причинный вывод на рыночных данных, оценка бизнеса, анализ ценных бумаг.

---

### Чем занимаюсь

**NLP и языковые модели.** Дообучение LLM, детекция и классификация текста, оценка качества генерации. Магистерская работа — гибридная трёхэтапная модель детекции и замены англицизмов в русскоязычных текстах: собственный корпус на 50 000+ единиц, XGBoost для детекции (F1 0.9884, ROC-AUC 0.999), дообученный Qwen2.5-1.5B-Instruct для перезаписи (BLEU 0.807, ROUGE ≈ 0.870).

**Эконометрика и финансы.** Регрессионный анализ с полной диагностикой предпосылок Гаусса—Маркова, проверка гипотез, прогнозирование с валидацией на контрольной выборке, модели бинарного выбора, CAPM и расчёт беты. Оценка бизнеса методом DCF с самостоятельным обоснованием ставок дисконтирования, сравнительный подход на мультипликаторах, фундаментальный и технический анализ акций.

**Причинный вывод (causal inference) на рыночных данных.** Event study: market model, abnormal и cumulative abnormal returns (CAR). Difference-in-differences с контрольной группой по nearest-neighbor matching и формальной проверкой parallel trends. Randomization inference, placebo-тесты, clustered standard errors, поправки на множественность (Holm, Benjamini—Hochberg).

**Данные и SQL.** Проектирование схем, ETL, аналитические витрины на PostgreSQL: оконные функции, оптимизация по плану запроса, дашборды.

**Открытый код.** Контрибьютор фреймворков для оценки языковых моделей и RAG: три принятых pull request, ещё восемь на ревью.

---

### Вклад в открытые проекты

| Проект | Что это | Вклад |
|---|---|---|
| [EleutherAI/lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness/pulls?q=author%3Anata2627) | Референсный фреймворк оценки языковых моделей | 2 PR приняты, 3 на ревью |
| [comet-ml/opik](https://github.com/comet-ml/opik/pulls?q=author%3Anata2627) | Платформа оценки и трассировки LLM-приложений | 1 PR принят, 1 на ревью |
| [run-llama/llama_index](https://github.com/run-llama/llama_index/pulls?q=author%3Anata2627) | Фреймворк для RAG и документных агентов | 3 PR на ревью |
| [deepset-ai/haystack](https://github.com/deepset-ai/haystack/pulls?q=author%3Anata2627) | Оркестрация LLM-пайплайнов | 1 PR на ревью |

---

### Избранные репозитории

**[moex-index-effect](https://github.com/nata2627/moex-index-effect)** — event study индексного эффекта на Московской бирже: что происходит с ценой и ликвидностью акции при включении в индекс IMOEX и исключении из него. 42 события за 2022–2026, market model и накопленная аномальная доходность (CAR), контрольная группа по nearest-neighbor matching, difference-in-differences по ликвидности, randomization inference на 1000 плацебо-дат, 15 проверок устойчивости (robustness), 39 тестов. Результат показан как есть, включая отрицательный: классического эффекта нет, зато после включения цена устойчиво снижается — CAR −18.3% за 60 дней, placebo p = 0.039.
`pandas` `statsmodels` `event study` `difference-in-differences` `matching` `causal inference`

**[moex-market-analytics](https://github.com/nata2627/moex-market-analytics)** — витрина аналитики российского фондового рынка на данных Московской биржи. Вся аналитика в SQL: оконные функции, CTE, материализованные представления, оптимизация по плану запроса. 46 бумаг, 47 672 строки котировок, архитектура `staging → core → marts`, дашборд в Metabase.
`PostgreSQL` `SQL` `Docker` `Metabase` `ETL`

**[anglicism_detection](https://github.com/nata2627/anglicism_detection)** — гибридная модель детекции и замены англицизмов. Магистерская работа: парсинг корпуса, разметка, сравнение классических алгоритмов с трансформерами (RuRoBERTa-large, XLM-RoBERTa), дообучение Qwen, оценка по BLEU/ROUGE.
`PyTorch` `transformers` `XGBoost` `natasha` `hydra`

**[rbc.ru-category-classification](https://github.com/nata2627/rbc.ru-category-classification)** — классификация новостей РБК по семи рубрикам. Собственный парсер, 8142 статьи, сравнение четырёх архитектур. Лучшей оказалась самая простая: рубрика определяется словарём, а не порядком слов.
`TensorFlow` `scikit-learn` `BeautifulSoup`

**[anglicism_detection — детекция ИИ-текста](https://github.com/nata2627/anglicism_detection)** — исследование отличимости машинно-сгенерированного текста на русском: собственный корпус 5080 документов (37 млн знаков), XLM-RoBERTa, ROC-AUC 0.906. Главная находка — детектор выучивает синтаксис, а не лексику: при замене синонимами пропускается 60% машинных фрагментов.
`PyTorch` `transformers` `llama.cpp` `pymorphy3`

**[pabd24](https://github.com/nata2627/pabd24)** — учебный проект по прикладному анализу больших данных: полный ML-цикл от парсинга ЦИАН до сервиса предсказания цен. DVC, S3, Docker, тесты.
`DVC` `Docker` `S3` `Flask`

**[gbd](https://github.com/nata2627/gbd)** — машинное обучение на графах: метрики, эмбеддинги вершин, предсказание свойств вершин на `ogbn-arxiv` (Open Graph Benchmark).
`Python` `networkx` `ogb`

**[rasa_bot](https://github.com/nata2627/rasa_bot)** — диалоговый бот на Rasa: интенты, домен, кастомные actions, тесты.
`Rasa` `Python`

---

### Стек

**Языки** Python · SQL · R · LaTeX

**Данные и ML** pandas · numpy · statsmodels · scikit-learn · XGBoost · matplotlib · seaborn

**Глубокое обучение и NLP** PyTorch · TensorFlow · transformers · datasets · accelerate · sentence-transformers · spaCy · nltk · natasha · дообучение и квантизация LLM

**Эконометрика** МНК (OLS) · диагностика предпосылок Гаусса—Маркова · логит/пробит · проверка гипотез · корреляционный анализ · эластичности · CAPM и расчёт беты · event study · difference-in-differences с fixed effects · matching · randomization inference · clustered standard errors · multiple testing correction (Holm, Benjamini—Hochberg)

**Финансы** DCF · мультипликаторы · оценка бизнеса · фундаментальный и технический анализ

**Базы данных** PostgreSQL · оконные функции и рамки окна · CTE · материализованные представления · индексы и `EXPLAIN ANALYZE` · MongoDB · ArangoDB · графовые БД

**Инструменты** Git · Jupyter · Docker · Docker Compose · Metabase · DVC · S3 · FastAPI · Excel

---

### Публикации

- **Борьба со страховым мошенничеством в цифровой среде** — Самоуправление, 2023, № 1 (134) · [elibrary](https://elibrary.ru/item.asp?id=50470488)
- **Анализ удельной цены предложения однокомнатных квартир на вторичном рынке г. Чебоксары** (в соавт. с С. Г. Стерником) — Российский экономический интернет-журнал, 2022, № 4 · [elibrary](https://elibrary.ru/item.asp?id=50243872)
- **Анализ влияния пандемии COVID-19 на финансовые результаты компаний-ритейлеров** — Самоуправление, 2022, № 4 (132) · [elibrary](https://elibrary.ru/item.asp?id=49288478)

---

📫 gordeevanatalia04@gmail.com
