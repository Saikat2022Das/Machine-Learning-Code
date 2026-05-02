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
    ![hypercube comparison]
    <img width="1350" height="766" alt="Image" src="https://github.com/user-attachments/assets/e5da9efa-cdb8-442f-bd82-90b8de99e155" />

    #### Basic Example — 4 Classes

      ```python
      from sklearn.datasets import make_classification
      
      X, y = make_classification(
          n_samples=200,
          n_features=5,
          n_classes=4,          # 4 classes
          n_informative=4,      # must be >= n_classes - 1
          n_clusters_per_class=1,
          random_state=42
      )
      ```
      
    #### The Rules When Increasing `n_classes`
      
    #### Rule 1 — `n_informative` must be enough
      
      ```python
      n_informative >= n_classes - 1
      ```
      
      So if `n_classes=4`, you need at least `n_informative=3`.
      
    #### Rule 2 — `n_informative` must be ≤ `n_features`
      
      ```python
      n_informative <= n_features
      ```
      
    #### Rule 3 — Total features must add up correctly
      
      ```python
      n_informative + n_redundant + n_repeated <= n_features
      ```

## Steps to Get a Direct CSV Link from GitHub

---

### Step 1 — Upload your CSV to GitHub
1. Go to your repository on GitHub
2. Click **Add file** → **Upload files**
3. Upload your `.csv` file and click **Commit changes**

---

### Step 2 — Open the CSV file
Click on the CSV file in your repository to open it

---

### Step 3 — Click "Raw" button
You will see a **Raw** button at the top right of the file viewer — click it

```
https://raw.githubusercontent.com/username/repo-name/main/filename.csv
```

> This is the direct link you need. The key is `raw.githubusercontent.com` — not the normal GitHub URL.

---

### ❌ Wrong URL (normal GitHub page)
```
https://github.com/username/repo-name/blob/main/filename.csv
```

### ✅ Correct URL (raw link)
```
https://raw.githubusercontent.com/username/repo-name/main/filename.csv
```

---

### Step 4 — Use it in pandas

```python
import pandas as pd

url = "https://raw.githubusercontent.com/username/repo-name/main/filename.csv"
df = pd.read_csv(url)

print(df.head())
```
    
     
