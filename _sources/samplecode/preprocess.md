## label encoding
```python
from sklearn import preprocessing

le = preprocessing.LabelEncoder()
df_train['Location'] = le.fit_transform(df_train.Location)
df_test['Location'] = le.transform(df_test.Location)
```