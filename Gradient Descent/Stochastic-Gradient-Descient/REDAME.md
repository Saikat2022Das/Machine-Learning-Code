# Stochastic Gradient Descent:
  - Here we update coefficients after one element. No need to wait for the full column.
  - In case of a non-convex function, we can use SGDRegresser.
  - Here we pick any data or row randomly, meaning stochastic way.
  - No store full data for calculating Gradient Descent, so no need very high machine.

# Disadvantage:
  - Due to random and fast convergence, sometimes it is still moving at optimal points.(That's why we used Learning Scheduler)
    
