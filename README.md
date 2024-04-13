## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
import pandas as pd
 df=pd.read_csv("/content/Encoding Data.csv")
 df

![316296378-eca0e23d-6ea3-4685-ad3e-3a3c688afce4](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/0fd340b6-5737-4791-a97e-d297c5a6733a)

from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])

![316296336-6f0fce59-7852-489d-a76f-db5988a45a3b](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/6e279d97-3fbb-42ac-896b-dec2cc923721)

df['bo2']=e1.fit_transform(df[["ord_2"]])
df
![316295056-84e9360b-9728-444d-bbe3-f7480e9633f6](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/db489211-8aaf-4ea7-ae06-45f411ffd099)

df['bo2']=e1.fit_transform(df[["ord_2"]])
df

![316295116-addbdb92-ff8a-41f3-af9e-bd97ac6800a2](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/74df712e-88e9-4cb8-a145-d773a660845c)

le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc

![316295165-1c7de496-371e-4a21-a189-7ed70ecc2900](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/779b9d82-4b58-4f11-9d7e-9f83f75fd3ac)

from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
df2=pd.concat([df2,enc],axis=1)
df2

![316295256-a8c5038b-2814-4b1d-8f85-c27b292c04d4](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/f60d1edc-ed5e-4589-8b43-e0c25c110f89)

pd.get_dummies(df2,columns=["nom_0"])

![316295310-797cb3cf-cc31-4c39-ba12-af1d740bbbed](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/354c5537-214f-4881-a4e1-c1b12ef92e10)

pip install --upgrade category_encoders

![316295375-eba5c171-3e23-483f-b4ed-6f4c47b5e89b](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/3bf0666a-c87a-4a8f-9fb7-b3dab9b91a72)

from category_encoders import BinaryEncoder
df=pd.read_csv("/content/data.csv")
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
fb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb

![316295450-9b983cb5-c712-49d8-bcd8-817ca7f56947](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/509342f8-36b1-45a6-8170-3224526303b7)

from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc["City"],y=cc["Target"])
cc=pd.concat([cc,new],axis=1)
cc

![316295534-0d2e7e51-9cb4-4530-a56d-39d1435d0249](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/89913742-f70f-407c-8d8b-d42053e2c3b3)

import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("/content/Data_to_Transform.csv")
df

![316295585-f71a4dd5-6389-4fb9-a209-81064b1d878f](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/16f33a63-f758-4d4c-930c-7ee2767a00bf)

df.skew()

![316295623-3e30db2a-11cd-4980-a53d-87e495cdba2d](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/7ca831df-fb26-4871-998b-a07a961382be)

np.log(df["Highly Positive Skew"])

![316295660-ea34c360-81a5-4760-bc9e-2c6a9d07be6c](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/08dbdd70-2876-4246-943d-7e55fa880c9d)

np.reciprocal(df["Moderate Positive Skew"])

![316295703-790eadf6-e770-4874-943c-ddfb7bca5113](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/b9638d29-a902-4aa9-83c2-8e65258e1890)

np.sqrt(df["Highly Positive Skew"])

![316295749-7e2ab48c-7321-477e-81e4-ba3d6b132bf5](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/60fde50c-f025-4a85-956a-74984361cc59)

np.square(df["Highly Positive Skew"])

![316295806-bcda767c-4193-4548-89ae-8ba49be8a323](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/c09d500e-4015-4787-a958-179e4ba0d372)

df["Highly Positive Skew_boxcox"],parameters=stats.boxcox(df["Highly Positive Skew"]) df

![316295883-7632047a-430d-4b18-8bab-abc86a475a5a](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/261816c5-bc3b-4e77-b07c-217a770748da)

df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Moderate Negative Skew"])
df.skew()

![316295945-90edf1a6-0480-49e3-9fe6-7ac276d2acf3](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/54daba97-11ad-4ec4-90d7-dd4d178d7b9f)

df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
df.skew()

![316295988-af78ba87-bd09-43e8-a612-406cad9d7686](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/893a714e-aa68-4a70-b285-fc5f79de8c13)

import matplotlib.pyplot as plt import seaborn as sns import statsmodels.api as sm import scipy.stats as stats

sm.qqplot(df["Moderate Negative Skew"],line='45')

plt.show()

![316296082-b72a5319-b492-4c91-981e-15bf8d38c539](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/d5c409b0-9bba-44ea-b2ba-07157f1f395d)

sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')

![316296150-9c011486-2fd5-4752-b434-702ecc5bebdc](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/328be47a-e30c-43e1-a8d7-57ae76404533)

from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)

df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])

sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()

![316296228-880ace95-7dd1-4732-941d-e007439a6fc5](https://github.com/kanimozhipannerselvam/EXNO-3-DS/assets/119476060/5367de50-8b03-432c-935e-e333b4598ace)



# RESULT:
    Hence performing Feature Encoding and Transformation process is Successful.
       
