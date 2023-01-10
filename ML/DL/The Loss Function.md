The **loss function** measures the disparity between the the target's true value and the value the model predicts.

Different problems call for different loss functions.

A common loss function for regression problems is the **mean absolute error** or **MAE**. For each prediction `y_pred`, MAE measures the disparity from the true target `y_true` by an absolute difference `abs(y_true - y_pred)`

![[VDcvkZN.png]]

Besides MAE, other loss functions you might see for regression problems are the **mean-squared error (MSE)** or the **Huber loss** (both available in Keras).

During training, the model will use the loss function as a guide for finding the correct values of its weights (lower loss is better). In other words, the loss function tells the network its objective.

