# Detect-Fake-Reviews-using-Reviewer-Centric-Features
Fake review detection helps organizations by maintaining their reputation, building consumer trust, enabling better decision-making based on genuine reviews, and improving product quality. 

# Abstract
The impact of reviews on any e-commerce site is of great importance, as it can be the base for a buyer's decision to buy any product. Buyer tries to evaluate the authenticity and quality of the product using the feedback given by other previous buyers in the form of review. But, sellers are taking advantage of the reviews by posting reviews in an attempt to promote or defame a product. Such reviews which are not a genuine opinion of an individual are termed as fake reviews. The existence of such fake reviews makes the buyer unable to make the right judgments of sellers, which can also cause the credibility of the platform to be downgraded. Thus, it is very important to identify the fake reviews on the platform. This Project will help to detect such fake reviews using a logistic regression model by considering reviewer centric features. 

# Dataset
Link:- https://www.kaggle.com/datasets/lievgarcia/amazon-reviews

Dataset contains 9 columns such as DOC_ID, LABEL, RATING, VERIFIED_PURCHASE, PRODUCT_CATEGORY, PRODUCT_ID, PRODUCT_TITLE, REVIEW_TITLE, REVIEW_TEXT.

Target Variable :- LABEL (label 1 => fake review & label 2 => genuine review)

# Methodology
At first relevant feature columns were extracted like rating, review_text, verified purchase and label was used as target variable. Then, categorical features were 
converted to numerical features using LabelEncoder. NLP techniques such as stopwords removing,lower casting the text,removing puntuations, tokenization,lemmatization and they join the tokens to strings and created new column called as clean text which is uased for further transactions.
Text data was extracted using CountVectorizer and Tf-idf (max_features = 1400). This was followed by calculating length for each review. Finally, our data having a feature vector of 1403 (1400 features of review content, rating, verified purchase, review length) was generated. Train test split of 80-20% was carried out on the data. This was followed by scaling the data by using MinMaxScaler class from sklearn library. The MinMaxScaler transforms features by scaling each feature to a given range. This range can be set by specifying the feature_range parameter (default at (0,1)).
Logistic regression model was trained on the train data for both CountVectorizer and Tf-idf using LogisticRegression in sklearn. Followed by this, hyperparameters of the model were tuned using GridSearch. Following is the list of optimal hyperparameters that result in best accuracy: c = 1, penalty = ‘l2’, solver = ‘newton-cg’.Then the accuracy of CountVectorizer and Tf-idf was compared and the same procedure was conducted by removing the 'Verified-Purchased' Column and used accuracy was compared.

# Results

## Comparing CountVectorizer and Tf-idf 
### CountVectorizer

Accuracy => 0.79         

Recall => 0.85          

Precision => 0.76          

### Tf-idf
           
Accuracy => 0.78

Recall => 0.80

Precision => 0.77

logistic regression model with Tf-idf and CountVectorizer using reviewer-centric features performs extremely well on our dataset by achieving an accuracy of 78% and 79% respectively.

## Comparing with Verified_Purchased and without Verified_Purchased
### with Verified Purchased

Accuracy => 0.79         

Recall => 0.85          

Precision => 0.76       

### without Verified_Purchased
            
Accuracy => 0.64

Recall => 0.62

Precision => 0.64

logistic regression model with CountVectorizer using “verified purchase” feature is 79% whereas when the feature is not used for classification, the same model achieves an accuracy of 64%. This result suggests that the “verified purchase” feature is very effective for identifying fake reviews. 
