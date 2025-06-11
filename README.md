# MIDUS-Project
MIDUS (Midlife in the United States) is a national longitudinal study of health and well-being. It collects data on a wide range of physical, psychological, and social factors. The study has been ongoing since the 1990s, with multiple waves of data collection. The purpose of this project is to explore the relationships between physical activity, social/psychological variables, and various health outcomes using the MIDUS datasets. 
# Data Sources:
MIDUS 1: Baseline survey conducted in the 1990s
MIDUS 2: Follow-up survey conducted in the 2000s 
MIDUS 3: Most recent follow-up survey conducted in the 2010s (https://www.google.com/url?q=https%3A%2F%2Fwww.icpsr.umich.edu%2Fweb%2FICPSR%2Fstudies%2F36346) 
Biomarker 1: Collected physical biomarker data from a subset of MIDUS participants (https://www.google.com/url?q=https%3A%2F%2Fwww.icpsr.umich.edu%2Fweb%2FICPSR%2Fstudies%2F38837%2Fpublications) 
Biomarker 2: Collected additional biomarker data from a different subset of MIDUS participants 
# Data Importing and Exploration
The datasets were downloaded as tsv from the Inter-university Consortium for Political and Social Research (ICPSR) website. The specific URLs for the MIDUS 3 and Biomarker 2 datasets were provided. Tsvs were converted into csv and were read in pandas dataframe. 
Individual datasets were merged into merged_data.csv based on the column ‘M2ID’
# Preprocessing of the merged dataset from null and duplicate values: 
Merged_data.csv was cleaned from missing values and duplicate rows and the output was saved to ‘cleaned_dataset.csv’ and ‘cleaned_dataset_no_duplicates.csv’. Variables were renamed from codes to their descriptions for clear understanding.
# Extraction of variables of interest from the merged and cleaned dataset: 
From the merged and cleaned dataset which has renamed columns ‘cleaned_dataset_renamed.csv’, variables of interest were extracted which included variables related to physical activity, psychological variables (eg. Stress, depression, loneliness) and health outcome variables related to blood pressure, chronic kidney disease, breast cancer etc. (these list of these variables is present in the file ‘Variables_final dataset_highlighted’). The dataset ‘final_dataset.csv’ was created with extracted relevant variables from the previous extracted dataset. 
# Feature Engineering:
Identified the relevant columns related to family history of Alzheimer's, breast cancer, stroke, circulation problems, high blood pressure, and heart disease in the final dataset and new columns were created as ‘Family history of Alzheimer’s’, ‘Family history of breast cancer’, ‘Family history of stroke’, ‘Family history of circulation problems’, ‘Family history of high blood pressure’, ‘Family history of heart  disease’, with the binary value sets of (1 for presence, 0 for absence) based on the value sets of columns in the original dataset (If any of the relevant columns had a value of 1 (indicating the presence of the condition), the new variable was set to 1If all the relevant columns had values other than 1 (missing, unknown, no, etc.), the new variable was set to 0).  
# Analysis of correlation between AHA Life essential 8 variables: 
Identified variables that could be coded as one of the 8 variables from AHA life essential 8 (https://www.google.com/url?q=https%3A%2F%2Fwww.heart.org%2Fen%2Fhealthy-living%2Fhealthy-lifestyle%2Flifes-essential-8) as –  eat better, be more active, quit tobacco, get healthy sleep, manage weight, control cholesterol, manage blood sugar and manage blood pressure. The list of identified AHA Life essential 8 variables is uploaded as a document.
Pearson and Spearman Bivariate correlations were analysed of the above variables selecting only women/ females and the result was saved in the file ‘bivariate_correlations_women_pearson.csv’ and the significant correlations was saved in the file ‘significance_matrix_woemn_pearson.csv’, ‘spearman_correlation_results.csv’.
Upon Pearson and Spearman Bivariate correlation analysis in females, the most frequently correlated physical activity variables with other variables are identified as - ‘C4H73AFD = How many times per day do you do exercise/activity A’, ‘C4H73CC = Exercise/Activity C – Coded’ and ‘C4H73DFW = How many days per week do you do exercise/activity D?’ 
# Identification and understanding of physical activity variables in the final dataset: 
The list of physical activity/ exercise related variables in the final dataset are uploaded into a document. 
Based on the documentation in the codebooks of the dataset, the letters (A, B, C, D, E, F, G) represent different types of exercises or physical activities reported by the respondents. From the variable names and labels, we can infer that: 
C4H73AC, C4H73BC, C4H73CC, etc. represent the coded type of activity for each category (A, B, C, etc.). 
C4H73AS, C4H73BS, C4H73CS, etc. indicate whether the activity is seasonal or not. 
C4H73AFD, C4H73BFD, C4H73CFD, etc. represent the frequency per day for each activity. 
C4H73AFW, C4H73BFW, C4H73CFW, etc. represent the frequency per week for each activity. 
C4H73AM, C4H73BM, C4H73CM, etc. represent the average minutes per session for each activity. 
C4H73AI, C4H73BI, C4H73CI, etc. represent the intensity of each activity. 
Looking at the coded values for each activity (e.g., C4H73AC, C4H73BC, etc.), we see categories like: Bicycling, Conditioning exercise, Dancing, Fishing and hunting, Home activities, Home repair, Lawn and garden, Miscellaneous, Music playing, Occupation, Religious activities, Running, Sports, Treadmill, Volunteer activities, Walking, Water activities, Winter activities, Combined activities and Inapp. Among these, the categories that likely represent leisure-time physical activities are identified as: Bicycling, Conditioning exercise, Dancing, Sports, Walking, Water activities, Winter activities and Threadmill.
# Creating refined total physical activity variable: 
The physical activity variables are combined together based on the most frequently correlated physical activity variables (coded activity type variable (e.g., C4H73AC, C4H73BC, etc.), and the corresponding variables for frequency per week (C4H73AFW), minutes per session (C4H73BM), and intensity (C4H73BI)) into one "total physical activity" variable which can tell us how many minutes of physical activity per week.  
Upon frequency distribution and cross tabulation of coded activity type variable (e.g., C4H73AC, C4H73BC, etc.), and the corresponding variables for frequency per week (C4H73AFW), minutes per session (C4H73BM), and intensity (C4H73BI), here are the summary of the findings: 
Exercise/Activity A: 
Walking (16.0) and conditioning exercise (2.0) are the most common activities in category A. 
Most activities in category A are done 3-5 days per week, with an average session duration of 30-60 minutes. 
The intensity of activities in category A is mostly moderate (2.0) or light (3.0). 
Exercise/Activity B: 
Sports (13.0), walking (16.0), and conditioning exercise (2.0) are the most common activities in category B. 
Most activities in category B are done 1-3 days per week, with an average session duration of 30-60 minutes. 
The intensity of activities in category B is mostly moderate (2.0) or light (3.0). 
Exercise/Activity C: 
Lawn and garden (7.0) is the most common activity in category C. 
Most activities in category C are done 3 days per week, with an average session duration of 30-180 minutes. 
The intensity of activities in category C is mostly moderate (2.0) or light (3.0). 
Exercise/Activity D: 
Conditioning exercise (2.0), walking (16.0), and home activities (5.0) are the most common activities in category D. 
Most activities in category D are done 1-2 days per week, with an average session duration of 30-120 minutes. 
The intensity of activities in category D is mostly light (3.0) or moderate (2.0). 
Exercise/Activity E: 
Lawn and garden (7.0), home activities (5.0), and fishing and hunting (4.0) are the most common activities in category E. 
Most activities in category E are done 1-3 days per week, with an average session duration of 30-60 minutes. 
The intensity of activities in category E is mostly light (3.0) or moderate (2.0). 
Exercise/Activity F: 
Home activities (5.0) and conditioning exercise (2.0) are the most common activities in category F. 
Most activities in category F are done 1-3 days per week, with an average session duration of 20-30 minutes. 
The intensity of activities in category F is mostly light (3.0) or moderate (2.0). 
Exercise/Activity G: 
Conditioning exercise (2.0) and lawn and garden (7.0) are the only reported activities in category G. 
Most activities in category G are done 1-7 days per week, with an average session duration of 60-90 minutes. 
The intensity of activities in category G is mostly moderate (2.0) or light (3.0). 
# Analysis of correlation between total_physical_activity variable and other variables in the final dataset: 
The correlation results are saved into the file ‘correlation of total physical activity with other variablescsv’ and ‘spearman_correlation_results.csv’ and correlations for total_physical_activity is saved to ‘physical_activity_correlations.xlsx’. 
# Analysis of time-points of MIDUS and Biomarker datasets to establish temporal relationship between physical activity and biomarkers: 
MIDUS 3 (2013-2014): 
Data collection period: May 2013 - November 2014 
This is the third wave of the longitudinal study 
Includes many of the same variables as previous waves, plus some new questions on topics like economic recession experiences 
Can be linked to MIDUS 1 and MIDUS 2 data using the M2ID variable 
MIDUS 2 (including Biomarker Project) (2004-2009): 
Data collection period: 2004-2009  
This is the second wave of the longitudinal study 
The Biomarker Project was conducted from July 30, 2004, to May 31, 2009 
It includes biological and physiological measures not present in the first wave 
Can be linked to other MIDUS datasets using the M2ID variable 
MIDUS 1 (1995-1996): 
Data collection period: 1995-1996 
This was the original baseline survey 
It established the foundation for the longitudinal study 
Key points: 
All waves can be linked using the M2ID variable, allowing for longitudinal analysis 
Many core variables are repeated across waves, with some additions in later waves (e.g., biomarkers in MIDUS 2, recession questions in MIDUS 3) 
MIDUS is designed as a longitudinal study following the same participants over time 
Only living respondents who completed the MIDUS 2 phone interview were eligible for MIDUS 3 
The MIDUS 2 Biomarker Project data can be particularly valuable for comparing biological measures with the MIDUS 3 Biomarker data
# Correlation analysis between total physical activity variables and motivation related variables (in the behaviour models) - Health Belief Model: 
We have identified relevant variables that fit into the above model using the keywords as below: 
Physical Activity:  total_physical_activity 
Depression: 'depress', 'sad', 'blue' 
Motivation: ‘motiv’, ‘energy’, ‘vigor’ 
Attitudes: attitude, fee about, think about 
Self-efficiency: confiden, able to, can do 
Intention: intend, plan to, will 
Perceived severity: serious, severe, consequen 
Perceived benefits: benefit, good for, help 
Perceived barriers: difficult, hard to, prevent 
Subjective norms: others think, expect me to, should 
Perceived behavioural control: control, up to me, decide 
We have identified below relevant variables based on the above key words as per the model -  
Physical Activity variables:  
total_physical_activity  
Depression variables:  
C4Q1A = MASQ Felt sad  
C4Q1L = MASQ Felt depressed  
C4Q3C = CESD I felt that I could not shake off the blues even with the help of my family and friends  
C4Q3F = CESD I felt depressed  
C4Q3R = CESD I felt sad  
C4QCESDDA = CESD Depressive Affect Subscale (C,F,I,J,N,Q,R)  
C4H1V = Have you ever had depression?  
Motivation variables:  
C4Q1AA = MASQ Felt like I had a lot of energy  
Attitudes variables:  
NA 
Self-efficacy variables:  
C4Q1FF = MASQ Was unable to relax  
C4Q4B = PSS Unable to control the important things in your life  
C4Q4D = PSS Confident about your ability to handle your personal problems  
C4Q4G = PSS Able to control irritations in your life  
intention variables:  
Perceived Susceptibility variables: 
Perceived Severity variables:  
Perceived Benefits variables:  
C4Q3C = CESD I felt that I could not shake off the blues even with the help of my family and friends  
Perceived Barriers variables:  
 C4Q4J = SS Difficulties were piling up so high that you couldnt overcome them  
C4AD510 = Sun AM How Difficult To Fall Asleep  
C4AD513 = Sun AM If Woke, Difficulty Getting To Sleep  
Subjective Norms variables:  
NA 
Perceived Behavioral Control variables:  
C4Q4B = PSS Unable to control the important things in your life  
C4Q4G = PSS Able to control irritations in your life  
C4Q4I = PSS Angered because of things that were outside of your control 
The correlation analysis between the above variables and total_physical_activity variable was performed and the result was sabed to ‘total Physical activity_motivation_correlations_MIDUS3_Health Belief Model.csv’ 
# Theory Planned Behaviour Model:
https://cdn.serc.carleton.edu/images/ASCN/change_theories/collection/figure_1._theory_planned_behavior_model_adapted_from_ajzen_2005._456.webp 
We have identified relevant variables that fit into the above model using the keywords as below: 
'Physical Activity': 'total_physical_activity' 
'Attitude': 'attitude', 'feel about', 'think about', 'opinion', 'belief', 'view', 'perception', 'like', 'dislike', 'enjoy', 'value', 'importance' 
'Subjective Norm': 'others think', 'expect me to', 'should', 'social pressure', 'norm', 'peer influence', 'family influence', 'social expectation', 'approval', 'disapproval', 
'Perceived Behavioral Control': 'control', 'up to me', 'decide', 'able to', 'can do', 'confidence', 'self-efficacy', 'capability', 'ease', 'difficulty', 
'Intention': 'intend', 'plan to', 'will', 'aim to', 'goal', 'objective', 'purpose', 'determination', 'motivation', 'commitment', 
'Behavioral Beliefs': 'outcome', 'result in', 'lead to', 'consequence', 'effect', 'impact', 'benefit', 'drawback', 'advantage', 'disadvantage', 
'Normative Beliefs': 'important others', 'approve', 'disapprove', 'social support', 'encouragement', 'discouragement', 'social influence', 'role model', 
'Control Beliefs': 'factors', 'facilitate', 'impede', 'barrier', 'obstacle', 'enabler', 'resource', 'opportunity', 'constraint', 'limitation' 
# The below list of variables were identified relevant to the above behaviour models: 
Physical Activity variables:  
total_physical_activity 
Attitude variables: 
C4Q1U = MASQ Felt like a failure 
C4Q1V = MASQ Felt like I was having a lot of fun 
C4Q1AA = MASQ Felt like I had a lot of energy 
C4Q1EE = MASQ Felt like crying  
C4Q1PP = MASQ Felt like I was choking 
C4Q1QQ = MASQ Looked forward to things with enjoyment 
C4Q1UU = MASQ Felt like I had a lot of interesting things to do 
C4Q1WW = MASQ Felt like I had accomplished a lot 
C4Q1XX = - MASQ Felt like it took extra effort get started 
C4Q1YY = MASQ Felt like nothing was very enjoyable 
C4Q1AAA = MASQ Felt like I had a lot to look forward to 
C4Q1EEE = MASQ Felt like there wasn't anything interesting or fun to do 
C4Q1KKK = MASQ Felt like I am a good person 
C4Q3B = CESD I did not feel like eating; my appetite was poor 
C4Q3P = CESD I enjoyed life 
C4Q3S = CESD I felt that people dislike me 
C4H62 = Since we last interviewed you, have you tried to quit smoking? 
Subjective Norm variables: 
NA 
Perceived Behavioural Control Variables: 
C4Q1FF - MASQ Was unable to relax 
C4Q4B = PSS Unable to control the important things in your life 
C4Q4G = PSS Able to control irritations in your life 
C4Q4I = PSS Angered because of things that were outside of your control 
C4H1A = Have you ever had heart disease? 
C4H1G = Have you ever had anemia or other blood disease? 
C4AD513 = Sun AM If Woke, Difficulty Getting To Sleep 
Family history of heart disease 
The correlation between the above variables are saved to ‘total_Physical_activity_TPB_correlations_MIDUS3.csv’ 
Identifying the variables related to physical activity (at least two timepoints), cancer and cardiovascular related variables along with demographics (age, BMI, sex education, income, etc) and finding correlations between them using z-scores 
The correlations between demographic, physical activity, cancer and cardiovascular variables was calculated and saved as ‘significant_correlations_PA_cancer_CVD_demographics.csv’ and their z scores were saved as ‘significant_correlations_PA_cancer_CVD_demographics_relevant_variables_zscores.csv’ and ‘Z-scores for relevant variables saved to 'significant_correlations_PA_cancer_CVD_demographics_relevant_variables_zscores.csv’.  
Intention Variables: NA 
Behavioral Beliefs variables: NA 
Normative Belief variables: NA 
Control Beliefs variables: NA 
# Theory Determinants: 
Identifying behaviour theory variables and assessing their correlation with the total physical activity variables using z-scores: 
Behaviour theory variables - these are psychological or social correlates to exercise/physical activity (behaviour). Behaviour theories as below - https://people.umass.edu/aizen/tpb.diag.html, https://en.wikipedia.org/wiki/Health_belief_model, https://en.wikipedia.org/wiki/Self-determination_theory.
Based on the above theory models, the below relevant variables are identified from the dataset ‘final_dataset_updated’ -  
#  Correlation analysis of Theory planned behaviour model variables: 
he correlation between above TPB variables are saved in ‘significant_correlations_TPB_PA_according_to_Theory_of_Planned_Behavior_model_zscores.csv’ and their Z scores are saved in ‘TPB_variables_PA_zscores_according_to_Theory_of_Planned_Behavior_model.csv’. 
The significant correlations between HBM variables and total physical activity according to Health Belief Model are saved to ‘significant_correlations_HBM_PA_according_to_Health_Belief_Model_zscores.csv’ and their Z-scores are saved to 'HBM_variables_PA_zscores_according_to_Health_Belief_Model.csv'. 
# Correlation analysis of Self Determination Theory: 
The Significant correlations between SDT variables and total physical activity according to Self-Determination Theory are saved in the file ‘significant_correlations_SDT_PA_according_to_Self_Determination_Theory_zscores.csv' and their Z-scores are saved to ‘'SDT_variables_PA_zscores_according_to_Self_Determination_Theory.csv'. 
# Correlation analysis of social cognitive learning theory: 
The Significant correlations between SCLT variables and total physical activity according to Social Cognitive Learning Theory are saved as ‘significant_correlations_SCLT_PA_according_to_Social_Cognitive_Learning_Theory_zscores.csv’ and their z-scores are saved as Z-scores for SCLT variables and physical activity saved to 'SCLT_variables_PA_zscores_according_to_Social_Cognitive_Learning_Theory.csv. 
# Interpretations of the above correlations between model variables and total physical activity: 
Based on the significant correlations between the model variables and total physical activity, the below are the interpretations for each each theoretical model. 
# Health Belief Model (HBM): 
The HBM results suggest that perceived severity of health conditions is strongly associated with physical activity. People who have experienced various health issues (e.g., cholesterol problems, high blood pressure, diabetes) tend to be more physically active. This could indicate that experiencing health problems motivates individuals to engage in preventive behaviors like exercise. 
Cues to action, particularly exposure to secondhand smoke, are positively correlated with physical activity. This unexpected result might suggest that awareness of health risks in one's environment could motivate healthier behaviors in other areas. 
Perceived barriers, such as feeling that everything is an effort, are negatively associated with physical activity, which aligns with the model's predictions. 
Self-efficacy shows a positive correlation with physical activity, supporting the idea that confidence in one's abilities promotes healthier behaviors. 
Perceived susceptibility shows mixed results, with some family history factors positively correlated and others negatively correlated with physical activity. 
# Theory of Planned Behavior (TPB): 
Attitudes towards life satisfaction and well-being show the strongest positive correlations with physical activity. This suggests that individuals who have a more positive outlook on life are more likely to engage in physical activity. 
Subjective norms, particularly those related to receiving respect or sympathy from others, show negative correlations with physical activity. This unexpected result might indicate that individuals who are less concerned with others' opinions are more likely to engage in physical activity. 
Perceived behavioral control variables all show positive correlations with physical activity, supporting the theory's prediction that individuals who feel more in control of their actions are more likely to engage in planned behaviors like exercise. 
# Self-Determination Theory (SDT): 
Intrinsic motivation shows the strongest positive correlations with physical activity. Feeling energetic, lively, and having interesting things to do are all associated with higher levels of physical activity. This supports the SDT's emphasis on intrinsic motivation as a key factor in sustained behavior. 
Competence, another key component of SDT, also shows positive correlations with physical activity. Feeling accomplished and proud of oneself is associated with higher levels of physical activity. 
Autonomy, represented by feelings of control and being on top of things, shows positive correlations with physical activity, aligning with SDT's predictions. 
Relatedness shows mixed results, with some loneliness indicators negatively correlated and others positively correlated with physical activity. 
Extrinsic motivation shows negative correlations with physical activity, which is consistent with SDT's proposition that external motivators are less effective for sustaining behaviors than intrinsic ones. 
# Social Cognitive Learning Theory (SCLT): 
Outcome expectations, particularly those related to life satisfaction and achieving important life goals, show the strongest positive correlations with physical activity. This supports SCLT's emphasis on the role of expected outcomes in shaping behavior. 
Self-efficacy shows positive correlations with physical activity, aligning with SCLT's central tenet that belief in one's abilities influences behavior. 
Sociostructural factors like gender, marital status, and education level show significant correlations with physical activity, highlighting the importance of environmental and personal factors in shaping behavior. 
Goals, specifically the goal to give back to society, shows a negative correlation with physical activity. This unexpected result might warrant further investigation. 
Overall, these results provide support for aspects of each theory while also highlighting areas that may require further research or refinement in the context of physical activity behavior.




