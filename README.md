# EXNO:4-DS
# AIM:
To read the given data and perform Feature Scaling and Feature Selection process and save the
data to a file.

# ALGORITHM:
STEP 1:Read the given Data.

STEP 2:Clean the Data Set using Data Cleaning Process.

STEP 3:Apply Feature Scaling for the feature in the data set.

STEP 4:Apply Feature Selection for the feature in the data set.

STEP 5:Save the data to the file.

# FEATURE SCALING:
1. Standard Scaler: It is also called Z-score normalization. It calculates the z-score of each value and replaces the value with the calculated Z-score. The features are then rescaled with x̄ =0 and σ=1

2. MinMaxScaler: It is also referred to as Normalization. The features are scaled between 0 and 1. Here, the mean value remains same as in Standardization, that is,0.

3. Maximum absolute scaling: Maximum absolute scaling scales the data to its maximum value; that is,it divides every observation by the maximum value of the variable.The result of the preceding transformation is a distribution in which the values vary approximately within the range of -1 to 1.

4. RobustScaler: RobustScaler transforms the feature vector by subtracting the median and then dividing by the interquartile range (75% value — 25% value).

# FEATURE SELECTION:
Feature selection is to find the best set of features that allows one to build useful models. Selecting the best features helps the model to perform well.

The feature selection techniques used are:

1.Filter Method

2.Wrapper Method

3.Embedded Method

# CODING AND OUTPUT:

```
import pandas as pd
from scipy import stats import numpy as np
df=pd.read_csv("bmi.csv")
df

```

<img width="711" height="704" alt="image" src="https://github.com/user-attachments/assets/6512230e-1071-47b1-b5c3-6f9870b91c5a" />

```
max_vals = np.max(np.abs(df[['Height', 'Weight']]), axis=0)
max_vals

```
<img width="1115" height="174" alt="image" src="https://github.com/user-attachments/assets/a0efd6da-dc1f-4a35-a888-34830c4ed787" />

```
from sklearn.preprocessing import StandardScaler
df=pd.read_csv("bmi.csv")
df.head()

```
<img width="1120" height="418" alt="image" src="https://github.com/user-attachments/assets/5885c1ca-d248-4d5d-b4fa-e9081a3fcb3a" />

```
from sklearn.preprocessing import StandardScaler
import pandas as pd
df=pd.read_csv("bmi.csv")
sc=StandardScaler()
df[['Height','Weight']]=sc.fit_transform(df[['Height','Weight']])
df

```

<img width="1137" height="699" alt="image" src="https://github.com/user-attachments/assets/839e1c54-f5a7-4ecd-95a4-6ea2233611b9" />

```
df.head(10)

```

<img width="1155" height="534" alt="image" src="https://github.com/user-attachments/assets/00a9172d-6571-491a-9969-8728d9939b52" />

```
from sklearn.preprocessing import MinMaxScaler
scaler=MinMaxScaler()
df[['Height','Weight']]=scaler.fit_transform(df1[['Height','Weight']])
df.head(10)

```

<img width="1111" height="560" alt="image" src="https://github.com/user-attachments/assets/284e3518-a1d1-45a0-9e39-103dccc02a99" />

```
from sklearn.preprocessing import MaxAbsScaler
scaler = MaxAbsScaler()
df=pd.read_csv("bmi.csv")
df.head()

```

<img width="1119" height="395" alt="image" src="https://github.com/user-attachments/assets/907f60cd-3f27-470f-9728-3a989dac488e" />

```
df[['Height','Weight']]=scaler.fit_transform(df[['Height','Weight']])
df

```

<img width="1110" height="636" alt="image" src="https://github.com/user-attachments/assets/801195e1-84da-41d9-a133-dfc26a5b3671" />

```
from sklearn.preprocessing import RobustScaler
scaler = RobustScaler()
df[['Height','Weight']]=scaler.fit_transform(df3[['Height','Weight']])
df.head()

```

<img width="1113" height="373" alt="image" src="https://github.com/user-attachments/assets/aaf8d7a8-82ed-444b-832c-4dd1dd1800dc" />

```
df=pd.read_csv("income(1) (1).csv")
df.info()

```

<img width="1112" height="643" alt="image" src="https://github.com/user-attachments/assets/5ec22925-c7cd-45b1-b33b-76a147655c27" />

```
categorical_columns = ['JobType', 'EdType', 'maritalstatus', 'occupation', 'relationship']
df[categorical_columns] = df[categorical_columns].astype('category')
df[categorical_columns]

```

<img width="1122" height="774" alt="image" src="https://github.com/user-attachments/assets/178f4c6f-5b2d-4f0f-aaee-a47feaf7ac11" />

```
df[categorical_columns] = df[categorical_columns].astype('category')
df[categorical_columns] = df[categorical_columns].apply(lambda x: x.cat.codes)
df[categorical_columns]

```

<img width="996" height="637" alt="image" src="https://github.com/user-attachments/assets/6304ff9d-f72d-473a-8d52-1531213b0d01" />

```
X = df.drop(columns=['SalStat'])
y = df['SalStat']
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
from sklearn.ensemble import RandomForestClassifier
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)
rf = RandomForestClassifier(n_estimators=100, random_state=42)
rf.fit(X_train, y_train)
rf

```

<img width="1011" height="391" alt="image" src="https://github.com/user-attachments/assets/32baf18c-55ae-4885-95c7-deb21cbe2ba1" />

```
df=pd.read_csv("income(1) (1).csv")
df.info()

```

<img width="962" height="576" alt="image" src="https://github.com/user-attachments/assets/5e591d93-f87a-41f6-a6e0-5f52e5c97162" />

```
import pandas as pd
from sklearn.feature_selection import SelectKBest, chi2, f_classif
categorical_columns = ['JobType', 'EdType', 'maritalstatus', 'occupation', 'relationship
df[categorical_columns] = df[categorical_columns].astype('category')
df[categorical_columns]

```

<img width="974" height="730" alt="image" src="https://github.com/user-attachments/assets/2b3c5d8c-aaf3-4e25-b8bc-980384190b7d" />

```
pip install skfeature-chappers

```

<img width="992" height="652" alt="image" src="https://github.com/user-attachments/assets/2d5d3186-e856-475a-a5d8-5ef00386e61e" />

```
df[categorical_columns] = df[categorical_columns].apply(lambda x: x.cat.codes)
df[categorical_columns]

```


<img width="960" height="534" alt="image" src="https://github.com/user-attachments/assets/11986001-3212-401a-bba0-6c129325d331" />

```
X = df.drop(columns=['SalStat'])
y = df['SalStat'] k_chi2 = 6
selector_chi2 = SelectKBest(score_func=chi2, k=k_chi2)
X_chi2 = selector_chi2.fit_transform(X, y)
selected_features_chi2 = X.columns[selector_chi2.get_support()]
print("Selected features using chi-square test:")
print(selected_features_chi2)

```

<img width="962" height="301" alt="image" src="https://github.com/user-attachments/assets/58466237-a882-4dce-af9a-1a961bf74995" />

```
import pandas as pd
from sklearn.feature_selection import SelectKBest, chi2, f_classif
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
selected_features = ['age', 'maritalstatus', 'relationship', 'capitalgain', 'capitalloss']
X = df[selected_features]
y = df['SalStat']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)
rf = RandomForestClassifier(n_estimators=100, random_state=42)
rf.fit(X_train, y_train)

```

<img width="972" height="387" alt="image" src="https://github.com/user-attachments/assets/0d7eb0e7-ba43-421c-836d-00c1e1a38e1b" />

```
y_pred = rf.predict(X_test)
from sklearn.metrics import accuracy_score
accuracy = accuracy_score(y_test, y_pred)
print(f"Model accuracy using selected features: {accuracy}")

```

<img width="958" height="189" alt="image" src="https://github.com/user-attachments/assets/247b2287-9cd0-4063-916b-e72b30f1ddb4" />

```
import numpy as np
import pandas as pd
from skfeature.function.similarity_based import fisher_score
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
categorical_columns = [ 'JobType', 'EdType', 'maritalstatus', 'occupation', 'relationshi df[categorical_columns] = df[categorical_columns].astype('category')
df[categorical_columns] = df[categorical_columns].apply(lambda x: x.cat.codes)
df[categorical_columns]

```

<img width="980" height="696" alt="image" src="https://github.com/user-attachments/assets/b5ad404e-bff9-4b7b-9b0e-4e9095cbd822" />

```
X = df.drop(columns=['SalStat'])
y = df['SalStat']
k_anova = 5
selector_anova = SelectKBest(score_func=f_classif,k=k_anova)
X_anova = selector_anova.fit_transform(X, y)
selected_features_anova = X.columns[selector_anova.get_support()]
print("\nSelected features using ANOVA:")
print(selected_features_anova)

```

<img width="975" height="308" alt="image" src="https://github.com/user-attachments/assets/50d1d892-e8a6-4f5f-b661-87a12cd62f1e" />

```
import pandas as pd
from sklearn.feature_selection import RFE
from sklearn.linear_model import LogisticRegression
df=pd.read_csv("income(1) (1).csv")
categorical_columns = [ 'JobType', 'EdType', 'maritalstatus', 'occupation', 'relationship']
df[categorical_columns] = df[categorical_columns].astype('category')
df[categorical_columns] = df[categorical_columns].apply(lambda x: x.cat.codes)
df[categorical_columns]

```

<img width="983" height="660" alt="image" src="https://github.com/user-attachments/assets/8502f1cd-d945-4def-b407-7c020fcbc604" />

```
X = df.drop(columns=['SalStat'])
y = df['SalStat']
logreg = LogisticRegression()
n_features_to_select =6
rfe = RFE(estimator=logreg, n_features_to_select=n_features_to_select)
rfe.fit(X, y)

```

<img width="591" height="881" alt="image" src="https://github.com/user-attachments/assets/72a50c88-54bc-488d-9735-e1f7def22875" />

<img width="605" height="254" alt="image" src="https://github.com/user-attachments/assets/7a37b278-17ff-4a01-83c0-a6d85b3e9816" />


# RESULT:

Thus, Feature Scaling and Feature Selection were successfully performed on the given dataset, and the important features were selected for further analysis.
