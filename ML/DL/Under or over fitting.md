

If the gap between **loss** and **validation loss** curves is quite small, and the validation loss never increases, so it's more likely that the network is **underfitting** that overfitting. It would be worth experimenting with more capacity to see if that's the case.

If the **validation loss begins to rise very early, while the training loss continues to decrease**. This indicates that the network has begun to **overfit**. At this point, we would need to try something to prevent it, either by reducing the number of units or through a method like early stopping.

To avoid Underfitting or Overfitting, we may want to stop during the training.
![[eP0gppr.png]]
In Keras, we include early stopping in our training through a callback. A **callback** is just a function you want to run every so often while the network trains. The early stopping callback will run after every epoch. (Keras has [a variety of useful callbacks](https://www.tensorflow.org/api_docs/python/tf/keras/callbacks) pre-defined, but you can [define your own](https://www.tensorflow.org/api_docs/python/tf/keras/callbacks/LambdaCallback), too.)

```python
from tensorflow.keras.callbacks import EarlyStopping

early_stopping = EarlyStopping(
    min_delta=0.001, # minimium amount of change to count as an improvement
    patience=20, # how many epochs to wait before stopping
    restore_best_weights=True,
)
```


