Prompt: 
Introduction to Analysis Method: Clear, concise explanation of the chosen analysis method, its relevance to the class, and its application in the context of the selected paper. Does it have useful code/data for analysis?

Random Forest Regression (RFR) is the analysis method used in this final project. An RFR is a machine learning model that predicts numbers (continuous values) by combining many decision trees.
(A decision tree is a simple model that makes predictions by asking a series of yes/no questions. It starts at the top (the root) and splits the data based on rules, like “Is age > 10?” or “Is harvest count high?”
Each split sends the data down a branch until it reaches a leaf, which gives the final prediction.) 
Random Forests build each tree using bootstrap samples and random subsets of features, introducing diversity in the ensemble. 
This randomness reduces variance and overfitting compared to individual decision trees, resulting in more stable and accurate models even with a slight increase in bias. 
RFR is a suitable method for the dataset that is used in this final project (AMWO recoveries) because it reduces variance, handles noisy ecological data well, and provides interpretable insights into variable importance.

Band recovery data in this paper are sparse and noisy. RFR reduce variance by averaging across many trees, making predictions more stable than if a single decision tree was used.

