# CryptoClustering

In this challenge, you'll use your knowledge of Python and unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes.

---

## Prepare the Data

- Use the `StandardScaler()` module from `scikit-learn` to normalize the data from the CSV file.
- Create a DataFrame with the scaled data and set the `"coin_id"` index from the original DataFrame as the index for the new DataFrame.

---

## Find the Best Value for `k` Using the Scaled DataFrame

Use the elbow method to find the best value for `k`:

1. Create a list with the number of `k` values from 1 to 11.
2. Create an empty list to store the inertia values.
3. Create a for-loop to compute the inertia for each value of `k`.
4. Create a dictionary with the data to plot the elbow curve.
5. Plot a line chart with all the inertia values to visually identify the optimal `k`.

**Notebook Question:**  
> What is the best value for `k`?

---

## Cluster Cryptocurrencies with K-Means (Scaled Data)

Steps:

- Initialize the K-Means model with the best value for `k`.
- Fit the model using the scaled DataFrame.
- Predict clusters using the model.
- Create a copy of the scaled DataFrame and add a `"CryptoCluster"` column.
- Create a scatter plot with `hvPlot`:
  - `x`: `"price_change_percentage_24h"`
  - `y`: `"price_change_percentage_7d"`
  - Color by cluster label
  - Hover info: `"coin_id"`

---

## Optimize Clusters with Principal Component Analysis (PCA)

- Apply PCA to reduce the scaled DataFrame to **three principal components**.
- Retrieve the **explained variance** of each component.

**Notebook Question:**  
> What is the total explained variance of the three components?

- Create a new DataFrame with the PCA data, indexed by `"coin_id"`.

---

## Find the Best Value for `k` Using the PCA DataFrame

Repeat the elbow method using the PCA-transformed data:

1. Loop from `k=1` to `k=11`, compute inertia for each.
2. Create a DataFrame for plotting.
3. Plot the elbow curve for PCA.

**Notebook Questions:**  
> What is the best value for `k` using PCA?  
> Does it differ from the original scaled DataFrame?

---

## Cluster Cryptocurrencies with K-Means (PCA Data)

- Initialize and fit the K-Means model using the PCA DataFrame.
- Predict and store clusters.
- Create a scatter plot:
  - `x`: `"PC1"`
  - `y`: `"PC2"`
  - Color by cluster label
  - Hover info: `"coin_id"`

**Notebook Question:**  
> What is the impact of using fewer features to cluster the data using K-Means?
