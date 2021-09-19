# Project 2


## Contents  


- [Problem Statement](#Problem-Statement)
- [Data](#Data)
- [Research](#Research)
- [Data Dictionary](#Data-Dictionary)  
- [Findings](#Findings)
- [Conclusions](#Conclusions)
- [Recommendations](#Recommendations)



## Problem Statement  

A real estate company is looking to sell their properties in the Ames, Iowa area and make a return on their investment. Hence, they are keen to know the valuation of their properties. They are also keen to know which housing features can contribute the most to the valuation, so that they can upgrade properties with a low ROI and appreciate its value.


## Data  


- [`train.csv`](./datasets/train.csv): Contains all of the training data for model
- [`new_test.csv`](./datasets/new_test.csv): Cntains the test data for model
- [`sample_sub_reg.csv`](./datasets/sample_sub_reg.csv): An example of a correctly formatted submission


## Research

* There are 80 variables focused on the quality and quantity of the many physical attributes of the property, with 2 additional observation identifiers. Most of the variables are information that a real estate company would want to know about a potential property.  

    * **20 continuous variables that relate to various area dimensions for each obseration**
        * Area measurements on the basement / main living area / porches are broken down into individual categories based on quality and type
        * Opportunity to use methods to combine the variables
    * **14 discrete variables to quantify the number of items within the house**
        * Number of kitchens / bedrooms / bathrooms located in the basement and above ground (grade).
        * Also included are the garage capacity and dates
    * **46 categorical variables, of which, 23 nominal & 23 ordinal**
        * Range from 2 to 28 classes with smallest being the street and largest being the neighbourhood.
        * Nominal variables identify various types of dwellings / garages / materials / environmental conditions
        * Ordinal variables rate items in the property
    * **2 observation identifiers**
        * The PID variable can be used in conjunction with the [Assessor's Office](http://www.cityofames.org/assessor/) or [Beacon](http://beacon.schneidercorp.com/) websites to directly view the records of a particular observation
    
    * **Others**
        * The neighbourhood variable can be used to model the location effect, and is of relevance when using the [map](http://www.amstat.org/publications/jse/v19n3/decock/AmesResidential.pdf) 
        
        
        
## Data Dictionary

<details> <summary> Data contains information from the Ames Assessor’s Office used in computing assessed values for individual residential properties sold in Ames, IA from 2006 to 2010
</summary>  

|Feature|Dataset|Type|Description|  
|:--|:-:|:-:|:--|  
|Order|Discrete|int64|Observation number|  
|PID|Nominal|int64|Parcel identification number - can be used with city web site for parcel review|  
|MS SubClass|Nominal|int64|Identifies the type of dwelling involved in the sale|  
|MS Zoning|Nominal|object|Identifies the general zoning classification of the sale|
|Lot Frontage|Continuous|float64|Linear feet of street connected to property|
|Lot Area|Continuous|int64|Lot size in square feet|
|Street|Nominal|object|Type of road access to property|
|Alley|Nominal|object|Type of alley access to property|
|Lot Shape|Ordinal|object|General shape of property|
|Land Contour|Nominal|object|Flatness of the property|
|Utilities|Ordinal|object|Type of utilities available|
|Lot Config|Nominal|object|Lot configuration|
|Land Slope|Ordinal|object|Slope of property|
|Neighborhood|Nominal|object|Physical locations within Ames city limits (map available)|
|Condition 1|Nominal|object|Proximity to various conditions|
|Condition 2|Nominal|object|Proximity to various conditions (if more than one is present)|
|Bldg Type|Nominal|object|Type of dwelling|
|House Style|Nominal|object|Style of dwelling|
|Overall Qual|Ordinal|int64|Rates the overall material and finish of the house|
|Overall Cond|Ordinal|int64|Rates the overall condition of the house|
|Year Built|Discrete|int64|Original construction date|
|Year Remod/Add|Discrete|int64|Remodel date (same as construction date if no remodeling or additions)|
|Roof Style|Nominal|object|Type of roof|
|Roof Matl|Nominal|object|Roof material|
|Exterior 1st|Nominal|object|Exterior covering on house|
|Exterior 2nd|Nominal)|object|Exterior covering on house (if more than one material)|
|Mas Vnr Type|Nominal|object|Masonry veneer type|
|Mas Vnr Area|Continuous|float64|Masonry veneer area in square feet|
|Exter Qual|Ordinal|object|Evaluates the quality of the material on the exterior|
|Exter Cond|Ordinal|object|Evaluates the present condition of the material on the exterior|
|Foundation|Nominal|object|Type of foundation|
|Bsmt Qual|Ordinal|object|Evaluates the height of the basement|
|Bsmt Cond|Ordinal|object|Evaluates the general condition of the basement|
|Bsmt Exposure|Ordinal|object|Refers to walkout or garden level walls|
|BsmtFin Type 1|Ordinal|object|Rating of basement finished area|
|BsmtFin SF 1|Continuous|float64|Type 1 finished square feet|
|BsmtFinType 2|Ordinal|object|Rating of basement finished area (if multiple types)|
|BsmtFin SF 2|Continuous|float64|Type 2 finished square feet|
|Bsmt Unf SF|Continuous)|float64|Unfinished square feet of basement area|
|Total Bsmt SF|Continuous|float64|Total square feet of basement area|
|Heating|Nominal|object|Type of heating|
|HeatingQC|Ordinal|object|Heating quality and condition|
|Central Air|Nominal|object|Central air conditioning|
|Electrical|Ordinal|object|Electrical system|
|1st Flr SF|Continuous|int64|First Floor square feet|
|2nd Flr SF|Continuous|int64|Second floor square feet|
|Low Qual Fin SF|Continuous|int64|Low quality finished square feet (all floors)|
|Gr Liv Area|Continuous|int64|Above grade (ground) living area square feet|
|Bsmt Full Bath|Discrete|float64|Basement full bathrooms|
|Bsmt Half Bath|Discrete|float64|Basement half bathrooms|
|Full Bath|Discrete|int64|Full bathrooms above grade|
|Half Bath|Discrete|int64|Half baths above grade|
|Bedroom|Discrete|int64|Bedrooms above grade (does NOT include basement bedrooms)|
|Kitchen|Discrete|int64|Kitchens above grade|
|KitchenQual|Ordinal|object|Kitchen quality|
|TotRms AbvGrd|Discrete|int64|Total rooms above grade (does not include bathrooms)|
|Functional|Ordinal|object|Home functionality (Assume typical unless deductions are warranted)|
|Fireplaces|Discrete|int64|Number of fireplaces|
|FireplaceQu|Ordinal|object|Fireplace quality|
|Garage Type|Nominal|object|Garage location|
|Garage Yr Blt|Discrete|int64|Year garage was built|
|Garage Finish|Ordinal|object|Interior finish of the garage|
|Garage Cars|Discrete|int64|Size of garage in car capacity|
|Garage Area|Continuous|float64|Size of garage in square feet|
|Garage Qual|Ordinal|object|Garage quality|
|Garage Cond|Ordinal|object|Garage condition|
|Paved Drive|Ordinal|object|Paved driveway|
|Wood Deck SF|Continuous|float64|Wood deck area in square feet|
|Open Porch SF|Continuous|float64|Open porch area in square feet|
|Enclosed Porch|Continuous|float64|Enclosed porch area in square feet|
|3-Ssn Porch|Continuous|float64|Three season porch area in square feet|
|Screen Porch|Continuous|float64|Screen porch area in square feet|
|Pool Area|Continuous|float64|Pool area in square feet|
|Pool QC|Ordinal|object|Pool quality|
|Fence|Ordinal|object|Fence quality|
|Misc Feature|Nominal|object|Miscellaneous feature not covered in other categories|
|Misc Val|Continuous|float64|$Value of miscellaneous feature|
|Mo Sold|Discrete|int64|Month Sold (MM)|
|Yr Sold|Discrete)|int64|Year Sold (YYYY)|
|Sale Type|Nominal|object|Type of sale|
|Sale Condition|Nominal|object|Condition of sale|
|SalePrice|Continuous|float64|Sale price|
    
</details>


## Findings

### EDA  

- The categorical (nominal & ordinal) variables will need to be mapped to numerical variables for its features to be useful in our modelling
- At first glance, columns 'Id','PID' seems like they won't be useful for modelling as they were random numbers for indexing the house, however we'll check this out later using a scatter plot to see if a relationship with 'SalePrice' exist
- Some features have similar names & functions which could be collinear, we'll verify their correlation using a heatmap
- There are missing values (Nan) which will need addressing
- Good to check for any duplicate rows
- Overall, there seems to be too many features, which would contribute to our model being overfitted. But we will take a slow iterative approach to this to avoid omitting features potentially useful for our model
#### Check for Duplicates / Outliers / Irrelevant Data / Target Variable

### Data Cleaning

#### Check for missing values
- 26 features with missing values
- Missing values were replaced with respective values (based on data documentation) and deductive imputation when required.
- Row with too many missing values were dropped

### Preprocessing and Feature Selection
- Features were combined or dropped due to collinearity
- Rank Ordinal Features
- Selected 45 Features for model
- One Hot Encode Nominal Features

### Model Benchmark
|Model|Hyperparams|Num Features|CV RMSE|Train RMSE|Holdout RMSE| 
|:--|:--|:--|:--|:--|:--|
|OLS (1 Feature)|-|1|56568|56210|58465|
|OLS (All Features)|-|199|37304|24079|30629|
|Ridge|Alpha=327|199|31256|26526|30604|
|Lasso|Alpha=893|66|31810|27160|30842|
|ElasticNet|Alpha=0.64 ratio=0.5|77|30729|27766|28643|


## Conclusions 

The top features that increases the saleprice seems reasonable. The ground living area and overall quality of the house were top, followed by the quality of the kitchen and the exterior and if the house is in the NrighHt and StoneBr neighbourhood.

On the flip side, the features that decreases the saleprice the most were due to location and age of house. The townhouse (both end and inside unit)  and the age of the unit, followed by if the house was banked, and if it belonged in the Edwards neighbourhood.

Some features that increase the value of the house can be done through modifications or renovations, within the legal limits of the land.

While the production model is accurate for predicting saleprices of homes below $300,000, above that the error starts to get bigger. I belive this is due to a lack of data for homes with higher sale prices.

Interestingly, most of the top features are on the exterior. This information will help us in our recommendation to the client.


## Recommendations

Some recommendations to client for them to appreciate their property prices
- Focus on making home improvements in the kitchen and exterior, get an assessor to grade the quality
- If planning to increase the ground living area, you should build a bigger garage as this would bring the most value
- Include a fireplace and ensure that the heating around the house is good quality
- Consider changing the roof style to be hip.

Model should not be used on other cities as its not a generalized model. Each city has different external factors that affect the housing prices that might not be accounted for in this model, like its climate and economical position etc. For a generalised model, new features will need to be included and a new model will need to be fitted, although this would generally cause our model to have a larger variance as some features applied to the model will not be relevant to particular cities.