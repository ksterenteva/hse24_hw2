# hse24_hw2
  
**Ссылки на google colab ноутбуки**

1. [Подготовка файлов для аннотации](https://colab.research.google.com/drive/1-gj9S3eBJtkiQWIH5y0dANXBHm5PocDL#scrollTo=XFN9gII7MfIn)

На данном этапе проводилось:
- предсказание генов (genes.fasta, proteins.fasta, gms2.lst)
- определение функций белков через сравнение с бактерией MIL-1 (создание BLAST-базы данных из аннотированных белков T. oleivorans MIL-1 и сопоставление наших предсказанных белков с данной базой) (scaffolds.hits_from_MIL_1.txt)
- Анализ совпадений и отсутствие аннотаций с белками MIL-1 (proteins.with_hits_from_MIL_1.txt) и (в proteins.without_MIL_1.fasta).
- Аннотация белков через базу данных SwissProt (scaffolds.hits_from_SwissProt.txt)

2. [Cоздание аннотированного генома бактерии в формате GenBank](https://colab.research.google.com/drive/1IX2W-IT90JuH-ItU1CQsLPguZ8pc0QJp#scrollTo=0DzhOFoAQ-KL)

- Создание словаря скаффолдов (scaffolds-3.fasta) и добавление основной информации (тип молекулы, текущая дата и категория данных) и сохранение в словаре scaffolds
- Добавление аннотации для каждого гена (координаты, ориентация и аминокислотнаяь последовательность) с использованием файла proteins.fasta
- Добавление функций белков с использованием данных MIL-1 (T_oleivorans_MIL_1.gbk) и файл совпадений scaffolds.hits_from_MIL_1.txt
- Добавление функций белков с SwissProt (uniprot_sprot.dat)
- Сохранение аннотированного генома в файл GENOME.gbk

   
3. [Бонус - предсказание рРНК (5S, 16S, 23S)](https://colab.research.google.com/drive/1joaXA5R_j4_CtZyt_ybwIfIBTdRDIoJG#scrollTo=whfMt6HnX6w2)

- Извлечение данных рРНК из генома MIL-1 с помощью файла (T_oleivorans_MIL_1.gbk)
- Формирование FASTA файла рРНК (файл resSeq.fasta)
- BLAST-сравнение (файл Data_inform.gbk)
- Анализ результатов BLAST - нахождение процента идентичности 

**Статистика по предсказанным и аннотированным генам**

<ins>Сколько было предсказано генов всего: 3607</ins>

На самом деле в геноме *Thalassolituus oleivorans* MIL-1 (по **GenBank,** https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_000355675.1/) содержится 3728 генов, из которых 3662 кодируют белки, а остальные 66 представлены РНК-генами (включая гены рРНК)

Предсказанные генов составляют 96.8% от общего числа известных. Это достаточно высокий уровень точности предсказания. Недостаток в 121 ген может объясняться несколькими причинами: неточность в сборке генома данной бактерии (неполное покрытие ридами или недостаточное их качество, ошибки секвенирование, ограничения в алгоритмах сборки), таких как особенности алгоритма аннотации, небольшие различия в версиях генома или возможные ошибки сборки и аннотации.


<ins>Сколько из них удалось аннотировать с помощью сравнения с бактерией MIL-1: 3325</ins>

<ins>Какое кол-во белков остались без аннотации функции: 282</ins>


92% генов успешно аннотированы на основе сходства с генами MIL-1. Это хороший результат, так как означает высокую степень консервативности между этими штаммами и достаточное качество предсказания генов. Оставшиеся 8% могут быть опосредованны контаминацией (загрязнение ДНК), это вполне возможно так как мы собирали геном бактерии, выделенной из воды с нефтью, на основании ридов (paired-end  и  mate-pairs), то есть помимо ДНК относящейся к данной бактерии могли захватить и ДНК другого организма или это могло произойти в лаборатории. 


<ins>Сколько с помощью БД SwissProt: 54</ins>

SwissProt ориентирован на высококачественные аннотации из широко изученных организмов, вероятно, многие бактериальные гены не имеют аналогов в этой базе данных. Аннотированные 54 гена в SwissProt скорее всего являются высококонсервативными белками с важными функциями, которые присутствуют и в других организмах, поэтому их удалось идентифицировать.


<ins>% сходства между соответствующими рРНК</ins>

Resemblance rRna 341494...343033
For seq = scaffold73_cov665  percents : ['100%'] 

For seq = scaffold3_cov273  percents : ['100%'] 

Resemblance rRna 341494...343033
For seq = scaffold69_cov665  percents : ['100%'] 

For seq = scaffold68_cov665  percents : ['100%'] 

For seq = scaffold70_cov714  percents : ['100%'] 

Resemblance rRna 341494...343033
For seq = scaffold69_cov665  percents : ['100%'] 

For seq = scaffold3_cov273  percents : ['100%'] 

Resemblance rRna 341494...343033
For seq = scaffold69_cov665  percents : ['99%'] 

For seq = scaffold3_cov273  percents : ['97%'] 

Resemblance rRna 341494...343033
For seq = scaffold69_cov665  percents : ['100%'] 

For seq = scaffold68_cov665  percents : ['100%'] 

For seq = scaffold70_cov714  percents : ['100%'] 

Resemblance rRna 341494...343033
For seq = scaffold73_cov665  percents : ['99%'] 

For seq = scaffold3_cov273  percents : ['100%'] 

Resemblance rRna 341494...343033
For seq = scaffold69_cov665  percents : ['100%'] 

For seq = scaffold3_cov273  percents : ['100%'] 

Resemblance rRna 341494...343033
For seq = scaffold69_cov665  percents : ['100%'] 

For seq = scaffold68_cov665  percents : ['100%'] 

For seq = scaffold70_cov714  percents : ['100%'] 

Resemblance rRna 341494...343033
For seq = scaffold73_cov665  percents : ['99%'] 

For seq = scaffold3_cov273  percents : ['100%'] 

Resemblance rRna 341494...343033
For seq = scaffold69_cov665  percents : ['100%'] 

For seq = scaffold3_cov273  percents : ['100%'] 

Resemblance rRna 341494...343033
For seq = scaffold69_cov665  percents : ['100%'] 

For seq = scaffold68_cov665  percents : ['100%'] 

For seq = scaffold70_cov714  percents : ['100%'] 


