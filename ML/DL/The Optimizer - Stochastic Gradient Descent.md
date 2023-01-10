The optimizer is an algorithm that adjusts the weights to minimize the loss.

Virtually all of the optimization algorithms used in deep learning belong to a family called **stochastic gradient descent**.

They are iterative algorithms that train a network in steps. One **step** of training goes like this:

1.  Sample some training data and run it through the network to make predictions.
2.  Measure the loss between the predictions and the true values.
3.  Finally, adjust the weights in a direction that makes the loss smaller.

Then just do this over and over until the loss is as small as you like (or until it won't decrease any further.)
![[rFI1tIk.gif]]

Each iteration's sample of training data is called a **minibatch** (or often just "batch"), while a complete round of the training data is called an **epoch**. The number of epochs you train for is how many times the network will see each training example.

https://harjot-dadhwal.medium.com/math-behind-the-gradient-descent-algorithm-8d6137d92e9

**What's In a Name?**  
The **gradient** is a vector that tells us in what direction the weights need to go. More precisely, it tells us how to change the weights to make the loss change _fastest_. We call our process gradient **descent** because it uses the gradient to _descend_ the loss curve towards a minimum. **Stochastic** means "determined by chance." Our training is _stochastic_ because the minibatches are _random samples_ from the dataset. And that's why it's called SGD!