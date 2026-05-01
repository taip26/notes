# Hate and Inciting Speech on Social Media

## Hate speech
How to identify content that may disturb users?

Identify anti-social elements/malicous speech

What is hate speech
 - speech that is designed to attack, disturb, or elicit a strong emotion from the target user
 - abusive or direct serious attact on an individual or group based on attributes such as race, ethinicity, religion, sexual orientation
 - often contains derogatory words but don't have to to be considered hate speech

Trends
 - upward trend of hate speech detected on social media platforms
 - moderation exists on some platforms but are absent on others (Gab)

Human moderators
 - Lots of effort, cannot deal with all hate speech instances, also reading hate speech can negatively affect the human mods, bias

Use AI with human input
 - AI can still be biased so need human in the loop (sexist, racist, etc.)

Problems with NLP-based methods
 1. dataset is based on one keyword
 2. class distribution is typically skewed (more non-hate than hate)

problem mitigations
 1. expand keyword list OR get posts from the community not based on keyword (ex. get all comments from a particular subreddit not based on keywords)
 2. balance dataset so the distribution is equal
  - train model on majority class (non-hate)
  - model learns the representation on how non-hate data is written instead of both
  - use autoencoder to learn anomoly detection (hate)

## Inciting Speech

Different from hate speech in that it incites an instrument to do harm or take actions against the target

More subtle than hate

Three rhetorical strategies
 - Identity - sentences that can stereotype or critize the target, including its beliefs, ideologies
 - Imputed misdeeds - express ongoing or past misdeeds
 - Exhortation - urge readers to act against the target (violence, discrimination, boycotts)

Supervised learning methods work well

Metrics
 - Precision, recall, sometimes f1
 - recall should be high in this case since we want to catch all hateful/inciting posts
