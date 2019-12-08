# Sentiment Analysis on Movie Reviews

* The Rotten Tomatoes movie review dataset is a corpus of movie reviews used for sentiment analysis, originally collected by Pang and Lee. 
* This competition presents a chance to benchmark your sentiment-analysis ideas on the Rotten Tomatoes dataset. 
* Label phrases on a scale of five values: 
    * negative
    * somewhat negative 
    * neutral
    * somewhat positive 
    * positive. 
    
* Obstacles like sentence negation, sarcasm, terseness, language ambiguity, and many others make this task very challenging.

## Some basic information about dataset
* The dataset is comprised of tab-separated files with phrases from the Rotten Tomatoes dataset. The train/test split has been preserved for the purposes of benchmarking, but the sentences have been shuffled from their original order.

    * train.tsv contains the phrases and their associated sentiment labels. We have additionally provided a SentenceId so that you can track which phrases belong to a single sentence.
    * test.tsv contains just phrases. You must assign a sentiment label to each phrase.

## Result of Submission
| Model    |      Notes    | Score |
|----------|:-------------:|------:|
| Logistics|  tuning hyperparameter and TfiDf | 0.59869 |
| Logistics|  tuning hyperparameter and count vector | 0.61467 |
| Logistics|  tuning hyperparameter and count vector  with binary | 0.61544 |
|  Transfer learning of FastAi| 4 Epochs | 0.64144 |
|  Transfer learning of FastAi| 6 Epochs | 0.66047 |

## Tuing logistic regression model
* C determines the strength of the regularization is called C, and higher values of C correspond to less regularization (where we can specify the regularization function).C is actually the Inverse of regularization strength(lambda)

* Regularization (L1 and L2)

* CountVectorizer with binary

## Transfer learning

* I used transfer learning for this task, to do that, I use a pre-trained model based on Wikipedia called wikitext-103. It is a model that’s already trained from the Wikipedia dataset(or ‘corpus’ in NLP terms) to predict the next words from a giving unfinished sentence.

* I will leverage the ‘language knowledge’ the model already learned from the Wikipedia dataset and build on top of that. To achieve the best results, we’ll need to ‘fine-tune’ the model to make it learn a bit from our ‘comments’ dataset since what people say in the comments are not necessarily the same with the more formal Wiki. Once the language model is fine-tuned, we can then use it to further do our classification task.

![](https://i.imgur.com/UI9YdWT.png)
