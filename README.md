# Product Clustering and Topic Assignment

This project focuses on clustering products based on their titles and assigning relevant topics to each cluster. The approach involves advanced techniques in data preprocessing, embedding, dimensionality reduction, clustering, and topic modeling.

## Table of Contents
- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)
- [Project Details](#project-details)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Overview
The goal of this project is to cluster products into meaningful groups based on their titles and assign topics to each cluster. Initially, BERT embeddings with PCA and t-SNE were used for clustering, but this approach yielded noisy results. The strategy was improved by using SBERT for embeddings, UMAP for dimensionality reduction, and HDBSCAN for clustering, resulting in better-defined clusters. Topics are assigned to each cluster using Llama-3-8b with prompt engineering.

## Installation
To get started, clone this repository and install the necessary dependencies:

```bash
git clone https://github.com/your-username/product-clustering.git
cd product-clustering
pip install -r requirements.txt
```

## Usage
1. Place your CSV file containing product titles in the `data` directory.
2. Run the preprocessing and embedding script:
    ```bash
    python preprocess_and_embed.py --input data/products.csv --output data/embeddings.pkl
    ```
3. Perform dimensionality reduction and clustering:
    ```bash
    python cluster.py --input data/embeddings.pkl --output data/clusters.pkl
    ```
4. Assign topics to the clusters:
    ```bash
    python topic_assignment.py --input data/clusters.pkl --output data/topics.csv
    ```

## Project Details
### Process overview
- This project aims to cluster products based on their titles and assign meaningful topics to each cluster. Initially, the project utilized BERT embeddings with PCA and t-SNE for dimensionality reduction and DBSCAN for clustering. However, this approach resulted in noisy and poorly defined clusters. 

- To improve the results, the project shifted to using SBERT for embeddings, which are better aligned for Retrieval-Augmented Generation (RAG) systems often employed in economic chatbots. For dimensionality reduction, UMAP was used due to its ability to preserve both global and local data structures, outperforming t-SNE. HDBSCAN was chosen for clustering due to its robustness in handling noise and detecting clusters of varying densities.

- Llama-3-8b was used for topic assignment, with prompt engineering ensuring that clusters with similar concepts received the same topic. The result is a more coherent and accurate clustering and topic assignment process.
### Data Preprocessing
- Tokenization and cleaning of product titles.
- Embedding using SBERT for alignment with RAG systems often used in economic chatbots.

### Dimensionality Reduction
- UMAP is used to reduce dimensions while preserving global and local structures, outperforming t-SNE.

### Clustering
- HDBSCAN is chosen for its ability to handle noise and find clusters of varying density.

### Topic Assignment
- Topics are assigned using Llama-3-8b with prompt engineering to ensure clusters with similar concepts receive the same topic.

## Results
The project demonstrates improved clustering performance and topic coherence using the described methods. The UMAP and HDBSCAN combination, along with SBERT embeddings, significantly reduces noise and enhances cluster definition.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request for any improvements or additions.

## License
This project is licensed under the MIT License.
