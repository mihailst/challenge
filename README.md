# Coding Challenge

Zuerst importiere ich die Daten in Python

import pandas as pd
url = "http://www.fa-technik.adfc.de/code/opengeodb/DE.tab"

df = pd.read_csv(url, sep='\t', engine='python')


Wir schauen uns durch df.head(n) unser Dataframe an

Export der Zwsichenergebnise
path = "C:\temp\data.csv"
df.to_csv(path)


Statistical metrics check
 
df.describe(include = "all")
 
Data cleansing
df.dropna(subset=["amt"], axis=0)
drop missing values along the column "amt follows 


Alle Records vom Typ = Stadt 
df.loc[df['typ'] == 'Stadt']

Save the data on local machine
df.to_csv("cities.csv", index=False)


Laden der Wetter-Stationen Datei
import pandas as pd
url = "https://www1.ncdc.noaa.gov/pub/data/ghcn/daily/ghcnd-stations.txt"


dfstations = pd.read_csv(url, sep='\t', engine='python')

dfstations.head(5)

 
headers = ["ID","LATITUDE","LONGITUDE","ELEVATION","STATE", "NAME","GSN FLAG",
         "HCN/CRN FLAG","WMO ID"]
print("headers\n", headers)

Ersetzung der Headers
dfstations.columns = headers
dfstations.head(10)


# SQL Queries auf die Tabellen 
--Weather-Daten für alle Stationen
select * from  KHS00651.DATA AS T1
join KHS00651.STATIONS AS T2
ON T1.ID = T2.ID

--Ermittlung TMAX
select * from  KHS00651.DATA AS T1
join KHS00651.STATIONS AS T2
ON T1.ID = T2.ID
where ELEMENT ='TMAX'
