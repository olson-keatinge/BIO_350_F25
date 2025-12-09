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

Tuesday December 7, 2025. 
I downloaded VSCode on my personal laptop to make the changes in the code. I attempted to add the changes via my github repository, but it wasn't successful. Instead of adding the changes to my model, I will anaylse how it can be improved in my discussion of the results in order to simplify the project. 



