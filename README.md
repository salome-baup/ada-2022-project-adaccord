# Cinema as a mirror of society's thoughts

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
- What are the most prevalent concerns of the world population ? OR How the cinema reflects the most prevalent concerns of the world population ?
- Which feelings are associated with these topics ?
- How are these concerns and feelings evolving over time ?

## Proposed additional datasets and files <a name="Proposed_additional_datasets_and_files"></a>
The following additional datasets are used or are planned to be used:
- Mappages Freebase/Wikidata: maps the given Freebase Ids to WikiData, used to recover ethnicities and actor names in the dataset.
- Metascore: weighted average of reviews from top published critic reviews for a given movie, will be used to weight the different concerns.
- names_dataset: provides information about names (popularity, country, gender), used to discard proper names from plot summaries.
- others ??

## Methods <a name="Methods"></a>
To characterize the plot summaries lexical fields, we perform topics extraction using natural language processing (NLP) techniques. The idea is to analyze the frequency of words and phrases in plot summaries, as well well as their relationship in order to find clusters of words that appear more frequently.   
The first technique used is the Latent Dirichlet Allocation (LDA), which is an unsupervised clustering technique commonly used for text analysis. In this case words are represented as topics, and plot summaries are represented as a collectecion of these word topics. This technique first requires data pre-processing to tokenize, PoS tags, lemmatize and removing stop words from the plot. Then LDA can be run and returns the most common topics among all the plots. LDA can be fine-tuned to improve results.  
The second technique used is BERT, a transformer-based model that have shown promising results in NLP tasks. +descrbibe
Finally, a sentiment analysis will be conducted to study the polarity of plot summaries and determine the glogal feelings associated with them.


## Proposed timeline <a name="Proposed_timeline"></a>

## Organisation within the team <a name="Organisation_within_the_team"></a>

## Questions for the TAs <a name="Questions"></a>
