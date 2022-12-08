# SimpleText@CLEF-2022 Tasks

[Home](./) | [Call for papers](./CFP) | [Important dates](./dates) | [Tasks](./tasks)  | [Tools](./tools) 
[Program](./program) | [Publications](./publications) | [Organisers](./organisers) | [Contact](./contact) | [CLEF-2023](https://simpletext-project.com/2023/clef)


---

## SimpleText Task Guidelines

We invite you to submit both automatic and manual runs! Manual intervention should be reported.

---

<button>[Access](./tasks)</button> | <button>[Shared task 1](./task1)</button> | <button>[Shared task 2](./task2)</button> | <button>[Shared task 3](./task3)</button>| <button>[Unshared task 4](./task4)</button>

<br>

## Task 2: What is unclear? Given a passage and a query, rank terms/concepts that are required to be explained for understanding this passage (definitions, context, applications,..).

The goal of this task is to decide which terms (up to 5) require explanation and contextualization to help a reader to understand a complex scientific text – for example, with regard to a query, terms that need to be contextualized (with a definition, example and/or use-case). 
For each passage, participants should provide a ranked list of difficult terms with corresponding scores on the scale 1-3 (3 to be the most difficult terms, while the meaning of terms scored 1 can be derived or guessed) and on the scale 1-5 (5 to be the most difficult terms). 
Passages (sentences) are considered to be independent, i.e. difficult term repetition is allowed. Term pooling and automatic metrics (accuracy of term binary classification, NDCG for term ranking, kappa statistics...) will be used to evaluate these results.

**Input format:** 
The train and the test data are provided in JSON and CSV formats with the following fields:
* `snt_id`: a unique passage (sentence) identifier
* `source_snt`: passage text
* `doc_id`: a unique source document identifier
* `query_id`: a query ID
* `query_text`: difficult terms should be extracted from sentences with regard to this query

*Input example:*

```
{"snt_id":"G06.2_2548923997_3",
"source_snt":"These communication systems render self-driving vehicles vulnerable to many types of malicious attacks, such as Sybil attacks, Denial of Service (DoS), black hole, grey hole and wormhole attacks.",
"doc_id":2548923997,
"query_id":"G06.2",
"query_text":"self driving"}
```

**Output format:** 

List of terms to be contextualized in a **JSON format** or a tabulated file TSV (for manual runs) with the following fields:
* `run_id`: Run ID starting with **team_id_task_id_**
* `manual`: Whether the run is manual {0,1}
* `snt_id`: a unique passage (sentence) identifier from the input file 
* `term`: Term or other phrase to be explained
* `term_rank_snt`: term difficulty rank within the given sentence
* `score_5`: term difficulty score on the scale from 1 to 5 (5 to be the most difficult terms)
* `score_3`: term difficulty score on the scale from 1 to 3 (3 to be the most difficult terms)

*Output example*:

```{json}
{"run_id":"NP_task_2_run1",
"manual":1,
"snt_id":"G06.2_2548923997_3",
"term":"black hole attack",
"term_rank_snt":1,
"score_5":5,
"score_3":3},

{"run_id":"NP_task_2_run1",
"manual":1,
"snt_id":"G06.2_2548923997_3",
"term":"grey hole attack",
"term_rank_snt":2,
"score_5":5,
"score_3":3},

{"run_id":"NP_task_2_run1",
"manual":1,
"snt_id":"G06.2_2548923997_3",
"term":"Sybil attack",
"term_rank_snt":3,
"score_5":5,
"score_3":3},

{"run_id":"NP_task_2_run1",
"manual":1,
"snt_id":"G06.2_2548923997_3",
"term":"wormhole attack",
"term_rank_snt":4,
"score_5":5,"score_3":3},

{"run_id":"NP_task_2_run1",
"manual":1,
"snt_id":"G06.2_2548923997_3",
"term":"Denial of service attack",
"term_rank_snt":5,
"score_5":4,
"score_3":3}
```

*Output format checker*

You can use this python3 script to check the output format. The script requires Python 3 and the Pandas library:
[Download python output checker](../check_format.py)

**Disclaimer:** By downloading and using these data, you agree to the terms of use. Any use of the data for any purpose other than academic research, would be in violation of the intended use of these data. 

Therefore, by downloading and using these data you give the following assurances with respect to the SimpleText data:
1. You will not use nor permit others to use the data in the SimpleText datasets in any way except for classes and academic research.
2. You will not at any time disclose, give, or transmit (in any manner or form or for any purpose) the data (or any portion thereof) to any location or person, including but not limiting to making the data available on the Internet, and copying the data onto any cloud-based storage system.
3. You will not release nor permit others to release the dataset or any part of it to any person. 

In case of violation of the conditions for access to the data for scientific purposes, this access may be withdrawn from the research entity and/or from the researcher. The research entity may also be liable to pay compensation for damages for third parties or asked to take disciplinary action against the offending researcher. 


### Evaluation
Term pooling and automatic metrics (accuracy of term binary classification, NDCG for term ranking, kappa statistics...) will be used to evaluate these results.

### Result submission:
Participants should put their run results into the folder Documents created for their user and **submit them by email** to *contact@simpletext-project.com*.

The email subject has to be in the format **\[CLEF TASK 2] TEAM_ID**. 

Runs should be submitted as a <ins>ZIP folder of the corresponding JSON files</ins>. Manual runs are allowed to be submitted in a CSV format. 

A confirmation email will be sent within 2 days after the submission deadline. 

## How to Cite
If you extend or use this work, please cite the [paper](https://doi.org/10.1007/978-3-031-13643-6_28) where it was introduced:
```
Liana Ermakova, Eric SanJuan, Jaap Kamps, Stéphane Huet, Irina Ovchinnikova, Diana Nurbakova, 
Sílvia Araújo, Radia Hannachi, Elise Mathurin, and Patrice Bellot. 2022. 
Overview of the CLEF 2022 SimpleText Lab: Automatic Simplification of Scientific Texts. 
In Experimental IR Meets Multilinguality, Multimodality, and Interaction: 13th International 
Conference of the CLEF Association, CLEF 2022, Bologna, Italy, September 5–8, 2022, Proceedings. 
Springer-Verlag, Berlin, Heidelberg, 470–494. https://doi.org/10.1007/978-3-031-13643-6_28
```
[Paper](https://doi.org/10.1007/978-3-031-13643-6_28)

[Dowload .BIB](../../BibTeX/ermakova_overview_2022.bib)
