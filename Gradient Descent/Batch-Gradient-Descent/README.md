# Batch Gradient Descent
## Where we update our coefficient once we read the whole dataset. 
## If input column has 3 rows like: X1, X2, X3
## Three coefficients will be here, B1, B2, B3, and B0 for Bias.
## Update Coefficient: 
  - B1 = B1 - (learning rate)*slop with respective to B1.
  - B2 = B2 - (learning rate)*slop with respective to B2.
  - And so on ...

## Diesadvantage:
  - Each epoch updates all coefficients that need the whole data stored in RAM, which is a storage problem.
  - Time complexity is too high.
  - If higher-dimensional data, then the chances of getting stuck in a local minimum.

## Where should we use?
  - Small dataset.
  - 2D or 3D dataset, then we can use it.
