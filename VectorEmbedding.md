
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
But there is no universal Euclidean similarity formula. Different systems can transform distance differently.

## Euclidean distance in high-dimensional embeddings

For a 1536-dimensional embedding:
$$ d(A,B)= \sqrt{ (a_1-b_1)^2+ (a_2-b_2)^2+ ... + (a_{1536}-b_{1536})^2 } $$
So you're effectively measuring distance across 1536 coordinates simultaneously.
You cannot visualize the actual space easily, but the mathematics is the same.

A and B point in exactly the same direction. C also points in the same direction.
But Euclidean distance sees: $$ d(A,B)=\sqrt{2} $$
while: $$ d(A,C)=\sqrt{19602} $$
So Euclidean distance considers C much farther away, despite all three vectors having the same direction.
This reveals a major property: Euclidean distance cares about both direction and magnitude.

## Euclidean distance is sensitive to magnitude

## For normalized vectors, Euclidean distance and cosine similarity produce the same ranking.

Why can we do that?  Because square root is a monotonic function.

Why does this matter for vector search?
Imagine millions of vectors. Computing: sqrt(...)

```
for every candidate is unnecessary if your only goal is: Which vectors are closest? You can compare squared distances instead.
So if the embedding model's magnitude carries information that isn't relevant to semantic similarity, Euclidean can behave differently from cosine.
This is why you should not blindly choose Euclidean simply because it is mathematically simple.
The embedding model and how it was trained matter.
```
## When is Euclidean distance useful?
```
Euclidean distance makes sense when:

Absolute geometric position/magnitude in embedding space is meaningful.

It can work especially well when the embedding space is designed or normalized in a way compatible with L2 distance.

In a vector database, you can explicitly choose L2/Euclidean nearest-neighbor search.

Euclidean distance measures the straight-line distance between two embedding vectors.
It is calculated as the square root of the sum of squared differences across all dimensions.
In vector search, a smaller Euclidean distance means the vectors are geometrically closer.
It is sensitive to vector magnitude, so its behavior can differ from cosine similarity.
For normalized vectors, Euclidean distance and cosine similarity produce the same nearest-neighbor ranking."
```
