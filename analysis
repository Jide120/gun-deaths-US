
# coding: utf-8

# In[2]: US Gun Deaths Guided Project Solutions Introducing US Gun Deaths Data


import csv
f = open("guns.csv", "r")
csvreader = csv.reader(f)
data = list(csvreader)
print(data[:5])


# In[3]: Removing Headers From A List Of Lists


headers = data[0]
data = data[1:]
print(headers)
print(data[:5])


# In[6]: Counting Gun Deaths By Year


years = [i[1] for i in data]
year_counts = {}
for year in years:
    if year in year_counts:
        year_counts[year] += 1
    else:
        year_counts[year] = 1
        
print(year_counts)


# In[14]: Exploring Gun Deaths By Month And Year

import datetime
dates = [datetime.datetime(year=int(i[1]), month=int(i[2]), day=1) for i in data]
print(dates[:5])
date_counts = {}
for date in dates:
    if date in date_counts:
        date_counts[date] += 1
    else:
        date_counts[date] = 1
        
print(date_counts)


# In[16]: Exploring Gun Deaths By Race And Sex


def category_count(index):
    categories = [i[index] for i in data]
    category_counts = {}
    for category in categories:
        if category in category_counts:
            category_counts[category] += 1
        else:
            category_counts[category] = 1
    return category_counts

sex_counts = category_count(5)
race_counts = category_count(7)
print(sex_counts)
print(race_counts)


# The most gun deaths seem to occur among white males. 
# 

# In[18]: Reading In A Second Dataset

second_f = open("census.csv", "r")
census = list(csv.reader(second_f))
print(census)


# In[20]: Computing Rates Of Gun Deaths Per Race


mapping = {
    "Asian/Pacific Islander": 15834141,
    "Black": 40250635,
    "Native American/Native Alaskan": 3739506,
    "Hispanic": 44618105,
    "White": 197318956
}

race_per_hundredk = {}
for key in race_counts:
    race_per_hundredk[key] = (race_counts[key]/mapping[key]) * 100000
    
print(race_per_hundredk)


# In[21]: Filtering By Intent


intents = [i[3] for i in data]
races = [i[7] for i in data]
homicide_race_counts = {}

for i, value in enumerate(races):
    if intents[i] == "Homicide":
        if value not in homicide_race_counts:
            homicide_race_counts[value] = 1
        else:
            homicide_race_counts[value] += 1
            
homicide_race_per_hundredk = {}
for key in race_counts:
    homicide_race_per_hundredk[key] = (homicide_race_counts[key]/mapping[key]) * 100000
    
print(homicide_race_per_hundredk)


# Homicides within the Black community far outweigh the number of homicides in any other community per 100000 capita. 
# 
