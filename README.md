# customer-segmentation

📌 CUSTOMER SEGMENTATION PROJECT — README.md
Customer Segmentation Using K‑Means Clustering
This project performs unsupervised customer segmentation using the popular Mall Customers dataset. The goal is to identify distinct customer groups based on purchasing behavior and demographic attributes, enabling targeted marketing strategies and data‑driven decision‑making.

📊 Dataset Overview
The dataset contains the following fields:

CustomerID – Unique identifier

Genre – Male/Female

Age

Annual Income (k$)

Spending Score (1–100)

For clustering, non‑informative fields (CustomerID, Genre) were removed.

🧹 Data Preprocessing
✔ Feature Selection
python
X = df.drop(['CustomerID', 'Genre'], axis=1)
✔ Standardization
K‑Means is distance‑based, so features were scaled using StandardScaler:

python
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
🧠 Modeling Approach
1. K‑Means Clustering
Number of clusters: 5

Random state: 42

Cluster labels added back to the dataset

python
kmeans = KMeans(n_clusters=5, random_state=42)
df['Cluster'] = kmeans.fit_predict(X_scaled)
🎨 Dimensionality Reduction & Visualization
t‑SNE Visualization
t‑SNE captures nonlinear relationships and produces a 2‑D representation of clusters.

python
tsne = TSNE(n_components=2, random_state=42)
df['TSNE1'], df['TSNE2'] = X_tsne[:, 0], X_tsne[:, 1]
PCA Visualization
PCA provides a linear projection of the data into 2 components.

python
pca = PCA(n_components=2)
df['PCA1'], df['PCA2'] = X_pca[:, 0], X_pca[:, 1]
Both visualizations show clear separation between clusters.

📈 Visual Outputs
t‑SNE Cluster Plot
Shows nonlinear structure

Highlights natural grouping patterns

PCA Cluster Plot
Shows variance‑based separation

Useful for understanding feature influence

📑 Cluster Profiling
Cluster profiling was performed using:

python
cluster_profile = df.groupby('Cluster').mean(numeric_only=True)
This reveals how clusters differ in:

Age

Annual Income

Spending Score

These insights can be used to create customer personas, such as:

High‑income, high‑spending customers

Young, low‑income, high‑spending customers

Older, moderate‑income, low‑spending customers

📌 Key Insights
Customers naturally form 5 distinct behavioral groups

Spending Score and Annual Income are strong drivers of segmentation

t‑SNE reveals clearer separation than PCA

Segments can be used for targeted marketing, loyalty programs, and personalized offers

📁 Repository Structure
Code
customer-segmentation/
│
├── README.md                # Project documentation
├── Mall_Customers.csv       # Dataset
└── customer_segmentation.py # Full clustering pipeline
🚀 Technologies Used
Python

Pandas

NumPy

Scikit‑Learn

Matplotlib

Seaborn

t‑SNE

PCA

📬 Contact
Toba Olorunsogo  
Data Analyst & Data Engineer
Winnipeg, MB
GitHub: @sogotobz
