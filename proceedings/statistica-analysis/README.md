# Statistical analysis of participants
The following are relevant columns names on the ADM files.

## Jupyter notebook
``` 
cd $HOME/repositories/2022-echocardiography-proceedings/proceedings/statistica-analysis
conda activate echo-paper-ve
jupyter notebook
```

## Demographic datafiles 
The following shows colums of potential variables to be considered and cross-related with the US echo datasets. 

### `adm_anonymised.csv`
ADMDTC: Day of admission   
ICUDTC: Date  
ICUTIME: Time   
TRANSFERANOTHERHOSP: Maybe not!  
ANOTHERADMDTC: ?  
SMOKERDAY: ciggarres consmption per month  
WEIGHT  
HEGITH  

* RELATED TO DISEASES 
HYPERTENSION  
ANGINA  
MYOCARDIAL  
CONGESTIVEGRADE13  
ANAEMIA  
CONGESTIVEGRADE4  
PERIPHERAL  
CEREBROVASCULAR  
CHRONIC  
SEVERE  
CONNECTIVE  
PEPTICULCER   
MILDLIVER  
MODERATELIVER  
HEMIPLEGIA  
MODERATEKIDNEY  
DIABETES  
DIABETESCHRONIC  
DEMENTIA  
METASTATIC  
AIDS  
ANYMALIGNANCY  
SMOKER  
ELECTIVESURGERY  
SMOKERDAY  
IMMUNOCOMPROMISED  
COMORBIDITIESOTHER: Contains info in Vienamise    

* RELATED TO BLOOD TEST
HAEMOGLOBIN  
PLAT  
WCC  
BILIRUBIN  
NA  
K  
CREATININE  
TNT  
ALBUMIN  
LACTATE  
PH  
HBA1C  
PT  
APTT
HCT  
* POINTCARE
* LABORATORY
* entry
* enteredtime

### `adm_den_sep_anonymised.csv`
* LOCATION
DATEOFILLNESS: the first day when patients felt symptoms  
SHOCKONSETDTC: date when the have low blood pressuare!  
SHOCKONSETTIME: time when the have low blood pressuare!  

SYSBP: systolic blood pressure  
DIABP: diastolic blood pressure  
HR: Heart rate  
VASOPRESSORS:  
VASOPRESSORSNAME:  

TEMP: Temperature  
URINE: urine ouput  
RESPIRATORYDISTRESS:  
RESP: Respiratory Rate (breads per minute)  
OXYGENREQUIREMENT: require oxigen via mechanical ventilation  
MAXFIO2: Oxygen parameters  
LOWESTSPO2: Oxygen parameters  
LOWESTPAO2: Oxygen parameters  
CPAP_BIPAP: BIPAP requirements  
INTUBATED: needs tubes?  
GCS: Glasgow Coma Scale  

SEDATION:  
