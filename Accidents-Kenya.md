## MAIN CAUSES OF ROAD ACCIDENTS IN KENYA
In this project, I'd be trying to establish which Counties in Kenya lead in fatal road crushes, using a csv data file that was compiled by Waweru Fidelis in August 2021, and saved as **accidents-kenya.csv** in the Kaggle website. 

Human mistakes, particularly with respect to drivers and pedestrians, is the main accident cause in Kenyan roads, while drivers have been blamed for careless or even drunken driving, pedestrians have been known to spurn traffic rules by crossing the streets at non-assigned points and disrespecting the traffic lights.

Road traffic crashes exert a huge burden on Kenya's economy and health care services. Current interventions are sporadic, uncoordinated and ineffective. Over three thousand people are killed annually on Kenyan roads. A four-fold increase in road fatalities has been experienced over the last 30 years. More than 75% of road traffic casualties are economically productive young adults. Pedestrians and passengers are the most vulnerable; they account for 80% of the deaths. Buses and matatus are the vehicles most frequently involved in fatal crashes.

Nairobi County is the leading in the number of fatal crushes,followed by Kiambu and Nakuru, according to Waweru Fidelis' dataset as recorded on https://www.kaggle.com/waawerufidelis/accidents-kenya.

### Data Exploration
Importing NumPy,Pandas,Matplotlib and Seaborn libraries, and reading the **accidents-kenya.csv** file into a Pandas DataFrame.


```python
import numpy as np
import pandas as pd
from matplotlib import pyplot as plt
import seaborn as sns
# Reading the csv file into pandas dataframe and assigning it to the variable accidents_kenya
accidents_kenya = pd.read_csv('accidents-database-.csv')
accidents_kenya
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>TIME 24 HOURS</th>
      <th>BASE/SUB BASE</th>
      <th>COUNTY</th>
      <th>ROAD</th>
      <th>PLACE</th>
      <th>MV INVOLVED</th>
      <th>BRIEF ACCIDENT DETAILS</th>
      <th>NAME OF VICTIM</th>
      <th>GENDER</th>
      <th>AGE</th>
      <th>CAUSE CODE</th>
      <th>VICTIM</th>
      <th>NO.</th>
      <th>Date DD/MM/YYYY</th>
      <th>Unnamed: 14</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>630</td>
      <td>KITUI</td>
      <td>MAKUENI</td>
      <td>KITUI-ITHOKWE</td>
      <td>KITUI SCHOOL</td>
      <td>KAV 479E &amp; KMCZ 732L SKYGO</td>
      <td>HEAD ON COLLISION</td>
      <td>UNKNOWN</td>
      <td>M</td>
      <td>26</td>
      <td>7</td>
      <td>M/CYCLIST</td>
      <td>1</td>
      <td>06/25/16</td>
      <td>so MM/DD/YYYY is the solution :)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>830</td>
      <td>VOI</td>
      <td>TAITA TAVETA</td>
      <td>MOMBASA-NAIROBI</td>
      <td>IKANGA</td>
      <td>KCC 763/ZF 0097 MAKE RENAULT TRUCK &amp; KMDN 759R...</td>
      <td>HEAD ON COLLISION</td>
      <td>UNKNOWN</td>
      <td>M</td>
      <td>28</td>
      <td>25</td>
      <td>M/CYCLIST</td>
      <td>1</td>
      <td>06/25/16</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1330</td>
      <td>MARIAKANI</td>
      <td>KILIFI</td>
      <td>MOMBASA-NAIROBI</td>
      <td>KATOLANI</td>
      <td>KMDK 017U HAOJIN</td>
      <td>THE UNKNOWN M/V HIT THE MOTOR CYCLE</td>
      <td>UNKNOWN</td>
      <td>M</td>
      <td>A &amp; J</td>
      <td>98</td>
      <td>M/CYCLIST</td>
      <td>1</td>
      <td>06/25/16</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2100</td>
      <td>ONGATA RONGAI</td>
      <td>NAKURU</td>
      <td>NAKURU-NAIROBI</td>
      <td>MAASAI LODGE</td>
      <td>KAL 900K RANGE ROVER</td>
      <td>THE VEHICLE KNOCKED DOWN A PEDESTRIAN WHO WAS ...</td>
      <td>UNKNOWN</td>
      <td>M</td>
      <td>65</td>
      <td>29</td>
      <td>PEDESTRIAN</td>
      <td>1</td>
      <td>06/25/16</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1900</td>
      <td>MATUU</td>
      <td>MACHAKOS</td>
      <td>MATUU-MWINGI</td>
      <td>KIVANDINI</td>
      <td>KAQ 865Z TOYOTA COROLLA</td>
      <td>THE VEHICLE OVERTOOK A M/CYCLE AND LOST CONTRO...</td>
      <td>UNKNOWN</td>
      <td>M</td>
      <td>A</td>
      <td>10</td>
      <td>PASSENGER</td>
      <td>1</td>
      <td>06/25/16</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1114</th>
      <td>1730</td>
      <td>KURIA</td>
      <td>MIGORI</td>
      <td>NTIMARU-KEHANCHA</td>
      <td>TARANGANYA SHOPPING CENTRE</td>
      <td>GK B 529 ISUZU DMAX &amp; M/J/PED</td>
      <td>THE VEHICLE KNOCKED DOWN A PEDESTRIAN</td>
      <td>CHARLES MUNATI</td>
      <td>M</td>
      <td>J</td>
      <td>36</td>
      <td>PEDESTRIAN</td>
      <td>1</td>
      <td>2/22</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1115</th>
      <td>1930</td>
      <td>SAGANA</td>
      <td>KIRINYAGA</td>
      <td>KENOL-MAKUTANO</td>
      <td>WACHORO AREA</td>
      <td>KBU 591M/ZF 5724 SCANIA &amp; KMEA 508C TIGER</td>
      <td>THE CYCLE HIT THE STATIONARY VEHICLE</td>
      <td>UNKNOWN</td>
      <td>M</td>
      <td>A</td>
      <td>37</td>
      <td>RIDER AND P/PASSENGER</td>
      <td>2</td>
      <td>2/22</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1116</th>
      <td>2145</td>
      <td>DTEO KASARANI</td>
      <td>NAIROBI</td>
      <td>THIKA RD</td>
      <td>CAR WASH AREA</td>
      <td>KCH 357W T/IST &amp; M/A/PED</td>
      <td>THE VEHICLE KNOCKED DOWN A PEDESTIRAN</td>
      <td>COLLINS KIARIE</td>
      <td>M</td>
      <td>20</td>
      <td>98</td>
      <td>PEDESTRIAN</td>
      <td>1</td>
      <td>2/22</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1117</th>
      <td>2039</td>
      <td>KANGUNDO</td>
      <td>MAKUENI</td>
      <td>NAIROBI-KANGUNDO</td>
      <td>MAKENZIE AREA</td>
      <td>KCC 374L HINO MINIBUS &amp; KMCG 188U SKYGO</td>
      <td>THE VEHICLE COLLIDED HEAD ON WITH THE M/CYCLE</td>
      <td>BENARD MUTUNGA</td>
      <td>M</td>
      <td>36</td>
      <td>82</td>
      <td>RIDER</td>
      <td>1</td>
      <td>2/22</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1118</th>
      <td>139</td>
      <td>DTEO DAGORETI</td>
      <td>NAIROBI</td>
      <td>WAIYAKI WAY</td>
      <td>KANGEMI STAGE</td>
      <td>KBR 741X HONDA CRV &amp; M/A/PED</td>
      <td>THE VEHICLE KNOCKED DOWN A PEDESTRIAN</td>
      <td>UNKNOWN</td>
      <td>M</td>
      <td>A</td>
      <td>98</td>
      <td>PEDESTRIAN</td>
      <td>1</td>
      <td>2/22</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1119 rows × 15 columns</p>
</div>




```python
accidents_kenya.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1119 entries, 0 to 1118
    Data columns (total 15 columns):
     #   Column                  Non-Null Count  Dtype 
    ---  ------                  --------------  ----- 
     0   TIME 24 HOURS           1114 non-null   object
     1   BASE/SUB BASE           1117 non-null   object
     2   COUNTY                  1116 non-null   object
     3   ROAD                    1116 non-null   object
     4   PLACE                   1113 non-null   object
     5   MV INVOLVED             1119 non-null   object
     6   BRIEF ACCIDENT DETAILS  1118 non-null   object
     7   NAME OF VICTIM          1118 non-null   object
     8   GENDER                  1119 non-null   object
     9   AGE                     1118 non-null   object
     10  CAUSE CODE              1091 non-null   object
     11  VICTIM                  1119 non-null   object
     12  NO.                     1115 non-null   object
     13  Date DD/MM/YYYY         1119 non-null   object
     14  Unnamed: 14             2 non-null      object
    dtypes: object(15)
    memory usage: 131.3+ KB


### Data Cleaning

Drpping all the rows that are not relevant to the objective of the project from the **accidents_kenya** DataFrame.


```python
accidents_kenya.drop(['ROAD', 'PLACE', 'MV INVOLVED', 'NAME OF VICTIM', 'AGE', 'CAUSE CODE'], axis = 1)

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>TIME 24 HOURS</th>
      <th>BASE/SUB BASE</th>
      <th>COUNTY</th>
      <th>BRIEF ACCIDENT DETAILS</th>
      <th>GENDER</th>
      <th>VICTIM</th>
      <th>NO.</th>
      <th>Date DD/MM/YYYY</th>
      <th>Unnamed: 14</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>630</td>
      <td>KITUI</td>
      <td>MAKUENI</td>
      <td>HEAD ON COLLISION</td>
      <td>M</td>
      <td>M/CYCLIST</td>
      <td>1</td>
      <td>06/25/16</td>
      <td>so MM/DD/YYYY is the solution :)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>830</td>
      <td>VOI</td>
      <td>TAITA TAVETA</td>
      <td>HEAD ON COLLISION</td>
      <td>M</td>
      <td>M/CYCLIST</td>
      <td>1</td>
      <td>06/25/16</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1330</td>
      <td>MARIAKANI</td>
      <td>KILIFI</td>
      <td>THE UNKNOWN M/V HIT THE MOTOR CYCLE</td>
      <td>M</td>
      <td>M/CYCLIST</td>
      <td>1</td>
      <td>06/25/16</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2100</td>
      <td>ONGATA RONGAI</td>
      <td>NAKURU</td>
      <td>THE VEHICLE KNOCKED DOWN A PEDESTRIAN WHO WAS ...</td>
      <td>M</td>
      <td>PEDESTRIAN</td>
      <td>1</td>
      <td>06/25/16</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1900</td>
      <td>MATUU</td>
      <td>MACHAKOS</td>
      <td>THE VEHICLE OVERTOOK A M/CYCLE AND LOST CONTRO...</td>
      <td>M</td>
      <td>PASSENGER</td>
      <td>1</td>
      <td>06/25/16</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1114</th>
      <td>1730</td>
      <td>KURIA</td>
      <td>MIGORI</td>
      <td>THE VEHICLE KNOCKED DOWN A PEDESTRIAN</td>
      <td>M</td>
      <td>PEDESTRIAN</td>
      <td>1</td>
      <td>2/22</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1115</th>
      <td>1930</td>
      <td>SAGANA</td>
      <td>KIRINYAGA</td>
      <td>THE CYCLE HIT THE STATIONARY VEHICLE</td>
      <td>M</td>
      <td>RIDER AND P/PASSENGER</td>
      <td>2</td>
      <td>2/22</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1116</th>
      <td>2145</td>
      <td>DTEO KASARANI</td>
      <td>NAIROBI</td>
      <td>THE VEHICLE KNOCKED DOWN A PEDESTIRAN</td>
      <td>M</td>
      <td>PEDESTRIAN</td>
      <td>1</td>
      <td>2/22</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1117</th>
      <td>2039</td>
      <td>KANGUNDO</td>
      <td>MAKUENI</td>
      <td>THE VEHICLE COLLIDED HEAD ON WITH THE M/CYCLE</td>
      <td>M</td>
      <td>RIDER</td>
      <td>1</td>
      <td>2/22</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1118</th>
      <td>139</td>
      <td>DTEO DAGORETI</td>
      <td>NAIROBI</td>
      <td>THE VEHICLE KNOCKED DOWN A PEDESTRIAN</td>
      <td>M</td>
      <td>PEDESTRIAN</td>
      <td>1</td>
      <td>2/22</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1119 rows × 9 columns</p>
</div>




```python
# Selecting only the COUNTY and NO. columns from the DataFrame
#assigning the resulting DataFrame to accidents_per_county.
accidents_per_county = accidents_kenya[['COUNTY','NO.']]
accidents_per_county
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>COUNTY</th>
      <th>NO.</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>MAKUENI</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>TAITA TAVETA</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>KILIFI</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NAKURU</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>MACHAKOS</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1114</th>
      <td>MIGORI</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1115</th>
      <td>KIRINYAGA</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1116</th>
      <td>NAIROBI</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1117</th>
      <td>MAKUENI</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1118</th>
      <td>NAIROBI</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>1119 rows × 2 columns</p>
</div>




```python
# Grouping the data by COUNTY column and sorting the values by NO. column in an a descending order.
accidents_per_county = accidents_per_county.groupby('COUNTY').count().sort_values(by=['NO.'], ascending=False).reset_index().head(10)
accidents_per_county

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>COUNTY</th>
      <th>NO.</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NAIROBI</td>
      <td>183</td>
    </tr>
    <tr>
      <th>1</th>
      <td>KIAMBU</td>
      <td>98</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NAKURU</td>
      <td>76</td>
    </tr>
    <tr>
      <th>3</th>
      <td>MAKUENI</td>
      <td>59</td>
    </tr>
    <tr>
      <th>4</th>
      <td>MACHAKOS</td>
      <td>50</td>
    </tr>
    <tr>
      <th>5</th>
      <td>KAKAMEGA</td>
      <td>40</td>
    </tr>
    <tr>
      <th>6</th>
      <td>NYERI</td>
      <td>38</td>
    </tr>
    <tr>
      <th>7</th>
      <td>KILIFI</td>
      <td>32</td>
    </tr>
    <tr>
      <th>8</th>
      <td>KAJIADO</td>
      <td>31</td>
    </tr>
    <tr>
      <th>9</th>
      <td>KISUMU</td>
      <td>30</td>
    </tr>
  </tbody>
</table>
</div>




```python
accidents_per_county.rename({'NO.': 'Number of Accidents','COUNTY':'County'}, axis=1, inplace=True)
accidents_per_county
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>County</th>
      <th>Number of Accidents</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NAIROBI</td>
      <td>183</td>
    </tr>
    <tr>
      <th>1</th>
      <td>KIAMBU</td>
      <td>98</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NAKURU</td>
      <td>76</td>
    </tr>
    <tr>
      <th>3</th>
      <td>MAKUENI</td>
      <td>59</td>
    </tr>
    <tr>
      <th>4</th>
      <td>MACHAKOS</td>
      <td>50</td>
    </tr>
    <tr>
      <th>5</th>
      <td>KAKAMEGA</td>
      <td>40</td>
    </tr>
    <tr>
      <th>6</th>
      <td>NYERI</td>
      <td>38</td>
    </tr>
    <tr>
      <th>7</th>
      <td>KILIFI</td>
      <td>32</td>
    </tr>
    <tr>
      <th>8</th>
      <td>KAJIADO</td>
      <td>31</td>
    </tr>
    <tr>
      <th>9</th>
      <td>KISUMU</td>
      <td>30</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Selecting only the COUNTY and VICTIM columns from the DataFrame
#assigning the resulting DataFrame to victims_per_county.

victims_per_county = accidents_kenya[['COUNTY','VICTIM']]
victims_per_county
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>COUNTY</th>
      <th>VICTIM</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>MAKUENI</td>
      <td>M/CYCLIST</td>
    </tr>
    <tr>
      <th>1</th>
      <td>TAITA TAVETA</td>
      <td>M/CYCLIST</td>
    </tr>
    <tr>
      <th>2</th>
      <td>KILIFI</td>
      <td>M/CYCLIST</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NAKURU</td>
      <td>PEDESTRIAN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>MACHAKOS</td>
      <td>PASSENGER</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1114</th>
      <td>MIGORI</td>
      <td>PEDESTRIAN</td>
    </tr>
    <tr>
      <th>1115</th>
      <td>KIRINYAGA</td>
      <td>RIDER AND P/PASSENGER</td>
    </tr>
    <tr>
      <th>1116</th>
      <td>NAIROBI</td>
      <td>PEDESTRIAN</td>
    </tr>
    <tr>
      <th>1117</th>
      <td>MAKUENI</td>
      <td>RIDER</td>
    </tr>
    <tr>
      <th>1118</th>
      <td>NAIROBI</td>
      <td>PEDESTRIAN</td>
    </tr>
  </tbody>
</table>
<p>1119 rows × 2 columns</p>
</div>




```python
#Grouping the data by VICTIM column and sorting the values by NO. column in an a descending order.
victims_per_county = victims_per_county.groupby('VICTIM').count().sort_values(by=['COUNTY'], ascending=False).reset_index().head(10)
victims_per_county

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>VICTIM</th>
      <th>COUNTY</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>PEDESTRIAN</td>
      <td>448</td>
    </tr>
    <tr>
      <th>1</th>
      <td>M/CYCLIST</td>
      <td>201</td>
    </tr>
    <tr>
      <th>2</th>
      <td>PASSENGER</td>
      <td>139</td>
    </tr>
    <tr>
      <th>3</th>
      <td>DRIVER</td>
      <td>115</td>
    </tr>
    <tr>
      <th>4</th>
      <td>P/PASSENGER</td>
      <td>75</td>
    </tr>
    <tr>
      <th>5</th>
      <td>P/CYCLIST</td>
      <td>21</td>
    </tr>
    <tr>
      <th>6</th>
      <td>RIDER</td>
      <td>21</td>
    </tr>
    <tr>
      <th>7</th>
      <td>PASSENGERS</td>
      <td>20</td>
    </tr>
    <tr>
      <th>8</th>
      <td>PEDAL CYCLIST</td>
      <td>6</td>
    </tr>
    <tr>
      <th>9</th>
      <td>RIDER &amp; P/PASSENGER</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>



Pedestrians,passengers and motor cyclists are the most vulnerable; they account for over 80% of the deaths.

### Data Visualization


```python
plt.figure(figsize=(12,6))
bar = sns.barplot(x="County",y="Number of Accidents",data=accidents_per_county)
bar.set_title("Road Accidents Per County: 2021,August",fontsize=16,weight='bold')
bar.set_xlabel('County',fontsize = 14, )
bar.set_ylabel('Number of Accidents',fontsize = 14)

plt.show()
```


    
![png](output_13_0.png)
    


Human mistakes, particularly with respect to drivers and pedestrians, is the main accident cause in Kenyan roads, while drivers have been blamed for careless or even drunken driving, pedestrians have been known to spurn traffic rules by crossing the streets at non-assigned points and disrespecting the traffic lights.

Road traffic crashes exert a huge burden on Kenya's economy and health care services. Current interventions are sporadic, uncoordinated and ineffective. Over three thousand people are killed annually on Kenyan roads. A four-fold increase in road fatalities has been experienced over the last 30 years. More than 75% of road traffic casualties are economically productive young adults. Pedestrians and passengers are the most vulnerable; they account for 80% of the deaths. Buses and matatus are the vehicles most frequently involved in fatal crashes.

Nairobi County is the leading in the number of fatal crushes accounting for over 170 cases per month on average,followed by Kiambu and Nakuru, according to Waweru Fidelis' dataset as recorded on https://www.kaggle.com/waawerufidelis/accidents-kenya.

Road safety interventions have not made any measurable impact in reducing the numbers, rates and consequences of road crashes. Despite the marked increase in road crashes in Kenya, little effort has been made to develop and implement effective interventions.


```python

```
