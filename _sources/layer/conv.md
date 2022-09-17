# Conv layer

## Conv出力の計算

- $W$: 画像の幅
- $P$: パディング
- $F$: フィルタサイズ
- $S$: ストライド
- $O$: 出力画像の幅

$$
O=\dfrac{W+2P-F}{S}+1
$$

### 例題
**Q. 高さ・幅・チャネル数=(224, 224, 3)の画像。パディングなし・ストライド1・フィルタ11x11でpoolingすると出力サイズは？**

$$O=\dfrac{224+2\times 0-11}{1}+1=224-11+1=214$$

入力のチャネル数に関係なく、poolingの出力チャネル数はフィルタの種類数になるので、答えは
214 x 214 x 1

**Q. (224, 224, 3)⇒[padding=0, stride=4, filter=(4,4)]⇒出力サイズは？**

$$\dfrac{224+2\times 0 - 4}{4}+1 = 220/4 + 1 = 56$$



## tensorflow

```python
import tensorflow as tf

tf.keras.layers.Conv2D(
    filters,
    kernel_size,
    strides=(1, 1),
    padding='valid',
    data_format=None,
    dilation_rate=(1, 1),
    groups=1,
    activation=None,
    use_bias=True,
    kernel_initializer='glorot_uniform',
    bias_initializer='zeros',
    kernel_regularizer=None,
    bias_regularizer=None,
    activity_regularizer=None,
    kernel_constraint=None,
    bias_constraint=None,
    **kwargs
)
```

## pytorch

```python
import torch

torch.nn.Conv2d(
    in_channels, 
    out_channels, 
    kernel_size, 
    stride=1, 
    padding=0, 
    dilation=1, 
    groups=1, 
    bias=True, 
    padding_mode='zeros', 
    device=None, 
    dtype=None)
```

## 1x1 畳み込み

GoogleNetの`Inception Module`で使われた。
周辺画素を畳み込まず、チャネル方向のみ畳み込む。

### 応用

- セマンティックセグメンテーションでの終盤の画素単位の識別器
- チャネル方向の次元削減

### 例題

```python
[[[1. 1.]
  [5. 7.]]

 [[2. 6.]
  [7. 3.]]

 [[1. 8.]
  [2. 2.]]]
```
に、1x1畳み込みを適用すると、結果はどうなるか？

```python
import numpy as np
import tensorflow as tf

x = np.array([
    [[1, 1], [5, 7]],
    [[2, 6], [7, 3]],
    [[1, 8], [2, 2]]
]).astype(np.float32)
# x.shape=>(3, 2, 2)

# channel lastにする
x = x.transpose(1,2,0)
# x.shape=>(2, 2, 3)

# add batch
x = np.expand_dims(x, 0)
# x.shape=>(1, 2, 2, 3)

# define 1x1 conv model
model = tf.keras.models.Sequential(
    tf.keras.layers.Conv2D(
        1, # filter
        1, # kernel
        input_shape=x.shape[1:],
        use_bias=False
        ),
)

model.get_weights()[0].shape
# => (1, 1, 3, 1)

weights = np.array([4, 4, 4]).astype(np.float32)
weights = np.expand_dims(weights, 0)
weights = np.expand_dims(weights, 0)
weights = np.expand_dims(weights, -1)
weights.shape
# => (1, 1, 3, 1)

model.set_weights([weights])

y = model(x)
# <tf.Tensor: shape=(1, 2, 2, 1), dtype=float32, numpy=
# array([[[[16.],
#          [60.]],
#
#         [[56.],
#          [48.]]]], dtype=float32)>

y = tf.squeeze(y, 0)
y = tf.squeeze(y, -1)
y
#<tf.Tensor: shape=(2, 2), dtype=float32, numpy=
#array([[16., 60.],
#       [56., 48.]], dtype=float32)>
```
