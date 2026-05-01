# Topic Modeling

How to find major topics from large corpus of text?

Given a sentiment, what are people acutally feeling that sentiment about?

Sometimes the text does not explicitly state the topic (keywords)
- aka latent or hidden topics

Posts can be multiple topics

Latent Dirichlet Allocation (LDA)
- assumes every document is a mix of topics
- assumes every topic is a mix of words
- input is amount of topics we want (t1 t2 t3)
 1. start by randomly assigning each word in each document with a topic
 2. count num times tk occurs in document d
  - make counts per document
 3. count number of times every word appears under topic k across corpus
 4. unassign word from its topic
  - reduce counts in doc topic counts and corpus topic counts
 5. reassign w_d,n a new topic based on A and B
  - A = prevalence of topic in doc
  - B = prevalence of word in each topic
  - pick based on A X B with some alpha and beta
  - 2 / 4 * 7 / 100
- repeat for multiple iterations, converges once words are reassigned to the same topic multiple times
- this learns the distributions of the words and topics
- alpha changes the topic distributions
 - 0 < a < 1 makes it more skewed towards a particular document
 - a = 1 makes the distributions more uniform
 - a > 1 makes all topics even more uniform

Coherence 
- for a pair of words, its log(Co-Occurrence(w_i,w_j)+1/Occurrence(w_i))
