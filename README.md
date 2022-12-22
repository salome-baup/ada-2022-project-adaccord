# 🎬 ${\color{#CC0000} \mathrm{Refl'action:\ Cinema\ as\ a\ mirror\ of\ society's\ thoughts}}$

## ${\color{#CC0000}\mathrm{Requirements}}$
You will find a requirement.txt file to install any required libraries.  
In addition, intermediary augmented datasets are present on a [GoogleDrive](https://drive.google.com/drive/folders/1pUw3DCFzGdlNXRTiX8NZgG0wjSsQYbkZ?usp=sharing). Those files are too big to be on GitHub.

## ${\color{#CC0000}\mathrm{Data story}}$
Our project's data story is available [here](https://clararenou.github.io/).

## ${\color{#CC0000}\mathrm{Repo\ architecture}}$

## ${\color{#CC0000}\mathrm{Table\ of\ Contents}}$
1. [Abstract](#Abstract)
2. [Research questions](#Research_questions)
3. [Proposed additional datasets and files](#Proposed_additional_datasets_and_files)
4. [Methods](#Methods)
5. [Timelime](#Timeline)
6. [Organisation within the team](#Organisation_within_the_team)
7. [Questions for the TAs](#Questions_for_the_TAs)


## ${\color{#CC0000}\mathrm{Abstract}}$  <a name="Abstract"></a> 

In the 17th century, Molière, the French playwright, actor and poet depicted the customs and morals of his day. The analysis of his work allows us today to have an idea of the societal issues and the questionings of that time. Artistic expression and, more precisely, the 7th art can provide a lot of information about society’s thoughts.   
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
In this part, we compute preliminary information about plot structure such as number of words and punctuation, polarity of words and the ten most tokens for each plots. In addition, the movie genre feature is explored. Then some statistics and visualizations are shown for all this information.

**Step 5: Topic extraction**  
First of all, genres are clustered in bigger genre categories.  
To characterize the plot summaries lexical fields, topics extraction are performed using natural language processing (NLP) techniques. The idea is to analyze the frequency of words and phrases in plot summaries, as well as their relationship in order to find clusters of words that appear more frequently.   
- The first technique used is the Latent Dirichlet Allocation (LDA), which is an unsupervised clustering technique commonly used for text analysis. In this case, words are represented as topics, and plot summaries are represented as a collectecion of these word topics. This technique returns the most common topics among all plots and can subsequently be fine-tuned to improve results. Each movie plot is then associated with a combination of tree different topics, where coefficients reprensent the propability for each topic. Finally, only the topic with the highest probability is kept.  
- The second technique used is the Bidirectional Encoder Representations from Transformers (BERT). It uses a transformer, that is an attention mechanism learning contextual relations between words via an encoder that reads the text input. The difference with this technique is that it reads the input text in a non-directional manner, which is why it is consider BidirectionaL. Finally, each plot is associated with one representtative topic.

**Step 6: Concerns categories**  
We were interested to know if societal concerns emerge from movies. Using the [Empath](https://github.com/Ejhfast/empath-client) tool, lexicon categories for concerns are created based on lead words. The selected concerns are: Ecology, Health, War & Conflicts, Technology, Space, Gender inequalities, LGBTQ+ community & Homophobia, Racism, Mental state, Human interactions & Relationships.  
- For this analysis, plot summaries have been preprocessed in a way corresponding to the Empath analysis tool. Tokens are not lemmatized and no casefolding is performed, character names are removed and bigrams are finally created. Then, those plot summaries were analyzed by Empath which gave a normalized score to each movie for each concern.
- The most present words in plot summaries for each category have been collected.

**Step 7: Sentiment analysis**  
Sentiment analysis has been conducted to study the polarity of plot summaries and determine the global feelings associated with them.
- The Valence Aware Dictionary for sEntiment Reasoning model, `VADER`, is first used to extract sentiment scores for four categories: positive, negative, neutral and compound. While neutral, positive and negative scores are probabilities to have each given sentiment, the compound score is the sum of positive, negative and neutral scores. This compound score is then normalized between -1 (most extreme negative) and +1 (most extreme positive).
- Then to refine our analysis, plot summaries are characterized with more complex sentiments using the `NRCLex` library which is able to measure emotional affect from a text body. Affect dictionary contains approximately 27'000 words, and is based on the National Research Council Canada (NRC) affect lexicon and the NLTK library's WordNet synonym sets ([see documentation](https://pypi.org/project/NRCLex/)). For our analysis, emotional affects include fear, anger, anticipation, trust, surprise, positive, negative, sadness, disgust, joy.

**Step 8: Results, Analyses and Interpretation**  
- Time evolution: topics, concerns and sentiments evolution over time is analyzed by splitting the movies according to their release dates or by periods of 5 years.
- Distribution of topics, concerns and sentiments among movies.
- Association of topics and sentiments and their co-evolution over time is analysed.
- Association of concerns with topics and sentiments.
- Statistical analysis is then performed.   

**Step 9: Github site creation and Datastory redaction**

## ${\color{#CC0000}\mathrm{Timeline}}$ <a name="Proposed_timeline"></a>
**Done for Milestone 2 (18/11/22):**
- Steps 1, 2, 3, 4 have been completed during Milestone 2.
- Step 5 has been started but needed improvements.  

**Miletsone 3: From 02/12/22 to 23/12/22:** 
- First week:
  - Step 5: Fine-tuning of LDA and BERT.
  - Step 6: Creation of concerns lexical categories and Empath analysis.
  - Step 7: Performing sentiment analysis.
  - Step 8: Visualisation of topics, concerns and sentiments independently across movies and time.
- Second week:
  - Step 8: Combined informations and visualizations
  - Step 8: Statistical testing
  - Step 9: Website creation
- Last week:
  - Step 8: Interpretations
  - Step 9: Data story writing

## ${\color{#CC0000}\mathrm{Organisation\ within\ the\ team}}$ <a name="Organisation_within_the_team"></a>
Anna: 

Clara:

Nearchos:

Salomé: 

