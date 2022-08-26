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
 
