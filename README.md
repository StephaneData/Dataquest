# Dataquest
Training in dataquest

# coding: utf-8

# In[1]:


import csv


# In[2]:


f=open("guns.csv")
data=list(csv.reader(f))


# In[3]:


print(data[0:5])


# In[4]:


headers=data[0]
data=data[1:]
print(headers)
print(data[0:5])


# In[5]:


years=[row[1]for row in data]


# In[6]:


year_counts={}
for year in years:
    if year in year_counts:
        year_counts[year]=year_counts[year] + 1
    else:
        year_counts[year]= 1


# In[7]:


print(year_counts)


# In[ ]:





# In[8]:


print(headers)


# In[9]:


import datetime

dates = [datetime.datetime(year=int(row[1]), month=int(row[2]), day=1) for row in data]
dates[:5]


# In[10]:


date_counts = {}

for date in dates:
    if date not in date_counts:
        date_counts[date] = 0
    date_counts[date] += 1

date_counts


# In[11]:


sexes = [row[5] for row in data]
sex_counts = {}
for sex in sexes:
    if sex not in sex_counts:
        sex_counts[sex] = 0
    sex_counts[sex] += 1
sex_counts


# In[12]:


races = [row[7] for row in data]
race_counts = {}
for race in races:
    if race not in race_counts:
        race_counts[race] = 0
    race_counts[race] += 1
race_counts


# In[13]:


import csv

with open("census.csv", "r") as f:
    reader = csv.reader(f)
    census = list(reader)
    
census


# In[14]:


mapping = {
    "Asian/Pacific Islander": 15159516 + 674625,
    "Native American/Native Alaskan": 3739506,
    "Black": 40250635,
    "Hispanic": 44618105,
    "White": 197318956
}



# In[15]:


race_per_hundredk={}
for k,v in race_counts.items():
    race_per_hundredk[k]=(v/mapping[k])*10000
race_per_hundredk


# In[20]:


intents = [row[3] for row in data]
homicide_rate_counts={}

for i, race in enumerate(races):
    if race not in homicide_rate_counts:
        homicide_rate_counts[race] = 0
    if intents[i] == "Homicide":
        homicide_rate_counts[race] += 1


# In[21]:


print(homicide_rate_counts)


# In[22]:


race_per_hundredk={}
for k,v in homicide_rate_counts.items():
    race_per_hundredk[k]=(v/mapping[k])*10000
race_per_hundredk


# In[ ]:




