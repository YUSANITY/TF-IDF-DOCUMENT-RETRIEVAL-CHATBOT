# TF-IDF DOCUMENT RETRIEVAL CHATBOT
### Methodology 
The chatbot will be created based on a document retrieval based chatbot architecture. 
It will be trained on a set of questions and answer dataset. When a user queries a question, the chatbot will find the most 
relevant answers in the set of possible response and then outputs the answer. 

### Data Requirements 
The Data required to train the chatbot need to be in a question and answer format. To obtain the best possible result, 
the questions and answer should be in a more generic nature regarding the topic. The repository contain the dataset 
(IE. legal_help_clean.csv) used to create the chatbot.

### Data Pre-Processing 
Text pre-processing are done using NLTK python package. The input user query is tokenized with the punctuation remove. 
Next, Part of Speech (POS) tagging is done before Lemmatization. Lastly, stop word is removed from the user input query.
The training text are pre-processed in the same way as the user input query to ensure consistency comparing cosine similarity. 

### Term Frequency – Inverse Document Frequency (TIF-IDF) Approach  
TF-IDF method the team will be used to give scores to document that look the same as the user’s query. 
This approach is built on two concepts: - 
1) Term Frequency which is the scoring of the frequency of the word in the current document.

        TF = (Number of times term t appears in a document)/ (Number of terms in the document)

2) Inverse Document Frequency which is a scoring of how rare the word is across documents.

        IDF = 1+log(N/n)
        Where, N is the number of documents and n is the number of documents a term t has appeared in.

What this approach will do is it will rescale the frequency of the words by how often they will appear in all documents
so that the scores for the frequent words across all documents are normalised. 

### Cosine Similarity 
After we transformed the texts using TF-IDF, we can get two real valued vectors in vector space. We thus can obtain the 
cosine similarity of any pair vectors by taking their dot product and divide it by the product of their norms which give 
the cosine of the angle between the vectors. Using the following formula, we can find the similarity between any 
two documents d1 and d2. 

       Cosine Similarity (d1, d2) = Dot product (d1, d2) / ||d1|| * ||d2||
       Where d1, d2 are two non-zero vectors.
       
### Threshold Settings
3 thresholds setting features is added to the chatbot to regulate the result to display for the front-end user.  
Except for threshold A, the threshold B and C and be adjusted depending on the dataset to obtain optimal result for the chatbot.

Threshold A: 
Allow the program to catch and display message if there is no matching similarity. This setting should not be adjusted. 

Threshold B: 
Allow the program to catch and prompt the user to rephrase the query to get better result if the similarity is too low. 
This setting can be adjusted to fit the dataset. 

Threshold C:
Allow the program to list high similarity results and randomly show one result to the user. This feature assumes that high cosine 
similarity response is probability correct, so random reply adds more dimensionality to the chatbot reply. This threshold setting 
can be adjusted to fit the dataset.
