# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
Data_set:
import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt


df = pd.read_csv('/content/drive/MyDrive/documents /Data_set (2).csv')
print(df.head(),"\n")

df.info()
print()

print(df.describe(),"\n")

df.isnull()
print(df.isnull().sum())
print()

df_fill_0 = df.fillna(0)
print(df_fill_0,"\n")

df_ffill = df.ffill()
print(df_ffill,"\n")

df_bfill = df.bfill()
print(df_bfill,"\n")

df['current_overall_rank'] = df['current_overall_rank'].fillna(df['current_overall_rank'].mean())
print(df,"\n")

df_dropna = df.dropna()
print(df_dropna,"\n")

sns.boxplot(x=df['current_overall_rank'])
plt.show()
print()

Q1 = df['current_overall_rank'].quantile(0.25)
Q3 = df['current_overall_rank'].quantile(0.75)
IQR = Q3 - Q1
print("IQR:", IQR,"\n")

outliers_iqr = df[
    (df['current_overall_rank'] < (Q1 - 1.5 * IQR)) |
    (df['current_overall_rank'] > (Q3 + 1.5 * IQR))
]
print(outliers_iqr,"\n")
ir_cleaned = df[
    ~((df['current_overall_rank'] < (Q1 - 1.5 * IQR)) |
      (df['current_overall_rank'] > (Q3 + 1.5 * IQR)))
]
print(ir_cleaned,"\n")

df_z = df['current_overall_rank']

z_scores = np.abs(stats.zscore(df_z))
print(z_scores,"\n")

threshold = 3
outliers_z = df_z[z_scores > threshold]
print("Outliers:",outliers_z,"\n")

df_z_cleaned = df_z[z_scores <= threshold]
print(df_z_cleaned,"\n")
<img width="740" height="433" alt="image" src="https://github.com/user-attachments/assets/3b3aab9d-77ce-4f68-9a57-d5f807d355e3" />
<img width="750" height="569" alt="image" src="https://github.com/user-attachments/assets/050b43a5-4d5e-49da-a9f5-44b7f212e7f8" />
<img width="647" height="540" alt="image" src="https://github.com/user-attachments/assets/d121baa3-c458-4e77-9db1-fe66e8a15fa4" />
<img width="553" height="394" alt="image" src="https://github.com/user-attachments/assets/480dc871-eaf4-4a67-9aa5-cd340d99f369" />

IRIS:
import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt
df = pd.read_csv('iris.csv')
print(df.head(),"\n")
df.info()
print()
print(df.describe(),"\n")
df.isnull()
print(df.isnull().sum())
print()
df_fill_0 = df.fillna(0)
print(df_fill_0,"\n")
df_ffill = df.ffill()
print(df_ffill,"\n")
df_bfill = df.bfill()
print(df_bfill,"\n")
df['sepal_length'] = df['sepal_length'].fillna(df['sepal_length'].mean())
print(df,"\n")
df_dropna = df.dropna()
print(df_dropna,"\n")
sns.boxplot(x=df['sepal_width'])
plt.show()
print()
Q1 = df['sepal_width'].quantile(0.25)
Q3 = df['sepal_width'].quantile(0.75)
IQR = Q3 - Q1
print("IQR:", IQR,"\n")
outliers_iqr = df[
(df['sepal_width'] < (Q1 - 1.5 * IQR)) |
(df['sepal_width'] > (Q3 + 1.5 * IQR))
]
print(outliers_iqr,"\n")
ir_cleaned = df[
~((df['sepal_width'] < (Q1 - 1.5 * IQR)) |
(df['sepal_width'] > (Q3 + 1.5 * IQR)))
]
print(ir_cleaned,"\n")
df_z = df['sepal_width']
z_scores = np.abs(stats.zscore(df_z))
print(z_scores,"\n")
threshold = 3
outliers_z = df_z[z_scores > threshold]
print("Outliers:",outliers_z,"\n")
df_z_cleaned = df_z[z_scores <= threshold]
print(df_z_cleaned,"\n")
<img width="678" height="560" alt="image" src="https://github.com/user-attachments/assets/f4fad729-17f2-45e4-98be-d0c250545d01" />
<img width="690" height="487" alt="image" src="https://github.com/user-attachments/assets/d4d2cd1e-0920-4ad8-8620-89fd5883fe9e" />
<img width="484" height="358" alt="image" src="https://github.com/user-attachments/assets/ad6ef559-01ec-4842-8fc0-b179772ca2e5" />

 LOANS:
import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt
df = pd.read_csv('Loan_data.csv')
print(df.head(),"\n")
df.info()
print()
print(df.describe(),"\n")
df.isnull()
print(df.isnull().sum())
print()
df_fill_0 = df.fillna(0)
print(df_fill_0,"\n")
df_ffill = df.ffill()
 print(df_ffill,"\n")
df_bfill = df.bfill()
print(df_bfill,"\n")
df['LoanAmount'] = df['LoanAmount'].fillna(df['LoanAmount'].mean())
print(df,"\n")
df_dropna = df.dropna()
print(df_dropna,"\n")
sns.boxplot(x=df['LoanAmount'])
plt.show()
print()
Q1 = df['LoanAmount'].quantile(0.25)
Q3 = df['LoanAmount'].quantile(0.75)
IQR = Q3 - Q1
print("IQR:", IQR,"\n")
outliers_iqr = df[
    (df['LoanAmount'] < (Q1 - 1.5 * IQR)) |
    (df['LoanAmount'] > (Q3 + 1.5 * IQR))
]
print(outliers_iqr,"\n")
ir_cleaned = df[
    ~((df['LoanAmount'] < (Q1 - 1.5 * IQR)) |
      (df['LoanAmount'] > (Q3 + 1.5 * IQR)))
]
print(ir_cleaned,"\n")
df_z = df['LoanAmount'].dropna()
z_scores = np.abs(stats.zscore(df_z))
print(z_scores,"\n")
threshold = 3
outliers_z = df_z[z_scores > threshold]
print("Outliers:",outliers_z,"\n")
     
df_z_cleaned = df_z[z_scores <= threshold]
print(df_z_cleaned,"\n")
<img width="792" height="649" alt="Screenshot 2026-02-11 210527" src="https://github.com/user-attachments/assets/b2083b41-f7df-44e7-b553-3ec498f9f0f1" />
<img width="793" height="585" alt="Screenshot 2026-02-11 210549" src="https://github.com/user-attachments/assets/8978b1f9-9780-4176-9e07-57a1e6a4bff4" />
<img width="830" height="594" alt="Screenshot 2026-02-11 210611" src="https://github.com/user-attachments/assets/6545c5e4-0a9f-491d-af4a-d1cc973279cd" />
<img width="836" height="700" alt="Screenshot 2026-02-11 210635" src="https://github.com/user-attachments/assets/f1d7f4fb-9be7-4e21-b597-db284e845307" />
<img width="546" height="557" alt="Screenshot 2026-02-11 210658" src="https://github.com/user-attachments/assets/0149b334-a5a7-4ab7-89b4-0ccdd98f1122" />

SAMPLIEDS:
import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt
df = pd.read_csv('SAMPLEIDS.csv')
print(df.head(),"\n")
df.info()
print()
print(df.describe(),"\n")
df.isnull()
print(df.isnull().sum())
print()
df_fill_0 = df.fillna(0)
print(df_fill_0,"\n")
df_ffill = df.ffill()
print(df_ffill,"\n")
df_bfill = df.bfill()
print(df_bfill,"\n")
df['TOTAL'] = df['TOTAL'].fillna(df['TOTAL'].mean())
print(df,"\n")
df_dropna = df.dropna()
print(df_dropna,"\n")
sns.boxplot(x=df['TOTAL'])
plt.show()
print()
Q1 = df['TOTAL'].quantile(0.25)
Q3 = df['TOTAL'].quantile(0.75)
IQR = Q3 - Q1
print("IQR:", IQR,"\n")
outliers_iqr = df[
(df['TOTAL'] < (Q1 - 1.5 * IQR)) |
(df['TOTAL'] > (Q3 + 1.5 * IQR))
]
print(outliers_iqr,"\n")
ir_cleaned = df[
~((df['TOTAL'] < (Q1 - 1.5 * IQR)) |
(df['TOTAL'] > (Q3 + 1.5 * IQR)))
]
print(ir_cleaned,"\n")
df_z = df['TOTAL'].dropna()
z_scores = np.abs(stats.zscore(df_z))
print(z_scores,"\n")
threshold = 3
outliers_z = df_z[z_scores > threshold]
print("Outliers:",outliers_z,"\n")
df_z_cleaned = df_z[z_scores <= threshold]
print(df_z_cleaned,"\n")
<img width="695" height="563" alt="image" src="https://github.com/user-attachments/assets/b7d42a20-e394-4398-aa70-b0789adcd5d6" />
<img width="772" height="749" alt="image" src="https://github.com/user-attachments/assets/836db396-1522-41f4-8e1a-9f1352edcc65" />
<img width="442" height="559" alt="image" src="https://github.com/user-attachments/assets/480f7c0a-692d-4930-9b30-3e2433b510da" />

HEIGHTS:
import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns
import matplotlib.pyplot as plt
df = pd.read_csv('heights.csv')
print(df.head(),"\n")
df.info()
print()
print(df.describe(),"\n")
df.isnull()
print(df.isnull().sum())
print()
df_fill_0 = df.fillna(0)
print(df_fill_0,"\n")
df_ffill = df.ffill()
print(df_ffill,"\n")
df_bfill = df.bfill()
print(df_bfill,"\n")
df['height'] = df['height'].fillna(df['height'].mean())
print(df,"\n")
df_dropna = df.dropna()
print(df_dropna,"\n")
sns.boxplot(x=df['height'])
plt.show()
print()
Q1 = df['height'].quantile(0.25)
Q3 = df['height'].quantile(0.75)
IQR = Q3 - Q1
print("IQR:", IQR,"\n")
outliers_iqr = df[
(df['height'] < (Q1 - 1.5 * IQR)) |
(df['height'] > (Q3 + 1.5 * IQR))
]
print(outliers_iqr,"\n")
ir_cleaned = df[
~((df['height'] < (Q1 - 1.5 * IQR)) |
(df['height'] > (Q3 + 1.5 * IQR)))
]
print(ir_cleaned,"\n")
df_z = df['height']
z_scores = np.abs(stats.zscore(df_z))
print(z_scores,"\n")
threshold = 3
outliers_z = df_z[z_scores > threshold]
print("Outliers:",outliers_z,"\n")
df_z_cleaned = df_z[z_scores <= threshold]
print(df_z_cleaned,"\n")
<img width="648" height="529" alt="image" src="https://github.com/user-attachments/assets/94a2532b-57aa-4e2d-ae07-9f251549825d" />
<img width="662" height="513" alt="image" src="https://github.com/user-attachments/assets/a20feccf-0b38-45c6-9e1d-1961324b31b6" />
<img width="320" height="394" alt="image" src="https://github.com/user-attachments/assets/ad9e4b32-af1c-42d2-b50a-484a7278ba05" />






# Result
          <<include your Result here>>
