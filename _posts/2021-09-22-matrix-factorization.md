---
layout: post
title:  "Matrix Factorization in Recommendation System"
author: gniliy
categories: [ ml ]
description: "Matrix Factorization in Recommendation System"
toc: false
---

[Recommendation system](https://developers.google.com/machine-learning/recommendation/overview/) consists of three major components: candidate generation, scoring and ranking.

Two common [candidate generation](https://developers.google.com/machine-learning/recommendation/overview/candidate-generation) approaches:
* content-based filtering
* collaborative filtering


Matrix Factorization is a typical model to learn the user and item embeddings: [Colab](https://colab.research.google.com/github/google/eng-edu/blob/main/ml/recommendation-systems/recommendation-systems.ipynb?utm_source=ss-recommendation-systems&utm_campaign=colab-external&utm_medium=referral&utm_content=recommendation-systems&hl=en#scrollTo=k0IFBGCx8_im).

A few notes:
* UMAP or t-SNE is helpful for visualization.
* Similarity metrics DOT vs cosine: the diff comes from the **norm**. The model tends to recommend popular movies. This can be explained by the fact that in matrix factorization models, the norm of the embedding is often correlated with popularity (popular movies have a larger norm), which makes it more likely to recommend more popular items. However, you may observe that some niche movies (ones with few ratings) have a high norm, leading to spurious recommendations. This can happen if the embedding of that movie happens to be initialized with a high norm. Then, because the movie has few ratings, it is infrequently updated, and can keep its high norm. This will be alleviated by using regularization.

This [article](https://datascience.stackexchange.com/questions/26902/how-exactly-does-matrix-factorization-help-with-collaborative-filtering?rq=1) gives brief explanation of MF. And this [QnA](https://datascience.stackexchange.com/questions/54576/how-does-recommendation-by-matrix-factorization-deal-with-new-movies-users-for) talks about the limitation of the MF method: what happens when it's **new, unseen user/movie**.

```
For instance it could initially recommend the most popular items (D) for new users,
then start recommending similar items to the ones he initially liked and finally 
when the user has rated enough items start looking for users with similar tastes.
```

Runtime serving [tutorial](https://developers.google.com/machine-learning/recommendation/dnn/retrieval)
