# Embeddings

- An embedding is a vector (list) of floating point numbers representing text such as words, sentences and documents. 

- They capture the context, hierarchy and similarity of text strings. 

- The spatial distances (and sometimes angles) between these vectors represent semantic relations. Small distances suggest high relatedness and large distances suggest low relatedness. The methods to infer similarity include: 
    - dot product;
    - cosine similarity; 
    - euclidean distance.

- Embeddings are commonly used for:
    - Search (where results are ranked by relevance to a query string);
    - Clustering (where text strings are grouped by similarity);
    - Recommendations (where items with related text strings are recommended);
    - Anomaly detection (where outliers with little relatedness are identified);
    - Diversity measurement (where similarity distributions are analyzed);
    - Classification (where text strings are classified by their most similar label).