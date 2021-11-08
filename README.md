## DataFrame_Joins
##Creating a data frame and using Joins.

import numpy as pd
import pandas as pd
emp1= pd.DataFrame({'empid':['E90','E87'],
 'Name':['Asif','Basit']})
emp1
emp2= pd.DataFrame({'empid':['E22','E74','E90'],
 'Name':['Minil','Akash','Asif']})
emp2

address= pd.DataFrame({'empid':['E87','E22','E49'], 
 'City':['Mumbai','Banglore','Pune'] , 
 'State':['Maharashtra','Karnataka','Maharashtra']})
address

#concat
ad=pd.concat([emp1,emp2])
ad
ad.reset_index(drop=True)

#Check duplicates
ad1=ad[ad.duplicated()]
ad1
ad.drop_duplicates(keep='last',inplace=True)
ad

#Remove duplicates
ad.reset_index(drop=True,inplace=True)
ad

#Inner Join
empl=pd.merge(ad,address,on='empid',how='inner')
empl

#Left outer Joins
emp2=pd.merge(ad,address,on='empid',how='left')
emp2

#Right Outer Joins
emp3=pd.merge(ad,address,on='empid',how='right')
emp3

#Full outer Joins
emp4=pd.merge(ad,address,on='empid',how='outer')
emp4

sal = pd.DataFrame({'empid':['E87','E22','E74','E90','E49'],
 'salary':['$10,000','$30,000','$20,000','$60,000','$90,000']})
sal

emplooyes_details=pd.merge(sal,emp4,on='empid',how='inner')
emplooyes_details

exp = pd.DataFrame({'employee_id':['E87','E22','E74','E90','E49'],
 'experience':['5 years','3 years','7 years','2 years','10 years']})
exp

pd.merge(emplooyes_details,exp,left_on='empid',right_on='employee_id',how='inner')

pd.merge(emplooyes_details,exp,left_on='empid',right_on='employee_id',how='inner').drop('employee_id',axis=1)

#Save the dataframe
employee_details=pd.merge(emplooyes_details,exp,left_on=['empid'],right_on=['employee_id'],how='inner').drop('employee_id',axis=1)
employee_details

employee_details



