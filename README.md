
# TLDR; A News Article Summarization and Classification Tool
Flatiron School Mod 5 Final Project
## Project Goals:
<ul>
  <li>Obtain news articles to analyze text data</li>
  <li>Utilize Natrural Language Tool Kit to preprocess text</li>
  <li>Train K-Means Clustering algorithm to segment groups of news articles based on similarities in text content</li>
  <li>Train supervised classification algorithms to predict which cluster a new article would fall closest to</li>
  <li>Perform pairwise cosine similarity on an article from user input to obtain extractive text summarization</li>
</ul>

## Exploratory Data Analysis
Data was obtained from Components.com, it included over 200k news articles from 2013-2017 coming from different news outlets.<br> 
ADD PICTURE OF DATAFRAME PREVIEW HERE<br>
After cutting out extrememly large and small articles, I ended with a datset of just over 100k articles, still a pretty good size to train with.

## K-Means Clustering
<br>
### Preprocessing
In order to preprocess the text data for K-Means, a number of initial steps have to be taken:<br>
<ul>
  <li>Tokenize words</li>
  <li>Lemmatize words</li>
  <li>Stem words</li>
  <li>Concatenate words of each record into a string and convert the entire pandas series into a list of strings</li>
  <li>Perform Count Vectorization and remove stop words</li>
  <li>Transform list of strings with TF-IDF transformation</li>
 </ul>
To speed up training stages, I cut each article down to it's first 100 words to perform clustering, this comes from the assumption that the article's main idea should most likely come up within it's first paragraph. After fitting many K-Means models, I settled on using the model with 12 clusters.
<br>
INSERT PICTURE OF CLUSTER DIST HERE<br>
### K-Means (12) clustering results
A preview of the top words in each cluster is below:<br> 
<ul>
  <li>Cluster 0: state, new, year, president, people, nation, one, unit, country, govern</li>
  <li>Cluster 1: Trump, president, Donald, would, white, house, campaign, American, Washington, administration, nation</li>
  <li>Cluster 2: Trump, republican, party, Donald, democrat, presidential, senate, candidate, GOP, voter, nominee</li>
  <li>Cluster 3: one, year, new, first, world, game, live, week, people, make, get, say, work, show</li>
  <li>Cluster 4: Clinton, Hillary, Trump, democrat, campaign, Sanders, presidential, election, emails, Bernie, support</li>
  <li>Cluster 5: Trump, Russia, investigation, intelligence, comey, election, director, Putin, Flynn</li>
  <li>Cluster 6: school, student, university, education, year, teacher, class, week, graduate</li>
  <li>Cluster 7: court, supreme, justice, judge, rule, federal, senate, law, appeal, Obama, legal</li>
  <li>Cluster 8: republican, care, health, house, bill, Trump, act, senate, Obamacare, president, insurance, reform</li>
  <li>Cluster 9: please, story, great, need, write, continue, step, block, display, extend, part, idea</li>
  <li>Cluster 10: company, year, percet, U.S., market, billion, bank, price, rate, stock, investor, share, report, oil</li>
  <li>Cluster 11: police, state, attack, kill, North Korea, Islam, Syria, president, military, force</li>
</ul>  

### Analyzing the clusters
Looking through the article clusters, a number of things stand out:
<ul>
  <li>Clusters 0, 1 and 2 seems to be mainly political and it looks like clusters 1 and 2 mainly lean towards articles regarding the republication election campaign. Cluster 0 seems to be quite broad politically.</li>
  <li>Cluster 3 looks extremely broad as well, and it is also the largest cluster BY FAR. This could be due to the fact that there are a large amount of articles in the dataset that have a wide range of topics.</li>
  <li>Cluster 4 is quite strong and it is mainly based on articles about the democratic party and Hillary Clinton</li>
  <li>Cluster 5 is specifically related to articles written about Russian meddling in the 2016 election </li>
  <li>Cluster 6 shows a strong relation to articles written about schooling</li>
  <li>Cluster 7 is highly related to the federal court system</li>
  <li>Cluster 8 looks to be primarily about political issues such as health care, tax reform etc </li>
  <li>Cluster 9 is another cluster that has a wide range of topics that don't seem to generalize to a small amount of ideas</li>
  <li>Cluster 10 is clearly made up of articles regarding financial markets</li>
  <li>Cluster 11 to me is the most impressive, this cluster seems to be built around police, military and foreign conflicts</li>
</ul>

