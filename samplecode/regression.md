# Regression

## xgb
```python
import xgboost as xgb

params = {
    'objective': 'reg:squarederror',
    'random_state':42,
    'eval_metric': 'rmse',
    'verbosity': 0,
    'gpu_id':0,
    'tree_method':'gpu_hist',
    }
num_round = 1000

dtrain = xgb.DMatrix(X_train, label=y_train)
dvalid = xgb.DMatrix(X_valid, label=y_valid)

model = xgb.train(
	params, dtrain, num_round,
	early_stopping_rounds=100,
	verbose_eval = 100,
	evals=[(dtrain, 'train'), (dvalid, 'eval')])
```

## ligtgbm
```python
import lightgbm as lgb

params0 = {
    'objective': 'rmse',
	'seed': 42,
    'boosting_type': 'gbdt',
    'n_jobs':-1,
    'verbose': -1}

train_weights = 1 / np.square(y_train)
valid_weights = 1 / np.square(y_valid)
train_dataset = lgb.Dataset(x_train, y_train, weight = train_weights)
valid_dataset = lgb.Dataset(x_valid, y_valid, weight = valid_weights)
model = lgb.train(params = params,
					num_boost_round=1000,
					train_set = train_dataset,
					valid_sets = [train_dataset, val_dataset],
					verbose_eval = 50,
					early_stopping_rounds=50,
					feval = feval_rmspe)
```
