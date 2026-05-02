## Here I uploaded all the small test datasets
  - Which anyone can use for practice purposes.
  - Like ML Practice
      - from sklearn.datasets import load_diabetes
   
  - Here is the Diagnosis dataset:
      - "https://raw.githubusercontent.com/gscdit/Breast-Cancer-Detection/refs/heads/master/data.csv"
      - Here, **df.columns**, then you can see id, Unnamed 32, these two are dropped. How **df.drop(columns=['id', 'Unnamed 32'], inplace=True)**
   
  - ### Linear Dataset:
    ```python
      from sklearn.datasets import make_regression
      
      X, y = make_regression(
          n_samples=100,      # Number of rows
          n_features=10,      # Number of columns
          n_informative=3,    # Important features
          n_targets=1,        # Output column
          noise=0.2,
          random_state=42
      )
      ```
    <img width="1350" height="766" alt="Image" src="https://github.com/user-attachments/assets/e5da9efa-cdb8-442f-bd82-90b8de99e155" />
     
