# Implementation-of-SVM-For-Spam-Mail-Detection

## AIM:
To write a program to implement the SVM For Spam Mail Detection.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Data Loading and Preparation:
Detect file encoding using chardet and load the CSV file with the correct
encoding using pandas .
Check for missing values and extract features ( v1 ) and labels ( v2 ) from the
dataset.
2. Data Splitting:
Split the data into training and testing sets using train_test_split .
3. Feature Extraction:
 Convert text data into numerical features using CountVectorizer .
4. Model Training and Evaluation:
Train an SVM model ( SVC ) on the transformed training data and predict
results on the test set.
Evaluate the model's performance using accuracy score from
sklearn.metrics .


## Program:
```
/*
Program to implement the SVM For Spam Mail Detection..
Developed by: SRIRAM B
RegisterNumber:  212223040203

import chardet
import pandas as pd
file = 'spam.csv'
with open(file, 'rb') as rawdata:
    result = chardet.detect(rawdata.read(100000))
data = pd.read_csv(file, encoding=result['encoding'])
data.head()
data.info()
data.isnull().sum()
x = data["v2"].values # Features (text)
y = data["v1"].values # Labels ("ham"/"spam")
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
y = le.fit_transform(y) # Encode labels (ham=0, spam=1)
from sklearn.model_selection import train_test_split
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.2, random_state=0)
from sklearn.feature_extraction.text import CountVectorizer
cv = CountVectorizer()
x_train = cv.fit_transform(x_train)
x_test = cv.transform(x_test)
from sklearn.svm import SVC
svc = SVC()
svc.fit(x_train, y_train)
y_pred = svc.predict(x_test)
from sklearn import metrics
accuracy = metrics.accuracy_score(y_test, y_pred)
print(f"Accuracy: {accuracy}")

*/
```

## Output:
![SVM For Spam Mail Detection](sam.png)
```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 5572 entries, 0 to 5571
Data columns (total 5 columns):
# Column Non-Null Count Dtype
--- ------ -------------- -----
0 v1 5572 non-null object
1 v2 5572 non-null object
2 Unnamed: 2 50 non-null object
3 Unnamed: 3 12 non-null object
4 Unnamed: 4 6 non-null object
dtypes: object(5)
memory usage: 217.8+ KB
Accuracy: 0.9766816143497757
```

## Result:
Thus the program to implement the SVM For Spam Mail Detection is written and verified using python programming.
