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
  - ### Linear Classification Dataset:
    ```python
      from sklearn.datasets import make_classification

      X, y = make_classification(
          n_samples = 100      # 100 rows.
          n_features = 3       # 3 columns.
          n_informative = 2    # Among 3 columns, only 2 are importatnt for finding classes, target.
          n_classes = 2        # Binary classification data like yes/no.
          random_state = 41    # Make reproducibility.
          n_clusters_per_class = 1    # Each class will have 1 cluster of data points in feature space.
          hypercube = True/False  # When True, cluster centers are placed at the vertices of a hypercube. Setting it to False places cluster centers randomly in feature space, making the distribution less structured.
          class_sep = 10  # Controls the separation between classes.
    )
    ```


    #### Hypercube Comparison
    ![hypercube comparison](<img width="1350" height="766" alt="Image" src="https://github.com/user-attachments/assets/e5da9efa-cdb8-442f-bd82-90b8de99e155" />)
    
     
