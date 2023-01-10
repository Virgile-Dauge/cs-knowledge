

**Accuracy** is one of the many metrics in use for measuring success on a **classification problem**. Accuracy is the ratio of correct predictions to total predictions: `accuracy = number_correct / total`

The problem with accuracy (and most other classification metrics) is that it can't be used as a loss function. SGD needs a loss function that changes smoothly, but accuracy, being a ratio of counts, changes in "jumps". So, we have to choose a substitute to act as the loss function. This substitute is the _cross-entropy_ function.

For classification, what we want instead is a distance between _probabilities_, and this is what cross-entropy provides. **Cross-entropy** is a sort of measure for the distance from one probability distribution to another

```python
model.compile(
    optimizer='adam',
    loss='binary_crossentropy',
    metrics=['binary_accuracy'],
)
```