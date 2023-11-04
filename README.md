# NYC_fire_discpatch

## Docker info:
Containerization is a great way to reproduce the same result without the same physical environment. 
For this project, dockerfile specifies the environments and instruction to build a docker, including the latest python version, requirements for installing, and the pythonfile location with the source code. The docker image is built and run through below command on the terminal. 
- docker build -t bigdataproject1:1.0 .
- docker run -e INDEX_NAME="fire" -e DATASET_ID="8m42-w767" -e APP_TOKEN= "fNKdrt3FWT3VaAcTWPVEAhuyn" -e ES_HOST= "https://search-cis9760-yixin-wu-7kuwho3oqyydzievonaugxcjbq.us-east-2.es.amazonaws.com" -e ES_USERNAME="llulloon" -e ES_PASSWORD="H0h0@0-4je4w5fu" bigdataproject1:1.0 --page_size=100000 --num_pages=50


## Project background: 
This project is using the Fire Incident Dispatch Data from NYC Open Data. 
There's more than eight millions total records, dating back to 2005. 
Each record has 29 attributes, contains the details of the incident, including the created time, the closed time, boroughs, incident type, and etc. 
It is accessed through Socrata Open Data API. 


## Result Analysis
I loaded five million records to AWS open search, dating from 2005 to 2015. 
<img width="640" alt="gauge" src="https://github.com/llulloon/NYC_fire_discpatch/assets/53155883/a83812ea-396d-4c1f-8c3a-93953ad1880a">


First, the fire dispatch incidents are pretty even every year from 2006 to 2014, between from 450,000 to 500,000 incidents. 

<img width="633" alt="bar chart" src="https://github.com/llulloon/NYC_fire_discpatch/assets/53155883/379c82c7-27ba-4013-952d-6ff83421cae6">



Next, does geographical location has a correlation with the incidents?

Brooklyn is the number one boroughs by fire incidents dispatch, followed by Manhattan, Queens and Bronx has significant lower numbers, while Staten Island only takes up 5.24% of all fire dispatch. 
The percentage of Brooklyn and Staten Island incidents are not surprising, since Brooklyn has the 1/3 of of NYC population, while Staten Island only has 5%. But it's interesting to find out that while Queens has the second largest population across five boroughs (3% lower than Brooklyn), the dispatch number is much lower. 

<img width="669" alt="Snipaste_2023-11-03_13-54-26" src="https://github.com/llulloon/NYC_fire_discpatch/assets/53155883/592d32a0-c58a-4684-8b61-f34cfb6bc192">


In term of average response second, Queens also has the longest dispatch time (283 seconds), while Brooklyn has the shortest (243 seconds).  

<img width="670" alt="Snipaste_2023-11-03_13-57-31" src="https://github.com/llulloon/NYC_fire_discpatch/assets/53155883/f30a2c24-db42-4992-9aa1-2e840342517a">



What affects the average dispatch time? 

Fire incidents type has a big influence. From the average dispatch time, clearly medical emergency has the shortest response time  (220 seconds), followed by fires (245-264 seconds), while non-medical emegencies has the longest time (308 seconds). The difference is 80 seconds, more than one minute.  

<img width="664" alt="Snipaste_2023-11-03_14-08-24" src="https://github.com/llulloon/NYC_fire_discpatch/assets/53155883/d5e4bb23-ab2b-4354-8202-a174af20bf22">


That's maybe one reason for Brooklyn's short response time, becasue it has more medical emergencies compare to other booroughs. 

<img width="660" alt="Snipaste_2023-11-03_13-56-22" src="https://github.com/llulloon/NYC_fire_discpatch/assets/53155883/15cd6b92-0d56-452e-8ab1-40bd28557f4c">


One more thing interests me is the alarm source. Fro the area chart, it seems clear that different type of incidents has major alarm source. Medical emergencies is mostly alarmed thorugh specific PD and EMS Medical Link. While non-medical emergencies and fire is alarmed mostly through phone call and 911. This may be another explanation of the shortest response time for medical incidents since they has a dedicated system of alarm. 

<img width="655" alt="Snipaste_2023-11-03_14-36-45" src="https://github.com/llulloon/NYC_fire_discpatch/assets/53155883/5a2b2487-a26e-4cba-b5d1-08ea127fce73">

