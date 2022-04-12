# Text Complexity DE Challenge 2022


Text forms an integral part of exchanging information and interacting with the world, correlating with quality and experience of life. Text readability is one of the factors which affects a reader's understanding of a text. The mapping of a body of text to a mathematical unit quantifying the degree of readability is the basis of readability assessment. This quantified unit is significant in informing the reader about how difficult the text content is to read. Readability assessment has diverse use cases and applications, such as helping to choose appropriate learning material for second language learners, people with disabilities, and providing targeted content for various groups in the general population (e.g. against misinformation). As readability might be influenced by representation, we only target the text complexity for readers in this task. Furthermore, a reliable text complexity estimator can be used to automatically evaluate simplified text (produced by authors or automatic simplifiers). 

This task consists of developing machine learning based regression models to predict the complexity of a sentence in German for German learners in the B level. We encourage participants to train deep learning based models since they show better performance in similar tasks.

We will use Codalab to organize the challenge. The Codalab competition page will be up on 20th April 2022.

[codalab](https://competitions.codalab.org/competitions/){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }


## Timeline
- **Trial data ready: April 11th, 2022**
- Training data ready: May 16th, 2022
- Baseline model ready: May 23rd, 2022.
- Test data ready: June 20th, 2022
- Evaluation starts: June 27th, 2022
- Evaluation end: July 4th, 2022
- Paper submission due: July 15th, 2022
- Camera ready due: August 12th, 2022
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
In the proposed task for GermEval 2022, participants should train models that predict the MOS complexity of sentences in the test dataset. A test dataset includes 300 sentences. We conduct subjective tests with German learners to collect subjective MOS scores for the test dataset. 

### Trial Data
|<sup>The name</sub>|<sup>Language</sub>|<sup>Domain</sub>|<sup># of instance</sub>|<sup>Reference</sub>|
|------|---|---|---|---|
|<sup>Liar, Liar Pants on Fire: A New Benchmark Dataset for Fake News Detection</sub>|<sup>English</sub>|<sup>Social Media</sub>|<sup>-</sub>|[<sup>[1]</sub>](#1-wang-william-yang--liar-liar-pants-on-fire-a-new-benchmark-dataset-for-fake-news-detection-arxiv-preprint-arxiv170500648-2017)|


## Evaluation

The blind test dataset will be published on June 20th, 2022. Each participating team has to submit the result of their prediction until July 4th 2022. The participating teams will submit the ID and predicted scores for the complexity of sentences in the test set. The Root Mean Squared Error (RMSE) after 3rd order mapping  will be used to measure errors (accuracy) of submissions compared to the subjective ratings.  RMSE is the standard deviation of the prediction errors, which is the difference of predicted values from actual values.

Due to bias or offsets, different gradients and different qualitative rank orders are always present in subjective evaluations. The statistical uncertainty always exists in the collected MOS. Therefore, a third-order polynomial function is applied to compensate for the possible variance between several subjective experiments in this challenge. For each model, we create one mapping function per test dataset. Then the mapped predictions were used to calculat the RMSE.


## Organizers

- [Salar Mohtaj](https://www.tu.berlin/index.php?id=29512), NLP Research Scientist,Technical University of Berlin,  DFKI Berlin
- [Babak Naderi](https://www.tu.berlin/index.php?id=29496), Research Scientist, Technical University of Berlin
- [Sebastian Möller](https://www.tu.berlin/index.php?id=16022), Professor Technical University of Berlin, Head of the Research Department Speech and Language Technology, DFKI


## References

[1] Naderi, B., Mohtaj, S., Ensikat, K., & Möller, S. (2019). Subjective assessment of text complexity: A dataset for german language. arXiv preprint arXiv:1904.07733.
