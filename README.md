# MorphemicEmbeddings

Морфемные эмбеддинги для редких слов на основе однокоренных.
Оценивание эмбеддингов осуществляется на задаче определения семантической близости пар слов.

**Файловая структура репозитория:**
	**RareWordMoprhemicEmbeddings.ipynb** - основной файл. Создаются морфемные эмбеддинги для редких слов на основе однокоренных. Оценивание эмбеддингов осуществляется на задаче определения семантической близости пар слов.
- папка **Data** содержит списки слов, которые подвергаются морфемному анализу:
	- **word2vec_RNC_vocab.txt** - список слов из предобученной word2vec модели, обученной на Национальном корпусе русского языка (https://ruscorpora.ru)
	- **word2vec_Araneum_vocab.txt** - список слов из предобученной word2vec модели, обученной на веб-корпусе Araneum (http://ucts.uniba.sk)
	- **word2vec_Tayga_vocab.txt** - список слов из предобученной word2vec модели, обученной на веб-корпусе Tayga (https://tatianashavrina.github.io/taiga_site)
	- **rare_words_RNC.txt** - список слов, которые отсутствуют в словаре модели, обученной на Национальном корпусе русского языка, но присутствуют в датасетах для оценивания семантической близости
	- **rare_words_Araneum.txt** - список слов, которые отсутствуют в словаре модели, обученной на веб-корпусе Araneum, но присутствуют в датасетах для оценивания семантической близости
	- **rare_words_Tayga.txt** - список слов, которые отсутствуют в словаре модели, обученной на веб-корпусе Tayga, но присутствуют в датасетах для оценивания семантической близости
Предобученные модели морфемного анализа берутся с сайта https://rusvectores.org/ru/.
- папка **MorphLists** содержит списки аффиксов, составленные на основе (Русская грамматика, 1980):
	- **prefixes.txt** - список окончаний
	- **interfixes.txt** - список интерфиксов
	- **suffixes_derivational.txt** - список словообразовательных суффиксов
	- **suffixes_inflectional.txt** - список словоизменительных суффиксов
	- **endings.txt** - список окончаний
	- **postfixes.txt** - список постфиксов
- папка **MorfessorMorphSegm** содержит предобученные модели морфемного анализа Morfessor и результаты морфемного анализа. Метод предложен (Smit P., Virpioja S., Grönroos S.A., Kurimo M. Morfessor 2.0: Toolkit for statistical morphological segmentation 2013; Virpioja S., Smit P., Grönroos S.A., Kurimo M. Morfessor 2.0: Python implementation and extensions for Morfessor Baseline. 2013):
	- папка **models** - модели морфемного анализа Morfessor
	- папка **results** - результаты морфемного анализа, полученные с помощью этих моделей
- папка **NeuralMorphSegm** содержит предобученные модели морфемного анализа на основе свёрточных нейронных сетей и результаты морфемного анализа. Метод предложен (Sorokin A., Kravtsova A. Deep Convolutional Networks for Supervised Morpheme Segmentation of Russian Language. 2018; https://github.com/AlexeySorokin/NeuralMorphemeSegmentation)
	- папка **config** - конфигурации для обучения моделей морфемного анализа
	- папка **models** - модели морфемного анализа на основе свёрточных нейронных сетей
	- папка **results** - результаты морфемного анализа, полученные с помощью этих моделей
- папка **SemanticSimilarity** содержит датасеты для оценивания семантической близости и результаты определения семантической близости для пар слов:
	- **rare_multimorphemic.tsv** - датасет для определения семантической близости пары слов на редких многоморфемных словах (Sadov M.A., Kutuzov A.B. Use of Morphology in Distributional Word Embedding Models: Russian Language Case. 2018. http://www.dialog-21.ru/media/4554/sadovmapluskutuzovab.pdf; https://github.com/sadov-m/DSM_morphology)
	датасеты с соревнования RUSSE-2015 в рамках конференции "Диалог"(Panchenko A., Loukachevitch N. V., Ustalov D., Paperno D., Meyer C. M., Konstantinova N. RUSSE: The First Workshop on Russian Semantic Similarity. 2015)
		- **ae-test.csv**, **ae2-test.csv** - для каждой пары слов указано, есть ли между ними ассоциативная связь
		- **hj-test.csv** - для каждой пары слов указаны экспертные оценки их семантической близости
		- **rt-test.csv** - для каждой пары слов указано, есть ли между ними синонимические или гипо-гиперонимические отношения
	- **rare_multimorphemic_tagged.tsv**, **ae-test_tagged.csv**, **ae2-test_tagged.csv**, **hj-test_tagged.csv**, **rt-test_tagged.csv** - те же данные, только к словам добавлены частеречные теги с помощью (https://github.com/deepmipt/DeepPavlov)
	- остальные файлы в папке имеют вид **{модель эмбеддингов}-{корпус, на котором обучена модель эмбеддингов}-{модель морфемного анализа}-{датасет для определения семантической близости} results.tsv** и представляют собой результаты для определения семантической близости пар слов.
