**Project Log:**

Week of Nov 17 2025
This final project analyses a banding/recovery dataset of several American Woodcock populations and was sourced from the paper, "Disentangling data discrepancies with integrated population models" (Saunders. SP., et al. 2019), to predict the population abundance estimation. A Random Forests Regression will be used. The x and y inputs and output respectively have been decided - 

Inputs (x variables): 
-	Temporal data 
    -   Banding year (B Year), recovery year (R Year)
    -   Banding/recovery month/day (B Month, R Month, etc.)
    -   Hunting season indicator (Hunt. Season)
-	Spatial data 
    -	Banding/recovery flyway (B Flyway, R Flyway)
    -	Banding/recovery region/state (B Region, R Region)
    -	Latitude/longitude (B Lat, B Long, R Lat, R Long)
    -	Coordinate precision (accuracy descriptors)
-	Biological and demographic information 
    -   Species (Species Game Birds::SPEC)
    -   Age (Age, Age::VAGE)
    -   Sex (Sex, Sex::VSEX)
    -   Condition (Condition::VCondition, Condition::VBandStatus)
-	Banding and recovery metadata
    -   Band type (original/current)
    -   Status (Status::VStatus)
    -   How obtained (How Obt::VHow)
    -   Who reported (Who::VWho)
    -   Permittee (Permits::Permittee)
    -   Report method (Rept Mthd::VRept Mthd)

These features capture when, where, and how birds were banded/recovered, plus their age/sex/condition.

Output (y variable):
-   Population abundance estimate
    -   Derived from banding/recovery counts aggregated by year, region, or flyway.


Some technical coding errors arose and have been delt with the labels and data, however some remain to be addressed in the first code block. This will be done next time. 


Week of Nov. 24, 2025
The AMWO recoveries data was re-evaluated and I decided to readjust the target goal and analysis of this project. The goal: 
The goal of this project is to develop a machine learning model that predicts the age at which American Woodcocks die based on different variables including banding year, banding month, banding flyway, banding region, recovery year, recovery month, recovery flyway, recovery region, sex, method of recovery, and status. If yes, what is the most important feature involved in predicting the age depending on the recovery month? 

A key objective is to evaluate feature importance to determine which variables most strongly influence age prediction, with a particular focus on how the importance of predictors varies depending on the recovery month. This will provide insights into seasonal or temporal patterns in age determination and help identify the most informative ecological and demographic factors for age classification.

Monday December 8, 2025. 
I realised that this model has very high weight on the feature of Birth year and month and recovery year and month. These features mathematically calculate the age of the birds, so naturally it will have high correlation; it is data leakage. 
Therefore, these features and predictors must not be included in the machine learning model due to the fact that they directly calculate the age of the birds.  
The meaningful predictors are features such as: 
Birth Flyway, Birth Region, Recovery Flyway, Recovery Region, Sex, How Obtained (shot, salvaged, found dead, etc.), Status (dead/alive)
These represent actual biological or human-influenced processes related to mortality. 

The features causing data leakage will be dropped in the code so as to avoid their inclusion in the machine learning model, however they will be maintained in the calculation of the age in months. 

Tuesday December 9, 2025. 
I downloaded VSCode on my personal laptop to make the changes in the code. I attempted to add the changes via my github repository, but it wasn't successful. Instead of adding the changes to my model, I will anaylse how it can be improved in my discussion of the results in order to simplify the project. 

Project Discussion:

For this project, the Random Forest Regressor analysis method was used, a machine-learning method that builds many decision trees and combines their predictions to model complex ecological patterns. Random forests are well suited to ecological data because they can handle nonlinear relationships, interactions among variables, and mixed data types—situations that are very common in wildlife studies. This makes the method directly relevant to our Quantitative Methods for Ecology course, where we focused on tools that can analyze variability in ecological systems and identify influential predictors. In the context of Saunders et al. (2019), which examines American Woodcock survival and recovery patterns, a random forest model provides a flexible way to explore which recovery variables are most associated with age at death. While the original paper uses integrated population modeling rather than machine learning, the dataset it provides is well-structured for predictive analysis, allowing the random forest approach to reveal additional patterns in the recovery data that complement traditional demographic methods

To prepare the dataset for machine learning, the American Woodcock banding and recovery records were organized into a structured input-output format. The input variables included information from the banding and recovery events—including banding year and month, recovery year and month, flyway, region, sex, method of recovery, and status—because these factors could influence how long a bird lived before being recovered. The target/output variable, age at death, was calculated in months using the time difference between banding and recovery. After cleaning missing or impossible values and encoding categorical data, the predictors (X) and target (y) were separated and used to train a Random Forest regression model. This setup allows the model to learn patterns linking the input features to age at death, evaluate its accuracy using a held-out test set, and ultimately determine which variables are most influential in predicting the age at which American Woodcocks die.

Random forest regressor was a suitable choice of model for this data set because this model handles mixed data types well, meaning it can manage both numerical and categorical variables naturally handling them without requiring strict assumptions or extensive processing. Random forest regressors are also good at capturing nonlinear relationships, which most ecological relationships are, because they combine many decision trees that split data in different ways. Furthermore, this type of modelling is stable even when data is messy (eg inconsistent sampling) – this is useful because the ensemble averages across many decision trees. This modelling type also performes well on small datasets – 100 rows is relatively small, however suitable for this project. Additionally, it also reduces overfitting compared to a single decision tree because using many decision trees and averaging their predictions helps to prevent the model from latching onto random noise or outliers which is important when working with wildlife recovery data.

The purpose of this project is to evaluate the extent to which certain variables in the American Woodcock Recoveries data set from paper Saunders et al. (2019) can predict American Woodcock age at death through a machine learning model, and to determine which features exert the strongest influence on prediction by recovery month. The random forest, machine learning model considers all the important features that may play a role in determining the age of death. The feature importance aspect of the model produced the proportional weight each feature held against the age of death. 

The graph, Global Feature Importance, indicates the proportion of importance allocated to each variable showing that recovery year (R Year), how the bird was obtained (How Obt), and recovery month (R month) were the most important features to determining the age of the Woodcocks at death. The features R Year, How Obt, and R Month held importance weights of over 35%, 32%, and 16% respectively, with the next most important feature being birth month (B Month) weighing about 5%.

The feature importance heatmap produced by the model revealed that the birth region (B Region) was the most important feature for indicating the age at death of birds recovered in month 10 with about 50% weight. The age of birds recovered in month 11 was most indicated by Sex which had a feature importance of about 35%. During month 12, birth month (B Month) was the most important feature with a weight of about 40%, followed by recovery region (R Region) with a weight of 30%. Overall, the model performed well in running the code and visualizing the data. These results reflect the original research question as the graph and map show the proportion of feature importance in relation to age at death. 

The model used a train-test data split to train the random forest regressor on 80% of the data, testing it on the remaining 20%, and using a random state of 42. 42 is a standard random state used in machine learning models, hence why it was chosen. The 20% test is important and a valid percentage split because it is not too large, there is still enough data to train the model, but the test data is not too small either – if the test sample were too small then the results would be unstable or easily distorted. The model used a train-test data split to ensure the random forest model was evaluating feature importance based on patterns that generalize beyond the training data. This prevents overfitting and makes the resulting feature importance values more reliable and biologically meaningful. 

While the machine learning model ran, visualized the results, and displayed the feature importance, the features that were indicated as being of highest importance were features that mathematically calculate age. This is referred to as a data leakage and leads to the model appearing very accurate during training because the model has access to information that, in this case, calculates the target variable. If recovery year is included, of course it will have very high feature importance because it is the age of the bird at death. After researching this topic, data fitting artificially increases model accuracy, creates overfitting, and leaves the model useless of prediction because it will fail when applied to real-world data or any new information. Data leakage also produces misleading feature importance in the model. This was not identified as a challenge to the validity of this model until it late and ultimately left in the code. Appropriate methods to address this challenge would include adding a code chunk to drop the data leakage from the model in Step 4 before the train-test data split.
For example:

leak_cols = ['B Year','B Month','R Year','R Month']
data = data.drop(columns=leak_cols) 
--

This would remove the features that directly mathematically calculate age, thereby removing the data leakage, and optimistically the model would then produce results that show biologically meaningful inference. The R Year, R Month, B Year, and B Month would no longer dominate the feature importance and skew results, and the actual ecological variables would be considered for the feature importance of which variables influence the age of death of the American Woodcocks.

Another challenge I had with this project was simply understanding what I needed to do with my research paper data and understanding the assignment as a whole. This took some time, I read through and contemplated my paper thoroughly, eventually asking for help and was redirected in a way that gave me a greater understanding of the project. At the beginning I could have saved time by asking for help sooner, so in the future that is what I will do. 

Once I had chosen a model and developed a research question, things flowed well and I found with research and some help from AI I was able to craft a code that ran without errors and displayed clear, comprehendible results which reflected the original research questions. This part of the project went really well, and I feel far more confident with my ability to navigate VS Code, GitHub, and develop a model based on a developed research question.

When I was reviewing my code and my results before submission, I realised I had made an error by including variables which impacted the results of the feature importance and machine learning model which led to data leakage. The variables I failed to remove from the calculations were ones which directly calculate age, meaning if the model is developed to compare which features influence the age at which an American Woodcock died, then naturally the recovery year and month, and birth year and month will carry the most influence over the age at which the birds died. This was a significant error on my part, however if resolved with the previously described method and code, then it would likely be resolved. The challenge I faced in actually adding the adjustments into the code was that I needed to download VS Code onto my personal laptop (where I was using the desktop on campus previously), create the environments, and make some adjustments to allow the code to run, which I carried out, however I had challenges that were proving to be too time consuming to dedicate the time needed to fix them. This led to my decision to leave the code as it is and explain in my reflection that this was one of the challenges I faced because I didn’t allow myself enough time to manage it to the most successful outcome. To avoid this problem in the future I will complete all my coding for projects on the original desktop/computer used or finish this stage of the project with enough time to allow myself to find a more effective solution. While the results produced from this model, may potentially be misleading, I am proud of how I have improved in my confidence and ability to use the platforms we have interacted with during this course and this final project including VS Code, GitHub, and SciKit Learn. Futhermore, I have learned how I can better utilise my resources and how to evaluate my models, their analyses and effectiveness. 

