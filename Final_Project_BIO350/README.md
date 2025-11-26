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



