# Abstract vs. concrete words in distributional semantic models

**Central question**: Do distributional properties of word use better predict human similarity judgments for **abstract** than **concrete** words?

# Data

We use the following datasets for our analysis:

* [SimVerb-3500](https://www.wikidata.org/wiki/Q43552147)
* SimLex-999  
* [WordSim-353](http://www.cs.technion.ac.il/~gabr/resources/data/wordsim353/)  
* [MTurk-771](http://www2.mta.ac.il/~gideon/mturk771.html)

In addition to the links provided above, this repository contains the raw datasets in the `data` directory.

The `processed` directory contains each of the raw datasets above, with the following features added:

* `w1_conc`: The Brysbaert concreteness rating for the first word in the comparison.  
* `w2_conc`: The Brysbaert concreteness rating for the second word in the comparison.  
* `decontextualized_elmo_similarity`: The cosine distance in ELMo embedding space. 
