## **Code1 - Setup**
**Target**
1.  Set up the skeleton with Relu, BatchNorm, GAP etc

**Results**
1.  Parameters - 6280
2.  Best training accuracy- 99.56%
3.  Best test accuracy - 99.33%

**Analysis**
1. Model is over-fitting
2. Variations in test set are not learned from training set. Can use augmentations to improve test accuracy.


## **Code2**
**Target**
1.  Added augmentations (random-rotate) to simulate complexities in test set. 

**Results**
1.  Parameters - 6280
2.  Best training accuracy- 99.17%
3.  Best test accuracy - 99.33%

**Analysis**
1. Model is under-fitting, but the test accuracy is closer to 99.40% due to random-rotate augmentation.
2. Active changes can be made to weights by reducing batch size. 


## **Code 3**
**Target**
1. Decreased the batch size from 128 to 64.

**Results**
1.  Parameters - 6280
2.  Best training accuracy- 99.22%
3.  Best test accuracy - 99.45%

**Analysis**
1. Model is still under-fitting
2. Test accuracy crosses 99.40%, but once. Need to vary learning rate for converging to a local minimum.


## **Code 4**
**Target**
1. Added LR scheduler for varying learning rate to converge the model to a local minimum.

**Results**
1.  Parameters - 6280
2.  Best training accuracy- 99.14%
3.  Best test accuracy - 99.40% 

**Analysis**
1. Reached the desired accuracy at 10th, 11th epochs as model converges to local minimum.
