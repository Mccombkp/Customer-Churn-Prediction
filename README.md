# Customer Churn Prediction

The data from below is from an AB test on whether a hypothetical, contractual TV company should offer a 7 day premium free trial for 7 days, as opposed to their current 24 hours premium trial. After the end of the trial period, those who have not cancelled, start their billing cycle and pay for the premium.

This company wants to know which policy would result in a higher customer LTV after 6 months. 

The data we have only goes to the beginning of March 2020, so we need to get a little creative on predicting 6 month LTV.

Fortunately, [Peter Fader and Bruce Hardie](http://brucehardie.com/papers/037/BdW_JIM_2018-01-10_rev.pdf) have shown the usefulness of using a Beta Discrete Weibull model to forecast retention.

My analysis is an example of how this model can be implemented using Python.

```python

import pandas as pd
import numpy as np
from pandasql import sqldf
DATA_PATH = 'https://raw.githubusercontent.com/Truebill/DS2_Challenge/master/tb_datascience_challenge2.csv'

df = pd.read_csv('TV_company_AB.csv')

df['total_premium_time'] = pd.to_datetime(df['premium_cancellation_date']) - pd.to_datetime(df['premium_signup_date'])
df.loc[(df['premium_signup_date'].notnull()), 'signup'] = 1
df.loc[(df['premium_signup_date'].isnull()), 'signup'] = 0

print('duplicated IDs: ' + str(df['user_id'].duplicated().sum()))
print('')
df.head()
```
