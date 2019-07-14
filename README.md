# Report about the analyze on “War and Peace“
- Author: Behnam Ghavimi (orcid: 0000-0002-4627-5371)
- source of "war and peace": [https://en.wikisource.org/wiki/War_and_Peace/Book_One](https://en.wikisource.org/wiki/War_and_Peace/Book_One "https://en.wikisource.org/wiki/War_and_Peace/Book_One")
List of Jupyter note books (python ocdes) implemented regarding the analyze:

## 0_Data_prepration_split_book_into_chapters.ipynb:
This notebook contains codes to clean text (due to removing head and tail of text which was added to text automatically and not part of the real text). Also, the code tried split text to different chapters and to save them into separate files. The chapter text files were stored in the directory in the project file:
./Data/Chapters/”

## 1_Phrase_word_distribution:
In this file, I tried to show some information about the distribution of words and phrases.
1. Just as a start, I generated Wordcloud diagram of the text of the book to get a general overview.
[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig1.png)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig1.png)

2.  Find out top 10 verbs, top 10 nouns, top 10 adj, and top 10 adv:
[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig2.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig2.PNG)

3.  Here, you can find distribution of top 10 verbs, nouns, and adjs in the progress of Text:
[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig3.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig3.PNG)

[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig4.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig4.PNG)

[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig5.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig5.PNG)

[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig6.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig6.PNG)

[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig7.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig7.PNG)

6- diagram of this top 10 rhetorical structure in progress of text:
[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig8.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig8.PNG)

7-  diagram of top 10 more general rhetorical structure in progress of text:
[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig9.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig9.PNG)
## 2_Named_Entities_Recognition_PLACE_PERSON:
In this part, I tried to extract person entities, place entities out of the text. Regarding this purpose, two functions implemented based on NLTK and Spacy libraries for NER. Afterward, these two functions were applied to the text. Finally, the outputs of the two functions were intersected to increase precision.
The results were stored into two sperated files:
- Persons:
	- "./Data/Persons.csv" 
	- 10 samples:
[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig10.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig10.PNG)

- Locations:
	- "./Data/Locations.csv"
	- 10 samples:
[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig11.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig11.PNG)

## 3_Sentiment_Analysis:
Two models were trained based on logisticRegression and Randomforest algorithms. Also since I used supervised algorithms, I need a train set of data. This train set was downloaded from:
[http://ai.stanford.edu/~amaas/data/sentiment/](http://ai.stanford.edu/~amaas/data/sentiment/ "http://ai.stanford.edu/~amaas/data/sentiment/")

Also, Tf-idf was used for generating sentence vectors. The comparison of these two algorithm showed that LogisticRegression outperforms.

Accuracy of LogisticRegression: 0.88408

Accuracy of RandomForestClassifier: 0.86552

Regarding this analysis, LogisticRegression is picked to generate the result. The model was applied to all sentences of the book, and the results were stored in the following directory:

- 	"./Data/Senteces_Sentiment.csv" 

Based on the number of positive and negative sentences in each chapter, I decided on the sentiment of each chapter:

- 	"./Data/Chapters_Sentiment.csv"

## 4_Text_Sumerization:
Regarding this task, I used to different algorithms (i.e, 1- TextRank algorithm based on word embedding, 2- Tf-IDF score)  and save the results into two separate files:

- Summery based on TextRank
	- "./Data/textRankSumery.txt”
- Summery based on Tf-Idf:
	- "./Data/tf_idf_summery.txt”
	
Regarding word embedding, pre-trained word vectors Glove is used. Also after ranking the sentences, for generating the results of each algorithm, 10 top sentences were picked.

## 5_Intent_extraction_based_on_Topic_modeling:
In the task, intent extraction is mentioned. Regarding intent extraction, usually supervised approaches are utilized. But regarding the supervised algorithms, we need a training set. I couldn’t think of a proper training set for this specific task. Therefore, I tried to attack the problem with an unsupervised algorithm. Regarding this purpose, I applied topic modeling on sentences. 

For topic modeling, one issue is picking the number of topics. Coherence measure was applied to different models with  different number of topics from 2 to 130, and the result is depicted in the following picture:
[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig12.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig12.PNG)

Also with “pyLDAvis.gensim” modules is used for investigating different model with different number of topics:

[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig14.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig14.PNG)

After this investigation, I went for ten topics, since I wanted to have a very separate number of topics for my experiments.

This model was applied on all sentences of the text of book (War and Peace). The disturbution of sentences into these topics can be found in the below:

[![](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig15.PNG)](https://raw.githubusercontent.com/behnam2014/NLP_PlayGround/master/figs/fig15.PNG)

The result was stored in the following directory:
	- "./Data/topic_modeling.csv"
Also for each topic by using top 9 words of each, labels were generated for the topics.

## 6_Key_extraction:
Regarding this task, three different approach were used:
	- Keyword extraction based on Rake library
		- './Data/Rake_Keyword_Extraction.txt'
		- './Data/Rake_Keyword_Extraction_Score.txt'
	- Keyword extraction based on Summa library
		- './Data/Suma_Keyword_Extraction.txt'
	- Keyword extraction based on Tf-idf
		- './Data/TF-IDF.txt'
