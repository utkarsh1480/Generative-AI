
## Measuring Similarity Between Vectors
```
1: Eucledian Similarity
2: Dot Produce
3: cosine Similarity
```
## How Vector Embeddings work
<img width="1340" height="620" alt="Screenshot 2026-09-27 at 10 37 11 PM" src="https://github.com/user-attachments/assets/02aa0a80-8ec1-4bb9-8e58-cb47f4a09869" />

### Rag pipeline with VectorEmbedding
```
User Query
    ↓
Embedding Model
    ↓
Query Vector
    ↓
Euclidean Distance
    ↓
Compare with document vectors
    ↓
Sort by smallest distance
    ↓
Top-K Chunks
    ↓
LLM
    ↓
Answer
```
