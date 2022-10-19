# US-Medical-Insurance-Costs
Disclaimer: Data was obtained from Codecademy website

##SCOPE
1. Load and inspect data
2. Aggregate data - calculate mean, median 
3. Build analysis functions
4. analyze data to determine how some of the variables influence an individual's insurance charge
5. Visualize data using matplotlib and seaborn

##FINDINGS
1. The insurance.csv dataset contains the data(seven attributes) of 1338 persons
2. The mean and median age of the patients are both 39 years. The oldest patient is 64 years old while the youngest is 18years old, putting the range at 46years. The scatter plot of charges vs age indicates a linear association between a patient's age and their insurance charge. The higher the age, the higher the insurance charge.
3. The mean and median BMI of the patients are 30.663 and 30.4 respectively. The scatter plot of charges vs BMI indicates a linear association between a patient's BMI and their insurance charge. The higher the BMI, the higher the insurance charge.
4. The average Insurance charge is $13,270.42 while the median insurance charge is $17,390.7275. The highest amount charged to at least one patient is approximately $63770.43 while the lowest amount charged to at least one patient is approximately $1121.87
5. About 20% of the patients are smokers. The side by side boxplot of charges vs smoker showing no overlap between the boxes, indicates that the smoker status of a patient is influential towards their insurance charge. 
6. All the patients are from either of the four regions: southwest, southeast, northwest, and northeast. An overlap in the boxes on the side by side boxplot of charges vs region indicates that location had no impact on insurance charge.

#Note:
patients and persons are used interchangeably in this analysis
