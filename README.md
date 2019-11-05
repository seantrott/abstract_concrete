# Abstract vs. concrete words in distributional semantic models

**Central question**: Do distributional properties of word use better predict human similarity judgments for **abstract** than **concrete** words?

# Data

We use the following datasets for our analysis:

* [SimVerb-3500](https://www.wikidata.org/wiki/Q43552147)
* SimLex-999  
* [WordSim-353](http://www.cs.technion.ac.il/~gabr/resources/data/wordsim353/)  
* [MTurk-771](http://www2.mta.ac.il/~gideon/mturk771.html)

In addition to the links provided above, this repository contains the raw datasets in the `data` directory.

The `data/processed` directory contains each of the raw datasets above, with the following features added:

* `w1_conc`: The Brysbaert concreteness rating for the first word in the comparison.  
* `w2_conc`: The Brysbaert concreteness rating for the second word in the comparison.  
* `decontextualized_elmo_similarity`: The cosine distance in ELMo embedding space. 

# Analysis

For each dataset, we perform several analyses. 

First, we ask whether `cosine distance` predicts `human similarity judgments` overall, and how well.

Second, we split wordpair comparisons into `Abstract`, `Concrete`, and `Mixed`, according to the following scheme:

* `Abstract`: both words in a wordpair comparison fall below the median concreteness level.  
* `Concrete`: both words in a wordpair comparison fall above the median concreteness level.  
* `Mixed`: one word falls below the median concreteness level, the other falls above.

We then regress `human similarity judgment ~ cosine distance` for the `Abstract` wordpairs and the `Concrete` wordpairs, and ask whether the `R^2` is higher for `Abstract` wordpairs than `Concrete` wordpairs. We find that distributional cues reliably predict human similarity judgments better for abstract wordpairs than concrete wordpairs.

Third, we begin with the dataset of `Concrete` wordpairs and iteratively replace each wordpair with a randomly sample pair from the `Abstract` dataset. We regress `human similarity judgment ~ cosine distance` on each iteration. We repeat this `N` times, to account for ordering effects in which abstract wordpairs were sampled first. Then we ask whether the `percentage of abstract wordpairs` in a dataset is positively related to the `R^2` on that dataset when regressing `human similarity judgment ~ cosine distance`. We find positive relationships across the datasets, suggesting that the predictive strength of distributional cues is indeed greater for abstract wordpairs. 