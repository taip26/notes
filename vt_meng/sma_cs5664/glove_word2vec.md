# Glove and Word2Vec

Get meaning of a word from its neighbors
- e.g. banking is surounded by debt, crisis, regulation, etc.

Word2Vec
- developed by google
- Limitations? - only considers local context

Continuous Bag of Words
- maximize probability of target word given the context words
- P(target | context)
- each word is a one-hot encoded vector based on the vocabulary
- predict center word based on a window of context (i.e. window=2 is predicting words two out from center word)
- get embeddings based on weights

Skip-Gram
- inverse of CBOW, P(context|target)

Word vectors give some semantic meaning
- king - man + woman ~ queen
- other examples include word tenses (walking - walked = swimming - swam), country-capital

when to use CBOW
- faster training than skip
- low mem
- better acc for freq words

when to use skip
- works well with small amt of training data
- when words/phrases are rare

GloVe Embeddings
- Global Vectors
- window-based co-occurrence matrix
- given co-occ matr and the corresponding probs (P(k|W)), if prob > 1, word k is closer to num, if < 1 closer to denom, if == 1 then word is either equidistant or irrelevent 
- glove is based on these ratios

