## Here I uploaded all the small test datasets
  - Which anyone can use for practice purposes.
  - Like ML Practice
      - from sklearn.datasets import load_diabetes
   
  - Here is the Diagnosis dataset:
      - "https://raw.githubusercontent.com/gscdit/Breast-Cancer-Detection/refs/heads/master/data.csv"
      - Here, **df.columns**, then you can see id, Unnamed 32, these two are dropped. How **df.drop(columns=['id', 'Unnamed 32'], inplace=True)**
   
  - Linear Dataset:
      - from sklearn.datasets import make_regression
       X, y = make_regression(
               n_samples = 100 # Number of Rows.
               n_features = 10 # Num of Columns
               n_informativ = 3 # 3 Important columns here.
               n_targets = 1 # Output Column
               noise = 0.2,
               random_state = 42
           )
     
