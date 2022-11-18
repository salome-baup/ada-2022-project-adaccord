# 🎬 Refl'action: Cinema as a mirror of society's thoughts

## Table of Contents
1. [Abstract](#Abstract)
2. [Research questions](#Research_questions)
3. [Proposed additional datasets and files](#Proposed_additional_datasets_and_files)
4. [Methods](#Methods)
5. [Proposed timeline](#Proposed_timeline)
6. [Organisation within the team](#Organisation_within_the_team)
7. [Questions for the TAs](#Questions)

## Abstract <a name="Abstract"></a>
In the 17th century, Molière, the French playwright, actor, and poet depicted the customs and morals of his day. The analysis of his work allows us today to have an idea of the societal issues and the questionings of that time. Artistic expression and, more precisely, the 7th art can provide a lot of information about society’s thoughts.   
The goal in this project is to analyze the content of plot summaries and characterized them by looking at the lexical fields, word occurrences, as well as the words polarity and general sentences. This would allow to identify the main concerns of society (e.g., climate catastrophe, war, technological disaster, family disunity) and evaluate the feelings associated with these topics. We also want to see the evolution of these concerns over time and include critical reviews of the movies to obtain a more complete characterization of the situation.

## Research Questions <a name="Research_questions"></a>
During this work, we will address those questions:  
- What are the most prevalent concerns of the world population reflected by cinema ?
- Which feelings are associated with these topics ?
- How are these concerns and feelings evolving over time ?

## Proposed additional datasets and files <a name="Proposed_additional_datasets_and_files"></a>
The following additional datasets are used or are planned to be used:
- Mappages Freebase/Wikidata: maps the given Freebase Ids to WikiData, used to recover ethnicities and actor names in the dataset.
- Metascore: weighted average of reviews from top published critic reviews for a given movie, will be used to weight the different concerns.
- names_dataset: provides information about names (popularity, country, gender), used to discard proper names from plot summaries.
- others ??

## Methods <a name="Methods"></a>
**Step 1: Metadata scrapping, cleaning, and dealing with duplicate or missing values**  
After loading the characters and movies datasets, columns are cleaned by removing the freebase ID. Then, duplicated values are checked in both datasets and finally missing values are handled.

**Step 2: Plot summaries pre-processing**  
Plot summaries are loaded, cleaned (only English ones are kept) and missing plots are checked. Then, pre-processing is performed, including tokenization to divide plots into lists of substrings, PoS tagging to categorize words, lemmatization to reduce the different forms of a word to one single form and finally stop words removal to only extract meaningful information.

**Step 3: Including Metascore**  
To obtain a better characterization of the movie at a time close to the release date, Metascore are loaded, missing values are checked and scores are then added to the movies dataset.

**Step 4: General preliminary analysis**  
This part contains a preliminary analysis of the plots structure with the information gathered until then. Some statistics and visualizations are shown concerning the number of words and punctuation, the polarity of words and the movie genre distribution. In addition, the ten most tokens for each plots are obtained.

**Step 5: Topic extraction**  
To characterize the plot summaries lexical fields, topics extraction are performed using natural language processing (NLP) techniques. The idea is to analyze the frequency of words and phrases in plot summaries, as well well as their relationship in order to find clusters of words that appear more frequently.   
- The first technique used is the Latent Dirichlet Allocation (LDA), which is an unsupervised clustering technique commonly used for text analysis. In this case, words are represented as topics, and plot summaries are represented as a collectecion of these word topics. This technique returns the most common topics among all plots and can subsequently be fine-tuned to improve results.  
- The second technique used is the Bidirectional Encoder Representations from Transformers (BERT). It uses a transformer, that is an attention mechanism learning contextual relations between words via an encoder that reads the text input. The difference with this technique is that it reads the input text in a non-directional manner, which is why it is consider BidirectionaL.

**Step 6: Sentiment analysis**  
Finally, a sentiment analysis will be conducted to study the polarity of plot summaries and determine the global feelings associated with them.

**Step 7: Results gathering and interpretation**

**Step 8: Github site creation and Datastory redaction**

## Proposed timeline <a name="Proposed_timeline"></a>
**Done for Milestone 2 (18/11/22):**
- Step 1 (finished)
- Step 2 (finished)
- Step 3 (finished)
- Step 4 (finished)
- Step 5 (started but need improvements)  

**Between 02/12/22 to 23/12/22:** 
- First week: finish part 5, that is fine-tuned LDA, analyse results from LDA and BERT and create visualizations.
- Second week: finish part 6, that is perfom Sentiment analysis, analyse data and create visualizations.
- Last week: finish part 7 and 8

## Organisation within the team <a name="Organisation_within_the_team"></a>

## Questions for the TAs <a name="Questions"></a>
