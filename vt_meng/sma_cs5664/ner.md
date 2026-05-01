# Named Entity Extraction

Examples of named entities
 - Hillary, Joe Biden, Trump
 - People, locations, orgs, geo-politics, times and dates
 - these can be ambiguous, London as a name or place

For a list of each type of named entity, can you tag each word a paragraph with the appropriate type?

NER extraction features:
 - embeddings for w_i and its neighboring words
 - part of speech for w_i + neighbors
 - presence of w_i in a gazetteer
 - w_i contains a particular prefix
 - w_i contains a particular suffix
 - w_i word shape + neighbors
  - lower, capitalized, all caps, mixed case, cap char with ., ends in digit, contains hyphen

sequence tagging
 - B beginning of entity
 - I inside
 - O outside
 - BIOOOBIOOOOBIOOO

gazetter is just a list of locations, so 1 if loc 0 otherwise

eval metrics
 - precision
 - recall
 - f1
