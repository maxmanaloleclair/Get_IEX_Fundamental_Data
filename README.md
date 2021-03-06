# Dowloading Historical IEX Fundamental Data for Analysis



A python project that demonstrates how to download IEX cloud data. Further projects will demonstrate how to analyze the data. 

  - Construct the url needed to extract IEX Cloud Data
  - Query Income Statement, Balance Sheet, and Cash Flow data even if records are missing
  - Download to CSV

# Key Features

  - Dynamically read and save JSON data to a dataframe, even annual if or quarterly reports are missing from IEX's dataset
 
  
# Steps

  - Register for [IEX Cloud](https://iexcloud.io/). The documentation for the API can be found [here](https://iexcloud.io/docs/api/). Note, a paid subscription is required for real data. 
  - Select tickers
  - Choose quarterly or annual data
  - Dowload data to CSV


If you want to test out the code, without paying for data, simply create a IEX cloud account and, change your settings to *sandbox testing * and adjust the API key accordingly. 



### Installation



```sh
pip install pandas
```

Import libraries

```sh
import pandas as pd
import os
```

### Steps

1) Set API Key. *You must use the sandbox api key to run the following code. This will allow you to test the feature without paying for IEX cloud premium data. 
```sh
token = 'Tpk_####aaaa#####aaaaa' 
```
2) Select any number of tickers and store in a list. 
```sh
tickers = ['MMM',
'AAPL',
'BA',
'CAT',
'DOW',
'GS',
'DIS']
```
3) Have the user choose which statement they are interested in analyzing. 

```sh
# Get input on statement type

statement_input = input('Which financial statement would you like to download. Please type either "income", "balance sheet", or "cash flow" \n\n')
if statement_input == 'income':
    statement_type = 'income'
if statement_input == 'balance sheet':
    statement_type = 'balance-sheet'
if statement_input == 'cash flow':
    statement_type = 'cash-flow'
    
# Get input on time period preference

a_or_q = input('Would you like annual or quarterly data. Please type either "annual" or "quarter"\n\n')
if a_or_q == 'annual':
    time_periods = 5
elif a_or_q == 'quarter':
    time_periods = 12 

```

Now you are ready to check out the rest of the code. The for loops that make up the bulk of the [code](https://github.com/maxmanaloleclair/Get_IEX_Fundamental_Data/blob/master/IEX%20Fundamental%20Data.ipynb), address the following issues:
   - Not all companies/tickers you select will have the same number of filings. Therefore, constructing the JSON URL and dataframe can not be looped through without iterrows. 
 - Statement data is stored in dictionaries within the JSON data. See the example below.

    | Ticker | README |
    | ------ | -------------------------------|
    | MMM | {'reportDate': '2019-09-26', 'fiscalDate': '2019-09-25', 'currency': 'USD','currentCash': 5601194501,'shortTermInvestments': None,'receivables': 13124947688, 'inventory': 1706643347, 'otherCurrentAssets': 1002026188,'currentAssets': 24300140861, 'longTermInvestments': 3368672438, 'propertyPlantEquipment': 32919501919, 'goodwill': 82754155898, 'intangibleAssets': 24105219314, 'otherAssets': 32945312127,'totalAssets': 195163570169,'accountsPayable': 14239033126,'currentLongTermDebt': 8993552148, 'otherCurrentLiabilities': 8890690430,'totalCurrentLiabilities': 32706996812, 'longTermDebt': 38955455233,'otherLiabilities': 9309880181, 'minorityInterest': 474558734,'totalLiabilities': 94222282915,'commonStock': 1845942405,'retainedEarnings': 44118898231,'treasuryStock': 3324025,'capitalSurplus': None,'shareholderEquity': 93147196380,'netTangibleAssets': -99038010007}] |


### Todos

 - Write more Tests
 - Check if code works for other IEX cloud data

License
----

MIT



