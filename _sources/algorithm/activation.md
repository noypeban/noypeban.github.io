# 活性化関数


## Sigmoid

$$
f(x) = \dfrac{1}{1+e^{-x}}
$$

$$
f'(x) = f(x)(1-f(x))
$$

```python
import numpy

def sigmoid(x):
  return 1.0/(1.0+np.exp(-x))
```

## ReLU

Rectified Linear Unit

$$
f(x) = \begin{cases}
0 & (x\leq 0) \\
x & (x>0)
\end{cases}
$$


$$
f(x)' = \begin{cases}
0 & (x\leq 0) \\
1 & (x>0)
\end{cases}
$$

```python 
def relu(x):
  return x*(x>0.0)
```

## Leaky ReLU 

$$ 
f(x) = \begin{cases}
\alpha x & x<0 \\
x & x \geq 0 
\end{cases}
$$

$$
f'(x) = \begin{cases}
\alpha & x<0\\
1 & x \geq 0 
\end{cases}
$$ 

```python 
import numpy 

def LeakyReLU(x, alpha=0.01):
  return np.where(x>=0.0, x, alpha * x)
```

## Softmax

$$ 
y_i = \dfrac{e^{x_i}}{\sum^n_{k=1} e^{x_k}} \quad(i = 1,2,\cdots ,n)
$$

$$ 
\dfrac{\partial y_i}{\partial x_j} = \begin{cases}
y_i(1-y_j) & i=j\\
-y_j y_i & i\neq j
\end{cases}
$$

```python
import numpy as np

def softmax(x):
  return np.exp(x) / np.sum(np.exp(x), axis=1, keepdims=True)
```

