# Built in function (Python)


# __call__ 

This function allows to write **classes** where their **instances are functions**.
- Example 1:


```python
class Product:
    def __init__(self):
        print("Instance Created")

    # Defining __call__ method
    def __call__(self, a, b):
        print(a * b)

# Instance created
ans = Product()

# __call__ method will be called
ans(10, 20)
```

- Example 2:

```python
class Linear():
    def __init__(self):
        self.w = tf.Variable(tf.random.normal([1]), name='weight')
        self.b = tf.Variable(tf.random.normal([1]), name='bias')
        
    def __call__(self, inputs):
        return inputs * self.w + self.b

import tensorflow as tf
model= Linear()
model(3).numpy()

```
