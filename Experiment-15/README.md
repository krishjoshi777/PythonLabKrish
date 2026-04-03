# Experiment No 15
## Title: Preprocessing Techniques for Text Data and NLP Techniques on Text Data
________________________________________
## Aim
To study the preprocessing techniques and Natural Language Processing (NLP) techniques used for analyzing text data.
________________________________________
## Tools / Software Required
•	Python 3.x
•	Google Colab / Jupyter Notebook
•	Python Libraries:
o	NLTK (Natural Language Toolkit)
o	Pandas
o	NumPy
________________________________________
## Theory
1. Text Data
Text data is a form of unstructured data that includes information in the form of words, sentences, or documents. Examples include emails, social media posts, reviews, articles, and messages.
Before applying machine learning or analysis, text data must be cleaned and processed. This process is known as text preprocessing.
________________________________________
2. Preprocessing Techniques for Text Data
Text preprocessing refers to the process of cleaning and transforming raw text into a format that can be analyzed by computers.
1. Text Cleaning
Text cleaning removes unnecessary elements such as:
•	Punctuation
•	Special characters
•	Extra spaces
•	Irrelevant symbols
This helps make the text clear and consistent.

2. Lowercasing
Lowercasing converts all text into lowercase letters so that similar words are treated the same.
Example:
Data Science → data science
This prevents duplication of words during analysis.

3. Tokenization
Tokenization is the process of splitting text into smaller units called tokens. Tokens can be words, sentences, or characters.
Example:
Sentence:
"Natural language processing is useful"
Tokens:
Natural, language, processing, is, useful

4. Stop Word Removal
Stop words are common words that do not add significant meaning to the text.
Examples:
•	is
•	the
•	and
•	in
•	of
Removing stop words helps reduce data size and improves analysis efficiency.

5. Stemming
Stemming reduces words to their root form by removing suffixes.
Examples:
Word	Stem
playing	play
running	run
studies	studi
Stemming simplifies words but may sometimes produce non-dictionary words.

6. Lemmatization
Lemmatization converts words into their base or dictionary form (lemma).
Examples:
Word	Lemma
running	run
better	good
studies	study
It is more accurate than stemming because it considers word meaning and grammar.
________________________________________
3. NLP Techniques on Text Data
Natural Language Processing (NLP) is a field of Artificial Intelligence that enables computers to understand and analyze human language.



1. Tokenization
Tokenization divides text into words or sentences, which helps computers process language more easily.

2. Part-of-Speech (POS) Tagging
POS tagging identifies the grammatical category of each word.
Examples of POS tags include:
•	Noun
•	Verb
•	Adjective
•	Adverb
Example:
Sentence: "Python is powerful"
Word	POS
Python	Noun
is	Verb
powerful	Adjective
________________________________________
3. Named Entity Recognition (NER)
Named Entity Recognition identifies important entities in text, such as:
•	Person names
•	Locations
•	Organizations
•	Dates
Example:
Sentence:
"Elon Musk founded SpaceX."
Entities identified:
•	Elon Musk → Person
•	SpaceX → Organization

4. Sentiment Analysis
Sentiment analysis determines the emotion or opinion expressed in text.
Types of sentiments:
•	Positive
•	Negative
•	Neutral
Example:
Review: “This phone is excellent.”
Sentiment: Positive

5. Text Vectorization
Text vectorization converts text into numerical format so that machines can process it.
Common techniques include:
•	Bag of Words (BoW)
•	TF-IDF (Term Frequency–Inverse Document Frequency)
These techniques represent text as numeric vectors for machine learning algorithms.

## Applications of NLP
NLP techniques are widely used in:
•	Chatbots and virtual assistants
•	Machine translation
•	Spam email detection
•	Sentiment analysis
•	Search engines
•	Recommendation systems

## Conclusion:
The preprocessing techniques and NLP techniques used for analyzing text data were studied successfully.


