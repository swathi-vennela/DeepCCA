# DeepCCA
Multi-view representation learning with DCCA

## Representation Learning 
This involves extracting features from the unlabeled input data by training a neural network. So that, we can learn good representations for the unlabeled data, and then use these representations to solve the supervised learning task. Modelling the input data in this way, helps in “understanding” the input data and making the further supervised learning task easier.

This makes the machine learning task easier:
○ Fewer examples will be needed for the prediction/classification task if relevant aspects of the input are already modeled.
○ Rich abstract representation of the data can make the prediction task simpler to be modeled. 

## Correlated Representations with CCA
Say, X1 is the first view of the data and, X2 is the second view of the data, CCA tries to learn linear mappings f1 and f2, such that, the correlation between f1(X1) and f2(X2) is maximized. By learning such correlated representations, we can:
1. Partially reconstruct information in the other view during the test time.
2. Remove noise that is uncorrelated across views.

## Deep CCA
To learn non-linear mappings of two views that are maximally correlated. 

![DeepCCA](https://www.researchgate.net/profile/K-Livescu/publication/255482849/figure/fig1/AS:669442673475591@1536618979256/A-schematic-of-deep-CCA-consisting-of-two-deep-networks-learned-so-that-the-output.png)

In this model, we take the two views, X1 and X2 of the data, then, each view is passed through a network with stacked non-linear layers, to get non-linear transformations of the two views, which are f1(X1), f2(X2).
Now, we perform CCA on the top of this. i.e., finding representations of f1(X1) and f2(X2) that are maximally correlated.
If the weights of the two networks are given by W1 and W2,
In the training time, we tune the two networks to learn the weights W1 and W2, that maximize the CCA objective.

## Implementation of DCCA on Noisy MNIST 
As discussed in the [On Deep Multi-view Representation Learning](http://proceedings.mlr.press/v37/wangb15.pdf), a noisy version of MNIST dataset is generated. <br><br>
<b>Optimizer used</b> : Adam <br>
<b> Activation Function </b> : Sigmoid <br> 
<b> Classifier </b> : SVM <br>
<b> Accuracy on test data </b> : 96.64% 

## Application 
This model can be applied on speech data. In speech data the two views being Acoustic view and Articulatory view. DCCA Acoustic features can model articulatory phenomena, improving the classifier performance. <br><br>
Do check out the Wisconsin XRMB database to explore more about this.
