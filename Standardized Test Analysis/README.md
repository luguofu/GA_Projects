# Project 1: Standardized Test Analysis

### Lo Kok Fu DSIF 2


### Problem Statement
Given that in 2016, the SATs and ACTs underwent a revamp. we want to study the participation rate for both tests from the southern region (Alabama, Arkansas, Delaware, Florida, Georgia, Kentucky, Louisiana, Maryland, Mississippi, North Carolina, Oklahoma, South Carolina, Tennesse, Texas, Virginia, West Virginia, District of Columbia) of the United States from then till 2019. 

We seek to identify trends in the data and to identify a state to be best recommended for College Board fund investment to boost SAT participation rates.and to provide recommendations for increasing of participation rate if necessary

The analysis will be split into the four relevant regions in the USA (Northeast, Midwest, South & West) and conclude with an overall recommended state. 

* I will only be covering the South Region while the rest of the regions are covered by the rest of the individuals in the group project. we will be combining the data and anaylsis for our presentation.


### Executive Summary

This project aims to analyze the data for student participation rates and scores by states in the southern region(combined states observations and recommendations to be presented in the group presentation). The data are organized into state level containing 2017, 2018, 2019 SAT/ACT participation rates, total and composite scores. This allows us to conduct a state by state comparison of data and observations.

A strong negative correlation is observed between ACT and SAT participation whereby states with more ACT participation, there would be low SAT participation as expected. the other strong negative correlation is between the participation rate and scores of both SAT and ACT exams. it is observed that increased participation would result in lower average scores. this is evident of selection bias. Hence, comparison of average scores among states with large participation rate should be avoided.

Participation rates in the South are healthy with no states falling below 50% participation in both ACT and SAT. It is also noteable that full participation of ACT/ SAT tests are driven by state policy requirements. 

For 2019, Virginia is the least performing state participation for SAT and ACT participation rates combined. Thus, we will be recommending Virginia from the southern region for College Board fund investment.

SAT school day is evidently able to encourage increase participation rate evidently from Florida's data. states with low participation rate should adopt such programmes to increase participation rate.


### External Sources

we can see from our external research gathered from edweek.org, that most of the states favour ACT over SATs.but in 2019, states are increasingly starting to shift towards to SAT testing as part of their graduation citeria. whilst there are still a number of states still requires their students to take their school administered end of courses while leaving the ACT/SAT as an option to supplement the students' citeria to graduate. we also can see that there was a significant shift for Delaware (source: whhy.org) and West virginia to adopt SAT as their state test.

the colleage school board has also implemented SAT school day to increase easier access to convinence and comfort, whereby SAT supportive states offers students to take the SAT test in the schools instead of trying to look for a testing center to participate in the test and the comfort of familiar surroundings and students taking the test. they also offered confindence practice testing whereby free, personalized practice plans for all students. 'Official SAT Practice on Khan Academy® provides every student with a practice plan built just for them, along with integrated coaching tools for teachers to view progress and support their students'.(quoted from https://collegereadiness.collegeboard.org/sat/k12-educators/sat-school-day/about#:~:text=SAT%20School%20Day%20provides%20schools,accepted%20at%20all%20U.S.%20colleges.).

Florida has also seen a significant shift to SAT test taking attributed to the SAT school day programme. it is worth studying the usefullness of this programe to drive up voluntary participation rates.

with these observations. SAT participation rates may still be increasingly popular as times goes by until the ACT board steps up its effort to entice students to take the ACT test to increase participation.

sources: 

* state requirements 16-17: https://www.edweek.org/leadership/what-tests-did-each-state-require-in-2016-17
* state requirements 18-19: https://www.edweek.org/teaching-learning/what-tests-does-each-state-require
* delware shift to SAT: https://whyy.org/articles/sat-to-the-rescue-why-delaware-and-other-states-are-embracing-a-new-role-for-an-old-test/ 
* which states requires the SAT or ACT: https://blog.prepscholar.com/which-states-require-the-act-full-list-and-advice    
* florida shifts to SAT: https://www.orlandosentinel.com/news/education/os-ne-sat-scores-florida-20190924-2ycpuogc2ndkrkwzdrkrjgrg64-story.html
* SAT school day: https://collegereadiness.collegeboard.org/sat/k12-educators/sat-school-day/about


### Dataset Dictionary for merged_act_sats_south_reg.csv

|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|act_2017.csv|State Name
|participation_act_17|float|act_2017.csv|Participation rate
|composite_act_17|float|act_2017.csv|Average Composite scores
|---|---|---|---|
|state|object|act_2018.csv|State Name
|participation_act_18 |float|act_2018.csv|Participation rate
|act_comp_18|float|act_2018.csv|Average Composite scores
|---|---|---|---|
|state|object|act_2019.csv|State Name
|participation_act_19|int|act_2019.csv|Participation rate
|composite_act_19|float|act_2019.csv|Average Composite scores
|---|---|---|---|
|state|object|sat_2017.csv|State Name
|participation_sat_17|float|sat_2017.csv|Participation rate
|total_sat_17|int|sat_2017.csv|Average Total scores
|---|---|---|---|
|state|object|sat_2018.csv|State Name
|participation_sat_18|int|sat_2018.csv|Participation rate
|sat_total_18|int|sat_2018.csv|Average Total scores
|---|---|---|---|
|state|object|sat_2019.csv|State Name
|participation_sat_19|int|sat_2019.csv|Participation rate
|sat_total_19|int|sat_2019.csv|Average Total scores


### Conclusion

Overall, the participation rate for the southern states are healthy in the region. The states does not fall within the region of less than 50 % participation for both tests. high participation rates are state policy driven as we can see in delware, alabama, arkansas, kentucky, louisiana, mississippi, north carolina and oklahoma participation rates data.

SATs school days is observed to be able to help in driving up voluntary participation rates as seen in Florida.

It is observed that Virginia was the lowest participation rate for SAT and ACT in 2019,


### Recommendations

We will be recommending Virginia to the College board fund investment to boost their SAT scores due to their low participation rate for both SAT and ACT in 2019.

It also noteable that SAT school day is evidently fruitful in assisting states to increase their participation as seen in Florida. This programme can be adopted for Viriginia and or any other states with non testing policy driven states with low participation rates.
1. whereby the easing of locating a testing center where student can take the test in their schools, giving the studet more comfort and familiar with the surrounding of environment and people.
2. School test day, the test to be conducted on a week day in school as part of the school's schedule. students need not take time off to participate in the the test or disruption of work schedule or family time.
3. builds confidence for students through offering of practice plans for tests
4. financial support for low income students for application of colleges

There are some states that still offers end of course tests as part of their graduation requirement. We will recommend states to drop these tests as a requirement for students to graduate high school, as this would reduce the load of tests that students would need to take and elimate different standards among all the states. we will propose for national test taking for either SAT or the ACT. schools could provide pre-assessment of their students to which test that the students are more incline to perform better and recommend students to take up either the ACT or SAT test. with this recommendation, states are better able to judge their performance and participation across all states.

Lastly, it is observed that SAT test scores are on the decline, thus it is also recommended that the colleage board look into how we can improve the student scores. More participation dosen't mean it is good. we will also want students to score better through better preparation and guidance. We will also need to take note of selection bias of data comparisons. there should be two groups of comparison whereby the 1st group will be comparisons between voluntary taking of test versus results and the 2nd group to be among state policy test driven  results. this recommendation would avoid selection bias and provide a more accurate result.

