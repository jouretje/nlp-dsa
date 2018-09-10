# nlp-dsa
DSA Case Study Outline

Purpose
Analyze information and emotional content of posts from health forums. Steps are outlined below and details are provided in the attached deliverable documents.

Goal
Develop a code book for rating information and emotional support of posts
Develop a classification model based on text features

Data requirements
Web-scraped discussion boards from the following:
	Healing Well (healingwell.com)
	What to Expect  whattoexpect.com)
The Lupussite (thelupussite.com)
Fertility (fertilitycommunity.com)
This is MS (thisisms.com)	
eHealth (ehealthforum.com)
Health Boards (www.healthboards.com/boards/) 
ADD Forums (www.addforums.com/forums/index.php) 
	WebMD (messageboards.webmd.com/) 
	Cancer Forums (cancerforums.net)
Sjogren’s World (sjogrensworld.org)
Patient Info (https://patient.info/forums)
ADDitude (www.additudemag.com/forums/)
	
Steps Taken
Identified active forum communities where members exchange informational and emotional support
Narrowed down potential health-related forums based on disease and exchange
Selected a training set for Sjogren’s World
Cleaned and translated posts
Developed a simple rating system for determining emotional and informational content based on a 3, 5 and 7 scale
Discussed which rating system might be best and decided to have each member rate informational and emotional content of the first 100 posts based on the 5 point scale
Evaluated inter-rater reliability among members and agreement was low (36% and 35%)
Revised the simple rating system into a more extensive code book. Provided additional clarification on definitions for each level of the 5 point scale
Replaced the training set of Sjogren’s World posts with a new set of posts that were more diverse and contained more informal/emotional rich content (and less administrative posts)
Had each member rate posts using the new code book and training set
Re-evaluated inter-rater reliability among members and noticed a much high agreement (53% informational and 65% emotional)
Used the code book to create a training set of 500 posts
Used the the training set to build a model and evaluate accuracy 


Model Development

1. Calculation of null accuracy as the benchmark for model accuracy
    Null accuracy Emotional = 50.8%
    Null accuracy Informational = 46.3%
 
2. Exploration of dataset: what features are distributed differently between categories?
    Group and count ratings, create visualizations of distribution of features to get an idea, eg:
 
3. Construct models with different vectorizers and classifiers, compare accuracy
    Vectorizers tried:
     CountVectorizer and Tf_idf
    Classifiers tried:
     Logistic Regression
     Multinomial Naive Bayes

4. Manually tune the vectorizer parameters, to get best accuracy
    Parameters tuned:
    Minimum document frequency
    N-gram range
    Removal of stop words
 

 5. Add additional features (other than tokenized/vectorized bag of words) to the model inputs
The text vectorizer (CountVec or Tf_idf) creates a compressed, sparse row matrix. So adding features requires a function that will also return a CSR matrix.

6. Results
    Best Informational model accuracy : 64% 
 TfIdf (min df = 3)
  multinomialNB
  addition of post length, counts of digits, counts of special characters
    Best Emotional model accuracy : 61.6% 
   Tfidf (min df = 3), 
   multinomial NB
   addition of count of digits in post

7. Future steps for model improvement
Automating the tuning of parameters (type of classifier, min doc frequency, n-gram range, etc)
Adding additional features to the model: semantic analysis, customized dictionaries, sentence and words-per-sentence metrics



Next Steps
Once a more robust and tunable classification system is developed, test various classification algorithms to obtain the best models for multiple disease-specific forums.
