# Final-Capstone-Project

In the past few years, with the advent of the Internet and the rise of instant gratification, companies who have been able to provide services on-demand have been the greatest winners. One of the companies that have led the transition to digital media consumption is Netflix. During the pandemic, they achieved even greater success through a significant increase in subscriptions. One of the technologies that streaming platforms like Netflix and its peers (i.e. Disney, Crave, Hulu) share is recommendation systems.

This paper looks at the logic behind recommendation systems and applying it to the Yelp dataset to provide personalized recommendations to the user based on data such as their reviews, ratings, location, and more. The dataset provides the information in .json form, and provides five files with information on users, businesses, reviews, check-ins, and tips. The sixth part of the dataset is in .jpg format, and will be disregarded for the purpose of this paper. Two common candidate generation approaches include content-based filtering, which is item-based filtering, and collaborative filtering, which uses user-based filtering (Google, 2022). The research questions that I will attempt to answer are: “For restaurant recommendations, do content-based filtering models or collaborative filtering models provide better suggestions?” and “What level of accuracy/performance can I achieve given these data points?”

To evaluate my models, I propose using the metric recall. As we are looking to create a Top-N recommendation list, recall is known to be effective in evaluating the ability of the model in finding relevant results (Cremonesi, P., & Turrin, R. (n.d.)). Currently, I am contemplating using the leave-one-out cross validation method (LOOCV), where it involves leaving a known rating to the side and later trying to predict it. Alternatives would be to use the k-fold cross-validation or the train-test split. As the Yelp dataset is very large, it may be computationally expensive to use k-fold cross-validation or the LOOCV methods. However, I will attempt to use the k-fold cross validation first, and then use the LOOCV, then the train-test split respectively.

I will be using Python to code this project. Tools that I am proposing to use include Python’s Pandas, Scikit-Learn, Numpy, Weka, and MatPlotLib libraries. With these tools, I will perform dimensionality reduction, data cleaning, exploratory data analysis, create training and test sets, and develop the content-based and collaborative. Then, I will evaluate this model with the aforementioned metric of recall.

**********************
EDIT: As an edit to the above abstract which was written prior to creating the content-based and collaborative filtering recommendation systems, the content-based recommendation system was created using the TF-IDF (Term Frequency Inverse Document Frequency) technique. This technique was performed on the "categories" column (alternatively, also the "text" column in the review.json object) in the business.json file (files last modified January 2022). Similarities scores between businesses were calculated using cosine similarity. Recommendations are then generated based on restaurants with the highest similarity scores. This model was evaluated using RMSE, MAE, and alternatively Precision at K. The "ratings" column in review.json was used to pull the actual ratings from a randomly picked user in the test dataset and compared to predicted ratings (a weighted average of the cosine similarity score and the "query business").

The collaborative filtering recommendations system was created using the Surprise library. Two approaches were considered: SVD (Singular Value Decomposition) and ALS (Alternating Least Squares). Both are variations of Matrix Factorization, but employ slightly different methods. When the two were compared in this model, SVD came out as the winner with lower RMSE and MAE scores. Evaluation was performed with K-Fold Cross Validation (5 folds) on RMSE and MAE metrics. For this model, the review.json and business.json objects were used as well.

In conclusion, based on this model, taking TF-IDF model representative of the content-based filtering system performance and matrix factorization representative of collaborative filtering recommendation system performance, collaborative filtering outperformed content-based filtering when generating restaurant recommendations, evaluated on RMSE and MAE scores.

The repository contains the files:
1) Abstract
2) Initial Code - MF (Matrix Factorization)
3) Initial Code - TF-IDF (Term-Frequency Inverse Document Frequency)
4) Literature Review, Data Description
5) businesseswithreviews Pandas Profile (HTML)
6) Final Report
7) Final Presentation

Link to EDA Report: https://github.com/dariayip/Final-Capstone-Project/blob/main/businesseswithreviewsEDAprofile.html

Link to Content-Based Filtering RS:
https://github.com/dariayip/Final-Capstone-Project/blob/main/Final%20Code/CIND820%20-%20Capstone%20Initial%20Code-TFIDF-v20-2.ipynb

Link to Collaborative Filtering RS:
https://github.com/dariayip/Final-Capstone-Project/blob/main/Final%20Code/CIND820%20-%20Capstone%20Initial%20Code-MF-v3.ipynb
