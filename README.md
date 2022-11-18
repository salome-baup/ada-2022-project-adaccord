# 🎬 ${\color{#CC0000} \mathrm{Refl'action:\ Cinema\ as\ a\ mirror\ of\ society's\ thoughts}}$

## ${\color{#CC0000}\mathrm{Table\ of\ Contents}}$
1. [Abstract](#Abstract)
2. [Research questions](#Research_questions)
3. [Proposed additional datasets and files](#Proposed_additional_datasets_and_files)
4. [Methods](#Methods)
5. [Proposed timeline](#Proposed_timeline)
6. [Organisation within the team](#Organisation_within_the_team)
7. [Questions for the TAs](#Questions_for_the_TAs)


## ${\color{#CC0000}\mathrm{Abstract}}$  <a name="Abstract"></a> 

In the 17th century, Molière, the French playwright, actor, and poet depicted the customs and morals of his day. The analysis of his work allows us today to have an idea of the societal issues and the questionings of that time. Artistic expression and, more precisely, the 7th art can provide a lot of information about society’s thoughts.   
The goal in this project is to analyze the content of plot summaries and characterized them by looking at the lexical fields, word occurrences, as well as the words polarity and general sentences. This would allow to identify the main concerns of society (e.g., climate catastrophe, war, technological disaster, family disunity) and evaluate the feelings associated with these topics. We also want to see the evolution of these concerns over time and include critical reviews of the movies to obtain a more complete characterization of the situation.

## ${\color{#CC0000}\mathrm{Research\ questions}}$ <a name="Research_questions"></a>
During this work, we will address those questions:  
- What are the most prevalent concerns of the world population reflected by cinema?
- Which feelings are associated with these topics?
- How are these concerns and feelings evolving over time?

## ${\color{#CC0000}\mathrm{Proposed\ additional\ datasets\ and\ files}}$ <a name="Proposed_additional_datasets_and_files"></a>
The following additional datasets are used or are planned to be used:
- [Mappages Freebase/Wikidata](https://developers.google.com/freebase#freebase-wikidata-mappings): maps the given Freebase Ids to WikiData, used to recover ethnicities and actor names in the dataset.
- [Metacritic](https://github.com/miazhx/metacritic): Metascore feature, a weighted average of reviews from top published critic reviews for a given movie, will be used to weight the different concerns.
- [names_dataset](https://pypi.org/project/names-dataset/): provides information about names (popularity, country, gender), used to discard proper names from plot summaries.

## ${\color{#CC0000}\mathrm{Methods}}$ <a name="Methods"></a>
**Step 1: Metadata scrapping, cleaning, and dealing with duplicate or missing values**  
After loading the characters and movies datasets, columns are cleaned by removing the freebase ID. Then, duplicated values are checked in both datasets and finally missing values are handled.

**Step 2: Plot summaries pre-processing**  
Plot summaries are loaded, cleaned (only English ones are kept) and missing plots are checked. Then, pre-processing is performed, including tokenization to divide plots into lists of substrings, PoS tagging to categorize words, lemmatization to reduce the different forms of a word to one single form and finally stop words removal to only extract meaningful information. We then augmented the movies dataset with this information.

**Step 3: Including Metascore**  
To obtain a better characterization of the movie at a time close to the release date, Metascore are loaded, missing values are checked and scores are then added to the movies dataset.

**Step 4: General preliminary analysis**  
In this part, we compute preliminary information about plot structure such as number of words and punctuation, polarity of words and the ten most tokens for each plots. In addition, the movie genre feature is explored. Then some statistics and visualizations are shown for all this indormation.

**Step 5: Topic extraction**  
To characterize the plot summaries lexical fields, topics extraction are performed using natural language processing (NLP) techniques. The idea is to analyze the frequency of words and phrases in plot summaries, as well as their relationship in order to find clusters of words that appear more frequently.   
- The first technique used is the Latent Dirichlet Allocation (LDA), which is an unsupervised clustering technique commonly used for text analysis. In this case, words are represented as topics, and plot summaries are represented as a collectecion of these word topics. This technique returns the most common topics among all plots and can subsequently be fine-tuned to improve results. Each movie plot is then associated with a combination of tree different topics, where coefficients reprensent the propability for each topic. Finally, only the topic with the highest probability is kept.  
- The second technique used is the Bidirectional Encoder Representations from Transformers (BERT). It uses a transformer, that is an attention mechanism learning contextual relations between words via an encoder that reads the text input. The difference with this technique is that it reads the input text in a non-directional manner, which is why it is consider BidirectionaL. Finally, each plot is associated with one representtative topic.

**Step 6: Sentiment analysis**  
As a next phase, a sentiment analysis will be conducted to study the polarity of plot summaries and determine the global feelings associated with them.

**Step 7: Time evolution analysis**  
Concerns and sentiments evolution over time will be analyzed by splitting the movies according to their release dates. Statistical analysis will then be performed to see any significative differences across periods of time. 

**Step 8: Results gathering and interpretation**  
Taking all the results together, we will draw conclusions and try to answer our research questions. 

**Step 9: Github site creation and Datastory redaction**

## ${\color{#CC0000}\mathrm{Proposed\ timeline}}$ <a name="Proposed_timeline"></a>
**Done for Milestone 2 (18/11/22):**
- Step 1 (finished)
- Step 2 (finished)
- Step 3 (finished)
- Step 4 (finished)
- Step 5 (started but needs improvements)  

**Between 02/12/22 to 23/12/22:** 
- First week: finish part 5, that is fine-tuned LDA, analyse results from LDA and BERT and create visualizations. Do part 6 that is perfom Sentiment analysis, analyse data and create visualizations.
- Second week: finish part 7, make statistical testings and visualisations.
- Last week: finish part 8 and 9

## ${\color{#CC0000}\mathrm{Organisation\ within\ the\ team}}$ <a name="Organisation_within_the_team"></a>
- Step 5: Nearchos, Clara
- Step 6: Clara, Anna
- Step 7: Salomé, Anna
- Step 8: Everybody
- Step 9: Everybody 

## ${\color{#CC0000}\mathrm{Questions\ for\ the\ TAs}}$ <a name="Questions_for_the_TAs"></a>
Do you know any existing model for multi-sentiment analysis? Which option do we have in order to have more complex sentiment classes such as sadness, fear, happiness, anger (...)?
