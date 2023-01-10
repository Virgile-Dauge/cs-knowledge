


# ReLU 
Applying a ReLU activation to a linear unit means the output becomes `max(0, w * x + b)`

# Sigmoid Activation
The cross-entropy and accuracy functions both require probabilities as inputs, meaning, numbers from 0 to 1. To covert the real-valued outputs produced by a dense layer into probabilities, we attach a new kind of activation function, the **sigmoid activation**.
![[FYbRvJo.png|The sigmoid function maps real numbers into the interval \[0,1\].]]

The sigmoid function maps real numbers into the interval [0,1]

To get the final class prediction, we define a _threshold_ probability. Typically this will be 0.5, so that rounding will give us the correct class: below 0.5 means the class with label 0 and 0.5 or above means the class with label 1. A 0.5 threshold is what Keras uses by default with its [accuracy metric](https://www.tensorflow.org/api_docs/python/tf/keras/metrics/BinaryAccuracy).

```python
model = keras.Sequential([
	# ...
	layers.Dense(1, activation='sigmoid'),
	# ...
])
```