# Most Similar Tweets in Real-Time

### Description
The web application will allow users to type their tweets and be presented with a list of most similar tweets previously posted.
This is a feature that people can interact with and would like to use.

## Motivation

Having the recent similar tweets available to the author would significantly enhance the user experience on twitter by 
creating a perspective of how connected we are; encouraging creativity and expressivity, enriching communications and
conversations and lead to much more exciting interactions on Twitter.
Trending Hashtags are consciously determined per tweet, usually offering creative variations or alternatives for the actual context of the tweet, sometimes even ironically unrelated phrases to express sarcasm; 
(hash)tags are secondary in importance as opposed to the tweet itself. Therefore, similarity of tweets is the more 
clear window into the flow of topics and use of language, and quickly result in growth of interaction.

### Challenge

The application has to process billions of tweets to find the most similar recommendations for any given new tweet as it is being typed. In order to implment this feature in real-time we must create a solution to significantly lower the computation run-time.

![alt tag](https://github.com/minoobeyzavi/Twinkle/blob/master/APP/static/img/Twinkle.png)


## Real-Time solution

```python
hv = HashingVectorizer(n_features=10000, non_negative=True)
docs_vectorized = hv.fit_transform(docs_joined).toarray()

# Local Sensitivity Hashing Forest
lshf = LSHForest(random_state=42, radius_cutoff_ratio=0.4)
lshf.fit(docs_vectorized)

# Distances & indices
dist, ind= lshf.radius_neighbors(docs_vectorized2, return_distance=True)
```

![alt tag](https://github.com/minoobeyzavi/Twinkle/blob/master/APP/static/img/Solution.png)

#### Data

Twitter Streaming API

#### What This Repo Contains

- Presentation
- Model explained in detail
- Code

![alt tag](https://github.com/minoobeyzavi/Twinkle/blob/master/APP/static/img/screenshot01.png)

![alt tag](https://github.com/minoobeyzavi/Twinkle/blob/master/APP/static/img/screenshot02.png)

### Future Direction

Transformative Suggestions on tweets whilst editing the tweet - to be offered as a feature on Twitter.
"J.F.Kennedy: I would never lie to you." -> "I have integrity for greater good”
This is modeled based on choice of words, context, strength of expressivity, expressions, grammar, punctuation, 
case-sensitivity, previous usage, conceptual vs literal alacrity and contradictions of the two
Conceptual:  "John F. Kennedy: I would never lie to you."
Literal: "Good Morning”
Giving weight power to words: "Audacity of Hope" vs. "Make America Great Again”

#### References

http://karpathy.github.io/2015/05/21/rnn-effectiveness/
https://dev.havenondemand.com/apis/analyzesentiment#overview
https://papers.nips.cc/paper/5635-grammar-as-a-foreign-language.pdf
https://www.researchgate.net/publication/221752656_The_Positivity_Scale
http://digitalcommons.unl.edu/cgi/viewcontent.cgi?article=1010&context=leadershipfacpub
