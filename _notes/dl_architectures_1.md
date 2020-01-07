---
layout: note
title: "Popular architectures"
category: DL
index: 2
headline: "Resnet, Inception"
picture: 
---

### Resnet
With the network depth increasing accuracy gets saturated and it is not a problem of overfitting, as it might first appear.
In simple words if we add some additional layers to pretraied network, new bigger network should work as good as the shallow or even better.
Resnets solve this problem, namely vanishing gradient problem.

![resnet_idea]({{ site.baseurl }}/assets/img/notes/resnet_idea.png)

Let us focus on a local neural network with desired mapping $$H(x)$$.
We let this network fit another mapping $$F(x) = H(x) - x$$. The original mapping is recast into $$F(x) + x$$.

Author's hyphothesis is that __it is easier to optimize this residual mapping $$F(x)$$ than to optimize the original unreferenced mapping $$H(s)$$.__

Formally building block (or _residual unit_) performs the following computation:

\\[
\begin{split}
&y_l = x_l + F(x_l, W_l) \\\\\\\\
&x_{l + 1} = f(y_l)
\end{split}
\tag{1}\label{eq1}
\\]

where $$f$$ is activation function, $$W_l$$ is weights matrix of the layer $$l$$.

We see that dimensions of $$x_l$$ and $$F$$ must be equal. If this is not the case we perform
linear projection $$A$$ which can be trainable or simply pad 0s to $$x_l$$.

\\[
\begin{equation}
y_l = Ax_l + F(x_l, W_l)
\end{equation}
\\]

Authors considered general form of the first equation:
\\[
\begin{equation}
y_l = h(x_l) + F(x_l, W_l)
\end{equation}
\\]
and they showed by experiments that the identity mapping is sufficient for addressing this problem.

##### Analysis
Let us take as activation function $$f(x) = ReLU(x)$$:
\\[
\begin{equation}
x_{l+1} = x_l + F(x_l, W_l)
\end{equation}
\\]

\\[
\begin{equation}
x_{L} = x_l + \sum_{i=l}^{i=L-1}F(x_i, W_i)
\end{equation}
\\]

Denoting loss functions as $$C$$, from the chain rule of backpropagation we get:
\\[
\begin{equation}
\frac{\partial C}{\partial x_l} = \frac{\partial C}{\partial x_L} \frac{\partial x_L}{\partial x_l}
\end{equation}
\\]

#### Inception


#### Links

1. [Deep Residual Learning for Image Recognition](https://arxiv.org/pdf/1512.03385.pdf)
2. [Identity Mappings in Deep Residual Networks](https://arxiv.org/pdf/1603.05027.pdf)