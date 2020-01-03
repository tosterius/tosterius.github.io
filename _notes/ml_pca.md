---
layout: note
title: Singular Value Decomposition (SVD). Principal Component Analysis (PCA).
category: ML
index: 6
headline:
picture:
---

### I. SVD

Let $$A_{[m \times n]}$$ be a data matrix with $$m$$ rows (documents or examples) and $$n$$ columns (terms or features).
SVD represents an input matrix as a product of three matrices (it is always possible to do for real matrix):
\\[
\begin{equation}
A_{[m \times n]} = U_{[m \times r]} \Sigma_{[r \times r]} V_{[n \times r]}^T,
\end{equation}
\\]
where

- $$U_{[m \times r]}$$  is the matrix of left singular vectors, $$r$$ is the number of _latent factors_
- $$\Sigma_{[r \times r]}$$ is diagonal matrix of the singular values. Also $$r$$ is the rank of matrix $$A$$
- $$V_{[n \times r]}^T$$ is the matrix of right singular vectors

All three matrices are unique. $$U$$ and $$V$$ are column orthonormal. Entities of $$\Sigma$$ matrix are
positive and sorted in decreasing order.

![svd_0]({{ site.baseurl }}/assets/img/notes/svd_0.png)

#### Math explanation
Let $$\mathbf{v}_0$$ and $$\mathbf{v}_1$$ be orthogonal vectors in some two-dimensional vector space $$S$$. We know that any two orthogonal vectors 
form a basis in two-dimensional space. Linear operator $$L$$ maps $$S$$ to $$Q$$:
\\[
\begin{split}
L \mathbf{v}_1 &= \mathbf{u}_1 \sigma_1\\ \;\;
L \mathbf{v}_2 &= \mathbf{u}_2 \sigma_2 
\end{split} \tag{1}\label{eq1}
\\]
where $$\mathbf{u}_1$$ and $$\mathbf{u}_2$$ are the unit vectors in $$Q$$.
And $$\sigma_1$$ and $$\sigma_2$$ are the lengths of the new vectors in space $$Q$$.

Any vector $$\mathbf{x}$$ can be written as:
\\[
\begin{equation}
\mathbf{x} = (\mathbf{x} \cdot \mathbf{v}_1) \mathbf{v}_1 + (\mathbf{x} \cdot \mathbf{v}_2), \mathbf{v}_2 \tag{2}\label{eq2}
\end{equation}
\\]
where $$\mathbf{x} \cdot \mathbf{v}$$ is just a projection $$\mathbf{x}$$ on to $$\mathbf{v}$$.

Multiplying both sides by $$M$$ rewrite the previous equation:
\\[
\begin{equation}
L \mathbf{x} = (\mathbf{x} \cdot \mathbf{v}_1) L \mathbf{v}_1 + (\mathbf{x} \cdot \mathbf{v}_2) L \mathbf{v}_2
\end{equation}
\\]
\\[
\begin{equation}
L \mathbf{x} = (\mathbf{x} \cdot \mathbf{v}_1) \mathbf{u}_1 \sigma_1 + (\mathbf{x} \cdot \mathbf{v}_2) \mathbf{u}_2 \sigma_2
\end{equation}
\\]
\\[
\begin{equation}
L \mathbf{x} = \mathbf{u}_1 \sigma_1 \mathbf{v}_1^{\top} \mathbf{x} + \mathbf{u}_2 \sigma_2 \mathbf{v}_2^{\top} \mathbf{x} \tag{3}\label{eq3}
\end{equation}
\\]
In the last equation we use the option $$\mathbf{x} \cdot \mathbf{v}_1 = \mathbf{x}^{\top} \mathbf{v}_1 = \mathbf{v}_1^{\top} \mathbf{x}$$.

Dividing the equation $$\ref{eq3}$$ by $$\mathbf{x}$$, we get
\\[
\begin{equation}
L = \mathbf{u}_1 \sigma_1 \mathbf{v}_1 + \mathbf{u}_2 \sigma_2 \mathbf{v}_2 \tag{4}\label{eq4}
\end{equation}
\\]

#### Sample

<br>
#### Links