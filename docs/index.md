# Text Complexity DE Challenge 2022


Text forms an integral part of exchanging information and interacting with the world, correlating with quality and experience of life. Text readability is one of the factors which affects a reader's understanding of a text. The mapping of a body of text to a mathematical unit quantifying the degree of readability is the basis of readability assessment. This quantified unit is significant in informing the reader about how difficult the text content is to read. Readability assessment has diverse use cases and applications, such as helping to choose appropriate learning material for second language learners, people with disabilities, and providing targeted content for various groups in the general population (e.g. against misinformation). As readability might be influenced by representation, we only target the text complexity for readers in this task. Furthermore, a reliable text complexity estimator can be used to automatically evaluate simplified text (produced by authors or automatic simplifiers). 

This task consists of developing machine learning based regression models to predict the complexity of a sentence in German for German learners in the B level. We encourage participants to train deep learning based models since they show better performance in similar tasks.

We will use Codalab to organize the challenge. The Codalab competition page will be up on 20th April 2022.

[codalab](https://codalab.lisn.upsaclay.fr/competitions/4964){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }


## Timeline
- **<strike>Trial data ready: April 11th, 2022</strike>** see [below](#trial-data)
- **<strike>Training data ready: May 16th, 2022</strike>** download from [here](https://raw.githubusercontent.com/babaknaderi/TextComplexityDE/master/TextComplexityDE19/ratings.csv)
- **<strike>Baseline model ready: May 23rd, 2022</strike>** see [here](https://codalab.lisn.upsaclay.fr/competitions/4964#results)
- **<strike>Test data ready: June 20th, 2022</strike>**
- **<strike>Evaluation starts: June 27th, 2022</strike>**
- **<strike>Evaluation end: July 4th, 2022</strike>** see [below](#results)
- Paper submission due: July 25nd, 2022 (extended)
- Camera ready due: August 15th, 2022
- KONVENS conference: September 12th-15th, 2022

## Data

The [TextComplexityDE](https://github.com/babaknaderi/TextComplexityDE) dataset [1] will be used for this task which includes about 1000 sentences in German that were taken from 41 Wikipedia articles in different article genres. 
Overall, the readability ratings were taken from multiple groups of German learners who participated in the subjective study. They mostly had German language levels between A2 and B.
During the subjective test, participants rated the complexity, understandability, and lexical difficulty of each sentence on 7 point Likert-scales:

 - **Complexity:** How do you rate the complexity of the sentence? Scale from _very easy (1)_ to _very complex (7)_.
 - **Understandability**: How well were you able to understand the sentence? Scale from _fully understood (1)_ to _didn't understand at all (7)_.
 - **Lexical difficulty**: Regarding the hardest words in the sentence: How difficult is it to you, to understand these words? Scale from _very easy (1)_ to _very difficult (7)_.
 - 
After the data cleansing, we calculated the arithmetic mean of ratings from all participants for each sentence, creating the **Mean Opinion Score (MOS)** for each scale. Further details about the dataset and the subjective testing can be found in [1].
In the proposed task for KONVENS 2022, participants should train models that predict the MOS complexity of sentences in the test dataset. A test dataset includes 300 sentences. We conduct subjective tests with German learners to collect subjective MOS scores for the test dataset. 

### Trial Data
<table>
<colgroup>
<col width="80%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Sentence</th>
<th>Complexity score</th>
</tr>
</thead>
<tbody>
<tr>
<td markdown="span">Als Nebenprodukt entstand damals natürlich auch die erste Seifenblase.</td>
<td markdown="span">1.60</td>
</tr>
<tr>
<td markdown="span">Griechische ärzte wandten bereits Hydrotherapie an, die sie von den ägyptern  übernommen hatten.</td>
<td markdown="span">2.13</td>
</tr>
<tr>
<td markdown="span">In Abgrenzung zum klassischen Rasiermesser wird ein Rasiermesser mit Wechselklinge als Shavette bezeichnet.</td>
<td markdown="span">3.25</td>
</tr>
<tr>
<td markdown="span">In Pompeji gefundene Exemplare von frühen Klapp-Rasiermessern mit 12 Zentimeter langen trapezförmigen Klingen und Griffen aus Elfenbein gehörten als Luxusobjekte zum Hausstand höherer Schichten.</td>
<td markdown="span">4.36</td>
</tr>
</tbody>
</table>


## Evaluation

The blind test dataset will be published on June 20th, 2022. Each participating team has to submit the result of their prediction until July 4th 2022. The participating teams will submit the ID and predicted scores for the complexity of sentences in the test set. The Root Mean Squared Error (RMSE) after 3rd order mapping  will be used to measure errors (accuracy) of submissions compared to the subjective ratings.  RMSE is the standard deviation of the prediction errors, which is the difference of predicted values from actual values.

Due to bias or offsets, different gradients and different qualitative rank orders are always present in subjective evaluations. The statistical uncertainty always exists in the collected MOS. Therefore, a third-order polynomial function is applied to compensate for the possible variance between several subjective experiments in this challenge. For each model, we create one mapping function per test dataset. Then the mapped predictions were used to calculat the RMSE.


## Results
The table contains the best result of each team on the test dataset. The teams are ranked based on RMSE_MAPPED evaluation metric.

<table>
<colgroup>
<col width="20%" />
<col width="30%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Rank</th>
<th>Team name</th>
<th>RMSE MAPPED</th>
<th>RMSE</th>
</tr>
</thead>
<tbody>
<tr>
<td markdown="span">1</td>
<td markdown="span">Alejandro Mosquera</td>
<td markdown="span">0.430</td>
<td markdown="span">0.449</td>
</tr>
<tr>
<td markdown="span">2</td>
<td markdown="span">AComplexity</td>
<td markdown="span">0.435</td>
<td markdown="span">0.442</td>
</tr>
<tr>
<td markdown="span">3</td>
<td markdown="span">HIIG</td>
<td markdown="span">0.446</td>
<td markdown="span">0.462</td>
</tr>
<tr>
<td markdown="span">4</td>
<td markdown="span">TUM Social Computing</td>
<td markdown="span">0.449</td>
<td markdown="span">0.466</td>
</tr>
<tr>
<td markdown="span">5</td>
<td markdown="span">deepset</td>
<td markdown="span">0.454</td>
<td markdown="span">0.484</td>
</tr>
<tr>
<td markdown="span">6</td>
<td markdown="span">TUMuch Complexity</td>
<td markdown="span">0.457</td>
<td markdown="span">0.489</td>
</tr>
<tr>
<td markdown="span">7</td>
<td markdown="span">HHUplexity</td>
<td markdown="span">0.473</td>
<td markdown="span">0.486</td>
</tr>
<tr>
<td markdown="span">8</td>
<td markdown="span">CCL</td>
<td markdown="span">0.516</td>
<td markdown="span">0.586</td>
</tr>
<tr>
<td markdown="span">9</td>
<td markdown="span">BBAW Zentrum Sprache</td>
<td markdown="span">0.553</td>
<td markdown="span">0.583</td>
</tr>
<tr>
<td markdown="span">10</td>
<td markdown="span">LGirrbach</td>
<td markdown="span">Error</td>
<td markdown="span">Error</td>
</tr>
</tbody>
</table>


## Program @KONVENS2022
The participants will present their works on September 12th at KONVENS2022 in Potsdam.

### Schedule

- **13:30 – 13:50**: Opening
- **13:50 – 14:10**: Everybody likes short sentences - A Data Analysis for the Text Complexity DE Challenge 2022 (BBAW Zentrum Sprache)
- **14:10 – 14:30**: HIIG at GermEval 2022: Best of Both Worlds Ensemble for Automatic Text Complexity Assessment (HIIG)
- **14:30 – 14:50**: TUM Social Computing at GermEval 2022: Towards the Significance of Text Statistics and Neural Embeddings in Text Complexity Prediction (TUM Social Computing)
- **14:50 – 15:10**: HHUplexity at Text Complexity DE Challenge 2022 (HHUplexity)
- **15:10 – 15:30**: Pseudo-Labels Are All You Need (Deepset)
- **15:30 – 16:00**: Break
- **16:00 – 16:20**: Text Complexity DE Challenge 2022 Submission Description: Pairwise Regression for Complexity Prediction (LGirrbach)
- **16:20 – 16:40**: TUM sebis at GermEval 2022: A Hybrid Model Leveraging Gaussian Processes and Fine-Tuned XLM-RoBERTa for German Text Complexity Analysis (TUMuch Complexity)
- **16:40 – 17:00**: Automatic Readability Assessment of German Sentences with Transformer Ensembles (AComplexity)

## Proceedings
The Proceedings of the shared task are available at [ACL Anthology](https://aclanthology.org/volumes/2022.germeval-1/).

## Organizers

- [Salar Mohtaj](https://www.linkedin.com/in/salar-mohtaj/), Research Scientist, SLT Research Department at DFKI Berlin, Technical University of Berlin, 
- [Babak Naderi](https://www.tu.berlin/index.php?id=29496), Research Scientist, Technical University of Berlin
- [Sebastian Möller](https://www.tu.berlin/index.php?id=16022), Professor Technical University of Berlin, Head of the Research Department Speech and Language Technology, DFKI


## References

[1] Naderi, B., Mohtaj, S., Ensikat, K., & Möller, S. (2019). Subjective assessment of text complexity: A dataset for german language. arXiv preprint arXiv:1904.07733.
