# US-Medical-Insurance-Costs
#import csv library
import csv
#import math library
import math
from statistics import median

#create empty lists to load insurance.csv column by column
ages = []
sexes = []
bmis = []
num_children = []
smoker_statuses = []
regions = []
insurance_charges = []

#create a function to open and load data into respective lists
def load_lst(lst, csv_file, column_name):
    with open(csv_file) as csv_data:
        csv_dict = csv.DictReader(csv_data)
        for row in csv_dict:
            lst.append(row[column_name])
        return lst

#call function to load lists
load_lst(ages, 'insurance.csv', 'age')
load_lst(sexes, 'insurance.csv', 'sex')
load_lst(bmis, 'insurance.csv', 'bmi')
load_lst(num_children, 'insurance.csv', 'children')
load_lst(smoker_statuses, 'insurance.csv', 'smoker')
load_lst(regions, 'insurance.csv', 'region')
load_lst(insurance_charges, 'insurance.csv', 'charges')

insurance_charges = 
['16884.924',
 '1725.5523',
 '4449.462',
 '21984.47061',
 '3866.8552',
 '3756.6216',
 '8240.5896',
 '7281.5056',
 '6406.4107',
 '28923.13692',
 '2721.3208',
 '27808.7251',
 '1826.843',
 '11090.7178',
 '39611.7577',
 '1837.237',
 '10797.3362',
 ...]

#create a dictionary of all medical insurance data where insurance charges are the keys
medical_data = {}
num_of_med_data = len(insurance_charges)

def create_dictionary(ages, sexes, bmis, num_children, smoker_statuses, regions, insurance_charges):
    for i in range(num_of_med_data):
        medical_data[insurance_charges[i]] = {'Age': ages[i], 'Sex': sexes[i], 'BMI': bmis[i], 'Children': num_children[i], 'Smoker': smoker_statuses[i], 'Region': regions[i], 'Insurance Charge': insurance_charges[i]}
    return medical_data

medical_data = create_dictionary(ages, sexes, bmis, num_children, smoker_statuses, regions, insurance_charges)
#print(medical_data)
print(medical_data[insurance_charges[2]])
{'Age': '28', 'Sex': 'male', 'BMI': '33', 'Children': '3', 'Smoker': 'no', 'Region': 'southeast', 'Insurance Charge': '4449.462'}

#find the total number of persons whose insuance data is recorded in insurance.csv/medical_data
total_persons = len(medical_data) + 1
print("We have a complete insurance data of {} persons in the US Medical Insurance Costs dataset.".format(total_persons))
print(range(total_persons))
We have a complete insurance data of 1338 persons in the US Medical Insurance Costs dataset.
range(0, 1338)

#find the mean of the ages 
ages_total = 0
for age in ages:
    ages_total += int(age)

average_age = ages_total/len(ages)
print("Average age of patients: {}.".format(math.floor(average_age)))
Average age of patients: 39.

#find the median of the ages 
sorted_ages = sorted(ages)
#print(sorted_ages)

def getMedian(lst):
    if len(sorted_ages) % 2 == 1:
        return int(sorted_ages[len(sorted_ages)//2])
    else:
        median_lower = int(sorted_ages[len(sorted_ages)//2 - 1])
        median_upper = int(sorted_ages[len(sorted_ages)//2])
        median_ages = (int(median_lower + median_upper)) / 2
        return median_ages
median_ages = getMedian(sorted_ages)
print("The median age of the patients is {}years old.".format(int(median_ages)))    

#check answer
#print(int(sorted_ages[668]))
#print(int(sorted_ages[669]))
The median age of the patients is 39years old.

#find the mean of the bmis 
bmis_total = 0
for bmi in bmis:
    bmis_total += float(bmi)

average_bmi = bmis_total/len(bmis)
print("Average BMI of the patients: {}.".format(round(average_bmi, 3)))
Average BMI of the patients: 30.663.

#find the median of the bmis 
sorted_bmis = sorted(bmis)
#print(sorted_bmis)

def getMedian(lst):
    if len(sorted_bmis) % 2 == 1:
        return sorted_bmis[len(sorted_bmis)//2]
    else:
        median_lower = float(sorted_bmis[len(sorted_bmis)//2 - 1])
        median_upper = float(sorted_bmis[len(sorted_bmis)//2])
        median_bmis = (median_lower + median_upper) / 2
        return median_bmis
median_bmis = getMedian(sorted_bmis)
print("The median BMI of the patients is {}.".format(median_bmis))
The median BMI of the patients is 30.4.

#find the mean of insurance charges 
total_insurance_charges = 0
for charge in insurance_charges:
    total_insurance_charges += float(charge)

average_insurance_charges = total_insurance_charges/len(insurance_charges)
print("Average Insurance Charge: ${}". format(round(average_insurance_charges, 2)))
Average Insurance Charge: $13270.42

#find the median of insurance charges 
insurance_charges.sort()

#///////////////////////////////////////STRETCH/////////////////////////////////////////////////////////////////////

#count the number of smokers
def count(smokers):
    total_smokers = 0
    for i in smoker_statuses:
        if i == 'yes':
            total_smokers += 1
    return total_smokers

num_smokers = count(smoker_statuses)
print("{} of {} are smokers.".format(num_smokers, total_persons))
274 of 1338 are smokers.

#check to see if non smokers = 1338 - 274
def count(smokers):
    total_non_smokers = 0
    for i in smoker_statuses:
        if i == 'no':
            total_non_smokers += 1
    return total_non_smokers

num_non_smokers = count(smoker_statuses)
print("{} of {} are non-smokers.".format(num_non_smokers, total_persons))
1064 of 1338 are non-smokers.
 
#calculate the proportion of smokers and non-smokers
print('About {}% of patients in this dataset are smokers'.format(round((num_smokers/total_persons) * 100), 2))
print('About {}% of patients in this dataset are non-smokers'.format(round((num_non_smokers/total_persons) * 100), 2))
About 20% of patients in this dataset are smokers
About 80% of patients in this dataset are non-smokers

#create a table showing all the attributes as columns
medical_df = pd.read_csv('insurance.csv')
print(medical_df)
      age     sex     bmi  children smoker     region      charges
0      19  female  27.900         0    yes  southwest  16884.92400
1      18    male  33.770         1     no  southeast   1725.55230
2      28    male  33.000         3     no  southeast   4449.46200
3      33    male  22.705         0     no  northwest  21984.47061
4      32    male  28.880         0     no  northwest   3866.85520
...   ...     ...     ...       ...    ...        ...          ...
1333   50    male  30.970         3     no  northwest  10600.54830
1334   18  female  31.920         0     no  northeast   2205.98080
1335   18  female  36.850         0     no  southeast   1629.83350
1336   21  female  25.800         0     no  southwest   2007.94500
1337   61  female  29.070         0    yes  northwest  29141.36030

[1338 rows x 7 columns]

#create a separate file for patients who are smokers
smokers_patients = medical_df[(medical_df.smoker == 'yes')]
print(smokers_patients)
      age     sex     bmi  children smoker     region      charges
0      19  female  27.900         0    yes  southwest  16884.92400
11     62  female  26.290         0    yes  southeast  27808.72510
14     27    male  42.130         0    yes  southeast  39611.75770
19     30    male  35.300         0    yes  southwest  36837.46700
23     34  female  31.920         1    yes  northeast  37701.87680
...   ...     ...     ...       ...    ...        ...          ...
1313   19  female  34.700         2    yes  southwest  36397.57600
1314   30  female  23.655         3    yes  northwest  18765.87545
1321   62    male  26.695         0    yes  northeast  28101.33305
1323   42  female  40.370         2    yes  southeast  43896.37630
1337   61  female  29.070         0    yes  northwest  29141.36030

[274 rows x 7 columns]

#create a separate file for patients who are non-smokers
non_smokers_patients = medical_df[(medical_df.smoker == 'no')]
print(non_smokers_patients)
      age     sex     bmi  children smoker     region      charges
1      18    male  33.770         1     no  southeast   1725.55230
2      28    male  33.000         3     no  southeast   4449.46200
3      33    male  22.705         0     no  northwest  21984.47061
4      32    male  28.880         0     no  northwest   3866.85520
5      31  female  25.740         0     no  southeast   3756.62160
...   ...     ...     ...       ...    ...        ...          ...
1332   52  female  44.700         3     no  southwest  11411.68500
1333   50    male  30.970         3     no  northwest  10600.54830
1334   18  female  31.920         0     no  northeast   2205.98080
1335   18  female  36.850         0     no  southeast   1629.83350
1336   21  female  25.800         0     no  southwest   2007.94500

[1064 rows x 7 columns]

#calculate min, max, and range of patients' ages
max_age = medical_df.age.max()
print("The oldest patient is {} years old".format(max_age))
min_age = medical_df.age.min()
print("The youngest patient is {} years old".format(min_age))
range_age = max_age - min_age
print("Range of ages of patients in this dataset: {} years".format(range_age))
The oldest patient is 64 years old
The youngest patient is 18 years old
Range of ages of patients in this dataset: 46 years

#calculate min, max, and range of patients' charges
max_charge = medical_df.charges.max()
print("The highest amount charged to at least one patient in this dataset is approximately ${}".format(round(max_charge, 2)))
min_charge = medical_df.charges.min()
print("The lowest amount charged to at least one patient in this dataset is approximately ${}".format(round(min_charge, 2)))
range_charge = max_charge - min_charge
print("Range of insurance charges is approximately ${}".format(round(range_charge, 2)))
The highest amount charged to at least one patient in this dataset is approximately $63770.43
The lowest amount charged to at least one patient in this dataset is approximately $1121.87
Range of insurance charges is approximately $62648.55

#print out and inspect data of high-paying patients
high_paying_patients = medical_df[medical_df.charges > 50000]
print(high_paying_patients)
      age     sex     bmi  children smoker     region      charges
34     28    male  36.400         1    yes  southwest  51194.55914
543    54  female  47.410         0    yes  southeast  63770.42801
577    31  female  38.095         1    yes  northeast  58571.07448
819    33  female  35.530         0    yes  northwest  55135.40209
1146   60    male  32.800         0    yes  southwest  52590.82939
1230   52    male  34.485         3    yes  northwest  60021.39897
1300   45    male  30.360         0    yes  southeast  62592.87309

#visualize how different attributes may or may not have been influential towards the insurance charge
#smoker(yes or no)
sns.boxplot(data = medical_df, x = 'smoker', y = 'charges')
plt.show()

#number of children
plt.scatter(x = medical_df.children, y = medical_df.charges)
plt.xlabel('Number of Children')
plt.ylabel('Insurance Charge ($)')
plt.show()

#age
plt.scatter(x = medical_df.age, y = medical_df.charges)
plt.xlabel('Age (Years)')
plt.ylabel('Insurance Charge ($)')
plt.show()

#BMI
plt.scatter(x = medical_df.bmi, y = medical_df.charges)
plt.xlabel('BMI')
plt.ylabel('Insurance Charge ($)')
plt.show()

#region
sns.boxplot(data = medical_df, x = 'region', y = 'charges')
plt.show()

#sex
sns.boxplot(data = medical_df, x = 'sex', y = 'charges')
plt.show()

#calculate pearson correlation to check the strength of the linear relationship between insurance charges and the other quantitative variables(number of children , age, and bmi)
#number of children
corr_children_charges, p = pearsonr(medical_df.children, medical_df.charges)
print("The correlation coefficient of {} indicates no linear association between the number of children a patient has and the insurance payment charged to them.".format(round(corr_children_charges, 1)))

#age
corr_age_charges, p = pearsonr(medical_df.age, medical_df.charges)
print("The correlation coefficient of {} indicates a linear association between a patient's age and the insurance payment charged to them.".format(round(corr_age_charges, 1)))

#BMI
corr_bmi_charges, p = pearsonr(medical_df.bmi, medical_df.charges)
print("The correlation coefficient of {} indicates a linear association between a patient's BMI and the insurance payment charged to them.".format(round(corr_bmi_charges, 1)))

The correlation coefficient of 0.1 indicates no linear association between the number of children a patient has and the insurance payment charged to them.
The correlation coefficient of 0.3 indicates a linear association between a patient's age and the insurance payment charged to them.
The correlation coefficient of 0.2 indicates a linear association between a patient's BMI and the insurance payment charged to them.


#FINDINGS
1. The insurance.csv dataset contains the data(seven attributes) of 1338 persons
2. The mean and median age of the patients are both 39 years. The oldest patient is 64 years old while the youngest is 18years old, putting the range at 46years. The scatter plot of charges vs age indicates a linear association between a patient's age and their insurance charge. The higher the age, the higher the insurance charge.
3. The mean and median BMI of the patients are 30.663 and 30.4 respectively. The scatter plot of charges vs BMI indicates a linear association between a patient's BMI and their insurance charge. The higher the BMI, the higher the insurance charge.
4. The average Insurance charge is $13,270.42 while the median insurance charge is $17,390.7275. The highest amount charged to at least one patient is approximately $63770.43 while the lowest amount charged to at least one patient is approximately $1121.87
5. About 20% of the patients are smokers. The side by side boxplot of charges vs smoker showing no overlap between the boxes, indicates that the smoker status of a patient is influential towards their insurance charge. 
6. All the patients are from either of the four regions: southwest, southeast, northwest, and northeast. An overlap in the boxes on the side by side boxplot of charges vs region indicates that location had no impact on insurance charge.

#Note:
patients and persons are used interchangeably in this analysis