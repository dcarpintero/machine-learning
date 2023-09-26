# Embeddings

- An embedding is a vector (list) of floating point numbers representing data such as words, sentences, documents, images or audio. Said numerical representation captures the context, hierarchy and similarity of the data. They can be used for downstream tasks such as classification, clustering, outlier detection and semantic search.

- The use of transformer neural networks has enabled to compute embeddings as the average of the  context-aware representations of each token (sub-word), which enables the algorithm to work with novel words and misspelt words.

- In practice a transformer is trained with a process called constractive learning, where pairs of similar sentences are moved together and dissimilar sentences' embeddings apart (typically randomly selected).

## Why are they useful?

- **Dimensionality Reduction**: Embeddings often reduce the dimensionality of the data, making it more manageable.

- **Contextual Relations**: They capture complex relationships between objects, like similarity, hierarchy, and context.

- **Efficiency**: In a high-dimensional space, it becomes easier to perform arithmetic operations that capture semantic meanings (e.g., king - man + woman = queen, in word vectors).

- **Search**: They improve the effectiveness of search algorithms by enabling better matching and ranking based on contextual similarity rather than mere textual or categorical matching.

## Applicability 

- When embedded data is represented as numerical vectors, the spatial distance (and sometimes angles) between two vectors measures their relatedness. Small distances suggest high relatedness and large distances suggest low relatedness. 

This becomes relevant in:

- Search (where results are ranked by relevance to a query string);
- Clustering (where text strings are grouped by similarity);
- Recommendations (where items with related text strings are recommended);
- Anomaly detection (where outliers with little relatedness are identified);
- Diversity measurement (where similarity distributions are analyzed);
- Classification (where text strings are classified by their most similar label).

## Basic Methods to Infer Similarity

- **Dot Product**: measures the product of the magnitudes of two vectors and the cosine of the angle between them. It ranges from -∞ to ∞, where a positive value represents vectors that point in the same direction, 0 represents orthogonal vectors, and a negative value represents vectors that point in opposite directions.

- **Cosine Similarity**: measures the cosine of the angle between two vectors in a vector space. It ranges from -1 to 1, where 1 represents identical vectors, 0 represents orthogonal vectors, and -1 represents vectors that are diametrically opposed.

- **Euclidean Distance**: measures the straight-line distance between two vectors in a vector space. It ranges from 0 to infinity, where 0 represents identical vectors, and larger values represent increasingly dissimilar vectors.

## Dense Retrieval

In practice the set of embeddings is often too large for exhaustive search and its high dimensionality makes pruning difficult to find the nearest dataset embeddings. Therefore, it is common to create an index for the embedded dataset to improve search efficiency and/or use algorithms that perform approximate matches.

### Approximate Nearest-Neighbor Vector Search Algorithms

Only stores the vectors.

- [ScaNN: Efficient Vector Similarity Search](https://blog.research.google/2020/07/announcing-scann-efficient-vector.html) (Google). 
- [FAISS: Facebook AI Similarity Search](https://ai.meta.com/tools/faiss/) (Meta). 
- [Annoy: Approximate Nearest Neighbors](https://pypi.org/project/annoy/): It has the ability to use static files as indexes, such that indexes can be shared across processes (Spotify)

### Vector Databases

Stores vectors and texts.
Easier to update, no need to rebuild the index.
Allow filtering and more advanced queries.

- [Weaviate](https://weaviate.io/)
- [Pinecone](https://www.pinecone.io/)
- [Chroma](https://www.trychroma.com/)
- [Quadrant](https://qdrant.tech/)
- [Vespa](https://vespa.ai/)

