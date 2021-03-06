# billboard-classifier
Predicting which songs on Spotify appear on the Billboard Top 100

I have always had a strong connection to music, and given how music is a reflection of society, I find features and trends in music to be very interesting. In this project, I visually explore the patterns found in American music over the last century, and leverage those patterns to create a model that can predict whether or not a song with a given set of attributes has appeared on the Billboard top 100 chart, a collection of the most popular songs in the United States updated every week.

To this end, an ensemble model has been created. This requires data on music in general, as well as data on what songs have achieved this status. For song attributes, a kaggle dataset of 160,000+ songs are their associated features derived from data sourced from Spotify was obtained. For billboard 100 data, a datset containing data going back to 1999 and was obtained and then cleaned. To ensure a valid comparison for the model, the spotify dataset was pruned down to just entries containing songs published in 1999 or later. Next the 'billboard' dataframe had to be pruned and reformatted to provide the right information for the model in a useable format. This dataframe was then joined with the pruned spotify dataframe using a jaccard join based on the artist and song title information in each row.

At this point work on the model could begin. The data was loaded in and the required packages were imported. Categorical features were one hot encoded and the primary artist of each song was target encoded to ensure the data was ready for machine learning models. All remaining non-numerical columns were dropped. After the data was split into train, validation, and test sets using scikit learn, its dimensionality was reduced using PCA with 22 components. Two helper functions were created to aide in construction of the models, one to obtain classification metrics on model results in an organized manner and one to tune hyperparameters.

Five supervised learning models were constructed: Logistic Regression, Random Forest, Adaboost (with the default base estimator of a decision tree classifier with a depth of 1), Support Vector Machines (SVM), and kNN. In each model, grid searches were performed to optimize the hyperparameters in the model with the help of a validation set. The individual learners achieved an accuracy of 40% to 60%. The ensemble model achieved an accuracy of 70%.

The Spotify data was obtained from Kaggle:
https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks

The Billboard data was also obtained from Kaggle:
https://www.kaggle.com/danield2255/data-on-songs-from-billboard-19992019
