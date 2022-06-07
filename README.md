# Predicting-Autism-in-Toddlers-

In this project, I applied machine learning techniques such as decision trees, random forest, multiple logistic regression, and naive Bayes to detect Autism Spectrum Disorder (ASD) in toddlers. Autistic Spectrum Disorder (ASD) is a neurodevelopmental condition associated with significant healthcare costs, and early diagnosis can significantly reduce these. It leads to numerous impairments in the spheres of social interaction, communication, the use of language, and imagination. In 2021, the Centre for Diseases Control (CDC) reported that 1 in 44 children in the United States was diagnosed with autism. Globally, the World Health Organization (WHO) quantifies that 1 in 100 children have autism. ASD has a detrimental impact on individuals. 31% of children with ASD face intellectual disability (intelligence quotient < 70) with significant challenges in daily function. Moreover, 28% of 8-year-old children with ASD have self-injurious behaviors, and two-thirds of children with ASD between the ages of 6 and 15 have been bullied. The cost of caring for Americans with ASD was $268 billion in 2015 and was projected to rise to $461 billion

ASD is diagnosed by looking for signs of development decays. Doctors analyze a patient’s development history and behavior in social interactions, learning, communication, and movement to make a diagnosis. ASD can be diagnosed as early as 18 months of age or young, and a diagnosis by an experienced professional by the age of 2 is usually considered reliable. The early detection of ASD is crucial because it permits intensive behavioural and education interventions at the earliest age possible, which may lead to better long-term outcomes by capitalizing on the brain’s neuroplasticity at a young age. However, most patients are not diagnosed, and hence do not receive the appropriate treatment, till a later age. This is especially true for lower socioeconomic groups and minority ethnicities. This is because they may be unable to afford to consort expert, who may charge as much as $500, and may believe that it is normal for their child to be socially excluded and unable to resonate with others because of their different culture.

The dataset used was downloaded from Kaggle (https://www.kaggle.com/datasets/fabdelja/autism-screening-for-toddlers), and was generated using an app, the ASD Tests Screening App. The app involved someone answering questions pertaining to the traits of toddlers. Based on the responses, a diagnosis was generated. It included 1054 datapoints.

The following explanatory variables were used (for questions A1-A10, Sex, Ethnicity, Born with Jaundice, Family member with ASD history, and Who is completing the test the responses were converted to factors)  :
1. A1:  Does your child look at you when you call his/her name?
2. A2: How easy is it for you to get eye contact with your child? 
3. A3: Does your child point to indicate that s/he wants something? (e.g. a toy that is 
out of reach) 
4. A4: Does your child point to share interest with you? (e.g. pointng at an 
interesting sight) 
5. A5: Does your child pretend? (e.g. care for dolls, talk on a toy phone) 
6. A6: Does your child follow where you’re looking? 
7. A7: If you or someone else in the family is visibly upset, does your child show signs 
of wantng to comfort them? (e.g. stroking hair, hugging them)
8. A8: Would you describe your child’s first words as: 
9. A9: Does your child use simple gestures? (e.g. wave goodbye) 
10. A10: Does your child stare at nothing with no apparent purpose? 
11. Age (in months)
12. Sex
13. Ethnicity
14. Born with jaundice
15. Family member with ASD history
16. Who is completing the test

The aformentioned variables were used to predict the Class variable (which was either yes or no, based on the ASD diagnosis), which was converted to a factor.

