# Project 1


### Contents:  
---

- [Problem Statement](#Problem-Statement)
- [Background](#Background)
- [Data](#Data)
- [Research](#Research)
- [Data Dictionary](#Data-Dictionary)  
- [Executive Summary](#Executive-Summary)
- [Conclusions and Recommendations](Conclusions-and-Recommendations)
___

## Problem Statement
---

Although ACT has been the overall leader since 2012, it was reported that more graduating seniors are taking the SAT in 2018<sup>1</sup>. The college board which owns the SAT has pushed to expand its market share through revising their test and making deals with states<sup>2</sup>. This project aims to explore trends in SAT and ACT participation for the years 2018-2019 and seeks to identify states that have significant changes in their SAT and ACT participation rates. It also seeks to know how the students are performing across states, and if this contributes to an increase in college acceptance.

<sup>1</sup>https://newsroom.collegeboard.org/more-2-million-students-class-2018-took-sat-highest-ever
<sup>2</sup>https://www.washingtonpost.com/education/2018/10/23/sat-reclaims-title-most-widely-used-college-admission-test/
___

## Background
---

The SAT and ACT are standardized tests that many colleges and universities in the United States require for their admissions process. This score is used along with other materials such as grade point average (GPA) and essay responses to determine whether or not a potential student will be accepted to the university.

The SAT has two sections of the test: Evidence-Based Reading and Writing and Math ([*source*](https://www.princetonreview.com/college/sat-sections)). The ACT has 4 sections: English, Mathematics, Reading, and Science, with an additional optional writing section ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html)). They have different score ranges, which you can read more about on their websites or additional outside sources (a quick Google search will help you understand the scores for each test):
* [SAT](https://collegereadiness.collegeboard.org/sat)
* [ACT](https://www.act.org/content/act/en.html)
___

## Data
---

* [`act_2017.csv`](./data/act_2017.csv): 2017 ACT Scores by State
* [`act_2018.csv`](./data/act_2018.csv): 2018 ACT Scores by State
* [`sat_2017.csv`](./data/sat_2017.csv): 2017 SAT Scores by State
* [`sat_2018.csv`](./data/sat_2018.csv): 2018 SAT Scores by State
___

## Research
--- 

Score range data and admission testing policies for popular colleges and universities<sup>1</sup>, public and private, chosen to represent a wide array of four-year postsecondary institutions in the U.S<sup>2</sup>. Some states reflect different requirements.

**Range of Scores**
- SAT (Reading&Writing/Math) = 200 to 800<sup>3</sup>
- SAT (Total) = 400 to 1600
- ACT (English/Math/Reading/Science/Composite) = 1 to 36<sup>4</sup>
---
<sup>1</sup>https://reachhighscholars.org/scores_and_acceptance.html  
<sup>2</sup>https://www.compassprep.com/college-profiles/  
<sup>3</sup>https://en.wikipedia.org/wiki/SAT  
<sup>4</sup>https://en.wikipedia.org/wiki/ACT_(test)

___

## Data Dictionary
---

|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|ACT/SAT|50 States of America and District of Columbia| 
|act_2017_participation|float64|ACT|Percentage participation of ACT in 2017|
|act_2017_english|int|ACT|Mean score of engish section of ACT in 2017 (Score: 1-36)|
|act_2017_math|int|ACT|Mean score of math section of ACT in 2017 (Score: 1-36)|
|act_2017_reading|int|ACT|Mean score of reading section of ACT in 2017 (Score: 1-36)|
|act_2017_science|int|ACT|Mean score of science section of ACT in 2017 (Score: 1-36)|
|act_2017_composite|int|ACT|Mean composite score of ACT in 2017 (Score: 1-36)|
|act_2018_participation|float64|ACT|Percentage participation of ACT in 2018|
|act_2018_composite|int|ACT|Mean composite score of ACT in 2018 (Score: 1-36)|
|sat_2017_participation|float64|SAT|Percentage participation of SAT in 2017|
|sat_2017_reading_and_writing|int|SAT|Mean score of reading & writing section of SAT in 2017 (Score: 200-800)|
|sat_2017_math|int|SAT|Mean score of math section of SAT in 2017 (Score: 200-800)|
|sat_2017_total|int|SAT|Mean total score of SAT in 2017 (Score: 400-1600)|
|sat_2018_participation|float64|SAT|Percentage participation of SAT in 2018|
|sat_2018_reading_and_writing|int|SAT|Mean score of reading & writing section of SAT in 2017 (Score: 200-800)|
|sat_2018_math|int|SAT|Mean score of math section of SAT in 2018 (Score: 200-800)|
|sat_2018_total|int|SAT|Mean total score of SAT in 2018 (Score: 400-1600)|

___

## Findings 
---

 - The median of both ACT participation rates are significantly higher than both SAT
    - This could signify that ACT is generally a more successful programme compared to SAT within states, but we are unable to conclude from here that ACT is the test most taken as it doesn't take into account the number of students taking the tests within states
- The measure of spread<sup>1</sup> grew wider for both tests from 2017 to 2018
    - For ACT, the median participation rate has decreased and the spread has grew towards a lower participation rate
    - On the contrary, for SAT, the median participation rate has increased and the spread grew towards a higher participation rate 
    - This shows that as lesser students take the ACT, more students are taking the SAT
- The 75th percentile range for both ACT participation rates is at 100%, whereas the 25th percentile range for both SAT participation rates is close to 0%
    - More states work with the ACT college board to administer ACT within their state's high schools<sup>2</sup>, which accounts for ACT having more states close to 100% participation rate      
---
<sup>1</sup> https://www.statisticshowto.com/probability-and-statistics/descriptive-statistics/box-plot/  
<sup>2</sup>https://blog.collegevine.com/states-that-require-the-act/  
___  


- Colorado & Illinois had the biggest decrease in ACT participation and a big increase in SAT participation
    - Colorado made SAT mandatory in state high schools mid 2017<sup>1</sup>   
    - Illinois provided the SAT not only as a mandatory college entrance exam, but also as a measure of school achievement<sup>2</sup>  
---
<sup>1</sup>https://www.testive.com/colorado-sat-change-2017/  
<sup>2</sup>https://chicago.chalkbeat.org/2018/7/27/21105418/illinois-has-embraced-the-sat-and-the-act-is-mad-about-it  


- Correlation -0.87 & -0.79 respectively
- For both SAT tests in 2017 & 2018, as the participation rate increases, the total scores decreases, indicating a negative correlatison between variables
    - This is due to selection bias in college admission test scores<sup>1</sup>, whereby the low participation rate in states represents a small subset of high-achieving students whom chose to take the tests on their own accord

---
<sup>1</sup>https://www.nber.org/system/files/working_papers/w14265/w14265.pdf  

___

## Conclusions and Recommendations
---

The participation rates for both SAT and ACT tests follow a similar distribution across both years, except for a few states like Illinois and Colorado that have adopted doing SAT state-wide due to legislative changes. The ACT has more state-wide adoption, while the SAT is catching up. 

For both tests, the lower the participation rate, the higher the mean scores. The higher the participation rate, the lower the mean scores. Hence, increasing the participation rate for any given state does not equate to higher college acceptance. 

Instead of increasing state participation rates, the college boards could commit resources to preparing and helping the existing students raise their grades, so that more of them qualify for college.